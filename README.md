# Aplicação WEB de Segmentação de Clientes através de modelo Clustering 

Este projeto está sendo desenvolvido durante o período da pós-graduação e 

## Objetivos 
1. Segmentação não supervisionada
2. Mapeamento de perfis
3. Arquitetura Desacoplada 
4. Visualização de impacto

## Tarefas
1. Definição do problema de Segmentação de Clientes; 
2. Definição de Arquitetura Hexagonal para organização de pastas e dependências do código;
3. Escolha de modelo de machine learning para treinamento de problema de cluster;
4. Escolha de ferramentas de avaliação do modelo;
5. Criação de dashboard final composto com características dos padrões de compra, assim. identificamos os clientes ATIVOS, EM RISCO e INATIVOS;

## Tecnologias utilizadas
- Linguagem : Python
- Bibliotecas para processamento de dados (Pandas, Matplotlib, Skit-learn )
- API : Fastapi
- Dashboard : Streamlit, Plotly, Seaborn
- Arquitetura : Ports & Adapters (Hexagonal), pytest


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
