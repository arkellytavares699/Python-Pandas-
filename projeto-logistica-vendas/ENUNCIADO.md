# 🚚 Projeto de Business Intelligence: Otimização de Margens e Performance Logística (Hub Aveiro)

> **Status do Projeto:** Em Desenvolvimento 🛠️  
> **Responsável:** Arquele Tavares (Técnico Especialista em Gestão de Informação e Ciência de Dados)  
> **Solicitante:** Direção de Operações (Hub Aveiro)

---

## 📋 Cenário de Negócio

A empresa centraliza a distribuição de mercadorias a partir do **Hub de Aveiro**. Apesar do crescimento do volume de vendas, observa-se uma **redução contínua da margem de lucro**, sugerindo que **custos logísticos elevados e ineficiências nas transportadoras parceiras** estão a impactar a rentabilidade.  

Os dados disponíveis estão **fragmentados e inconsistentes**:  

- Vendas registradas no **MariaDB (SQL)**  
- Relatórios mensais de **três transportadoras** enviados em **Excel**, cada um com colunas diferentes, valores ausentes e pequenas inconsistências  

O objetivo é consolidar estas informações num **pipeline de Business Intelligence**, permitindo análises estratégicas e decisões baseadas em dados.

---

## 🎯 Objetivos do Projeto

1. **Integração e Harmonização de Dados**  
   - Consolidar as bases de vendas e transportadoras, lidando com **nomes de colunas inconsistentes, valores ausentes e erros de digitação**.  
   - Preparar os dados para análises avançadas e criação de KPIs.

2. **Cálculo de Indicadores Financeiros e Logísticos**  
   - Lucro estimado e margem percentual por venda  
   - Custo logístico por **km** e por **kg** transportado  
   - Lead time e atraso de entrega  
   - ROI por rota/cidade

3. **Análise de Performance das Transportadoras**  
   - Ranking de eficiência baseado em velocidade de entrega e atrasos  
   - Identificação de transportadoras com maior custo ou menor confiabilidade  
   - Determinar quais rotas impactam negativamente a rentabilidade

4. **Suporte à Tomada de Decisão**  
   - Relatórios visuais em **Power BI** ou Python, permitindo **simulações e otimizações logísticas**  
   - Identificação de melhorias operacionais e estratégicas

---

## 🏗️ Arquitetura da Solução (Pipeline ETL)

O projeto segue o fluxo **Extract, Transform, Load (ETL)**:

1. **Data Ingestion**  
   - Extração de dados da base SQL (MariaDB)  
   - Carregamento de arquivos Excel das transportadoras  

2. **Data Harmonization**  
   - Padronização de chaves primárias (`id_pedido`)  
   - Normalização de colunas com nomes inconsistentes  
   - Tratamento de valores ausentes e correção de erros de digitação

3. **Intelligence Layer**  
   - Criação de colunas calculadas:  
     - `LucroEstimado`  
     - `MargemPercent`  
     - `CustoPorKM` e `CustoPorKG`  
     - `LeadTime` e indicador `Atrasado`  

4. **Business Insights**  
   - Dashboards e relatórios de exceção  
   - Rankings de transportadoras e rotas  
   - Identificação de oportunidades de otimização de custos

---

## 📊 Estrutura das Tabelas

### Base de Vendas (SQL)
| Coluna | Descrição |
| :--- | :--- |
| `ID_Pedido` | Identificador único da venda (PK) |
| `DataVenda` | Data da transação |
| `CidadeDestino` | Cidade de entrega |
| `ValorVenda` | Valor bruto da venda |
| `PesoKG` | Peso da mercadoria |
| `DistanciaKM` | Distância calculada a partir de Aveiro |
| `ArmazemOrigem` | Local de origem (fixo: Aveiro) |
| `TipoFrete` | Transportadora associada |
| `StatusEntrega` | Estado da entrega (Entregue, Em trânsito, Atrasado, etc.) |
| `DataPrevEntrega` | Data prevista de entrega |
| `LucroEstimado` | Valor estimado de lucro |
| `MargemPercent` | Margem percentual da venda |

### Relatórios Logísticos (Excel)
| Transportadora | Coluna de ID | Observações |
| :--- | :--- | :--- |
| **Rápida A** | `cod_envio` | Envio rápido, baixa margem de erro |
| **Pesada B** | `ID_Venda` | Carga pesada, prazo maior |
| **Geral C** | `id_pedido` | Operação geral, status variável, atrasos simulados |

> **Observação:** As colunas podem apresentar inconsistências de nomes, valores ausentes ou erros de digitação, simulando a realidade de operações logísticas.

---

## 🛠️ Tecnologias Utilizadas
- **Python 3.12**  
- **Pandas:** Manipulação e tratamento de dados  
- **SQLAlchemy:** Conexão e extração de dados do MariaDB  
- **MariaDB/MySQL:** Base relacional de vendas  
- **Excel:** Relatórios das transportadoras  

---

## 📉 Resultados Esperados
- Consolidação das 4 fontes de dados em **dataset único e limpo**  
- Identificação de **rotas com ROI negativo**  
- Ranking detalhado de eficiência por transportadora  
- Simulações de **cenários logísticos** considerando peso, distância e custo  
- Dashboards para apoio à tomada de decisão  

---

> _Este projeto faz parte do portfólio de Gestão de Informação e Ciência de Dados (Nível 5) - IEFP._

