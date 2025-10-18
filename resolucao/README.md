## Google Colab (código) de resolução: https://colab.research.google.com/drive/19RtrcS1mf3BfwthSmMZOujQqx4Hylm8o?usp=sharing
---

# Formulação do Problema de Programação Linear - Jaisson Rações

- **Objetivo:** Maximizar o lucro total da safra, respeitando regras de agricultura, logística e produção de rações.

-----------

## Conjuntos

| Símbolo | Descrição                                                                                             |
| ------- | ----------------------------------------------------------------------------------------------------- |
| **F**   | Fazendas = {Maruim, Gaúcha, Campos Gerais, Pantanal, Cerrado, Capital}                                |
| **G**   | Grãos = {Milho, Soja, Sorgo, Trigo, Aveia, Girassol}                                                  |
| **L**   | Linhas de ração = {BC-G, BL-L, AV-P, EQ-M, OV-M, PA-PET, AQ-T}                                        |
| **P**   | Embalagens = {std, bb} (algumas linhas não têm bb)                                                    |
| **I**   | Ingredientes = {Milho, FareloSoja, Sorgo, FareloTrigo, Aveia, FareloGirassol, Calcário, Óleo, Premix} |
| **K**   | Tipos de caminhão = {pequeno, médio, grande}                                                          |


## Parâmetros

| Parâmetro | Descrição   |
| :-----: | ------------- |
| ------- | ------------- |
| ------- | ------------- |
| ------- | ------------- |


### Agricultura
| Parâmetro | Descrição   |
| :-----: | ------------- |
| **A<sub>f</sub>** | área da fazenda *f* (ha)   |
| **P<sub>f,g</sub><sup>adj</sup>** | produtividade ajustada (t/ha)   |
| **C<sub>g</sub><sup>sem</sup>**, **C<sub>g</sub><sup>man</sup>** | custos (R$/ha) |


### Logística
| Parâmetro | Descrição   |
| :-----: | ------------- |
| **D<sub>f</sub>** | distância (km, ida)  |
| **cap<sub>k</sub>** | capacidade (t/viagem)   |
| **c<sub>k</sub><sup>km</sup>**, **c<sub>k</sub><sup>fix</sup>** | custos (R$/km, R$/viagem) |
> Custo por viagem = `2 · Df · cₖᵏᵐ + cₖᶠⁱˣ`


### Rações
| Parâmetro | Descrição   |
| :-----: | ------------- |
| **price<sub>l,p</sub>** | preço (R$/item)   |
| **w<sub>l,p</sub>** | peso (kg/item)  |
| **c<sub>l,p</sub><sup>proc</sup>** | processo (R$/kg)  |
| **c<sub>l,p</sub><sup>pack</sup>** | embalagem (R$/item) |
| **Q<sub>l,p</sub><sup>max</sup>** | demanda máxima   |
| **P(l)** | embalagens disponíveis para *l* |

### Composição / compra / venda
| Parâmetro | Descrição   |
| :-----: | ------------- |
| **α<sub>i,l</sub>** | fração do ingrediente *i*   |
| **buy<sub>i</sub>**, **sell<sub>i</sub>** | preços (R$/t)   |
| **map(g)** | mapeamento grão → ingrediente |

### Políticas
| Parâmetro | Descrição   |
| :-----: | ------------- |
| **γ = 0.025** | mínimo de 2,5% por linha   |
| **h = 10** | mínimo 10 ha se plantado |

-----

## Variáveis

| Variável | Tipo | Significado |
|:-----------:|:-------:|-------------|
| **x<sub>f,g</sub>** | contínua | hectares de *g* plantados em *f* |
| **z<sub>f,g</sub>** | binária | 1 se o grão *g* é plantado em *f* |
| **y<sub>f,g,k</sub>** | inteira | viagens de caminhão *k* de *f* com *g* |
| **q<sub>l,p</sub>** | inteira | itens produzidos (linha *l*, embalagem *p*) |
| **m** | inteira | mínimo de itens por linha (2,5%) |
| **buyQty<sub>i</sub>**, **sellQty<sub>i</sub>**, **use<sub>i</sub>** | contínuas | compra, venda e uso (t) |
| **prod<sub>f,g</sub>**, **ship<sub>f,g</sub>** | contínuas | produção e embarque (t) |

-----

## Função Objetivo

$$\max \sum_{l,p} \text{price}_{l,p} q_{l,p} + \sum_{i} \text{sell}_{i} \text{sellQty}_{i} - \sum_{f,g} (C_g^{\text{sem}} + C_g^{\text{man}}) x_{f,g} - \sum_{f,g,k} (2D_f c_k^{\text{km}} + c_k^{\text{fix}}) y_{f,g,k} - \sum_{i} \text{buy}_{i} \text{buyQty}_{i} - \sum_{l,p} (c_{l,p}^{\text{proc}} w_{l,p} + c_{l,p}^{\text{pack}}) q_{l,p}$$

-----

## Restrições

---
### (R1) Uso total da área

$$\large \sum_g x_{f,g} = A_f \quad \forall f$$

---
### (R2) Plantio mínimo (10 ha se plantado)

$$\large x_{f,g} \ge 10z_{f,g}, \quad x_{f,g} \le A_f z_{f,g} \quad \forall f,g$$

---
### (R3) Produção e embarque

$$prod_{f,g} = P^{\text{adj}}_{f,g} x_{f,g}$$

$$ship_{f,g} = prod_{f,g} \quad \forall f,g$$

---
### (R4) Capacidade de transporte (viagens inteiras)

$$\large \sum_k cap_k y_{f,g,k} \ge ship_{f,g} \quad \forall f,g$$

---
### (R5) Balanço de ingredientes

$$\large \sum_{f:\text{map}(g)=i} ship_{f,g} + buyQty_i - sellQty_i = use_i \quad \forall i$$

---
### (R6) Consumo na produção

$$\large use_i = \sum_{l,p} \alpha_{l,i} \left(\frac{w_{l,p}}{1000}\right) q_{l,p} \quad \forall i$$

---
### (R7) Demanda máxima

$$\large 0 \le q_{l,p} \le Q^{\max}_{l,p} \quad \forall l,p$$

---
### (R8) Mínimo de 2,5% por linha (arredondado p/ cima)

$$\large m \ge 0.025 \sum_{l,p} q_{l,p}, \quad \sum_{p \in P(l)} q_{l,p} \ge m \quad \forall l$$

---
### (R9) Presença de todos os tamanhos

$$\large q_{l,p} \ge 1 \quad \forall l, p \in P(l)$$


---------
