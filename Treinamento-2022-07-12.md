# Tópicos do treinamento 2022-07-12

- Revisão de acessos, setup local e serviços em nuvem

- Criar um repositorio no github, se possível
- Configuração do dbt Cloud

- Os tipos de arquivos em um projeto de dbt
  - .sql
  Arquivos contendo instruções SQL e macros com sintaxe JINJA2
  O que é JINJA2?
  https://docs.getdbt.com/docs/building-a-dbt-project/jinja-macros
  - .yml
  Arquivos utilizados para aplicar configurações ou associar testes e documentação.
  https://www.redhat.com/pt-br/topics/automation/what-is-yaml
  - .md
  Arquivos de texto onde podemos adicionar regras de formatação através de comandos específicos.
  https://docs.pipz.com/central-de-ajuda/learning-center/guia-basico-de-markdown

- Abordagem Teórica das principais pastas do projeto e suas finalidades
  - analyses
  https://docs.getdbt.com/docs/building-a-dbt-project/analyses
  - dbt_packages (não trackeado)
  https://docs.getdbt.com/docs/building-a-dbt-project/package-management
  Vamos aproveitar para criar o packages.yml e adicionar o dbt_utils
  - logs (não trackeado)
  - macros
  https://docs.getdbt.com/docs/building-a-dbt-project/jinja-macros
  - models
  O centro do projeto, é aqui onde todos os modelos, mapeamento de origens e configurações serão aplicados.
  Analisar os exemplos existentes
  - seeds
  Versionamento de datasets utilizados de forma estática, bastante útil para testes e budget
  https://docs.getdbt.com/docs/building-a-dbt-project/seeds
  - snapshots
  Em BI, existe um conceito de Slowly Change Dimension, ou SCD, que é tratado de forma direcionada com o tipo de materialização Snapshot.
  Os modelos que utilizam este tipo de materialização são executados com um comando diferente e são salvos nesta pasta
  https://docs.getdbt.com/docs/building-a-dbt-project/snapshots
  - target (não trackeado)
  Pasta contendo os modelos compilados do projeto, bastante útil para debug e reuso em outras ferramentas pois é SQL puro
  - tests
  Pasta com testes singulares ou genericos. Testes singulares são consultas SQL simples e os genéricos são parametrizáveis e desenvolvidas em sintaxe JINJA
  https://docs.getdbt.com/docs/building-a-dbt-project/tests

- As principais camadas de um projeto
  - Source
  - Staging
  - Intermediate
  - Marts

- Source: Documentação e testes
  - Mapear a origem tpch_sf1
  - Adicionar documentação simplificada
  - Explicar o uso de documentação com .md e outros formatos
  https://docs.getdbt.com/docs/building-a-dbt-project/documentation
  - Adicionar testes genericos e explicar as opções default
  https://docs.getdbt.com/docs/building-a-dbt-project/tests

- Principais comandos no dbt
  - dbt deps
  - dbt compile
  - dbt seed
  - dbt snapshot
  - dbt run
  - dbt test
  - dbt build
  - dbt docs generate
  - dbt docs serve

- Verificar a documentação até o momento e analisar logs de execução