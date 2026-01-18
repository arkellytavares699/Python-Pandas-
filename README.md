# 📊 Pandas — Guia Prático para Análise de Dados em Python

Este repositório é um **manual claro, directo e utilizável** para trabalhar com a biblioteca **pandas**, uma das ferramentas centrais da análise de dados em Python.

Aqui encontras desde conceitos fundamentais até exemplos práticos usados em **análise de dados, ciência de dados e automação**.

---

## 🐼 O que é o pandas?

O **pandas** é uma biblioteca Python de alto desempenho para **manipulação e análise de dados estruturados**. Trabalha sobretudo com:

* **Series** → dados unidimensionais
* **DataFrames** → tabelas bidimensionais (semelhantes a folhas de Excel ou tabelas SQL)

É amplamente utilizado em:

* Análise de dados
* Ciência de dados
* Business Intelligence
* Machine Learning
* ETL e automação

---

## ⚙️ Instalação

```bash
pip install pandas
```

Ou, com Anaconda:

```bash
conda install pandas
```

---

## 🚀 Importação básica

```python
import pandas as pd
```

---

## 🧱 Estruturas principais

### 📌 Series

```python
s = pd.Series([10, 20, 30, 40])
print(s)
```

---

### 📌 DataFrame

```python
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [25, 30, 35],
    'Cidade': ['Lisboa', 'Porto', 'Aveiro']
})

print(df)
```

---

## 📂 Leitura e escrita de dados

### Ler ficheiros

```python
pd.read_csv('dados.csv')
pd.read_excel('dados.xlsx')
pd.read_json('dados.json')
```

### Guardar ficheiros

```python
df.to_csv('output.csv', index=False)
df.to_excel('output.xlsx', index=False)
```

---

## 🔍 Exploração de dados

```python
df.head()
df.tail()
df.info()
df.describe()
df.shape
df.columns
```

Estas funções dão-te uma **radiografia rápida** do conjunto de dados.

---

## 🧹 Limpeza de dados

### Valores nulos

```python
df.isna()
df.dropna()
df.fillna(0)
```

### Remover duplicados

```python
df.drop_duplicates()
```

---

## 🎯 Seleção de dados

```python
df['Nome']
df[['Nome', 'Idade']]

df.loc[0]
df.iloc[0]
```

### Filtros

```python
df[df['Idade'] > 30]
```

---

## 🔄 Operações comuns

### Ordenação

```python
df.sort_values(by='Idade', ascending=False)
```

### Agrupamento

```python
df.groupby('Cidade')['Idade'].mean()
```

---

## 🧮 Estatísticas básicas

```python
df['Idade'].mean()
df['Idade'].sum()
df['Idade'].min()
df['Idade'].max()
```

---

## 🔗 Junções (merge)

```python
pd.merge(df1, df2, on='id', how='inner')
```

Tipos de junção:

* `inner`
* `left`
* `right`
* `outer`

---

## 📈 Integração com visualização

O pandas funciona muito bem com:

* matplotlib
* seaborn
* plotly

Exemplo rápido:

```python
df['Idade'].plot(kind='hist')
```

---

## 🧠 Boas práticas

* Usa nomes de colunas claros
* Evita loops quando podes usar operações vetorizadas
* Explora `.apply()` com moderação
* Confirma sempre tipos de dados (`df.dtypes`)

---

## 📚 Recursos úteis

* Documentação oficial: [https://pandas.pydata.org/docs/](https://pandas.pydata.org/docs/)
* Pandas Cookbook
* Kaggle Datasets

---

## 📜 Licença

Este projeto está sob licença MIT. Consulta o ficheiro `LICENSE` para mais informações.

---

✨ **Se sabes trabalhar com pandas, sabes conversar com dados.**
