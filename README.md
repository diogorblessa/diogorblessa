# Olá, eu sou o Diogo 👋

Desenvolvedor no Rio de Janeiro, com base em dados e foco em backend. Construo aplicações, integrações entre sistemas, automações e agentes de IA, sempre buscando código testável, organizado e bem documentado.

## 💼 Experiência

- 🔗 **Integrações e pipelines**: desenvolvimento e manutenção de fluxos ETL/ELT e integrações entre sistemas para clientes de varejo, shopping centers, cooperativa financeira e alimentos, do levantamento de requisitos à entrega
- 🎯 **Plataformas de marketing e CDPs**: modelagem de tabelas para segmentação de audiências e integração com Salesforce Marketing Cloud, Salesforce Data Cloud, Oracle Responsys, Oracle Unity, Insider e mParticle
- 📊 **Dados em mídia paga**: dashboards e acompanhamento de KPIs de campanhas em Google Ads, Meta Ads e GA4
- 🤖 **Freelancer**: automações com n8n, Make e Python, chatbots com IA, web scraping e sites em WordPress
- ⚙️ **Operações**: mapeamento de processos, relatórios e padronização com POPs e Kanban

## 🚀 Projetos

### 🛒 [Plataforma de dados para e-commerce com agente de IA](https://github.com/diogorblessa/projeto-pipeline-ELT-engenharia-supabase-dbt)
Monorepo em Python que extrai dados de um bucket S3, carrega no PostgreSQL Supabase e transforma com dbt em camadas Bronze, Silver e Gold. Sobre essa base rodam duas aplicações: um dashboard em Streamlit e um bot no Telegram que usa a API do Claude com tool use para responder perguntas em linguagem natural consultando o banco, com acesso restrito a consultas de leitura.

- 🧰 **Ferramentas**: Python, uv, boto3, SQLAlchemy, dbt, PostgreSQL, Streamlit, Claude API, python-telegram-bot, Docker
- ✅ **Boas práticas**: testes com pytest usando mocks e SQLite em memória, lint com ruff, configuração tipada com pydantic-settings e segredos via `.env`

### 🏦 [Pipeline de reclamações contra bancos](https://github.com/diogorblessa/mvp_engenharia_de_dados_puc)
Pipeline no Databricks que processa os dados públicos do consumidor.gov.br e entrega um modelo em esquema estrela para responder quais problemas mais crescem nas reclamações contra bancos. Inclui script local de download com validação e manifesto de linhagem, transformações em PySpark e documentação de cada tabela e coluna no Unity Catalog.

- 🧰 **Ferramentas**: Databricks, PySpark, SQL, Delta Lake, Unity Catalog, databricks-connect, VS Code, uv
- ✅ **Boas práticas**: verificações com `assert` que interrompem a execução quando algo não bate, commits semânticos com guia próprio e decisões de projeto documentadas

### 💳 Previsão de churn de cartão de crédito
Modelo de classificação que prevê se um cliente vai cancelar o cartão, da [análise exploratória e pré-processamento](https://github.com/diogorblessa/mvp-credit-card-churn-parte-01) à [modelagem e avaliação](https://github.com/diogorblessa/mvp-credit-card-churn-parte-02). Comparei vários algoritmos contra um baseline, otimizei hiperparâmetros com validação cruzada e salvei o pipeline final para reuso.

- 🧰 **Ferramentas**: Python, pandas, scikit-learn, XGBoost, matplotlib, seaborn, joblib, Google Colab

### 📋 [JobFlow](https://github.com/diogorblessa/jobflow)
Aplicação para organizar candidaturas a vagas, criada na Imersão Engenharia de Software da Alura com o Google. O próximo passo é um agente de IA que compara cada vaga com o perfil do candidato.

- 🧰 **Ferramentas**: React, TypeScript

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

- 🐍 Django e desenvolvimento backend
- 🏛️ Arquitetura de software
- 🔄 DevOps e CI/CD
- 🧠 Machine Learning e agentes de IA

## 📫 Contato

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/diogorblessa/)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white)](mailto:diogorblessa@gmail.com)
 
-->
