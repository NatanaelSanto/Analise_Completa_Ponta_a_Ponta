# Projeto: Pipeline de BI Automatizado (Google Sheets para Power BI)

## 📋 Visão Geral
Este projeto consistiu na criação de um pipeline de dados robusto e escalável para transformar registros brutos coletados via Google Forms em um modelo de dados pronto para análise de alta performance no Power BI. O foco principal foi a transição de uma estrutura plana (tabela única) para um Modelo Dimensional (Star Schema).

## 🛠️ Tecnologias Utilizadas
Fonte de Dados: Google Sheets (via Google Forms).

ETL & Preparação: Power Query (M Language).

Modelagem de Dados: Power BI Desktop.

Metodologia: Esquema Estrela (Star Schema).

## 🏗️ Etapas do Desenvolvimento
### 1. Conexão e Automação de Dados
Estabelecimento de conexão dinâmica com o Google Sheets, garantindo que o processo de atualização seja 100% automático.

Configuração do Power Query como um "motor de receitas", onde cada nova entrada no formulário passa automaticamente por todas as etapas de limpeza sem intervenção manual.

### 2. Engenharia e Limpeza de Dados (ETL)
Padronização de Datas: Tratamento de conflitos de localidade (Locale) para converter formatos americanos/ISO em datas brasileiras, removendo a redundância de horas para otimizar a performance.

Sanitização de Strings: Aplicação de funções Trim (Remover espaços) e Capitalize Each Word para garantir que erros de digitação humana no formulário não gerassem duplicidades de produtos.

Deduplicação: Criação de uma Tabela Dimensão de Produtos (dim_products) através da remoção de duplicatas da base bruta, garantindo a integridade referencial.

### 3. Modelagem Dimensional e Governança
Criação de Chaves Primárias (IDs):

Desenvolvimento de IDs únicos para vendas (Ex: VND-001) e produtos (Ex: PRD-0001) usando Linguagem M.

Uso de funções de texto (Text.PadStart) para garantir que os IDs mantenham um alinhamento visual e organizacional profissional.

Relacionamento entre Tabelas (Mesclagem):

Substituição do relacionamento por nomes (instável) por relacionamentos via IDs Numéricos/Texto, utilizando a técnica de Mesclagem de Consultas.

Resolução de Problemas Técnicos: Identificação e correção de inflação de linhas causada pelo uso inadvertido de Fuzzy Matching (Correspondência Difusa), garantindo que a Fato_Vendas mantivesse a contagem exata de 87 registros originais.

### 4. Otimização de Arquitetura
Gerenciamento de Carga: Configuração de consultas como "Apenas Conexão" para as etapas intermediárias, reduzindo o consumo de memória RAM e o tamanho do arquivo final.

Preparação para o Power BI: Estruturação da consulta final (Fato_Vendas) contendo apenas as chaves (IDs) e valores métricos, seguindo as melhores práticas de mercado para BI.

## 📊 Resultados Alcançados
Integridade de Dados: O modelo é imune a mudanças de nomes de produtos; basta alterar na dimensão para que todo o histórico seja atualizado.

Escalabilidade: O sistema suporta o crescimento do volume de vendas sem necessidade de reprocessamento manual.

Performance: Modelo otimizado para filtragem rápida no Power BI através de chaves indexadas.

### 5. Inteligência de Dados (Linguagem DAX)
Para garantir cálculos precisos e performáticos, foram desenvolvidas medidas personalizadas utilizando DAX (Data Analysis Expressions), centralizadas em uma tabela exclusiva de medidas:

Total de Faturamento: Cálculo agregador do valor bruto de vendas.

Quantidade Vendida: Soma total de unidades transacionadas.

Ticket Médio: Métrica estratégica calculada via DIVIDE para identificar o valor médio por transação, permitindo análise de eficiência de vendas.

### 6. Visualização e Insights de Negócio
O Dashboard foi projetado com foco em User Experience (UX) e Storytelling, apresentando os seguintes insights:

Análise de Tendência: Gráfico de linhas correlacionando o Volume de Vendas vs. Ticket Médio, permitindo identificar picos de demanda e variações na rentabilidade.

Mix de Produtos (Pareto): Gráfico de pizza destacando o "Top 3 Faturamento", revelando que o item Cadeado é o principal gerador de receita (43% do faturamento do grupo).

Performance Comparativa: Gráficos de barras contrastando o faturamento por produto vs. a quantidade física vendida, essencial para identificar produtos de alto valor unitário vs. produtos de giro.

Design Clean: Interface com navegação intuitiva, cartões de KPI destacados e filtros temporais dinâmicos.

### 🔗 Acesso ao Projeto
Dashboard Interativo: CLIQUE AQUI PARA ACESSAR O RELATÓRIO ONLINE

Arquivo de Dados: O arquivo .pbix está disponível na pasta raiz deste repositório para consulta da estrutura de modelagem.

### 💡 Conclusão
Este projeto demonstra a capacidade de transformar dados desestruturados em ativos estratégicos. Através da aplicação de Star Schema e ETL avançado, o resultado final não é apenas um gráfico, mas um ecossistema de dados confiável que suporta a tomada de decisão baseada em fatos.
