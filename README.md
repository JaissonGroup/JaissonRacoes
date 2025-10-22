## https://jaissongroup.github.io/JaissonRacoes/

<img width="650" height="650" alt="jaissonracoes-logo" src="https://github.com/user-attachments/assets/d5da9ed4-0db6-4bd3-95da-0df530f593dc" />


### Trabalho de Pesquisa Operacional com o Professor Jaisson
Neste trabalho, vamos resolver um problema de Programação Linear utilizando o método simplex. O problema será modelado a partir de uma empresa fictícia de Rações.

# Problema:
A Jaisson Rações é uma empresa verticalmente integrada que produz rações para animais. A empresa é dona de fazendas, caminhões e uma fábrica, cuidando desde à produção da matéria prima, até o transporte e processamento dos grãos em rações.
Para os cálculos, desconsidere tempo.
Utilizando os dados disponibilizados pela empresa, e respeitando suas regras de négocio, ajude a Jaisson Rações a **maximizar seu lucro**, além do valor máximo de lucro possível por safra, a empresa precisa que você forneca os seguintes dados:

- Quais grãos serão plantados em cada fazenda e sua quantidade de hectares.
- Quais caminhões farão o transporte de quais fazendas.
- A quantidade de sacos de ração de cada linha e tamanho.
- O custo da empresa com agricultura por fazenda.
- O custo total da empresa com agricultura (todas as fazendas).
- O custo da empresa com logística por fazenda.
- O custo total da empresa com logística (todas as rotas)
- O custo total da empresa com ingredientes comprados. (todas as rações)
- O custo total de produção de cada tipo de ração. (cada linha e cada tamanho)
- O custo total da produção de todas as rações.
- O custo total de operação da empresa.
- O faturamento total da empresa.
- O lucro da empresa.


# Regras de Negócio

- Todos os tipos de ração precisam ser produzidas, ou seja, todas as linhas em todos os tamanhos.
- Nenhum tipo de ração pode representar menos de 2.5% da produção total, arredondado para o número inteiro de cima, isso é contabilizado por quantidade de items, ou seja, independe do tamanho. Isso garante a presença da empresa em todos os mercados. (Se a Jaisson produzir 100 items, cada linha precisa ter no mínimo 3 items produzidos)
- Todas as fazendas devem ter sua área total de hectares cultivadas.
- Uma fazenda pode produzir vários tipos diferentes de grão, porém um tipo de grão não pode ocupar menos de 10 hectares em uma fazenda.
- Nenhum grão pode ser deixado nas fazendas, a produção total deve ser transportada para a fábrica.
- Caminhões só podem ter um destino por viagem, ele não pode passar por duas fazendas, por exemplo.
- Caminhões podem realizar múltiplas viagens por safra. Em cada viagem: um único destino e um único grão.
- Se sobrar grão na fábrica, poderão ser vendidos a preço tabelado de venda.
- Se faltar grão na fábrica, poderão ser comprados a preço tabelado de compra.




------------------------

# Informações do Cenário:

------------------------

## Rações Produzidas


| Código  | Categoria          | Descrição                                                                 |
|---------|-------------------|----------------------------------------------------------------------------|
| **BC-G**   | **Bovino de corte**    | Formulação energética de alto ganho de peso, indicada para confinamento e terminação de gado de corte. |
| **BL-L**   | **Vaca leiteira**      | Mistura balanceada com foco em proteína e minerais, para vacas em lactação com alta produção de leite. |
| **AV-P**   | **Galinha poedeira**   | Ração completa para aves de postura, com níveis de cálcio otimizados para qualidade da casca dos ovos. |
| **EQ-M**   | **Equinos**            | Ração equilibrada para cavalos de trabalho leve ou lazer, garantindo energia e boa digestibilidade. |
| **OV-M**   | **Ovinos/Caprinos**    | Mistura adaptada para pequenos ruminantes, favorecendo ganho de peso e saúde do rebanho. |
| **PA-PET** | **Pássaros**           | Ração premium para aves ornamentais e pets, com alto valor agregado e nutrientes específicos. |
| **AQ-T**   | **Tilápia**            | Formulação extrusada de alta digestibilidade, indicada para peixes em fase de crescimento e engorda. |


## Tamanhos de Embalagem por Linha de Ração

| Linha / Código   | Tamanho Padrão | Alternativa (alto volume) |
|------------------|----------------|---------------------------|
| **BC-G (Corte)** | 30 kg          | Big bag 1.000 kg          |
| **BL-L (Leite)** | 30 kg          | Big bag 1.000 kg          |
| **AV-P (Poedeira)** | 25 kg       | Big bag 1.000 kg          |
| **EQ-M (Equinos)** | 25 kg        | —                         |
| **OV-M (Ov/Capr)** | 30 kg        | Big bag 1.000 kg          |
| **PA-PET (Pássaros)** | 15 kg     | —                         |
| **AQ-T (Tilápia)** | 25 kg        | Big bag 1.000 kg          |


## Preços por Linha de Ração

###  BC-G (Bovino de Corte)
| Linha              | Embalagem 30 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| BC-G (Corte)       | R$ 78,00        | R$ 2.200         |
| Preço por kg       | R$ 2,60/kg      | R$ 2,20/kg       |

---

###  BL-L (Vaca Leiteira)
| Linha              | Embalagem 30 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| BL-L (Leite)       | R$ 88,00        | R$ 2.480         |
| Preço por kg       | R$ 2,93/kg      | R$ 2,48/kg       |

---

###  AV-P (Galinha Poedeira)
| Linha              | Embalagem 25 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| AV-P (Poedeira)    | R$ 75,00        | R$ 2.150         |
| Preço por kg       | R$ 3,00/kg      | R$ 2,15/kg       |

---

###  EQ-M (Equinos)
| Linha              | Embalagem 25 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| EQ-M (Equinos)     | R$ 105,00       | Não produzido    |
| Preço por kg       | R$ 4,20/kg      | —                |

---

###  OV-M (Ovinos/Caprinos)
| Linha              | Embalagem 30 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| OV-M (Ov/Capr)     | R$ 82,00        | R$ 2.300         |
| Preço por kg       | R$ 2,73/kg      | R$ 2,30/kg       |

---

###  PA-PET (Pássaros)
| Linha              | Embalagem 15 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| PA-PET (Pássaros)  | R$ 98,00        | Não produzido    |
| Preço por kg       | R$ 6,53/kg      | —                |

---

###  AQ-T (Tilápia)
| Linha              | Embalagem 25 kg | Big bag 1.000 kg |
|--------------------|-----------------|------------------|
| AQ-T (Tilápia)     | R$ 80,00        | R$ 2.250         |
| Preço por kg       | R$ 3,20/kg      | R$ 2,25/kg       |




## Composição das Rações (%)

| Ingrediente            | BC-G Corte | BL-L Leite | AV-P Poedeira | EQ-M Equinos | OV-M Ov/Capr | PA-PET Pássaros | AQ-T Tilápia |
|------------------------|:----------:|:----------:|:-------------:|:------------:|:------------:|:---------------:|:------------:|
| **Milho**              | 55%        | 34.5%      | 55%           | 25%          | 40%          | 45%             | 25%          |
| **Farelo de soja**     | 18%        | 28%        | 20%           | 8%           | 20%          | 4%              | 35%          |
| **Sorgo**              | 10%        | 9.5%       | 5%            | 0%           | 10%          | 0%              | 10%          |
| **Farelo de trigo**    | 10%        | 15%        | 5%            | 20%          | 15%          | 8%              | 10%          |
| **Aveia**              | 0%         | 5%         | 2%            | 40%          | 0%           | 25%             | 2.5%         |
| **Farelo de girassol** | 3%         | 5%         | 0%            | 3%           | 10%          | 15%             | 10%          |
| **Calcário calcítico** | 1%         | 1.5%       | 10%           | 1%           | 2%           | 1%              | 0.5%         |
| **Óleo de soja**       | 2%         | 0.5%       | 2%            | 2%           | 2%           | 1%              | 5%           |
| **Pré-mix vit/min**    | 1%         | 1%         | 1%            | 1%           | 1%           | 1%              | 2%           |


## Quantidade de Ingredientes - Embalagem Tamanho Padrão

| Ingrediente            | BC-G (30kg) | BL-L (30kg) | AV-P (25kg) | EQ-M (25kg) | OV-M (30kg) | PA-PET (15kg) | AQ-T (25kg) |
| ---------------------- | :---------------: | :---------------: | :------------------: | :-----------------: | :-----------------: | :--------------------: | :-----------------: |
| **Milho**              |      16.5 kg      |      10.4 kg      |        13.8 kg       |        6.3 kg       |       12.0 kg       |         6.8 kg         |        6.3 kg       |
| **Farelo de soja**     |       5.4 kg      |       8.4 kg      |        5.0 kg        |        2.0 kg       |        6.0 kg       |         0.6 kg         |        8.8 kg       |
| **Sorgo**              |       3.0 kg      |       2.9 kg      |        1.3 kg        |        0.0 kg       |        3.0 kg       |         0.0 kg         |        2.5 kg       |
| **Farelo de trigo**    |       3.0 kg      |       4.5 kg      |        1.3 kg        |        5.0 kg       |        4.5 kg       |         1.2 kg         |        2.5 kg       |
| **Aveia**              |       0.0 kg      |       1.5 kg      |        0.5 kg        |       10.0 kg       |        0.0 kg       |         3.8 kg         |        0.6 kg       |
| **Farelo de girassol** |       0.9 kg      |       1.5 kg      |        0.0 kg        |        0.8 kg       |        3.0 kg       |         2.3 kg         |        2.5 kg       |
| **Calcário calcítico** |       0.3 kg      |       0.5 kg      |        2.5 kg        |        0.3 kg       |        0.6 kg       |         0.2 kg         |        0.1 kg       |
| **Óleo de soja**       |       0.6 kg      |       0.2 kg      |        0.5 kg        |        0.5 kg       |        0.6 kg       |         0.2 kg         |        1.3 kg       |
| **Pré-mix vit/min**    |       0.3 kg      |       0.3 kg      |        0.3 kg        |        0.3 kg       |        0.3 kg       |         0.2 kg         |        0.5 kg       |

## Quantidade de Ingredientes - Big Bag 1000 kg

| Ingrediente            | BC-G | BL-L | AV-P | EQ-M | OV-M  | PA-PET | AQ-T |
| ---------------------- | :--------: | :--------: | :-----------: | :----------: | :----------: | :-------------: | :----------: |
| **Milho**              |   550 kg   |   345 kg   |     550 kg    |    -         |    400 kg    |      -          |    250 kg    |
| **Farelo de soja**     |   180 kg   |   280 kg   |     200 kg    |     -        |    200 kg    |      -          |    350 kg    |
| **Sorgo**              |   100 kg   |    95 kg   |     50 kg     |     -        |    100 kg    |       -         |    100 kg    |
| **Farelo de trigo**    |   100 kg   |   150 kg   |     50 kg     |    -         |    150 kg    |      -          |    100 kg    |
| **Aveia**              |    0 kg    |    50 kg   |     20 kg     |    -         |     0 kg     |      -          |     25 kg    |
| **Farelo de girassol** |    30 kg   |    50 kg   |      0 kg     |     -        |    100 kg    |      -          |    100 kg    |
| **Calcário calcítico** |    10 kg   |    15 kg   |     100 kg    |     -        |     20 kg    |      -          |     5 kg     |
| **Óleo de soja**       |    20 kg   |    5 kg    |     20 kg     |     -        |     20 kg    |      -          |     50 kg    |
| **Pré-mix vit/min**    |    10 kg   |    10 kg   |     10 kg     |     -        |     10 kg    |      -          |     20 kg    |



## Grãos Produzidos / Ingredientes

| Grão        | Ingrediente
|-------------|----------------------------|
| **Milho**   | Milho                      |
| **Soja**    | Farelo de Soja             |
| **Sorgo**   | Sorgo                      |
| **Trigo**   | Farelo de trigo            |
| **Aveia**   | Aveia                      |
| **Girassol**| Farelo de girassol         |
| **Comprado**   | Calcário calcítico         |
| **Comprado**   | Óleo de soja               |
| **Comprado**   | Pré-mix mineral vitamínico |

## Valores dos Ingredientes Compradoo

| Ingrediente            | Preço (R$/kg) |
|------------------------|---------------|
| **Calcário calcítico** | R$ 0,40       |
| **Óleo de soja**       | R$ 6,00       |
| **Pré-mix vit/min**    | R$ 15,00      |


## Demanda máxima por linha de ração

| Linha                 | Máx. itens padrão | Máx. big bags |
| --------------------- | ----------------: | ------------: |
| **BC-G (Corte)**      |           150.000 |         3.000 |
| **BL-L (Leite)**      |           110.000 |         2.200 |
| **AV-P (Poedeira)**   |           105.000 |         1.125 |
| **EQ-M (Equinos)**    |            60.000 |             0 |
| **OV-M (Ov/Capr)**    |            60.000 |         1.200 |
| **PA-PET (Pássaros)** |            50.000 |             0 |
| **AQ-T (Tilápia)**    |            60.000 |         1.500 |


## Fazendas da Jaisson Rações.

| Fazenda                   | Localização        | Área (ha) | Porte   |
|---------------------------|--------------------|:---------:|:-------:|
| **Fazenda Maruim**        | Corupá – SC        |    300    | Pequena |
| **Fazenda Gaúcha**        | Passo Fundo – RS   |    400    | Pequena |
| **Fazenda Campos Gerais** | Ponta Grossa – PR  |    500    | Pequena |
| **Fazenda Pantanal**      | Dourados – MS      |   1200    | Média   |
| **Fazenda Cerrado**       | Sorriso – MT       |   2500    | Grande  |
| **Fazenda Capital**       | Rio Verde – GO     |   2200    | Grande  |
| ***ÁREA TOTAL***          | ------------------ | **7100**  | ------- |


## Condições agroambientais por fazenda

| Fazenda                    | Radiação solar (kWh/m²/dia) | Dispon. de água | pH (acidez) | Textura do solo  | Temp. média (°C)     | Fertilidade natural |
|----------------------------|:---------------------------:|:---------------:|:-----------:|:----------------:|:-------------------:|:-------------------:|
| **Fazenda Maruim**         |            Baixa             |      Alta       |    Ácido      |     Argilosa     |       Frio         |        Média        |
| **Fazenda Gaúcha**         |            Media             |      Alta       |   Ácido       |     Argilosa     |       Frio         |        Alta         |
| **Fazenda Campos Gerais**  |            Media             |      Média      |    Ácido      |     Argilosa     |       Frio         |        Média        |
| **Fazenda Pantanal**       |            Alta              |      Alta      |    Básico      |     Arenosa      |       Quente       |        Baixa        |
| **Fazenda Cerrado**        |            Alta              |      Média      |    Básico     |     Arenosa      |       Quente       |        Baixa        |
| **Fazenda Capital**        |            Alta              |      Média      |    Básico     |     Arenosa      |       Quente       |        Baixa        |


## Perfil agronômico desejado por grão

| Grão         | Água       | pH ideal | Textura preferida         | Temp. ideal (°C) | Radiação (kWh/m²/dia)  | Fertilidade     |
|--------------|:----------:|:--------:|:-------------------------:|:----------------:|:---------------------:|:----------------:|
| **Milho**    | Alta       | Básico   | Argilosa                  | Quente            | Alta                 | Alta             |
| **Soja**     | Muita      | Básico   | Argilosa                  | Quente            | Alta                 | Alta             |
| **Sorgo**    | Pouca      | Básico   | Arenosa                   | Quente            | Alta                 | Média            |
| **Trigo**    | Média      | Ácido    | Argilosa                  | Frio              | Média                | Média            |
| **Aveia**    | Média      | Ácido    | Argilosa                  | Frio              | Média                | Média            |
| **Girassol** | Pouca      | Básico   | Arenosa                   | Quente            | Alta                 | Média            |


## Pesos de importância (somam 100% por grão)

| Grão         | Água |  pH  | Textura | Temperatura | Radiação | Fertilidade |
|--------------|:----:|:----:|:-------:|:-----------:|:--------:|:-----------:|
| **Milho**    | 22%  | 13%  |  13%    |    22%      |   15%    |    15%      |
| **Soja**     | 20%  | 17%  |  13%    |    20%      |   16%    |    14%      |
| **Sorgo**    | 13%  | 13%  |  20%    |    22%      |   16%    |    16%      |
| **Trigo**    | 18%  | 18%  |  14%    |    22%      |   16%    |    12%      |
| **Aveia**    | 18%  | 18%  |  14%    |    22%      |   16%    |    12%      |
| **Girassol** | 13%  | 13%  |  17%    |    20%      |   17%    |    20%      |


## Produção Média Padrão (toneladas por ha) (dados da íntegra)

| Grão         | Produção Média Padrão (t/ha) |
|--------------|------------------------------|
| **Milho**    | 6.0 t/ha                     |
| **Soja**     | 3.8 t/ha                     |
| **Sorgo**    | 3.2 t/ha                     |
| **Trigo**    | 3.0 t/ha                     |
| **Aveia**    | 2.8 t/ha                     |
| **Girassol** | 1.8 t/ha                     |


## Produção Por Fazenda (a partir dos pesos de importância)

A produção de um grão \(g\) em uma fazenda \(f\) é dada por:

$$
P_{ajustada}(g,f) = P_{base}(g) \cdot \left( 1 + \frac{1}{100} \sum_{i=1}^{n} m_i(g,f) \cdot w_i(g) \right)
$$

Onde:

- \(P_{base}(g)\) = produção padrão do grão \(g\) (t/ha).  
- \(w_i(g)\) = peso (em %) do fator \(i\) para o grão \(g\).  
- \(m_i(g,f)\) = comparação entre a condição da fazenda \(f\) e o perfil ideal do grão \(g\):

$$
m_i(g,f) =
\begin{cases}
+1 & \text{se a condição da fazenda = perfil ideal do grão} \\
-1 & \text{se a condição da fazenda ≠ perfil ideal do grão}
\end{cases}
$$

- \(n\) = número total de fatores considerados (aqui: 6 → Água, pH, Textura, Temperatura, Radiação, Fertilidade).


### Fazenda Maruim
| Grão         |   Produção base (t/ha) | Ajuste total (%)   |   Produção ajustada (t/ha) |
|--------------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.8 | +32.0%             |                       3.7  |
| **Girassol** |                    1.8 | -60.0%             |                       0.72 |
| **Milho**    |                    6   | -30.0%             |                       4.2  |
| **Soja**     |                    3.8 | -34.0%             |                       2.51 |
| **Sorgo**    |                    3.2 | -68.0%             |                       1.02 |
| **Trigo**    |                    3   | +32.0%             |                       3.96 |


### Fazenda Gaúcha
| Grão         |   Produção base (t/ha) | Ajuste total (%)   |   Produção ajustada (t/ha) |
|--------------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.8 | +40.0%             |                       3.92 |
| **Girassol** |                    1.8 | -100.0%            |                       0    |
| **Milho**    |                    6   | 0.0%               |                       6    |
| **Soja**     |                    3.8 | -6.0%              |                       3.57 |
| **Sorgo**    |                    3.2 | -100.0%            |                       0    |
| **Trigo**    |                    3   | +40.0%             |                       4.2  |


### Fazenda Campos Gerais
| Grão         |   Produção base (t/ha) | Ajuste total (%)   |   Produção ajustada (t/ha) |
|--------------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.8 | +100.0%            |                       5.6  |
| **Girassol** |                    1.8 | -60.0%             |                       0.72 |
| **Milho**    |                    6   | -74.0%             |                       1.56 |
| **Soja**     |                    3.8 | -74.0%             |                       0.99 |
| **Sorgo**    |                    3.2 | -68.0%             |                       1.02 |
| **Trigo**    |                    3   | +100.0%            |                       6    |


### Fazenda Pantanal
| Grão         |   Produção base (t/ha) | Ajuste total (%)   |   Produção ajustada (t/ha) |
|--------------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.8 | -100.0%            |                       0    |
| **Girassol** |                    1.8 | +34.0%             |                       2.41 |
| **Milho**    |                    6   | +44.0%             |                       8.64 |
| **Soja**     |                    3.8 | +46.0%             |                       5.55 |
| **Sorgo**    |                    3.2 | +42.0%             |                       4.54 |
| **Trigo**    |                    3   | -100.0%            |                       0    |


### Fazenda Cerrado
| Grão         |   Produção base (t/ha) | Ajuste total (%)   |   Produção ajustada (t/ha) |
|--------------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.8 | -64.0%             |                       1.01 |
| **Girassol** |                    1.8 | +34.0%             |                       2.41 |
| **Milho**    |                    6   | 0.0%               |                       6    |
| **Soja**     |                    3.8 | +6.0%              |                       4.03 |
| **Sorgo**    |                    3.2 | +42.0%             |                       4.54 |
| **Trigo**    |                    3   | -64.0%             |                       1.08 |


### Fazenda Capital
| Grão         |   Produção base (t/ha) | Ajuste total (%)   |   Produção ajustada (t/ha) |
|--------------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.8 | -64.0%             |                       1.01 |
| **Girassol** |                    1.8 | +34.0%             |                       2.41 |
| **Milho**    |                    6   | 0.0%               |                       6    |
| **Soja**     |                    3.8 | +6.0%              |                       4.03 |
| **Sorgo**    |                    3.2 | +42.0%             |                       4.54 |
| **Trigo**    |                    3   | -64.0%             |                       1.08 |




## Produção Total Máxima Possível de Grão por Fazenda

### Fazenda Maruim
| Grão         |   Produção Máxima Possível (ton) |
|--------------|------------------------|
| **Aveia**    |                 1108.8 t |
| **Girassol** |                  216   t |
| **Milho**    |                 1260   t |
| **Soja**     |                  752.4 t |
| **Sorgo**    |                  307.2 t |
| **Trigo**    |                 1188   t |


### Fazenda Gaúcha
| Grão         |   Produção Máxima Possível (ton) |
|--------------|------------------------|
| **Aveia**    |                 1568   t |
| **Girassol** |                    0   t |
| **Milho**    |                 2400   t |
| **Soja**     |                 1428.8 t |
| **Sorgo**    |                    0   t |
| **Trigo**    |                 1680   t |


### Fazenda Campos Gerais
| Grão         |   Produção Máxima Possível (ton) |
|--------------|------------------------|
| **Aveia**    |                   2800 t |
| **Girassol** |                    360 t |
| **Milho**    |                    780 t |
| **Soja**     |                    494 t |
| **Sorgo**    |                    512 t |
| **Trigo**    |                   3000 t |


### Fazenda Pantanal
| Grão         |   Produção Máxima Possível (ton) |
|--------------|------------------------|
| **Aveia**    |                    0   t |
| **Girassol** |                 2894.4 t |
| **Milho**    |                10368   t |
| **Soja**     |                 6657.6 t |
| **Sorgo**    |                 5452.8 t |
| **Trigo**    |                    0   t |


### Fazenda Cerrado
| Grão         |   Produção Máxima Possível (ton) |
|--------------|------------------------|
| **Aveia**    |                   2520 t |
| **Girassol** |                   6030 t |
| **Milho**    |                  15000 t |
| **Soja**     |                  10070 t |
| **Sorgo**    |                  11360 t |
| **Trigo**    |                   2700 t |


### Fazenda Capital
| Grão         |   Produção Máxima Possível (ton) |
|--------------|------------------------|
| **Aveia**    |                 2217.6 t |
| **Girassol** |                 5306.4 t |
| **Milho**    |                13200   t |
| **Soja**     |                 8861.6 t |
| **Sorgo**    |                 9996.8 t |
| **Trigo**    |                 2376   t |


## Preço de Cultivo por Grão

| Grão         | Semente (R$/ha) | Manutenção (R$/ha) |
| ------------ | --------------: | -----------------: |
| **Milho**    |          R$ 670,00 |           R$ 1785,00 |
| **Soja**     |          R$ 483,00 |           R$ 2433,00 |
| **Sorgo**    |          R$ 294,00 |           R$ 1692,00 |
| **Girassol** |          R$ 312,00 |           R$ 2364,00 |
| **Trigo**    |          R$ 410,00 |           R$ 3024,00 |
| **Aveia**    |          R$ 272,00 |           R$ 2327,00 |

## Fábrica de Rações Jaisson Rações

- A fábrica que produz e distribui as rações da Jaisson Rações é localizada em Pirabeiraba, SC.


## Distância de cada fazenda até a Fábrica

| Fazenda                   | Localização        | Distancia até Fábrica (km) |
|---------------------------|--------------------|----------------------------|
| **Fazenda Maruim**        | Corupá – SC        | 70 km                      |
| **Fazenda Gaúcha**        | Passo Fundo – RS	 | 566 km                     |
| **Fazenda Campos Gerais** | Ponta Grossa – PR  | 228 km                     |
| **Fazenda Pantanal**      | Dourados – MS      | 954 km                     |
| **Fazenda Cerrado**       | Sorriso – MT       | 2143 km                    |
| **Fazenda Capital**       | Rio Verde – GO     | 1287 km                    |
| ***FÁBRICA***             | Pirabeiraba – SC   | 0 km                       |


## Frota de Caminhões da Jaisson Rações

| Tamanho     | Modelo (exemplo)                                         |  Frota  | Capacidade (t) | Custo (R$/km) | **Custo fixo por viagem** |
| ----------- | -------------------------------------------------------- | :-----: | :------------: | :-----------: | ------------------------: |
| **Pequeno** | **VW Constellation 30.330 8x2** (truck graneleiro)       | **105** |     **20**     |  **R$ 8,00**  |             **R$ 128,00** |
| **Médio**   | **Mercedes-Benz Actros 2651 6x4** + semirreboque 3 eixos |  **70** |     **35**     |  **R$ 10,50** |            **R$ 1064,00** |
| **Grande**  | **Scania R 450 6x4** + bitrem graneleiro (9 eixos)      |  **35** |     **60**     |  **R$ 12,00**  |            **R$ 9024,00** |




## Valor de VENDA de grãos excedentes da fábrica (retirado na fabrica, sem frete)

| Grão         | Preço (R$/t) |
| ------------ | :----------: |
| **Milho**    |  R$ 450,00  |
| **Soja**     |  R$ 840,00  |
| **Sorgo**    |  R$ 680,00  |
| **Trigo**    | R$ 1260,00 |
| **Aveia**    | R$ 1020,00 |
| **Girassol** | R$ 1640,00 |


## Valor de COMPRA de grãos faltantes da fábrica (entregue na fábrica, sem frete)
| Grão         | Preço (R$/t) |
| ------------ | :----------: |
| **Milho**    | R$ 1380,00 |
| **Soja**     | R$ 1380,00 |
| **Sorgo**    | R$ 1120,00 |
| **Trigo**    | R$ 2060,00 |
| **Aveia**    | R$ 1670,00 |
| **Girassol** | R$ 2680,00 |


## Custo da Produção na Fábrica (Tamanho Padrão)

| Linha                 | Peso (kg) | Processo (R$/kg) | Embalagem (R$/un) | **Custo por item (R$)** |
| --------------------- | --------: | ---------------: | ----------------: | ----------------------: |
| **BC-G (Corte)**      |     30 kg |          R$ 0,10 |           R$ 5,00 |             **R$ 8,00** |
| **BL-L (Leite)**      |     30 kg |          R$ 0,11 |           R$ 5,00 |             **R$ 8,30** |
| **AV-P (Poedeira)**   |     25 kg |          R$ 0,12 |           R$ 4,50 |             **R$ 7,50** |
| **EQ-M (Equinos)**    |     25 kg |          R$ 0,12 |           R$ 4,50 |             **R$ 7,50** |
| **OV-M (Ov/Capr)**    |     30 kg |          R$ 0,11 |           R$ 5,00 |             **R$ 8,30** |
| **PA-PET (Pássaros)** |     15 kg |          R$ 0,16 |           R$ 4,00 |             **R$ 6,40** |
| **AQ-T (Tilápia)**    |     25 kg |          R$ 0,24 |           R$ 4,50 |            **R$ 10,50** |


## Custo da Produção na Fábrica (Big Bag)

| Linha                 | Peso (kg) | Processo (R$/kg) | Embalagem (R$/bb) | **Custo por big bag (R$)** |
| --------------------- | --------: | ---------------: | ----------------: | -------------------------: |
| **BC-G (Corte)**      | 1000 kg   |          R$ 0,10 |          R$ 95,00 |              **R$ 195,00** |
| **BL-L (Leite)**      | 1000 kg   |          R$ 0,11 |          R$ 95,00 |              **R$ 205,00** |
| **AV-P (Poedeira)**   | 1000 kg   |          R$ 0,12 |          R$ 95,00 |              **R$ 215,00** |
| **EQ-M (Equinos)**    | 1000 kg   |                — |                 — |                      **—** |
| **OV-M (Ov/Capr)**    | 1000 kg   |          R$ 0,11 |          R$ 95,00 |              **R$ 205,00** |
| **PA-PET (Pássaros)** | 1000 kg   |                — |                 — |                      **—** |
| **AQ-T (Tilápia)**    | 1000 kg   |          R$ 0,24 |          R$ 95,00 |              **R$ 335,00** |


----------------
----------------
----------------

# RESOLUÇÃO:

### Google Colab (código) de resolução: https://colab.research.google.com/drive/19RtrcS1mf3BfwthSmMZOujQqx4Hylm8o?usp=sharing
---

## Formulação do Problema de Programação Linear - Jaisson Rações

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


------------------
------------------
------------------

# RESULTADOS

# RELATÓRIO COMPLETO — JAISSON RAÇÕES
> #### Relatório com todos os dados solicitados pelo enunciado do problema.


----------

## 🌾 GRÃOS PLANTADOS POR FAZENDA (ha)

### Fazenda Maruim
| Grão | Área | Custo de Cultivo |
| :--: | :--: | :--------------: |
| Aveia | 300 ha. | R$ 779.700,00 |
| **Total** | **300 ha.** | **R$ 779.700,00** |

### Fazenda Gaucha
| Grão | Área | Custo de Cultivo |
| :--: | :--: | :--------------: |
| Milho | 400 ha. | R$ 982.000,00 |
| **Total** | **400 ha.** | **R$ 982.000,00** |

### Fazenda Campos Gerais
| Grão | Área | Custo de Cultivo |
| :--: | :--: | :--------------: |
| Trigo | 481,67 ha. | R$ 1.654.043,34 |
| Aveia | 18,33 ha. | R$ 47.648,33 |
| **Total** | **500 ha.** | **R$ 1.701.691,68** |

### Fazenda Pantanal
| Grão | Área | Custo de Cultivo |
| :--: | :--: | :--------------: |
| Milho | 951,39 ha. | R$ 2.335.659,72 |
| Soja | 248,61 ha. | R$ 724.950,00 |
| **Total** | **1.200 ha.** | **R$ 3.060.609,72** |

### Fazenda Cerrado
| Grão | Área | Custo de Cultivo |
| :--: | :--: | :--------------: |
| Sorgo | 13,22 ha. | R$ 26.246,70 |
| Girassol | 2.486,78 ha. | R$ 6.654.634,25 |
| **Total** | **2.500 ha.** | **R$ 6.680.880,95** |

### Fazenda Capital
| Grão | Área | Custo de Cultivo |
| :--: | :--: | :--------------: |
| Milho | 20 ha. | R$ 49.100,00 |
| Soja | 997,52 ha. | R$ 2.908.764,27 |
| Sorgo | 436,12 ha. | R$ 866.140,97 |
| Girassol | 746,36 ha. | R$ 1.997.254,12 |
| **Total** | **2.200 ha.** | **R$ 5.821.259,35** |


### 💰 CUSTO TOTAL AGRÍCOLA: R$ 19,026,141.70

----------

## 🚛 LOGÍSTICA — TRANSPORTES POR FAZENDA E CUSTOS

### Fazenda Maruim:
| Grão | Caminhão Pequeno | Custo Pequeno | Caminhão Médio | Custo Médio | Caminhão Grande | Custo Grande |
| :--: | :-------------: | :-----------: | :-----------: | :---------: | :------------: | :----------: |
| Aveia | 56 viagens | R$ 69.888,00 | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 |
| **Custo Total** |  **R$ 69.888,00** |

### Fazenda Gaucha:
| Grão | Caminhão Pequeno | Custo Pequeno | Caminhão Médio | Custo Médio | Caminhão Grande | Custo Grande |
| :--: | :-------------: | :-----------: | :-----------: | :---------: | :------------: | :----------: |
| Milho | 1 viagem | R$ 9.184,00 | 68 viagens | R$ 880.600,00 | 0 viagens | R$ 0,00 |
| **Custo Total** |  **R$ 889.784,00** |


### Fazenda Campos Gerais:
| Grão | Caminhão Pequeno | Custo Pequeno | Caminhão Médio | Custo Médio | Caminhão Grande | Custo Grande |
| :--: | :-------------: | :-----------: | :-----------: | :---------: | :------------: | :----------: |
| Trigo | 1 viagem | R$ 3.776,00 | 82 viagens | R$ 479.864,00 | 0 viagens | R$ 0,00 |
| Aveia | 0 viagens | R$ 0,00 | 3 viagens | R$ 17.556,00 | 0 viagens | R$ 0,00 |
| **Custo Total** |  **R$ 501.196,00** |


### Fazenda Pantanal:
| Grão | Caminhão Pequeno | Custo Pequeno | Caminhão Médio | Custo Médio | Caminhão Grande | Custo Grande |
| :--: | :-------------: | :-----------: | :-----------: | :---------: | :------------: | :----------: |
| Milho | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 137 viagens | R$ 4.373.040,00 |
| Soja | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 23 viagens | R$ 734.160,00 |
| **Custo Total** |  **R$ 5.107.200,00** |

### Fazenda Cerrado:
| Grão | Caminhão Pequeno | Custo Pequeno | Caminhão Médio | Custo Médio | Caminhão Grande | Custo Grande |
| :--: | :-------------: | :-----------: | :-----------: | :---------: | :------------: | :----------: |
| Sorgo | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 1 viagens | R$ 60.456,00 |
| Girassol | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 100 viagens | R$ 6.045.600,00 |
| **Custo Total** |  **R$ 6.106.056,00** |


### Fazenda Capital:
| Grão | Caminhão Pequeno | Custo Pequeno | Caminhão Médio | Custo Médio | Caminhão Grande | Custo Grande |
| :--: | :-------------: | :-----------: | :-----------: | :---------: | :------------: | :----------: |
| Milho | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 2 viagens | R$ 79.824,00 |
| Soja | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 67 viagens | R$ 2.674.104,00 |
| Sorgo | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 33 viagens | R$ 1.317.096,00 |
| Girassol | 0 viagens | R$ 0,00 | 0 viagens | R$ 0,00 | 30 viagens | R$ 1.197.360,00 |
| **Custo Total** |  **R$ 5.268.384,00** |


### 💰 CUSTO TOTAL LOGÍSTICO: R$ 17,942,508.00

----------

## 📦🏭 QUANTIDADE E CUSTOS DA PRODUÇÃO DE RAÇÕES

### Linha BC-G (Bovino corte)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 150.000 itens   | R$ 1.200.000,00 |
| Big Bag | 3.000 itens   | R$ 585.000,00 |


### Linha BL-L (Vaca leiteira)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 110.000 itens   | R$ 913.000,00 |
| Big Bag | 2.200 itens   | R$ 451.000,00 |


### Linha AV-P (Galinha poedeira)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 105.000 itens   | R$ 787.500,00 |
| Big Bag | 1.125 itens   | R$ 241.875,00 |


### Linha EQ-M (Equinos)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 60.000 itens   | R$ 450.000,00 |
| Big Bag | 0 itens   | R$ 0,00 |


### Linha OV-M (Ovelhas e Cabras)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 60.000 itens   | R$ 498.000,00 |
| Big Bag | 1.200 itens   | R$ 246.000,00 |


### Linha PA-PET (Pássaros)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 50.000 itens   | R$ 320.000,00 |
| Big Bag | 0 itens   | R$ 0,00 |


### Linha AQ-T (Tilápia)
| Tamanho | Quantidade | Custo |
| :-----: | :--------: | :-----: |
| Padrão  | 60.000 itens   | R$ 630.000,00 |
| Big Bag | 1.500 itens   | R$ 502.500,00 |


### 🧾 CUSTO TOTAL DE INGREDIENTES EXTRAS COMPRADOS: R$ 7,540,237.50

### 💰 CUSTO TOTAL DE PRODUÇÃO DE RAÇÕES: R$ 6,824,875.00

----------

## 🧮 CUSTO TOTAL DE OPERAÇÃO: R$ 51,333,762.20

## 💵 FATURAMENTO TOTAL: R$ 81,523,341.23

## 🏆 LUCRO FINAL (ótimo global): R$ 30,189,579.03

