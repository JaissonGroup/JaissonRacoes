# RESOLUCAO


# Formulação do Problema de Programação Linear - Jaisson Rações

> **Objetivo:** maximizar o lucro da safra respeitando regras de negócio de agricultura, logística e produção de rações.

---

## Conjuntos

- **Fazendas:** F = {Maruim, Gaúcha, Campos, Gerais, Pantanal, Cerrado, Capital}
- **Grãos:** G = {Milho, Soja, Sorgo, Trigo, Aveia, Girassol}
- **Linhas de ração:** L = {BC-G, BL-L, AV-P, EQ-M, OV-M, PA-PET, AQ-T}
- **Embalagens:** P = {std, bb} (padrão e big-bag; algumas linhas **não** têm `bb`)
- **Ingredientes:** I = {Milho, FareloSoja, Sorgo, FareloTrigo, Aveia, FareloGirassol, Calcário, Óleo, Premix}
- **Tipos de caminhão:** K = {pequeno, médio, grande}

---

## Parâmetros

### Agricultura / produção

- **A<sub>f</sub>**: área (ha) da fazenda f
- **P<sup>base</sup><sub>g</sub>**: produtividade padrão (t/ha) do grão g
- **P<sup>adj</sup><sub>f,g</sub>**: produtividade **ajustada** (t/ha) do grão g na fazenda f
- **C<sup>sem</sup><sub>g</sub>, C<sup>man</sup><sub>g</sub>**: custos (R$/ha) de semente e manutenção do grão g

### Distâncias e frota

- **D<sub>f</sub>**: distância (km, **ida**) da fazenda f até a fábrica
- **cap<sub>k</sub>**: capacidade do caminhão k (t/viagem)
- **c<sup>km</sup><sub>k</sub>**: custo variável por km (R$/km) do caminhão k
- **c<sup>fix</sup><sub>k</sub>**: custo fixo por viagem (R$) do caminhão k

  > **Prática comum:** custo variável por viagem = 2 × D<sub>f</sub> × c<sup>km</sup><sub>k</sub> (ida e volta)

### Rações (receita, processo, embalagem, demanda)

- **price<sub>l,p</sub>**: preço de venda por **item** (R$) da linha l na embalagem p
- **w<sub>l,p</sub>**: peso do item (kg)
- **c<sup>proc</sup><sub>l,p</sub>**: custo de **processo** (R$/kg)
- **c<sup>pack</sup><sub>l,p</sub>**: custo de **embalagem** (R$/item ou R$/bb)
- **Q<sup>max</sup><sub>l,p</sub>**: demanda máxima (itens)
- **P(l) ⊆ P**: embalagens **permitidas** para a linha l (ex.: P(EQ-M) = {std})

### Composição das rações

- **α<sub>l,i</sub>**: fração **em massa** do ingrediente i na linha l (ex.: 0,55 de milho em BC-G)

  > Mesma fórmula para `std` e `bb`; muda apenas o w<sub>l,p</sub>.

### Compra/venda de grãos (na fábrica)

- **buy<sub>i</sub>**: preço de **compra** (R$/t) do ingrediente i
- **sell<sub>i</sub>**: preço de **venda** (R$/t) do ingrediente i

### Mapeamento grão → ingrediente

- **map(g) ∈ I** (Milho→Milho; Soja→FareloSoja; Sorgo→Sorgo; Trigo→FareloTrigo; Aveia→Aveia; Girassol→FareloGirassol)

### Parâmetros de política

- **γ = 0.025**: participação mínima por **linha** (2,5%) **em itens**
- **h̲ = 10**: área mínima (ha) por grão **se** plantado em f  *(exige MILP para "se/então")*

---

## Variáveis de decisão

### Agricultura

- **x<sub>f,g</sub> ≥ 0**: hectares de g plantados em f
- **z<sub>f,g</sub> ∈ {0,1}** (MILP opcional): 1 se g é plantado em f (para impor mínimo de 10 ha)
- **Auxiliar:** prod<sub>f,g</sub> = P<sup>adj</sup><sub>f,g</sub> × x<sub>f,g</sub> (t) — produção de g em f

### Logística

- **y<sub>f,g,k</sub> ≥ 0**: número de **viagens** do tipo k levando g de f à fábrica
- **ship<sub>f,g</sub> ≥ 0**: toneladas de g embarcadas de f (pode ser eliminada via igualdade)

### Produção de ração

- **q<sub>l,p</sub> ≥ 0**: **itens** produzidos da linha l na embalagem p
- **Auxiliar:** Q<sub>tot</sub> = Σ<sub>l</sub> Σ<sub>p∈P(l)</sub> q<sub>l,p</sub>

### Balanço de ingredientes

- **buyQty<sub>i</sub> ≥ 0**: toneladas **compradas** do ingrediente i
- **sellQty<sub>i</sub> ≥ 0**: toneladas **vendidas** (excedente) do ingrediente i
- **use<sub>i</sub> ≥ 0**: toneladas **consumidas** do ingrediente i na produção

---

## Função Objetivo — **Maximizar Lucro**

```
max  [Receita de rações]
   + Σ_l Σ_{p∈P(l)} price_{l,p} × q_{l,p}
   
   + [Venda de excedentes]
   + Σ_i sell_i × sellQty_i
   
   - [Custo agrícola (R$/ha)]
   - Σ_{f,g} (C^sem_g + C^man_g) × x_{f,g}
   
   - [Frete (ida/volta) + fixo]
   - Σ_{f,g,k} (2 × D_f × c^km_k + c^fix_k) × y_{f,g,k}
   
   - [Compra de ingredientes]
   - Σ_i buy_i × buyQty_i
   
   - [Processo (R$/kg) + Embalagem (R$/item)]
   - Σ_l Σ_{p∈P(l)} (c^proc_{l,p} × w_{l,p} + c^pack_{l,p}) × q_{l,p}
```

> **Unidades:** c<sup>proc</sup> está em **R$/kg** (segundo os dados). Logo, o termo correto é c<sup>proc</sup><sub>l,p</sub> × w<sub>l,p</sub> × q<sub>l,p</sub>.  
> Se preferir modelar c<sup>proc</sup> em **R$/t**, então use c<sup>proc</sup><sub>l,p</sub> × (w<sub>l,p</sub>/1000) × q<sub>l,p</sub>.

---

## Restrições

### (1) Uso total da área por fazenda

```
Σ_g x_{f,g} = A_f    ∀ f ∈ F
```

### (2) (MILP opcional) Mínimo de 10 ha por grão **se** plantado

```
x_{f,g} ≥ h̲ × z_{f,g}
x_{f,g} ≤ A_f × z_{f,g}
```

∀ f, g

> No **PL puro**, remova z<sub>f,g</sub> (o mínimo vira recomendação/penalidade).

### (3) Produção e embarque (nada fica na fazenda)

```
prod_{f,g} = P^adj_{f,g} × x_{f,g}    ∀ f, g
ship_{f,g} = prod_{f,g}               ∀ f, g
```

### (4) Capacidade de transporte

```
Σ_k cap_k × y_{f,g,k} ≥ ship_{f,g}    ∀ f, g
```

> Com **PL contínuo**, viagens podem ser fracionárias; para viagens inteiras, imponha y<sub>f,g,k</sub> ∈ ℤ<sub>+</sub> (MILP) e pode trocar "≥" por "=" se quiser casar exatamente.

### (5) Balanço de ingredientes na fábrica

```
Σ_{f: map(g)=i} ship_{f,g} + buyQty_i - sellQty_i = use_i    ∀ i ∈ I
```

### (6) Consumo de ingredientes pela produção

```
use_i = Σ_l Σ_{p∈P(l)} α_{l,i} × (w_{l,p}/1000) × q_{l,p}    ∀ i ∈ I
```

> w<sub>l,p</sub>/1000 converte **kg/item** → **t/item**, compatível com ship, buyQty, sellQty (em t).

### (7) Demanda máxima por linha/embalagem

```
0 ≤ q_{l,p} ≤ Q^max_{l,p}    ∀ l, ∀ p ∈ P(l)
```

> Para linhas **sem** big-bag: definir Q<sup>max</sup><sub>l,bb</sub> = 0.

### (8) Mix mínimo por **linha** (todas as linhas produzidas)

```
Σ_{p∈P(l)} q_{l,p} ≥ γ × Σ_l' Σ_{p∈P(l')} q_{l',p}    ∀ l ∈ L
```

> Isto garante a presença de todas as linhas com ao menos 2,5% dos **itens**.  
> Para o "**arredondado para cima**", use q **inteiro** (MILP) ou aplique arredondamento em pós-processamento.

### (9) Todas as linhas e **tamanhos existentes**

- Já coberto por (8) no nível **linha**.
- Se quiser **forçar** presença de cada tamanho permitido:

```
q_{l,p} ≥ ε    ∀ l, p ∈ P(l)
```

com ε pequeno (ex.: 1 item).

---

## Unidades (cheque de consistência)

| Variável | Unidade | Observação |
|----------|---------|-----------|
| x | ha | Produção via P<sup>adj</sup> (t/ha) → prod (t) |
| ship | t | Viagens y (viagens); capacidade cap (t/viagem) |
| q | itens | w (kg/item); α (adimensional); use (t) |
| c<sup>proc</sup> | R$/kg | Aplicado sobre q via w |
| c<sup>pack</sup> | R$/item | Custo por item produzido |
| Custos agrícolas | R$/ha | Multiplicados por x |
| Frete | R$/viagem | 2×D×c<sup>km</sup> + c<sup>fix</sup> por y |

---

## Observações práticas

1. **Viagens fracionárias** (PL) vs **inteiras** (MILP): escolha conforme exigência da disciplina.
2. **Mínimo de 10 ha** por grão/fazenda: requer binária z<sub>f,g</sub> (MILP) para "se/então".
3. **2,5% arredondado p/ cima**: exige q inteiros (MILP) ou ajuste depois da solução contínua.
4. **Compra/venda**: preços "na fábrica" (sem frete) — não vincular logística a compras.
5. **Receita de venda de grão**: só sobre o excedente próprio (sellQty<sub>i</sub>).
6. **Metas mínimas de venda** (se necessário): incluir q<sub>l,p</sub> ≥ Q<sup>min</sup><sub>l,p</sub>.

---

## Sugestão de nomes (código)

```python
x[f,g]          # hectares
prod[f,g]       # = Padj[f,g] * x[f,g] (produção em t)
y[f,g,k]        # viagens
q[l,p]          # itens produzidos
buyQty[i]       # t compradas
sellQty[i]      # t vendidas
use[i]          # t consumidas

# Parâmetros:
alpha[l,i]
w[l,p]
price[l,p]
c_proc[l,p]
c_pack[l,p]
Qmax[l,p]
cap[k]
ckm[k]
cfix[k]
D[f]
Csem[g]
Cman[g]
```

---

Se estiver ok, no próximo passo você receberá um **esqueleto em Python (PuLP/OR-Tools)** com:
- Ingestão das tabelas
- Construção do modelo
- Solução e relatório (**áreas plantadas, viagens por fazenda/tipo, produção por linha/tamanho, custos por bloco, faturamento e lucro**)
