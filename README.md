<div align="center">
  <img alt="Agidesk Challenge"
    src="agidesk-logo.svg"
  />

</div>

<h2 align="center">
   Agidesk SignUp Flow
</h2>

<p align="center">

  <img alt="language version" src="https://img.shields.io/badge/Node-v_v20.14.0-339933?logo=node.js">

  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/Fred-Reis/agi-monorepo">

  
  <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/Fred-Reis/agi-monorepo">

  <img alt="GitHub repo size in bytes" src="https://img.shields.io/github/repo-size/Fred-Reis/agi-monorepo">

</p>

<hr/>

<h3 align="center">Links:</h3>

<p align="center">

  <a href="#-sobre-esse-projeto">
    <img src="https://img.shields.io/badge/Sobre_o_Projeto-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#-arquitetura">
    <img src="https://img.shields.io/badge/Arquitetura-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#-banco-de-dados">
    <img src="https://img.shields.io/badge/Banco-de-Dados-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#-testes">
    <img src="https://img.shields.io/badge/Testes-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#-tecnologias-e-ferramentas">
    <img src="https://img.shields.io/badge/Tecnologias_Ferramentas-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#-executando-o-projeto">
    <img src="https://img.shields.io/badge/Executando_Projeto-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#-configurando-o-docker">
    <img src="https://img.shields.io/badge/Configurando_Docker-a5a5a5"/>
  </a>&nbsp;&nbsp;
  <a href="#author-frederico-reis">
    <img src="https://img.shields.io/badge/Author-a5a5a5"/>
  </a>

</p>

# 💡 Sobre esse projeto:

A proposta desse projeto era construir uma aplicação fullstack que permitisse ao usuário criar um usuário e enviar um email de confirmação para o usuário:



# 📑 Backend

## 📐 Arquitetura:

O projeto foi concebido utilizando a metodologia de DDD - Domain Driven Design, seguindo os princípios do SOLID e Design Patterns.
Separando responsabilidades, diminuindo acoplamentos, facilitando na refatoração e estimulando o reaproveitamento do código.

## 🔥 Banco de dados:

A API possui apenas um endpoint, que deve respeitar a seguinte chamada:

`http://{HOST}/recipes/?i={ingredient_1},{ingredient_2}`

Exemplo:

`http://localhost:5432/recipes/?i=garlic,eggs`

A resposta de requisição deveria ter como estrutura: um array com as palavras chaves (ingredientes da chamada) organizados em ordem alfabética e uma lista de receitas:

```JSON
{
	"keywords": ["egg", "garlic"],
	"recipes": [
    {
		"title": "Roast Garlic Fresh Pasta Recipe",
		"ingredients": ["garlic", "egg yolks", "eggs", "pasta", "flour"],
		"link": "http://www.grouprecipes.com/33194/roast-garlic-fresh-pasta.html",
		"gif": "https://media.giphy.com/media/xBRhcST67lI2c/giphy.gif"
	   },{
		"title": "Maria's Stuffed Chicken Breasts",
		"ingredients": ["chicken", "eggs", "garlic", "salt"],
		"link":"http://allrecipes.com/Recipe/Marias-Stuffed-Chicken-Breasts/Detail.aspx",
		"gif":"https://media.giphy.com/media/I3eVhMpz8hns4/giphy.gif"
	  }
	]
}
```

# 🧪 Testes:

Foram implementados testes unitários utilizando [Jest](https://jestjs.io/);

Para executar os testes basta executar o seguinte comando na raiz do projeto:

```bash
$ npm test
```

Os detalhes do teste serão apresentados no seu console.

Também será gerado automáticamente na raiz do seu projeto uma pasta chamada `coverage`, dentro dela terá uma outra pasta chamada `Lcov-report`. Dentro dessa pasta terá um arquivo `index.html` abra ele no seu browser e tenha acesso a mais detalhes dos testes executados.

# 🛠 Tecnologias e Ferramentas:

Algumas das tecnologias e ferramentas utilizadas nesse projeto.

- [**NodeJS**](https://nodejs.org/en/);
- [Docker;](https://www.docker.com/);
- [Insomnia](https://insomnia.rest/download/);
- [Notion](https://www.notion.so/?utm_source=google&utm_campaign=brand_alpha&utm_content=row&utm_term=notion&gclid=CjwKCAjw1cX0BRBmEiwAy9tKHs5ggnFG4dmfW38kOuGDTQS1-YjRGg01PuIriv8ftUuAUzeoU7QFFxoCAkIQAvD_BwE);
- EsLint;
- Prettier;
- Express;
- Jest;

# 🏁 Executando o projeto:

1 - Para rodar pela primeira vez o seu projeto será necessário a criação de uma pasta.

```bash
$ mkdir <nome-da-pasta>
```

2 - Agora entre na pasta criada.

```bash
$ cd <nome-da-pasta>
```

3 - Vamos clonar o repositório

```bash
$ git clone https://github.com/Fred-Reis/delivery-much_tech-test
```

4 - Execute o comando a seguir para a criação da pasta `node_modules`

```bash
$ npm install
```

5 - Para iniciar o servidor em modo desenvolvimento execute o seguinte comando

```bash
$ npm dev:server
```

> Recomendo o uso do [Insomnia](https://insomnia.rest/download/) para testar as chamadas ao servidor

# 🐳 Configurando o Docker

O projeto possui um arquivo chamado `Dockerfile` que possui as configurações para o deploy do projeto em um container do [Docker](https://www.docker.com/), ele é quem irá passar todos parâmetros que o Docker utilizará para criar nossa imagem.

Vamos partir da premissa que você já tem o docker instalado e pronto para receber a criação de uma imagem, caso ainda não tenha recomendo seguir esse [GUIA](https://www.notion.so/Instalando-o-Docker-373b5fed9526414c8bf018275248cf10).

### 🖼 Criando Imagem

Agora com o Docker devidamente instalado vamos começar criando a imagem do nosso projeto dentro do Docker usando o comando `docker build`.

O comando a seguir recebe uma flag `-t` que ira permitir que você crie um nome para a sua imagem:

> ❗️Importante: É necessário que você esteja dentro da raiz do seu projeto para executar o comando abaixo, pois ele irá utilizar o "." para informar que o contexto da build é o diretório atual. E não esqueça o ponto!

```bash
$ docker build -t nome_usuário/delivery-much-image .
```

A primeira vez irá demorar um pouco pois o Docker irá baixar a imagem do NodeJs também.

Com o comando a seguir é possível ver a sua imagem que foi criada:

```bash
$ docker images
```

### 📦 Criando um container

Com nossa imagem já criada vamos criar um container usando o comando `docker run` vamos usar aqui algumas flags para nos ajudar:

- `-p` Vai fazer o direcionamento das portas, a primeira será a porta que você irá utilizar para acessar pelo seu navegador, aconselho a `5432` que é a porta padrão utilizada pelo Docker, mas fique a vontade para escolher a porta que for melhor pra você, mas lembresse dela pois será a porta que você irá acessar o container no Docker. A segunda porta **OBRIGATORIAMENTE** será a `3333` que foi a porta declarada no nosso arquivo `Dockerfile`, e será a porta que o Docker irá ouvir da sua máquina.
- `-d` Isso executa o container em segundo plano.
- `--name` Permite dar um nome ao nosso container.

```bash
$ docker run --name <nome-container> -p 5432:3333 -d <nome-da-nossa-imagem>
```

Se tudo deu certo até aqui execute o comando a seguir e você verá o seu container.

```bash
$ docker ps -a
```

Agora dê o start no seu container com o comando:

```bash
$ docker start <id do container>
```

E com o comando abaixo você decerá ver o seu container executando

```bash
$ docker ps
```

Caso isso não aconteça execute o comando abaixo e veja o que aconteceu de errado com a execução do seu container

```bash
$ docker logs <id do container>
```

Será mostrado os logs que foram gerados.

<br/>

Se você chegou até aqui é sinal que tudo deu certo e você agora já pode fazer a sua chamada direto do seu browser 😱 seguindo o exemplo abaixo.

`http://localhost:5432/recipes/?i=garlic,eggs`

<br/>

😃 Agora busque as suas receitas e ...
**SEJA FELIZ!**.

<h4 align="center">
  "Stay hungry stay foolish!"
</h4>

<br/>

---

<h3 align="center">
Author: <a alt="Fred-Reis" href="https://github.com/Fred-Reis">Frederico Reis</a>
</h3>

<p align="center">

  <a alt="Frederico Reis" href="https://www.linkedin.com/in/frederico-reis-dev/">
    <img src="https://img.shields.io/badge/LinkedIn-Frederico_Reis-0077B5?logo=linkedin"/></a>
  <a alt="Frederico Reis" href="https://github.com/Fred-Reis ">
  <img src="https://img.shields.io/badge/Fred_Reis-GitHub-000?logo=github"/></a>

</p>

Feito com ♥️
