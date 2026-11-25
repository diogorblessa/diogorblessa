# Olá, eu sou o Diogo 👋

Desenvolvedor de software com foco em backend e 2 anos de experiência em integração de serviços via APIs REST, código modular orientado a objetos, tratamento de exceções, testes automatizados e pipelines de dados de grande volume. Tem sólida base em bancos de dados relacionais, como SQL Server, PostgreSQL e Oracle. Atuou em projetos de consultoria para cooperativas de crédito, fintechs, seguradoras e e-commerces, transformando requisitos de negócio em funcionalidades em ambiente ágil.

## 💼 Experiência

- 🔗 **Integrações e pipelines**: desenvolvimento e manutenção de fluxos ETL/ELT e integrações entre sistemas para clientes de varejo, shopping centers, cooperativa financeira e alimentos, do levantamento de requisitos à entrega
- 🎯 **Plataformas de marketing e CDPs**: modelagem de tabelas para segmentação de audiências e integração com Salesforce Marketing Cloud, Salesforce Data Cloud, Oracle Responsys, Oracle Unity, Insider e mParticle
- 📊 **Dados em mídia paga**: dashboards e acompanhamento de KPIs de campanhas em Google Ads, Meta Ads e GA4
- 🤖 **Freelancer**: automações com n8n, Make e Python, chatbots com IA, web scraping e sites em WordPress
- ⚙️ **Operações**: mapeamento de processos, relatórios e padronização com POPs e Kanban

## 🚀 Projetos

### 💰 [Mini core bancário em .NET](https://github.com/diogorblessa/core-bancario-dotnet)
🚧 Em andamento, entregue por fases. Um mini core bancário cujo núcleo é um ledger contábil por partidas dobradas: os eventos do ledger alimentam uma conciliação contra um extrato externo, e um relatório regulatório de crédito, inspirado no Documento 3040 (SCR) do Banco Central, é gerado a partir dos saldos dos contratos no ledger. Todos os dados são fictícios.

- 🏗️ **Arquitetura**: monolito modular em que cada módulo tem quatro projetos (Domain, Application, Infrastructure e Contracts) e schema próprio no SQL Server, e um módulo só enxerga o Contracts de outro; conciliação e relatório regulatório viram processos próprios (serviço e Worker Service) conforme as fases avançam
- 📒 **Ledger**: toda transação contábil fecha débitos e créditos em zero, com idempotência por chave, concorrência otimista, períodos contábeis e outbox gravado na mesma transação
- 📨 **Mensageria e resiliência**: eventos publicados no RabbitMQ por um outbox relay e consumidos pela conciliação, com retry e fila de mensagens mortas
- 📄 **Relatório regulatório**: Worker Service que calcula a posição de crédito por cliente, valida contra a contabilidade e contra um XSD e envia o XML para o S3, emulado localmente pelo Floci
- 🧪 **Testes e qualidade de código**: TDD com xUnit v3, testes de integração com containers reais via Testcontainers, warnings tratados como erro e estilo verificado com dotnet format
- 🔁 **CI e fluxo de trabalho**: GitHub Actions rodando format, build, testes e build do Docker Compose; main protegida, uma branch e um pull request com checklist de autorrevisão por tarefa, Conventional Commits e ADRs para as decisões de arquitetura
- 🗺️ **Fases**: estrutura do repositório, CI, Docker Compose e ADRs concluídos; em seguida vêm ledger, conciliação, crédito com relatório regulatório e, opcionalmente, frontend em React e deploy na AWS
- 🧰 **Ferramentas**: C#, .NET 11, ASP.NET Core, SQL Server, RabbitMQ, xUnit, Testcontainers, Docker, GitHub Actions, Floci

### 📋 [JobFlow](https://github.com/diogorblessa/jobflow)
Plataforma para profissionais de tecnologia organizarem candidaturas a vagas, criada na Imersão Engenharia de Software da Alura com o Google. Integra uma aplicação web em React e TypeScript a um agente de IA em Python com Google ADK, que analisa de forma honesta e fundamentada a aderência do perfil do candidato aos requisitos de cada vaga.

- 🖥️ **Frontend**: cadastro, edição, busca e filtro de candidaturas em 8 etapas do processo seletivo, alertas de prazo e perfil profissional; código organizado em componentes, serviços, tipos e utilitários, com persistência em `localStorage`
- 🤖 **Agente**: separação de responsabilidades em módulos de configuração, prompt e ferramentas; skill com divulgação progressiva, carregada sob demanda; regra de ativação que pede só os dados que faltam; classificação de cada requisito em atendido, parcial ou lacuna e reanálise comparada à análise anterior
- 🔒 **Segurança e menor privilégio**: o agente só tem ferramentas de leitura e escrita restritas a uma pasta, sem acesso a shell; chaves de API e análises com dados pessoais ficam fora do controle de versão
- 🧪 **Testes**: suíte determinística com pytest, sem chamadas ao modelo, que valida o isolamento das ferramentas, a injeção da data no prompt, a carga da skill e a criação de diretórios
- 📐 **Processo**: diretrizes de arquitetura documentadas para o agente e commits semânticos com guia próprio
- 🧰 **Ferramentas**: React, TypeScript, Vite, Tailwind CSS, Python, Google ADK, uv, pytest

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

## 🛠️ Stack

**💻 Linguagens e frameworks**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![C#](https://img.shields.io/badge/C%23-512BD4?style=flat&logo=csharp&logoColor=white)
![.NET](https://img.shields.io/badge/.NET-512BD4?style=flat&logo=dotnet&logoColor=white)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-512BD4?style=flat&logo=dotnet&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikitlearn&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat&logo=vite&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189FDD?style=flat&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat&logo=sqlalchemy&logoColor=white)
![PyArrow](https://img.shields.io/badge/PyArrow-D22128?style=flat&logoColor=white)

**🗄️ Bancos de dados e nuvem**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat&logo=supabase&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=flat&logo=googlecloud&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat&logo=databricks&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=flat&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat&logo=duckdb&logoColor=black)
![Delta Lake](https://img.shields.io/badge/Delta_Lake-003366?style=flat&logoColor=white)
![Unity Catalog](https://img.shields.io/badge/Unity_Catalog-FF3621?style=flat&logo=databricks&logoColor=white)

**🔧 Ferramentas**

![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat&logo=pytest&logoColor=white)
![xUnit](https://img.shields.io/badge/xUnit-5E2B97?style=flat&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat&logo=dbt&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat&logo=n8n&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat&logo=anthropic&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat&logo=pydantic&logoColor=white)
![uv](https://img.shields.io/badge/uv-DE5FE9?style=flat&logo=uv&logoColor=white)
![Poetry](https://img.shields.io/badge/Poetry-60A5FA?style=flat&logo=poetry&logoColor=white)
![pre-commit](https://img.shields.io/badge/pre--commit-FAB040?style=flat&logo=precommit&logoColor=black)
![Gemini API](https://img.shields.io/badge/Gemini_API-8E75B2?style=flat&logo=googlegemini&logoColor=white)
![Google ADK](https://img.shields.io/badge/Google_ADK-4285F4?style=flat&logo=google&logoColor=white)
![Black](https://img.shields.io/badge/Black-000000?style=flat&logoColor=white)
![isort](https://img.shields.io/badge/isort-EF8336?style=flat&logoColor=white)
![Flake8](https://img.shields.io/badge/Flake8-3776AB?style=flat&logoColor=white)
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000000?style=flat&logo=opentelemetry&logoColor=white)
![Telegram Bot API](https://img.shields.io/badge/Telegram_Bot_API-26A5E4?style=flat&logo=telegram&logoColor=white)

## 🎓 Formação

- 💻 Bacharelado em Ciência da Computação, Universidade Veiga de Almeida (em andamento)
- 📈 Pós-graduação em Data Science and Analytics, PUC-Rio
- 🏭 Bacharelado em Engenharia de Produção, Universidade Veiga de Almeida

## 📚 Estudando agora

- 🟣 C# e .NET e desenvolvimento backend
- 🏛️ Arquitetura de software
- 🔄 DevOps e CI/CD
- 🧠 Machine Learning e agentes de IA

## 📫 Contato

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/diogorblessa/)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white)](mailto:diogorblessa@gmail.com)
