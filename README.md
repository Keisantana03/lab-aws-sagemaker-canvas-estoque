# Desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas"

## DESCRIÇÃO: 

Aplicar conceitos práticos de Machine Learning (ML) utilizando o SageMaker Canvas para criar previsões de estoque. Objetivo: Desenvolver um modelo de previsão de estoque utilizando o SageMaker Canvas e documentar o processo em um repositório no GitHub. 

## CRIAÇÃO DO DATASET:

Criei um novo dataset com a ajuda do Chat GPT, afim de ter resultados diferentes. Para construção do dataset utilizei como prompt: 

*"Atue como um cientista de dados e crie um dataset em formato CSV com no mínimo 1000 registros. Gostaria que esse arquivo refletisse o histórico de esoque e vendas de produtos com as seguintes colunas: ID_PRODUTO (numerico incremental), DIA (iniciando em 31/12/2023), QUANTIDADE_ESTOQUE. QUANTIDADE_VENDAS_PRODUTO (colocando a quantidade de venda de determinado produdo) Nesse sentido, garanta que haja uma diversidade interessante de produtos (pelo menos 25 IDs diferentes) para um sistema de gerenciamento inteligente de estoque. Além disso, garanta que cada produto tenha uma quantidade inicial em estoque que vá decrescendo de maneira variável dia a dia (se tudo for vendido manter o estoque zerado). Na prática, usarei este dataset para treinar um modelo de machine learning."*

### Resumo do dataset: 
1000 linhas e 4 colunas.

**ID_PRODUTO**: Tipo de dados: Quantitativo. Descrição: Identificador numérico para cada produto.

**DIA**: Tipo de dados: Quantitativo. (Utilizada como marcação temporal) Descrição: Representa a data em que os dados de estoque e vendas foram registrados, começando em 31/12/2023.

**QUANTIDADE_ESTOQUE**: Tipo de dados: Quantitativo. Descrição: Indicxa a quantidade de estoque disponível para o produto em uma data específica.

**QUANTIDADE_VENDAS_PRODUTO**: Tipo de dados: Quantitativo. Descrição: Representa a quantifdade de venda de uma produto específico em uma data específica. 

![image](https://github.com/user-attachments/assets/07f4851d-6c2c-4462-831b-653102989b60)


## CONSTRUINDO O MODELO

Na criação do modelo através do Sage Maker Canvas, selecionei o tipo Análise preditiva - *Construa modelos usando conjuntos de dados tabulares para prever uma ou várias categorias, bem como problemas de regressão e previsão de séries temporais.*

**Selecionado a QUANTIDADE_ESTOQUE como coluna alvo para prever**. O modelo deve prever a quantidade de estoque usando os valores de dados passados para prever valores de dados futuros.

Escolha de que preveja 2 dias no futuro. Usando calendario de feriados do Brasil para melhorar a previsão.
Como sugestão, aceitei substituir todos os valores ausentes por ZERO em QUANTIDADE_ESTOQUE e substituir todos os valores ausentes por MEDIANA em QUANTIDADE_VENDAS_PRODUTO

## ANALISE 1° MODELO.

Primeiro modelo treinado utlizando a função QUICK BUILD, treinamento rápido de 15 minutos. 

Status do primeiro modelo:

![image](https://github.com/user-attachments/assets/90da181d-b613-44ad-9d2e-17d753399d47)

Onde é possível identificar que as métricas Avg.wQL, MAPE e WAPE estão sem valores. E as metricas RSME E MASE estão com os valores 0.000

A falta de valores para algumas métricas pode indicar: cálculo ainda não realizado ou métricas não aplicáveis ou problema na coleta de dados.
A ausência de valores para as outras métricas impede uma avaliação mais completa do desempenho do modelo.
Esses com valores perfeitos de RMSE e MASE, pois podem indicar overfitting (superajuste) do modelo aos dados de treinamento, o que pode levar a um desempenho ruim em novos dados.


As colunas de impacto nesse primeiro modelo foram: QUANTIDADE_VENDAS_PRODUTO com 12.94% e Feriados brasileiros com 0.46%

![image](https://github.com/user-attachments/assets/31026e86-5481-4267-9e9a-81e36c7473ab)

Utilizando a previsão unica, em alguns itens. 


ITEM 13: 

![single_prediction_results](https://github.com/user-attachments/assets/5461a744-e568-4c55-830f-6bbf8a5b09cb)


ITEM 23:

![single_prediction_results (1)](https://github.com/user-attachments/assets/a21e0b9f-9c35-41eb-8b6b-2084f01daee8)

ITEM 8:

![single_prediction_results (2)](https://github.com/user-attachments/assets/c32022bd-537e-47e0-b877-25d790d6d7bf)


## CONCLUSÃO

Consegui identificar que nesse  modelo, apenas o item 13 mostrou valores diferentes na previsão, e apenas para o P90. Os outros itens estão iguais as imagens do item 23 e 8. Devido a ausencia de algumas métricas também  não é possível verificar o desempenho do modelo. 







Não foi possível gerar novos modelos para a previsão desses cenários, tanto em outro quick buil como no standard build, pois apareceu a seguinte mensagem: ![image](https://github.com/user-attachments/assets/dcdce9d2-d438-40cf-aa2a-16f4b825ad87)










