# Olá, eu sou o Diogo 👋

Desenvolvedor de software com foco em backend e 2 anos de experiência em serviços de integração com APIs REST, código modular com orientação a objetos, tratamento de exceções, testes automatizados e pipelines de dados com grandes volumes, com forte base em bancos relacionais com SQL Server, PostgreSQL e Oracle e otimização de consultas. Trabalhou em projetos de consultoria para cooperativas de crédito, fintechs, seguradoras e e-commerce, transformando requisitos de negócio em funcionalidades em ambiente ágil.

## 💼 Experiência

- 🔗 **Integrações e pipelines**: desenvolvimento e manutenção de fluxos ETL/ELT e integrações entre sistemas para clientes de varejo, shopping centers, cooperativa financeira e alimentos, do levantamento de requisitos à entrega
- 🎯 **Plataformas de marketing e CDPs**: modelagem de tabelas para segmentação de audiências e integração com Salesforce Marketing Cloud, Salesforce Data Cloud, Oracle Responsys, Oracle Unity, Insider e mParticle
- 📊 **Dados em mídia paga**: dashboards e acompanhamento de KPIs de campanhas em Google Ads, Meta Ads e GA4
- 🤖 **Freelancer**: automações com n8n, Make e Python, chatbots com IA, web scraping e sites em WordPress
- ⚙️ **Operações**: mapeamento de processos, relatórios e padronização com POPs e Kanban

## 🚀 Projetos

### 🛒 [Plataforma de dados para e-commerce com agente de IA](https://github.com/diogorblessa/projeto-pipeline-ELT-engenharia-supabase-dbt)
Pipeline ELT de ponta a ponta: extrai arquivos Parquet de um bucket S3, carrega no PostgreSQL (Supabase) e transforma com dbt até um modelo dimensional com data marts por área de negócio (Vendas, Customer Success e Pricing). Sobre essa base rodam duas aplicações: um dashboard em Streamlit com uma página por diretoria e um agente no Telegram que usa a API do Claude com tool use para responder perguntas consultando o banco e gerar relatórios executivos.

- 🏗️ **Arquitetura**: monorepo com uv workspace e pacotes independentes para extração/carga e para transformação; arquitetura medalhão com Bronze (views que servem de contrato do dado bruto), Silver (limpeza, tipagem, deduplicação e integridade referencial) e Gold (dimensões, fatos e marts); agente com dois modos de execução, interativo por polling e standalone para agendamento via cron
- 🧪 **Testes e qualidade de código**: testes unitários com pytest, isolando dependências externas com mocks de boto3 e SQLite em memória; lint e formatação com ruff
- 🔒 **Segurança**: configuração tipada com pydantic-settings e `SecretStr`, credenciais só no `.env` e nunca nos logs; o agente executa apenas consultas de leitura (`SELECT`/`WITH`)
- 🐳 **Reprodutibilidade**: ambiente em Docker e docker-compose e um script que roda carga e transformação em sequência
- 📄 **Documentação**: especificação (PRD) para os modelos dbt, o dashboard e o agente, além do schema completo das tabelas Gold
- 🧰 **Ferramentas**: Python, uv, boto3, pandas, SQLAlchemy, dbt, PostgreSQL, Streamlit, Claude API, python-telegram-bot, Docker, pytest, ruff

### 🏦 [Pipeline de reclamações contra bancos](https://github.com/diogorblessa/mvp_engenharia_de_dados_puc)
Pipeline no Databricks que leva mais de 10 milhões de reclamações públicas do consumidor.gov.br do arquivo bruto até um esquema estrela, para responder quais problemas mais crescem nas reclamações contra bancos e se a resolução está piorando.

- 🏗️ **Arquitetura**: arquitetura medalhão no Unity Catalog, com um notebook por etapa e responsabilidade única (ingestão, perfilamento, limpeza, modelagem, catálogo e análise) e um script local de download separado da plataforma
- 🔁 **Idempotência**: toda gravação recria a tabela e o script de download pula arquivos já válidos, então qualquer etapa pode ser executada de novo sem duplicar dados
- ✅ **Fail fast e qualidade de dados**: verificações com `assert` que interrompem a execução antes de gravar (nenhuma conversão perde valor, chaves únicas, integridade referencial, totais que batem entre camadas) e perfilamento com hipóteses testadas sobre os dados brutos
- 🧭 **Rastreabilidade**: manifesto com o SHA-256 de cada arquivo de origem (linhagem desde a fonte), colunas de controle de ingestão e catálogo com a descrição de todas as tabelas e colunas
- 🧩 **Modelagem**: chaves substitutas determinísticas com `xxhash64`, junk dimension e decisões de modelagem justificadas por evidências medidas nos dados
- 🛠️ **Fluxo de desenvolvimento**: notebooks versionados no Git e sincronizados com o workspace via Git folder, desenvolvimento no VS Code com databricks-connect e commits semânticos com guia próprio
- 🧰 **Ferramentas**: Databricks, PySpark, SQL, Delta Lake, Unity Catalog, databricks-connect, VS Code, uv

### 💳 [Previsão de churn de cartão de crédito](https://github.com/diogorblessa/mvp-credit-card-churn-parte-01)
Classificação binária supervisionada que prevê se um cliente vai cancelar o cartão, numa base desbalanceada (cerca de 16% de churn). O projeto vai da análise exploratória e do pré-processamento à modelagem, otimização e avaliação, chegando a F1 de 0,91 e ROC-AUC de 0,99 no conjunto de teste.

- 🔬 **Método**: baseline como piso a ser superado, comparação de 5 modelos de famílias diferentes com validação cruzada e otimização de hiperparâmetros com `RandomizedSearchCV`
- 📏 **Métricas**: F1, recall e ROC-AUC da classe de churn em vez de acurácia, com avaliação final em dados não vistos, análise de erros e importância das variáveis
- 🛡️ **Prevenção de vazamento de dados**: remoção de colunas derivadas do alvo, divisão estratificada antes de qualquer ajuste e pré-processamento dentro de um `Pipeline` com `ColumnTransformer`, ajustado só no treino
- 🔁 **Reprodutibilidade**: semente única em todas as etapas, versões e hiperparâmetros registrados em metadados e pipeline final salvo com joblib para reuso
- 🧪 **Análise exploratória**: hipóteses de negócio testadas e fechadas com evidência, tratamento de multicolinearidade, encoding, outliers por IQR, variáveis derivadas e transformação logarítmica
- 🧰 **Ferramentas**: Python, pandas, NumPy, scikit-learn, XGBoost, matplotlib, seaborn, joblib, Google Colab
- 📂 **Repositórios**: [Parte 1: análise exploratória e pré-processamento](https://github.com/diogorblessa/mvp-credit-card-churn-parte-01) e [Parte 2: modelagem e avaliação](https://github.com/diogorblessa/mvp-credit-card-churn-parte-02)

### 📋 [JobFlow](https://github.com/diogorblessa/jobflow)
Plataforma para profissionais de tecnologia organizarem candidaturas a vagas, criada na Imersão Engenharia de Software da Alura com o Google. Integra uma aplicação web em React e TypeScript a um agente de IA em Python com Google ADK, que analisa de forma honesta e fundamentada a aderência do perfil do candidato aos requisitos de cada vaga.

- 🖥️ **Frontend**: cadastro, edição, busca e filtro de candidaturas em 8 etapas do processo seletivo, alertas de prazo e perfil profissional; código organizado em componentes, serviços, tipos e utilitários, com persistência em `localStorage`
- 🤖 **Agente**: separação de responsabilidades em módulos de configuração, prompt e ferramentas; skill com divulgação progressiva, carregada sob demanda; regra de ativação que pede só os dados que faltam; classificação de cada requisito em atendido, parcial ou lacuna e reanálise comparada à análise anterior
- 🔒 **Segurança e menor privilégio**: o agente só tem ferramentas de leitura e escrita restritas a uma pasta, sem acesso a shell; chaves de API e análises com dados pessoais ficam fora do controle de versão
- 🧪 **Testes**: suíte determinística com pytest, sem chamadas ao modelo, que valida o isolamento das ferramentas, a injeção da data no prompt, a carga da skill e a criação de diretórios
- 📐 **Processo**: diretrizes de arquitetura documentadas para o agente e commits semânticos com guia próprio
- 🧰 **Ferramentas**: React, TypeScript, Vite, Tailwind CSS, Python, Google ADK, uv, pytest

## 🛠️ Stack

**💻 Linguagens e frameworks**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)

**🗄️ Bancos de dados e nuvem**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat&logo=supabase&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=flat&logo=googlecloud&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat&logo=databricks&logoColor=white)

**🔧 Ferramentas**

![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat&logo=pytest&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat&logo=dbt&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat&logo=n8n&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat&logo=anthropic&logoColor=white)

## 🎓 Formação

- 💻 Bacharelado em Ciência da Computação, Universidade Veiga de Almeida (em andamento)
- 📈 Pós-graduação em Data Science and Analytics, PUC-Rio
- 🏭 Graduação em Engenharia de Produção, Universidade Veiga de Almeida
- 🧑‍💻 Imersão Engenharia de Software: Dev na Era da IA (Alura + Google for Startups)

## 📚 Estudando agora

- 🟣 C# e .NET e desenvolvimento backend
- 🏛️ Arquitetura de software
- 🔄 DevOps e CI/CD
- 🧠 Machine Learning e agentes de IA

## 📫 Contato

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/diogorblessa/)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white)](mailto:diogorblessa@gmail.com)
