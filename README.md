**🚀 Tech Challenge - Fase 3: Engenharia de Dados com AWS Glue & Spark
**Este repositório contém a solução desenvolvida para a etapa de processamento e transformação de dados do Tech Challenge (Fase 3). O projeto consiste em uma pipeline de dados serverless utilizando os recursos da AWS (Amazon Web Services) para catalogar, filtrar, transformar e armazenar dados da PNAD COVID-19 (Pesquisa Nacional por Amostra de Domicílios).


📌 Objetivo do Projeto
O objetivo principal deste script é extrair os dados brutos da pesquisa PNAD COVID-19 (previamente integrados e catalogados), realizar a seleção de variáveis críticas divididas em três pilares analíticos (Populacional, Clínico e Econômico) e salvar o resultado otimizado em formato colunar (.parquet) para futuras análises de People/Data Analytics e Business Intelligence.

Os pilares de análise foram estruturados da seguinte forma:

Pilar Populacional: Idade dos respondentes (a002).

Pilar Clínico: Sintomas reportados como febre (b0011), tosse (b0012), dificuldade respiratória (b0014) e busca por atendimento médico (b005).

Pilar Econômico (Vulnerabilidade): Recebimento de auxílio emergencial (f0021).


🛠️ Tecnologias e Ferramentas Utilizadas
Python / PySpark: Linguagem e motor de processamento distribuído para manipulação eficiente de grandes volumes de dados.

AWS Glue (Glue Context & DynamicFrames): Serviço de integração de dados serverless para extração e catalogação automatizada.

AWS Glue Data Catalog: Repositório de metadados utilizado para acessar a tabela de origem (tech_challenge_fase3_brunno).

Amazon S3 (Simple Storage Service): Armazenamento de objetos utilizado tanto para a zona de consumo dos dados brutos quanto para o destino da camada processada.

Apache Parquet: Formato de arquivo de armazenamento colunar, ideal para consultas analíticas de alta performance e redução de custos de armazenamento/processamento.


🚀 Estrutura do Script de ETL
O script em formato Jupyter Notebook (.ipynb) executa as seguintes etapas lógicas utilizando uma sessão do AWS Glue PySpark:

Ingestão de Dados: Carrega o DynamicFrame diretamente do catálogo de dados do Glue (db_hospital_pnad).

Seleção e Filtragem (Feature Selection): Reduz a dimensionalidade do dataset selecionando apenas as colunas de interesse (v0001, a002, b0011, b0012, b0014, b005, f0021).

Conversão e Validação: Converte o frame do Glue para um DataFrame Spark padrão para validação estrutural e exibição de amostras.

Escrita Otimizada: Exporta os dados finais consolidados de volta para o Amazon S3 em formato Parquet com o modo de escrita configurado para sobrescrever dados antigos (overwrite).


## 📂 Estrutura do Repositório

O repositório está organizado da seguinte forma para facilitar a navegação e execução do projeto:

```text
├── Tech_Challenge_03 - Brunno_Terceiro.ipynb: Jupyter Notebook configurado para o ambiente do Glue PySpark. Contém a lógica de extração do catálogo de dados, a seleção rigorosa das features da PNAD Covid-19 e o processo de salvamento em formato otimizado no Amazon S3.

├── Tech_Challenge_03 - Gráficos.pbix: Arquivo de relatório do Power BI contendo as modelagens visuais, gráficos gerenciais e os principais insights extraídos a partir das tabelas de pilares.

├── Resultados - Pilar_Econômico.csv: Arquivo de dados exportado contendo o agregador estatístico que cruza o recebimento de auxílio emergencial (recebeu_auxilio) com o respectivo resultado dos testes de COVID-19.

├── Resultados - Pilar_Populacional.csv: Dataset compilado contendo a distribuição demográfica dos indivíduos por idade (idade) e o volume histórico de registros associados a casos de internação.

├── Resultados - Pilar_Sintomas.csv: Base de dados sintetizada com o volume total de ocorrências combinadas para as variáveis clínicas de febre, tosse e dificuldade respiratória.

├── README.md: Este arquivo de documentação, responsável por centralizar o contexto do desafio, a arquitetura da solução em nuvem e a especificação técnica das entregas.
