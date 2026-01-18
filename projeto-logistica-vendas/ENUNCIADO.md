# 🚚 Projeto: Otimização de Margens e Performance Logística (Hub Aveiro)

> **Status do Projeto:** Em Desenvolvimento 🛠️  
> **Responsável:** Arquele Tavares (Data Science Specialist)  
> **Solicitante:** Direção de Operações (O "Chefe")

---

## 📋 Cenário de Negócio
A nossa empresa centraliza a distribuição a partir do **Hub de Aveiro**. Enfrentamos um desafio crítico: o volume de vendas cresce, mas a margem de lucro está a diminuir. Suspeitamos que os custos de transporte e a ineficiência das transportadoras parceiras estão a comprometer a rentabilidade.

Os dados estão fragmentados: as vendas residem num servidor **SQL (MariaDB)**, enquanto as três transportadoras parceiras enviam relatórios mensais em **Excel** com estruturas de dados inconsistentes.

### 🎯 O Desafio do "Chefe"
O Diretor de Operações exige respostas baseadas em dados para as seguintes questões:
1. **Unificação de Dados:** É possível consolidar 3 fontes externas de logística com a base interna de vendas?
2. **Rastreio de Prejuízo:** Quais rotas (cidades) apresentam fretes superiores à margem da venda?
3. **Auditoria de Performance:** Qual transportadora é a mais célere e qual apresenta maior índice de atrasos?
4. **Métricas de Eficiência:** Qual o custo real por **KM** percorrido e por **KG** transportado?

---

## 🏗️ Arquitetura da Solução (Pipeline ETL)

O projeto utiliza o fluxo **Extract, Transform, Load (ETL)** para processar a informação:

1.  **Data Ingestion:** Extração de dados do MariaDB via `SQLAlchemy` e carregamento de arquivos flat (Excel).
2.  **Data Harmonization:** Padronização de chaves primárias (`id_pedido`) e limpeza de tipos de dados.
3.  **Intelligence Layer:** Criação de colunas calculadas: *Lucro Líquido*, *Custo/KM* e *Lead Time*.
4.  **Business Insights:** Geração de relatórios de exceção e exportação para tomada de decisão.

---

## 📊 Estrutura dos Dados

### Base de Vendas (SQL)
| Coluna | Descrição |
| :--- | :--- |
| `id_pedido` | Identificador único da venda (PK) |
| `cidade_destino` | Cidade de entrega |
| `valor_venda` | Valor bruto da transação |
| `peso_kg` | Peso físico da mercadoria |
| `distancia_km` | Distância calculada a partir de Aveiro |

### Relatórios Logísticos (Excel)
* **Transp. A:** Foco em envios rápidos (Coluna: `cod_envio`).
* **Transp. B:** Foco em carga pesada (Coluna: `ID_Venda`).
* **Transp. C:** Operação geral (Coluna: `id_pedido`).

---

## 🛠️ Tecnologias Utilizadas
* **Python 3.12**
* **Pandas:** Motor de transformação de dados.
* **SQLAlchemy:** Abstração de conexão com a Base de Dados.
* **MariaDB/MySQL:** Armazenamento relacional das vendas.

---

## 📉 Resultados Esperados
* Identificação de rotas com ROI negativo.
* Ranking de eficiência por transportadora.
* Otimização da escolha logística baseada no peso e distância.

---
_Este projeto faz parte do portfólio de Gestão de Informação e Ciência de Dados (Nível 5) - IEFP._
