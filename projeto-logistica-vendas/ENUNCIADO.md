# 🚚 Projeto de Business Intelligence – Hub Aveiro
## Otimização de Margens e Performance Logística

**Status do Projeto:** Em desenvolvimento 🛠️  
**Responsável:** Arquele Tavares  
**Solicitante:** Direção de Operações – Hub Aveiro

---

## 📋 Cenário do Projeto

A empresa centraliza a distribuição de mercadorias a partir do Hub de Aveiro. Apesar do aumento das vendas, foram identificados:

- Custos logísticos elevados que afetam a margem de lucro;
- Atrasos em entregas que impactam a satisfação do cliente;
- Fragmentação de dados entre várias transportadoras e a base de vendas interna.

Para responder a estes desafios, o projeto integra dados da **base de vendas (MariaDB/Linux)** com os **relatórios Excel das três transportadoras**, criando um dataset único e consistente para análise em BI.

---

## 🎯 Objetivos do Projeto

1. **Receção e Tratamento dos Dados**
   - Ler os ficheiros Excel das três transportadoras;
   - Corrigir nomes de colunas inconsistentes (`cod_envio`, `ID_Venda`, `id_pedido_c`);
   - Tratar valores nulos e inconsistências (`peso_kg`, `custo_frete`);
   - Preparar os dados para integração com a tabela de vendas.

2. **Extração da Tabela de Vendas**
   - Conexão à base MariaDB em Linux usando Python/SQLAlchemy;
   - Extração da tabela de vendas;
   - Limpeza e validação de dados: valores nulos, tipos corretos, consistência de chaves primárias.

3. **Integração e Consolidação**
   - Merge das tabelas de transportadoras com a tabela de vendas pelo `id_pedido`;
   - Inclusão de colunas essenciais na tabela final:
     - `transportadora` – qual empresa vai enviar cada pedido;
     - `data_prevista_entrega` – data calculada a partir do SLA;
     - `data_entrega` – data real considerando atrasos;
     - `prazo_entrega_dias` – SLA da transportadora;
     - `status_prazo` – indicador “No prazo” ou “Atrasado”.

4. **Criação de Colunas Calculadas (Indicadores de BI)**
   - **Lucro Estimado:** `valor_venda - custo_produto - custo_frete`;
   - **Margem Percentual:** `(LucroEstimado / valor_venda) * 100`;
   - **Custo Logístico por KM:** `custo_frete / distancia_km`;
   - **Custo Logístico por KG:** `custo_frete / peso_kg`;
   - **Lead Time:** diferença entre `data_venda` e `data_entrega`;
   - **Status de entrega:** identificação de atrasos.

5. **Preparação Final para BI**
   - Dataset final limpo e enriquecido com métricas;
   - Exportação para MariaDB/Linux para consulta direta em Power BI;
   - Estrutura pronta para criação de dashboards e KPIs estratégicos.

---

## 🏗️ Fluxo do Projeto (Pipeline ETL)

### 1️⃣ Extract (Extração)
- Carregamento das 3 tabelas de transportadoras em Excel;
- Conexão à base MariaDB/Linux e extração da tabela de vendas.

### 2️⃣ Transform (Tratamento e Harmonização)
- Normalização de nomes de colunas e chaves primárias;
- Tratamento de valores ausentes (`peso_kg` preenchido com média por categoria);
- Conversão de tipos de dados corretos (datas, numéricos);
- Cálculo de colunas derivadas (`LucroEstimado`, `MargemPercent`, `CustoPorKM`, `CustoPorKG`, `LeadTime`, `status_prazo`).

### 3️⃣ Load (Carregamento)
- Merge das tabelas de vendas e transportadoras;
- Exportação da tabela final para MariaDB/Linux;
- Disponibilização para análise em Power BI.

---

## 📊 Estrutura das Tabelas

### Base de Vendas (MariaDB/Linux)
| Coluna | Descrição |
|--------|-----------|
| id_pedido | Identificador único da venda |
| data_venda | Data da transação |
| cidade_destino | Cidade de entrega |
| categoria | Tipo de produto |
| valor_venda | Valor bruto da venda |
| peso_kg | Peso da mercadoria (preenchido após tratamento) |
| custo_produto | Custo do produto |
| distancia_km | Distância desde Aveiro |
| armazem_origem | Origem fixa: Aveiro |

### Tabelas das Transportadoras (Excel)
| Transportadora | Coluna ID | Custo | Prazo | Status |
|----------------|-----------|-------|-------|-------|
| Rápida A | cod_envio | custo_frete_a | dias_entrega_a | status_a |
| Pesada B | ID_Venda | frete_b | prazo_b | status_b |
| Geral C | id_pedido_c | custo_envio_c | dias_c | status_c |

> Estas tabelas apresentam pequenas inconsistências, intencionais para simular desafios reais de integração de dados.

### Tabela Final Consolidada
| Coluna | Descrição |
|--------|-----------|
| id_pedido | Identificador único da venda |
| data_venda | Data da transação |
| cidade_destino | Cidade de entrega |
| categoria | Tipo de produto |
| valor_venda | Valor bruto da venda |
| peso_kg | Peso da mercadoria (valores nulos preenchidos por média) |
| custo_produto | Custo do produto |
| custo_frete | Custo logístico da transportadora |
| transportadora | Nome da transportadora responsável pelo envio |
| prazo_entrega_dias | SLA da transportadora |
| data_prevista_entrega | Data prevista calculada a partir do SLA |
| data_entrega | Data real de entrega (considerando atrasos) |
| status_prazo | Indicador “No prazo” ou “Atrasado” |
| distancia_km | Distância desde Aveiro |
| armazem_origem | Origem fixa: Aveiro |
| LucroEstimado | Valor do lucro por venda |
| MargemPercent | Percentual de margem da venda |
| CustoPorKM | Custo por quilómetro transportado |
| CustoPorKG | Custo por quilograma transportado |
| LeadTime | Dias totais até a entrega |

---

## 🧠 Métricas e KPIs
- Ranking de transportadoras por eficiência (velocidade, atrasos, custo médio);
- Identificação de rotas com ROI negativo;
- Análise de categorias mais rentáveis;
- Simulações de cenários logísticos para decisões estratégicas:
  - Alterar transportadora
  - Variar peso ou distância
  - Avaliar impacto no lucro e margem

---

## 🛠️ Tecnologias Utilizadas
- **Python 3.12** – Criação e manipulação de dados, ETL
- **Pandas** – Tratamento, limpeza e transformação de dados
- **Excel** – Receção de relatórios das transportadoras
- **SQLAlchemy / MariaDB** – Extração e carregamento de dados em Linux
- **Power BI** – Visualização e análise de KPIs estratégicos
- **Linux (VM)** – Ambiente de base de dados e scripts
- **Apache** – Suporte à infraestrutura de dados

---

## 📉 Resultados Esperados
- Consolidação de **4 fontes de dados** num dataset único e limpo
- Identificação clara de **rotas e transportadoras críticas**
- Dashboards detalhados com métricas de eficiência e rentabilidade
- Demonstração prática de competências em:
  - Business Intelligence
  - Engenharia de Dados
  - SQL e Linux
  - Preparação de dados para análise em Power BI

---

📌 *Este projeto reflete a execução completa de um pipeline de BI corporativo, desde a receção de dados até à análise e visualização de métricas estratégicas.*
