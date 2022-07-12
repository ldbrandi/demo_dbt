# Treinamento dbt - Módulo 01

## O que é dbt?

Um framework voltado para transformação de dados viabilizando o uso de boas práticas de engenharia de software em projetos de Analytics Engineering. Suas principais caracteristicas são o foco em SQL para a codificação das soluções, modularização de processos, documentação automatizada, testes unitários e de integração, e direcionamento nativo para fluxo de CI/CD.

Para saber mais sobre dbt, visite o site oficial em https://www.getdbt.com/.

## Pré-requisitos para execução dos exemplos

- Criar uma conta na plataforma [Snowflake](https://www.snowflake.com/) que permite acesso gratuito por 50 dias ou o equivalente a 400 USD.
- Criar uma conta no [dbt Cloud](https://cloud.getdbt.com/) para realização da etapa de deployment. A conta é gratuita por 14 dias com todos os serviços disponíveis, porém gratuita para sempre restrita à apenas um desenvolvedor após os 14 dias.
- Criar uma conta (caso não tenha) no [Github](https://github.com/).

<details>
<summary markdown="span">
Caso já tenha utilizado seu e-mail para as contas gratuitas, siga estas etapas:
</summary>

- Crie um novo e-mail, preferencialmente [Gmail](https://accounts.google.com/signup/v2/webcreateaccount?flowName=GlifWebSignIn&flowEntry=SignUp), para utilizar nas novas contas do Snowflake e dbt Cloud.
- Caso tenha problemas em acessar o e-mail na rede interna, utilize o celular para criar e verificar os e-mails recebidos.
</details>

<br>

## Setup local

O dbt oferece 2 opções para que os desenvolvedores possam trabalhar em seus modelos: um setup local com dbt core e linha de comando (open-source); e o dbt cloud, que oferece uma IDE online para desenvolvimento fora as demais funcionalidades da plataforma.

Para os exemplos abordados nesse projeto, vamos utilizar o dbt core e instalação local para desenvolvimento e o dbt Cloud para o ambiente de deployment (produção) dos modelos criados. Para os que preferem instalação via algum gerenciador de pacotes, o [Chocolatey](https://chocolatey.org/install) é o mais utilizado para windows.

Sendo assim, no ambiente local do desenvolvedor, precisaremos das seguintes ferramentas:

<details>
<summary markdown="span">
Git
</summary>

Download direto: https://git-scm.com/downloads

Download via Chocollatey: `choco install git -y`
</details>

<details>
<summary markdown="span">
Python
</summary>

Download direto: https://www.python.org/downloads/

Download via Chocollatey:
```
choco install pyenv -y
pyenv install 3.9.6 -r
pyenv global 3.9.6
```

Para verificar se a instalação correu bem, rode o seguinte comando em uma nova aba do seu terminal: `python -V`

O resultado deve ser a versão do Python instalada. Se retornar algo diferente disso, pode haver um problema na instalação.
</details>

<details>
<summary markdown="span">
VS Code
</summary>

Download direto: https://code.visualstudio.com/download

Download via Chocollatey: `choco install vscode -y`
</details>

<details>
<summary markdown="span">
dbt
</summary>

A instalação do dbt é feita diretamente no Python, através do `pip`.

Para esta demonstração, utilizaremos o adaptador para Snowflake, portanto execute o comando a seguir em uma aba do seu terminal:
`pip install dbt-snowflake`

Para testar a instalação, execute o comando `dbt --version`.
</details>

<br>

Uma vez que estes softwares estejam instalados, podemos realizar a configuração do dbt e inicializar um projeto do zero. 

Para começar, vamos criar um novo repositório no Github, com nome `demo_dbt` e o restante das configurações default.

![Criando novo Repositório](/documents/images/new-repo.png)

Agora podemos clonar o repositório vazio em nosso ambiente local. Uma recomendação é criar uma pasta para os projetos, o que facilita a organização. Nos exemplos a seguir, o repo será clonado no seguinte path: `C:\Users\lucas\Projects\demo_dbt`

Para fazer o mesmo, seguiremos a seguinte ordem:

- Criar um novo diretório `Projects` no seu usuário
  - Para isso, abra o PowerShell e navegue até o diretório raíz do seu usuário com o comando: `cd C:\Users\lucas` (troque "lucas" pelo seu usuário)
  - Depois rode o comando `mkdir Projects` para criar a nova pasta
  - Por fim, podemos navegar para dentro desta nova pasta utilizando `cd Projects` onde iremos clonar o repositório demo_dbt.
- Clonar o novo repositório utilizando o comando `git clone https://github.com/ldbrandi/demo_dbt.git` (substitua o "ldbrandi" pelo seu usuário do Github)

<details>
<summary markdown="span">
Caso seja o rpimeiro uso de Git, configure seus dados locais
</summary>

Rode os seguintes comandos em qualquer pasta do seu terminal:

- `git config --global user.email "seu.email@gmail.com"`
- `git config --global user.name "Seu Nome"`
</details>

---

Agora podemos inicializar o projeto do dbt utilizando seu próprio assistente. Para isso, vamos executar o comando `dbt init` dentro da pasta `demo_dbt`.

Este comando vai solicitar alguns inputs do usuário para a comunicação com o Snowflake. Responda as perguntas da seguinte forma:
```
account: <account>.<region> (ex.: lzb14412.us-east-1)
database: ANALYTICS_DEV
password: <senha>
role: accountadmin
schema: <snowflake_username> (ex.: lbrandi)
threads: 4
type: snowflake
user: <snowflake_username> (ex.: lbrandi)
warehouse: compute_wh
```

Ao concluir este comando, o dbt irá criar automaticamente as principais pastas do projeto, alguns exemplos e o arquivo `profiles.yml`, que armazena todos os dados de conexão com o Snowflake.

Para acessar este arquivo, navegue até o diretótio oculto `C:\Users\<username>\.dbt`. A forma mais simples é pelo comando:
```
cd C:\Users\<username>\.dbt
code profiles.yml
```

Ele deve ser parecido com [profiles_sample.yml](../profiles_sample.yml).

---

Com o projeto devidamente inicializado e o perfil de acesso criado corretamente, navegue de volta para a pasta do projeto e execute o comando `dbt debug`, que validará todos os requisitos básicos para o funcionamento do projeto. O output deve ser semelhante a este:

![dbt debug](/documents/images/dbt-debug.png)