# 🚚 Projeto de Business Intelligence – Hub Aveiro
## Otimização de Margens e Performance Logística

**Status do Projeto:** Em desenvolvimento 🛠️  
**Responsável:** Arquele Tavares  
**Perfil:** Técnico Especialista em Gestão de Informação e Ciência de Dados (Nível 5 – IEFP)  
**Solicitante:** Direção de Operações – Hub Aveiro

---

## 📋 Cenário de Negócio

A empresa centraliza a distribuição de mercadorias a partir do **Hub de Aveiro**. Apesar do crescimento consistente do volume de vendas, observa-se uma **redução contínua da margem de lucro**, indicando que custos logísticos elevados e ineficiências operacionais nas transportadoras parceiras estão a impactar negativamente a rentabilidade.

Os dados disponíveis refletem um cenário realista e desafiante:

- 📦 **Vendas** simuladas com Python/Pandas, com possibilidade de integração futura em **MariaDB/MySQL** em **Linux (VM)**  
- 📊 **Relatórios mensais de três transportadoras**, em ficheiros Excel, com:
  - Colunas inconsistentes (`cod_envio`, `ID_Venda`, `id_pedido_c`)
  - Valores ausentes
  - Status de entrega variável

O objetivo é consolidar estas fontes num **pipeline de Business Intelligence**, garantindo qualidade dos dados e suporte à decisão estratégica.

---

## 🎯 Objetivos do Projeto

### 1️⃣ Integração e Harmonização de Dados
- Consolidação da base de vendas com ficheiros Excel de transportadoras
- Normalização de chaves primárias (`id_pedido`)
- Padronização de nomes de colunas inconsistentes
- Tratamento de valores nulos e pequenos erros simulados (`peso_kg` ausente)
- Preparação dos dados para análises e visualizações

### 2️⃣ Cálculo de Indicadores Financeiros e Logísticos
- 💰 **Lucro Estimado** = `valor_venda - custo_produto - custo_frete`
- 📈 **Margem Percentual** = Lucro / `valor_venda` * 100
- 🚛 **Custo Logístico por KM** e por KG transportado
- ⏱️ **Lead Time de entrega**
- ⚠️ **Indicador de atraso**
- 📍 **ROI por rota e cidade de destino**

### 3️⃣ Análise de Performance das Transportadoras
- Ranking por:
  - Velocidade de entrega
  - Taxa de atrasos (`status_a`, `status_b`, `status_c`)
  - Custo médio logístico
- Identificação de transportadoras com maior impacto negativo na margem
- Análise de rotas críticas com ROI negativo

### 4️⃣ Suporte à Tomada de Decisão
- Dashboards analíticos (Power BI e/ou Python)
- Relatórios de exceção e alertas operacionais
- Simulações de cenários logísticos:
  - Alteração de transportadora
  - Variação de distância, peso e custo
- Apoio à otimização estratégica da rede logística

---

## 🏗️ Arquitetura da Solução (Pipeline ETL)

### 🔹 Extract (Extração)
- Leitura de ficheiros Excel das transportadoras com Pandas
- Criação da tabela de vendas simulada via Python
- Possibilidade de extração futura de **MariaDB/MySQL** alojada em Linux (VM)

### 🔹 Transform (Transformação)
- Harmonização das chaves primárias (`id_pedido`)
- Normalização de colunas inconsistentes
- Limpeza e validação de dados (valores ausentes e pequenos erros)
- Criação de colunas calculadas:
  - `LucroEstimado`
  - `MargemPercent`
  - `CustoPorKM`
  - `CustoPorKG`
  - `LeadTime`
  - `Atrasado`

### 🔹 Load (Carregamento)
- Escrita dos dados tratados em Excel e/ou base MariaDB
- Preparação da camada analítica para BI

---

## 🧠 Camada de Inteligência (Intelligence Layer)
- Métricas agregadas por:
  - Transportadora
  - Cidade / Rota
  - Categoria de produto
  - Período temporal
- KPIs estratégicos de rentabilidade e eficiência
- Identificação automática de outliers logísticos

---

## 📊 Estrutura das Tabelas

### 📁 Base de Vendas (simulada em Python)
| Coluna | Descrição |
|--------|-----------|
| id_pedido | Identificador único da venda |
| data_venda | Data da transação |
| cidade_destino | Cidade de entrega |
| categoria | Tipo de produto |
| valor_venda | Valor bruto da venda |
| peso_kg | Peso da mercadoria (alguns nulos) |
| custo_produto | Custo do produto |
| distancia_km | Distância a partir de Aveiro |
| armazem_origem | Origem (fixo: Aveiro) |

### 📁 Relatórios Logísticos (Excel)
| Transportadora | Coluna ID | Custo | Prazo | Status |
|----------------|-----------|-------|-------|-------|
| Rápida A | cod_envio | custo_frete_a | dias_entrega_a | status_a |
| Pesada B | ID_Venda | frete_b | prazo_b | status_b |
| Geral C | id_pedido_c | custo_envio_c | dias_c | status_c |

> ⚠️ As colunas apresentam inconsistências e valores ausentes propositais para simular cenários reais de negócio.

---

## 🛠️ Tecnologias Utilizadas
- 🐍 **Python 3.12** – Criação de dados e ETL
- 📊 **Pandas** – Manipulação e tratamento de dados
- 🗄️ **Excel** – Relatórios logísticos externos
- 🔗 **SQLAlchemy / MariaDB** – Futuro carregamento para base relacional Linux (VM)
- 🐧 **Linux (VM)** – Ambiente de dados e serviços
- 🌐 **Apache** – Demonstração de serviços e infraestrutura

---

## 📉 Resultados Esperados
- Consolidação de **4 fontes de dados** num dataset único e limpo
- Identificação clara de **rotas com ROI negativo**
- Ranking detalhado de eficiência por transportadora
- Simulações logísticas baseadas em custo, peso, distância e categoria
- Dashboards analíticos para suporte à decisão
- Demonstração prática de competências em:
  - Business Intelligence
  - Engenharia de Dados
  - Linux e bases de dados

---

📌 *Projeto desenvolvido para fins académicos e de portfólio no âmbito do Curso Nível 5 – Gestão de Informação e Ciência de Dados (IEFP).*

