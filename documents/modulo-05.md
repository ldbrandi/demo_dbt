# Treinamento dbt - Módulo 05

Configuração do dbt Cloud.
- Environment
- Job
- Docs

Deployment.
- New Branch
- Add new models
- Merge into Main

Modelos incrementais. (https://docs.getdbt.com/docs/building-a-dbt-project/building-models/configuring-incremental-models)
- Adicionar um novo seed para adicionar novas linhas diariamente (sem alteração das anteriores)
- dbt seed
- dbt run -s aux_exchange_rates
- dbt run -s aux_exchange_rates --full-refresh 
- se não pudessemos usar uma unique_key https://docs.getdbt.com/reference/resource-configs/snowflake-configs#merge-behavior-incremental-models

Snapshots. (https://docs.getdbt.com/docs/building-a-dbt-project/snapshots)
- Adicionar novo seed para ajustar linhas existentes
- dbt seed
- dbt snapshot

Se sobrar tempo, refatoração do projeto para melhor documentação e qualidade dos comandos SQL.