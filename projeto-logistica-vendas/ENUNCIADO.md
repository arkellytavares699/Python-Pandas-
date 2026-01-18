🚚 Projeto: Otimização de Margens e Performance Logística (Hub Aveiro)
Status do Projeto: Em Desenvolvimento 🛠️

Responsável: Arquele Tavares (Data Science Specialist)

Solicitante: Direção de Operações (O "Chefe")

📋 Cenário de Negócio (A Simulação)
A nossa empresa centraliza a distribuição a partir do Hub de Aveiro. Atualmente, enfrentamos um problema crítico: o volume de vendas cresce, mas a margem de lucro está a diminuir. Suspeitamos que os custos de transporte e a ineficiência das transportadoras parceiras estão a "comer" o nosso lucro.

Os dados estão espalhados: as vendas estão no nosso servidor SQL (MariaDB), mas as três transportadoras com que trabalhamos enviam relatórios mensais em Excel com formatos completamente diferentes.

🎯 O Desafio do Chefe
O Diretor de Operações exigiu respostas para as seguintes perguntas:

Visibilidade Total: Conseguimos unificar os dados de 3 transportadoras diferentes com a nossa base de vendas SQL?

Rastreio de Prejuízo: Quais são as rotas (Cidades) onde o frete é tão caro que a venda dá prejuízo?

Auditoria de Performance: Qual transportadora é a mais rápida e qual cumpre melhor os prazos de entrega?

Eficiência de Carga: Qual é o nosso custo real por quilómetro percorrido e por quilo transportado?

🏗️ Arquitetura da Solução
Para resolver este problema, o projeto foi estruturado em 4 etapas de Engenharia e Ciência de Dados:

Data Ingestion (SQL + Pandas): * Importação da base de dados de vendas para o MariaDB.

Conexão via SQLAlchemy para extração automatizada.

Data Harmonization (ETL): * Padronização de nomes de colunas (IDs de pedidos inconsistentes).

União de tabelas (concat) e cruzamento de dados (merge).

Intelligence Layer (Cálculos): * Criação de métricas de negócio: Lucro Líquido, Custo/KM e Lead Time (Dias de entrega).

Business Insights: * Geração de relatórios de exceção (Alerta de Lucro Negativo).

📊 Estrutura dos Dados Fonte
Vendas (SQL): id_pedido, data_venda, cidade_destino, categoria, valor_venda, peso_kg, distancia_km.

Transportadora A (Excel): Foco em envios rápidos, usa cod_envio.

Transportadora B (Excel): Foco em grandes volumes, usa ID_Venda.

Transportadora C (Excel): Operação geral, usa id_pedido.

🛠️ Tecnologias Utilizadas
Python 3.12

Pandas (Tratamento e análise)

SQLAlchemy (Ponte entre Python e SQL)

MariaDB / MySQL (Armazenamento de dados de vendas)

📈 Resultados Esperados
Redução de custos logísticos através da escolha da transportadora certa por rota.

Identificação de categorias de produtos que não suportam o custo de frete atual.

Dashboard de performance de entrega para renegociação de contratos.
