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

- Milho
- Soja -> Farelo de Soja
- Sorgo
- Trigo -> Farelo de trigo
- Aveia
- Girassol -> Farelo de girassol
- Calcário calcítico
- Óleo de soja
- Pré-mix mineral / vitamínico


## Links do Google Colab
- **Gráficos de composição das rações:** https://colab.research.google.com/drive/1-btODBNLbsUJ2gSM1pOw75CPSVsphiZr?usp=sharing
