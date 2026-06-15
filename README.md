# CEASA Price Forecast

Projeto de análise e previsão exploratória de preços de hortifrutigranjeiros comercializados no Mercado do Produtor de Juazeiro, utilizando dados públicos extraídos das publicações da Autarquia Municipal de Abastecimento (AMA), vinculada à Prefeitura de Juazeiro.

## 1. Contexto do problema

O Mercado do Produtor de Juazeiro é um importante centro de comercialização de hortifrutigranjeiros no Vale do São Francisco. Produtores, comerciantes e compradores precisam tomar decisões relacionadas à compra, venda, estoque e negociação de produtos agrícolas.

No entanto, os preços desses produtos podem variar ao longo do tempo por fatores como oferta, demanda, sazonalidade, clima, disponibilidade de produtos e dinâmica do mercado atacadista.

Diante desse cenário, este projeto utiliza dados públicos de cotações para analisar o comportamento dos preços e construir uma solução exploratória de previsão de preço médio de referência.

## 2. Objetivo

O objetivo deste projeto é coletar, tratar, analisar e modelar dados públicos de cotações de produtos hortifrutigranjeiros comercializados no Mercado do Produtor de Juazeiro.

A proposta é:

- coletar dados públicos da AMA;
- organizar os dados em uma base estruturada;
- realizar análise exploratória dos preços;
- identificar produtos com maior frequência e variação;
- construir modelos de regressão para prever o preço médio;
- avaliar os modelos com métricas de desempenho;
- apresentar visualizações dos principais resultados.

A variável alvo do projeto é o preço médio do produto, representado pela coluna `avg_price`.

## 3. Fonte de dados

A fonte utilizada foi a página da Autarquia Municipal de Abastecimento (AMA), no portal da Prefeitura de Juazeiro.

Fonte:

- AMA — Prefeitura de Juazeiro  
  https://www.juazeiro.ba.gov.br/category/autarquia-municipal-de-abastecimento-ama/

Os dados foram extraídos de publicações públicas relacionadas às cotações dos hortifrutigranjeiros comercializados no Mercado do Produtor de Juazeiro.

## 4. Coleta dos dados

A coleta foi realizada por meio de web scraping utilizando Python, `requests` e `BeautifulSoup`.

O processo consistiu em:

1. acessar as páginas da categoria AMA;
2. identificar publicações relacionadas às cotações;
3. coletar título, link e data das publicações;
4. acessar cada notícia individualmente;
5. extrair o texto da publicação;
6. identificar produtos e preços mencionados no conteúdo textual;
7. organizar os registros em uma base tabular.

Foram encontradas 164 notícias relacionadas às cotações e, após a extração textual, foram obtidos registros de preços para análise.

## 5. Tratamento dos dados

Como os dados foram extraídos de textos de notícias, foi necessário realizar uma etapa de limpeza e padronização.

As principais etapas foram:

- conversão das datas para formato datetime;
- padronização dos nomes dos produtos;
- remoção de registros inválidos;
- remoção de duplicidades;
- padronização das unidades de comercialização;
- criação da variável `unit_simple`;
- organização da base final para análise e modelagem.

Após a limpeza, a base final ficou com registros estruturados contendo informações como data, produto, unidade, preço médio, fonte e mercado.

## 6. Análise exploratória

Na análise exploratória, foram avaliados:

- quantidade de registros;
- período disponível na base;
- quantidade de produtos únicos;
- distribuição dos preços médios;
- produtos com mais registros;
- produtos com maior preço médio;
- produtos com maior variação de preço;
- evolução temporal dos produtos mais frequentes;
- unidades de comercialização mais comuns.

A análise mostrou que a base possui produtos com diferentes unidades de comercialização, como quilo, caixa, saco e cento. Por isso, a interpretação dos preços deve considerar a unidade informada.

## 7. Modelagem

Foram construídos modelos de regressão para prever o preço médio dos produtos.

As variáveis utilizadas foram:

- nome do produto;
- unidade de comercialização simplificada;
- ano da cotação;
- mês da cotação;
- dia da semana.

A variável alvo foi:

- `avg_price`

Os modelos testados foram:

- Baseline pela média geral;
- Regressão Linear;
- Árvore de Decisão;
- Random Forest;
- Gradient Boosting.

## 8. Avaliação dos modelos

Os modelos foram avaliados com as métricas:

- MAE;
- RMSE;
- R².

O baseline baseado na média geral apresentou o melhor resultado geral. Entre os modelos de machine learning, o Gradient Boosting foi o que apresentou melhor desempenho.

Esse resultado indica que, para a base atual, modelos simples ainda são mais adequados do que modelos mais complexos. Isso ocorre principalmente pelo volume reduzido de dados, pela diversidade de produtos e pela ausência de uma tabela padronizada de cotações.

## 9. Resultados

O projeto demonstrou que dados públicos da AMA podem ser coletados, tratados e utilizados para construir uma base inicial de análise de preços.

Apesar das limitações, foi possível:

- estruturar dados originalmente não padronizados;
- identificar produtos com maior frequência;
- analisar variações de preços;
- comparar modelos preditivos;
- observar as limitações da modelagem com poucos dados.

A solução deve ser interpretada como uma previsão exploratória de preço médio de referência, e não como recomendação final de preço de venda.

## 10. Limitações

As principais limitações do projeto foram:

- volume reduzido de registros;
- dados extraídos de textos não padronizados;
- poucos registros históricos por produto;
- diferentes unidades de comercialização;
- ausência de variáveis como oferta, demanda, qualidade do produto, clima e volume comercializado.

Essas limitações impactaram o desempenho dos modelos preditivos.

## 11. Trabalhos futuros

Como melhorias futuras, recomenda-se:

- ampliar a base histórica;
- extrair tabelas completas das cotações;
- padronizar melhor produtos e unidades;
- incluir novas fontes públicas;
- utilizar variáveis externas, como sazonalidade, clima e volume de oferta;
- testar modelos específicos por produto;
- construir uma recomendação de preço de referência com maior confiança.

## 12. Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Requests
- BeautifulSoup
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## 13. Estrutura do projeto

```text
ceasa-price-forecast/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── ceasa_price_forecast.ipynb
├── README.md
├── .gitignore
├── LICENSE
