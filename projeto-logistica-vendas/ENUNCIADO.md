# 🌍 COVID-19 Global Data Analysis Pipeline

## 🔹 Descrição do Projeto
Este projeto tem como objetivo construir um **pipeline completo de Business Intelligence (BI) aplicado a dados globais de COVID-19**. Os dados são coletados de fontes oficiais, tratados no Python, armazenados em uma base SQL em Linux e disponibilizados em dashboards interativos no Power BI.  

O foco principal é transformar dados brutos em **insights estratégicos**, permitindo análises de evolução de casos e mortes, tendências por país e continente, além de métricas normalizadas por população.

---

## 🛑 Problema
A pandemia de COVID-19 gerou um grande volume de dados diários, vindos de múltiplas fontes globais, muitas vezes **incompletos ou inconsistentes**.  
Os desafios principais são:  
- Dados diários com diferentes formatos e códigos de países  
- Valores nulos ou inconsistentes na população ou nos casos reportados  
- Necessidade de consolidar os dados em **uma única base confiável** para análise  
- Preparação para dashboards que permitam insights visuais rápidos  

---

## 🎯 Objetivos
1. Extrair dados globais oficiais de COVID-19 (ECDC)  
2. Tratar e limpar os dados no Python usando Pandas  
3. Criar métricas derivadas relevantes:  
   - Casos e mortes acumuladas  
   - Casos ativos  
   - Taxa de mortalidade  
   - Casos por 100.000 habitantes  
4. Armazenar os dados tratados em **MariaDB/Linux**  
5. Gerar dashboards interativos no Power BI com métricas globais e por continente/país  

---

## 🧰 Metodologia / Pipeline ETL

### 1️⃣ Extract – Extração
- Fonte: [ECDC](https://pandemicdatalake.blob.core.windows.net/public/curated/covid-19/ecdc_cases/latest/ecdc_cases.csv)  
- CSV global com colunas: `date_rep, cases, deaths, countries_and_territories, country_territory_code, pop_data_2018, continent_exp`  
- Dados carregados no Pandas para tratamento inicial  

### 2️⃣ Transform – Transformação
- Limpeza de colunas desnecessárias (`day`, `month`, `year`, `geo_id`, `load_date`, `iso_country`, `daterep`)  
- Conversão de datas para tipo `datetime`  
- Preenchimento de valores nulos na população (`NaN`)  
- Criação de métricas derivadas:  
  - **Casos acumulados** por país  
  - **Mortes acumuladas**  
  - **Casos por 100.000 habitantes**  
  - **Taxa de mortalidade**  
- Filtragem de países ou continentes para análises específicas  

### 3️⃣ Load – Carregamento
- Base de dados: **MariaDB no Linux**  
- Criação de tabela `covid_global_data`  
- Inserção do DataFrame Pandas tratado na base SQL  
- Garantia de integridade e padronização de tipos  

### 4️⃣ Visualização – Power BI
- Conexão direta ao MariaDB  
- Dashboards interativos por país e continente  
- KPIs e gráficos de tendência:  
  - Evolução diária e acumulada de casos e mortes  
  - Comparação entre países e continentes  
  - Casos normalizados por população  
  - Alertas de crescimento rápido  

---

## 📊 Tecnologias Utilizadas
- **Python 3.12** – ETL e tratamento de dados  
- **Pandas** – Limpeza, transformação e criação de métricas  
- **SQL (MariaDB/Linux)** – Armazenamento estruturado e seguro  
- **Power BI** – Visualização, dashboards e análise interativa  
- **CSV oficial ECDC** – Fonte confiável e atualizada  

---

## 📝 Estrutura do Dataset
| Coluna | Significado |
|--------|------------|
| `date_rep` | Data do relatório (YYYY-MM-DD) |
| `cases` | Novos casos diários confirmados |
| `deaths` | Novas mortes diárias |
| `countries_and_territories` | Nome do país/território |
| `country_territory_code` | Código ISO Alpha-3 do país |
| `pop_data_2018` | População do país (2018) |
| `continent_exp` | Continente do país |

---

## 💡 Resultados Esperados
- Dataset consolidado, limpo e estruturado pronto para análise  
- Métricas claras e dashboards interativos para monitorar a evolução da pandemia  
- Possibilidade de comparar países, continentes e analisar tendências globais  

---

## 🚀 Como Executar
1. Clonar o repositório:  
```bash
git clone https://github.com/seu-usuario/covid-global-dashboard.git

