# 🚚 Hub Aveiro – BI & Logística

## Descrição do Projeto

Este projeto simula um **pipeline completo de Business Intelligence** aplicado à logística de um hub central em Aveiro. Ele integra dados de vendas, transportadoras e métricas logísticas para análise de desempenho e tomada de decisão estratégica.

O foco principal é:
- Otimização de custos logísticos;
- Avaliação de performance das transportadoras;
- Análise de margem de lucro por produto, rota e categoria;
- Preparação de dados para dashboards em **Power BI**.

---

## 🎯 Objetivos da Análise

1. **Análise de Vendas e Custos**
   - Calcular lucro estimado por pedido: `LucroEstimado = valor_venda - custo_produto - custo_frete`.
   - Determinar margem percentual de cada venda: `(LucroEstimado / valor_venda) * 100`.
   - Identificar categorias de produtos mais rentáveis.

2. **Avaliação Logística**
   - Medir **eficiência das transportadoras**: custo médio por pedido, atrasos e SLA.
   - Analisar **custo por km** e **custo por kg**: `CustoPorKM = custo_frete / distancia_km`, `CustoPorKG = custo_frete / peso_kg`.
   - Determinar lead time real vs. previsto e status de entrega.

3. **Simulações Estratégicas**
   - Comparar diferentes transportadoras para cada rota.
   - Avaliar impacto de variações de peso, distância ou custo no lucro.
   - Identificar rotas com ROI negativo para decisões de melhoria.

---

## 🗂️ Estrutura de Dados

### 1️⃣ Base de Vendas (MariaDB/Linux)

| Coluna | Descrição |
|--------|-----------|
| id_pedido | Identificador único do pedido |
| data_venda | Data da transação |
| cidade_destino | Cidade de entrega |
| categoria | Tipo de produto |
| valor_venda | Valor da venda |
| peso_kg | Peso do produto (tratado e preenchido) |
| custo_produto | Custo do produto |
| distancia_km | Distância desde o armazém de Aveiro |
| armazem_origem | Origem da mercadoria (Aveiro) |

### 2️⃣ Transportadoras (Excel)

| Transportadora | Coluna ID | Custo | Prazo (SLA) | Status |
|----------------|-----------|-------|-------------|--------|
| Rápida A | cod_envio | custo_frete_a | dias_entrega_a | status_a |
| Pesada B | ID_Venda | frete_b | prazo_b | status_b |
| Geral C | id_pedido_c | custo_envio_c | dias_c | status_c |

> As tabelas podem conter inconsistências intencionais para simular desafios reais de integração.

### 3️⃣ Tabela Consolidada Final

| Coluna | Descrição |
|--------|-----------|
| id_pedido | Identificador do pedido |
| data_venda | Data da transação |
| cidade_destino | Cidade de entrega |
| categoria | Tipo de produto |
| valor_venda | Valor da venda |
| peso_kg | Peso do produto |
| custo_produto | Custo do produto |
| custo_frete | Custo logístico da transportadora |
| transportadora | Nome da transportadora responsável |
| prazo_entrega_dias | SLA da transportadora |
| data_prevista_entrega | Data calculada a partir do SLA |
| data_entrega | Data real de entrega |
| status_prazo | No prazo / Atrasado |
| distancia_km | Distância desde Aveiro |
| armazem_origem | Origem (Aveiro) |
| LucroEstimado | Valor do lucro por pedido |
| MargemPercent | Percentual de margem |
| CustoPorKM | Custo por quilómetro transportado |
| CustoPorKG | Custo por quilograma transportado |
| LeadTime | Dias até entrega real |

---

## 🔄 Fluxo do Projeto (Pipeline ETL)

1. **Extract (Extração)**
   - Importação dos ficheiros Excel das transportadoras.
   - Extração da tabela de vendas do MariaDB/Linux.

2. **Transform (Tratamento e Enriquecimento)**
   - Limpeza de dados: valores nulos, tipos corretos, nomes de colunas consistentes.
   - Merge das transportadoras com a tabela de vendas pelo `id_pedido`.
   - Criação de métricas derivadas para análise de BI.

3. **Load (Carregamento)**
   - Exportação do dataset final para MariaDB/Linux.
   - Disponibilização para **Power BI** através de conexão direta com o servidor.

---

## 📊 KPIs e Métricas Principais

- **Lucro estimado** e **margem percentual** por pedido, categoria e transportadora.
- **Custo logístico por km** e **por kg**.
- **Lead time médio** vs. SLA e atrasos.
- Ranking de transportadoras por eficiência e custo.
- Identificação de rotas críticas e produtos com baixa rentabilidade.
- Simulação de cenários para decisões estratégicas.

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.12** – Manipulação e tratamento de dados.
- **Pandas** – Limpeza, transformação e análise.
- **MariaDB/Linux** – Base de dados central.
- **SQLAlchemy** – Conexão e ETL em Python.
- **Excel** – Receção de relatórios das transportadoras.
- **Power BI** – Criação de dashboards e análise visual.
- **Linux (VM)** – Ambiente de execução do pipeline.
- **Apache** – Suporte à infraestrutura de dados.

---

## 🎯 Resultados Esperados

- Dataset consolidado e limpo, pronto para análise em Power BI.
- Insights claros sobre **margens, custos logísticos e eficiência das transportadoras**.
- Dashboards estratégicos para tomada de decisão baseada em dados.
- Demonstração prática de competências em:
  - **Business Intelligence**
  - **Engenharia de Dados**
  - **SQL e Linux**
  - **Preparação de dados para análise visual**

---

📌 *Este projeto representa um pipeline completo de BI corporativo, desde extração e tratamento de dados até análise estratégica de logística e performance de vendas.*
