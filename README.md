<div align="center">

# 📊 Mapeamento de Perfis Socioeconômicos
### *Modelo de Clustering com Dados da Pesquisa "Condições de Vida 2017" (IBGE)*

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Scikit-Learn](https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-239120?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/)

---

*Aplicação Web desenvolvida para análise, clusterização e visualização interativa de dados socioeconômicos e vulnerabilidade alimentar.
            Este projeto está sendo desenvolvido durante o processo de desenvolvimento de habilidades em Ciência de Dados.*

</div>


## Resumo do projeto : 

- Este projeto utiliza dataset da base de dados do IBGE, nomeado "Condições de Vida 2017". 

- Objetivo: Realizar o mapeamento de perfis socioeconômicos através das condições de moradia,infraestrutura e padrão de vida 

- Contexto : Como o mapeamento de perfis socioeconômicos influenciam na criação de planos de desenvolvimento sustentável?

## Passos para o desenvolvimento do projeto :

1. Realizar da Análise Exploratória de Dados
2. Aplicar a Featuring Engeneering para geração de Indíces para avaliação da infraestrutura, vulnerabilidade alimentar e capacidade dos grupos sociais da pesquisa
3. Aplicar modelo de clustering
4. Criação de dashboard para visualização de perfis de socioeconômicos (Alta vulnerabilidade, Em Risco e Estruturado)
   

## Base de dados de Análise 
- Pesquisa do IBGE -  Condições de Vida 2017 : 
- Cobertura Temporal: 2017 - 2018
- Unidade de Análise: Domicílio / Unidade de Consumo
- Conformidade com LGPD
- Dicionário resumido dos Campos 
    1. Identificadores e Localização (Chaves)
    2. Avaliação de Padrão de Vida e Serviços Básicos (STRING)
    3. Problemas Habitacionais e Socioambientais
    4. Dificuldades Financeiras e Insegurança Alimentar (EBIA)
    5. Avaliação Subjetiva de Renda e Pesos Amostrais

- Perguntas da EBIA (Insegurança Alimentar / Fatos objetivamente ocorridos)
- Exemplo: Houve falta de alimentos por conta da falta de dinheiro? Deixaram de fazer uma refeição?
    - 1 : SIM
    - 2 : NÃO

- Perguntas de Avaliação de Padrão de Vida
- Exemplo : Como você considera o seu padrão de vida em relação a moradia/alimentação/vestuário/saúde/lazer?
    - 1: BOM
    - 2: SATISFATÓRIO
    - 3: RUIM
    - 4: NÃO DISPONÍVEL/NÃO UTILIZADO
 
      
## Tecnologias utilizadas
- Linguagem : Python
- Bibliotecas para processamento de dados (Pandas, Matplotlib, Skit-learn )
- API : Fastapi
- Dashboard : Streamlit, Plotly, Seaborn
- Arquitetura : Ports & Adapters (Hexagonal), pytest


## Organização do projeto 
```text
rfm_segmentation/
│
├── src/
│   ├── domain/                    # CORE: Lógica pura do negócio (Sem dependências externas)
│   │   ├── models/
│   │   │   └── customer_rfm.py    # Entidades de Domínio e Value Objects
│   │   └── ports/                 # Interfaces (Contratos)
│   │       ├── customer_repository_port.py  # Porta de Saída (Driven)
│   │       └── rfm_service_port.py          # Porta de Entrada (Driver)
│   │
│   ├── application/               # CASOS DE USO
│   │   └── rfm_use_cases.py
│   │
│   └── infrastructure/            # ADAPTADORES: Frameworks, Banco de Dados, Libs
│       ├── adapters/
│       │   ├── pandas_customer_repository.py  # Adaptador de Saída (Busca e processa dados)
│       │   └── fastapi_controller.py          # Adaptador de Entrada (API HTTP)
│       └── config.py
│
└── main.py                        # Ponto de entrada 
```

## Como rodar 

```sh

# Instalar as dependências do projeto 
pip install -r requirements.txt

# Rodar a aplicação (BACKEND)
python -m api.main

# Rodar o streamlit (FRONTEND)
streamlit run dashboard/app.py

```
