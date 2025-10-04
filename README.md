# Jaisson Rações
### Trabalho de Pesquisa Operacional com o Professor Jaisson
Neste trabalho, vamos resolver um problema de Programação Linear utilizando o método simplex. O problema será modelado a partir de uma empresa fictícia de Rações.




## Rações Produzidas


| Código  | Categoria          | Descrição                                                                 |
|---------|-------------------|----------------------------------------------------------------------------|
| **BC-T**   | **Bovino de corte**    | Formulação energética de alto ganho de peso, indicada para confinamento e terminação de gado de corte. |
| **BL-L**   | **Vaca leiteira**      | Mistura balanceada com foco em proteína e minerais, para vacas em lactação com alta produção de leite. |
| **AV-P**   | **Galinha poedeira**   | Ração completa para aves de postura, com níveis de cálcio otimizados para qualidade da casca dos ovos. |
| **EQ-M**   | **Equinos**            | Ração equilibrada para cavalos de trabalho leve ou lazer, garantindo energia e boa digestibilidade. |
| **OV-M**   | **Ovinos/Caprinos**    | Mistura adaptada para pequenos ruminantes, favorecendo ganho de peso e saúde do rebanho. |
| **PA-PET** | **Pássaros**           | Ração premium para aves ornamentais e pets, com alto valor agregado e nutrientes específicos. |
| **AQ-T**   | **Tilápia**            | Formulação extrusada de alta digestibilidade, indicada para peixes em fase de crescimento e engorda. |



## Composição das Rações (%)

| Ingrediente            | BC-T Corte | BL-L Leite | AV-P Poedeira | EQ-M Equinos | OV-M Ov/Capr | PA-PET Pássaros | AQ-T Tilápia |
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


## Grãos Produzidos / Ingredientes

| Grão        | Ingrediente
|-------------|----------------------------|
| **Milho**   | Milho                      |
| **Soja**    | Farelo de Soja             |
| **Sorgo**   | Sorgo                      |
| **Trigo**   | Farelo de trigo            |
| **Aveia**   | Aveia                      |
| **Girassol**| Farelo de girassol         |
| ---------   | Calcário calcítico         |
| ---------   | Óleo de soja               |
| ---------   | Pré-mix mineral vitamínico |


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

| Tamanho   | Modelo            | Frota | Capacidade (t) | Custo (R$/km) | Custo por t.km (R$/t.km) |
|-----------|-------------------|:-----:|:--------------:|:-------------:|:------------------------:|
| Pequeno   | VW Delivery       |   3   |       5 t      |   R$ 2,50     |       R$ 0,50            |
| Médio     | Mercedes Atego    |   2   |      10 t      |   R$ 3,50     |       R$ 0,35            |
| Grande    | Iveco Tector      |   1   |      15 t      |   R$ 4,50     |       R$ 0,30            |






------------

## Regras de Negócio

- Todas as fazendas devem ter sua área total utilizada.
- A quantidade mínima de produção de cada tipo de ração deve ser respeitada.
- Cada caminhão só pode fazer uma viagem com um único destino por safra.



------------

## Links Google Colab (código)
- Calcular Produção por Fazenda: https://colab.research.google.com/drive/1pTE2eD9M3s4WdMI8yQtazyfOeL7Pb-R0?usp=sharing


## Fontes
- Embrapa                
https://www.embrapa.br/

- Embrapa Pronasolos          
https://www.embrapa.br/pronasolos

- Embrapa Sistema Brasileiro de Classificação de Solos                 
https://www.embrapa.br/busca-de-publicacoes/-/publicacao/1176834/sistema-brasileiro-de-classificacao-de-solos

- Embrapa Solos brasileiros
https://www.embrapa.br/tema-solos-brasileiros/solos-do-brasil
