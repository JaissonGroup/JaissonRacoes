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


# Fazendas da Jaisson Rações.

| Fazenda               | Localização        | Área (ha) | Porte   |
|---------------------------|--------------------|:---------:|:-------:|
| **Fazenda Maruim**        | Lages – SC         |    300    | Pequena |
| **Fazenda Gaúcha**        | Passo Fundo – RS   |    400    | Pequena |
| **Fazenda Campos Gerais** | Ponta Grossa – PR  |    500    | Pequena |
| **Fazenda Pantanal**      | Dourados – MS      |   1200    | Média   |
| **Fazenda Cerrado**       | Sorriso – MT       |   2500    | Grande  |
| **Fazenda Capital**       | Rio Verde – GO     |   2200    | Grande  |


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
| **Milho**    | 3.9 t/ha                     |
| **Soja**     | 3.5 t/ha                     |
| **Sorgo**    | 1.5 t/ha                     |
| **Trigo**    | 1.3 t/ha                     |
| **Aveia**    | 2.4 t/ha                     |
| **Girassol** | 2.7 t/ha                     |


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
| Grão     |   Produção base (t/ha) |   Ajuste total (%) |   Produção ajustada (t/ha) |
|----------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.4 |                 32 |                       3.17 |
| **Girassol** |                    2.7 |                -60 |                       1.08 |
| **Milho**    |                    3.9 |                -30 |                       2.73 |
| **Soja**     |                    3.5 |                -34 |                       2.31 |
| **Sorgo**    |                    1.5 |                -68 |                       0.48 |
| **Trigo**    |                    1.3 |                 32 |                       1.72 |


### Fazenda Gaúcha
| Grão     |   Produção base (t/ha) |   Ajuste total (%) |   Produção ajustada (t/ha) |
|----------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.4 |                 40 |                       3.36 |
| **Girassol** |                    2.7 |               -100 |                       0    |
| **Milho**    |                    3.9 |                  0 |                       3.9  |
| **Soja**     |                    3.5 |                 -6 |                       3.29 |
| **Sorgo**    |                    1.5 |               -100 |                       0    |
| **Trigo**    |                    1.3 |                 40 |                       1.82 |


### Fazenda Campos Gerais
| Grão     |   Produção base (t/ha) |   Ajuste total (%) |   Produção ajustada (t/ha) |
|----------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.4 |                100 |                       4.8  |
| **Girassol** |                    2.7 |                -60 |                       1.08 |
| **Milho**    |                    3.9 |                -74 |                       1.01 |
| **Soja**     |                    3.5 |                -74 |                       0.91 |
| **Sorgo**    |                    1.5 |                -68 |                       0.48 |
| **Trigo**    |                    1.3 |                100 |                       2.6  |


### Fazenda Pantanal
| Grão     |   Produção base (t/ha) |   Ajuste total (%) |   Produção ajustada (t/ha) |
|----------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.4 |               -100 |                       0    |
| **Girassol** |                    2.7 |                 34 |                       3.62 |
| **Milho**    |                    3.9 |                 44 |                       5.62 |
| **Soja**     |                    3.5 |                 46 |                       5.11 |
| **Sorgo**    |                    1.5 |                 42 |                       2.13 |
| **Trigo**    |                    1.3 |               -100 |                       0    |


### Fazenda Cerrado
| Grão     |   Produção base (t/ha) |   Ajuste total (%) |   Produção ajustada (t/ha) |
|----------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.4 |                -64 |                       0.86 |
| **Girassol** |                    2.7 |                 34 |                       3.62 |
| **Milho**    |                    3.9 |                  0 |                       3.9  |
| **Soja**     |                    3.5 |                  6 |                       3.71 |
| **Sorgo**    |                    1.5 |                 42 |                       2.13 |
| **Trigo**    |                    1.3 |                -64 |                       0.47 |


### Fazenda Capital
| Grão     |   Produção base (t/ha) |   Ajuste total (%) |   Produção ajustada (t/ha) |
|----------|------------------------|--------------------|----------------------------|
| **Aveia**    |                    2.4 |                -64 |                       0.86 |
| **Girassol** |                    2.7 |                 34 |                       3.62 |
| **Milho**    |                    3.9 |                  0 |                       3.9  |
| **Soja**     |                    3.5 |                  6 |                       3.71 |
| **Sorgo**    |                    1.5 |                 42 |                       2.13 |
| **Trigo**    |                    1.3 |                -64 |                       0.47 |







-----------------------------------

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
