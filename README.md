  <img src="https://www.kindpng.com/picc/m/81-811458_jupyter-notebook-logo-hd-png-download.png" width="210" height="140">



# Análise de dados (cartão de crédito)
 Análise do motivo de cancelamento do cartão.

  ## Requisitos:
 - Ter o jupyter notebook instalado.
 - Ter o arquivo ClientesBanco.csv nas mesma pasta do arquivo analise_dados.ipynb

## Pacotes instalados:
- Pandas
```bash
pip install pandas
```
- Plotly
```bash
pip install plotly
```
## Processo das ferramentas que foram usadas:

Importação da base de dados para o python, e definição do enconding para o python aceitar caracteres do português.

``` python
tabela = pd.read_csv('ClientesBanco.csv',encoding = 'latin1')
```

Exclusão da coluna 'CLIENTNUM'da tabela.

```python
tabela = tabela.drop('CLIENTNUM',axis=1)
```

Tirando valores vazios da tabela.

```python
tabela = tabela.dropna()
```
Apresentando um resumo estatístico dos dados.

```python
display(tabela.describe().round(1))
```
Contando a quantidade de clientes x cancelados na coluna Categoria da tabela.

```python
qtde_categoria = tabela['Categoria'].value_counts()
display(qtde_categoria)
```
Código visualizar em forma de porcentagem

```python
qtde_categoria_perc = tabela['Categoria'].value_counts(normalize=True)
display(qtde_categoria_perc)
```
Código que cria um gráfico em forma de histograma para visualização dos dados, utilizando o for para  percorremos toda a tabela para fazer todos os graficos de todas as colunas.

```python
for coluna in tabela:
    grafico = px.histogram(tabela, x = coluna ,color = 'Categoria')
    grafico.show()
```
    
## Aprendizagem
- Utilizando gráficos para vizualizar os dados , pode ser uma grande ferramenta para acharmos o problema envovido.

## Dificuldade
- Tratar corretamente os dados, avaliando valores nulos na tabela.