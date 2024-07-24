# Desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas"

## DESCRIÇÃO: 

Aplicar conceitos práticos de Machine Learning (ML) utilizando o SageMaker Canvas para criar previsões de estoque. Objetivo: Desenvolver um modelo de previsão de estoque utilizando o SageMaker Canvas e documentar o processo em um repositório no GitHub. 

## CRIAÇÃO DO DATASET:

Criei um novo dataset com a ajuda do Chat GPT, afim de ter resultados diferentes. Para construção do dataset utilizei como prompt: 

*"Atue como um cientista de dados e crie um dataset em formato CSV com no mínimo 1000 registros. Gostaria que esse arquivo refletisse o histórico de esoque e vendas de produtos com as seguintes colunas: ID_PRODUTO (numerico incremental), DIA (iniciando em 31/12/2023), QUANTIDADE_ESTOQUE. QUANTIDADE_VENDAS_PRODUTO (colocando a quantidade de venda de determinado produdo) Nesse sentido, garanta que haja uma diversidade interessante de produtos (pelo menos 25 IDs diferentes) para um sistema de gerenciamento inteligente de estoque. Além disso, garanta que cada produto tenha uma quantidade inicial em estoque que vá decrescendo de maneira variável dia a dia (se tudo for vendido manter o estoque zerado). Na prática, usarei este dataset para treinar um modelo de machine learning."*

### Resumo do dataset: 
1000 linhas e 4 colunas
Colunas separadas em ID_PRODUTO, DIA, QUANTIDADE_ESTOQUE e QUANTIDADE_VENDAS_PRODUTO.

**ID_PRODUTO**: Tipo de dados: Quantitativo. Descrição: Identificador numérico para cada produto.
**DIA**: Tipo de dados: Quantitativo. (Utilizada como marcação temporal) Descrição: Representa a data em que os dados de estoque e vendas foram registrados, começando em 31/12/2023.
**QUANTIDADE_ESTOQUE**: Tipo de dados: Quantitativo. Descrição: Indicxa a quantidade de estoque disponível para o produto em uma data específica.
**QUANTIDADE_VENDAS_PRODUTO**: Tipo de dados: Quantitativo. Descrição: Representa a quantifdade de venda de uma produto específico em uma data específica. 


## CONSTRUINDO O MODELO

Na criação do modelo através do Sage Maker Canvas, selecionei o tipo Análise preditiva - *Construa modelos usando conjuntos de dados tabulares para prever uma ou várias categorias, bem como problemas de regressão e previsão de séries temporais.*

**Selecionado a QUANTIDADE_ESTOQUE como coluna alvo para prever**. O modelo deve prever a quantidade de estoque usando os valores de dados passados para prever valores de dados futuros.

Escolha de que preveja 2 dias no futuro. Usando calendario de feriados do Brasil para melhorar a previsão.
Como sugestão, aceitei substituir todos os valores ausentes por ZERO em QUANTIDADE_ESTOQUE e substituir todos os valores ausentes por MEDIANA em QUANTIDADE_VENDAS_PRODUTO





