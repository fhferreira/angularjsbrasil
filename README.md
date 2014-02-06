O foco dessa série é ensinar AngularJs e criar situações que o AngularJs possa ser a solução.

<ol>
	<li>Introdução&#10004;</li>
	<li>MVC&#10004;</li>
	<li>MVVM</li>
	<li>HandleBars</li>
	<li>Iniciando uma aplicação&#10004;</li>
	<li>Olá Mundo&#10004;</li>
	<li>Scope</li>
	<li>Injeção de Dependências</li>
	<li>Controllers</li>
	<li>Routers</li>
	<li>RootScope</li>
	<li>Services</li>
	<li>Filters</li>
	<li>Directives</li>
</ol>


# 1 - Introdução
	
O AngularJs surgiu em meados de 2009, foi criado por dois funcionários da Google e após um tempo a Google
adotou o projeto e hoje existe uma equipe focada somente no AngularJs.
AngularJs é um framework JavaScript MVC/MVVM, fácil de ser aprendido e a curva de aprendizado é pequena em relação a outros frameworks. Como toda a linguagem, no começo é fácil, mas conforme vai se aprofundando, é necessário um pouco mais de atenção, mas não irá desanimar. O AngularJs é uma ferramenta essencial para quem deseja criar sistemas (web apps) com facilidade e ter todo controle do lado client.

# 2 - MVC

O MVC é uma abreviatura de Model, View, Control, uma pattern (padrão) que é conhecida no mundo Server Side. Serve para padronizar o desenvolvimento/arquitetura de sistemas e facilitar o controle de informações.
Vamos entender melhor como funciona:

***Model*** - É a parte do sistema onde é recebido as informações do banco de dados/web-service e etc. Para tratar essas informações no client, eventualmente usamos o ```$.ajax (XHR - XMLHttpRequest)``` para jQuery, no AngularJs usamos o ```$http```, essas funções tem o intuito de enviar e receber informações através do [GET,POST,PUT,DELETE] no formato JSON. A model conversa com a Control no momento em que a Control envia ou busca informações. Abaixo segue uma estrutura JSON.

```
{
    "users": [{
        "name": "Nicholas Eduardo",
        "id": "9999"
    }]
}

```


***View*** - As informações que o usuário visualiza nos sites através do HTML, é renderizado a partir do momento em que a Control envia informações para View. As informações estáticas inseridas no HTML no momento do desenvolvimento é diferente das informações que são inseridas dinâmicamente. 

***Control*** - O nome já diz, controla as informações que vem da Model e renderiza na View.

Ex: Em um cadastro de produto, os campos para serem preenchidos são a View, a partir do momento que você envia as informações do produto para serem cadastradas, essas informações passam pela Control, que verifica campos preenchidos, formatos e etc. E após isso conversa com a Model para enviar as informações ao banco de dados.

Nota: JSON, um acrônimo para "JavaScript Object Notation", é um formato leve para intercâmbio de dados computacionais. JSON é um subconjunto da notação de objeto de JavaScript, mas seu uso não requer JavaScript exclusivamente  - <a href="http://pt.wikipedia.org/wiki/JSON">Wikipedia</a>
# HandleBars

O handlebars são os caracteres especiais ```{{algumacoisa}}```, eles que fazem a renderização das informações de variáveis do AngularJs, porém isso fica muito vago na explicação. No ***Olá Mundo***, explicarei melhor.

# Iniciando uma aplicação

Para iniciar uma aplicação no corpo HTML é necessário inserir as referências do AngulaJS nos scripts.

```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body>
<script src="http://code.angularjs.org/1.2.11/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.11/angular-route.min.js"></script>
</body>
</html>
```

O primeiro script é referente ao Angular e segundo script é referente as rotas, que irei explicar mais adiante.

Após ter incluido os arquivos, é necessário inserir directivas do Angular para que ele consiga identificar no corpo do HTML, que o arquivo é uma aplicação angular, como fazemos?

A directiva principal do angular é a ***ng-app***, é ela que dirá ao angular para que comece a trabalhar naquele HTML.

```
<!DOCTYPE html>
<html ng-app>
<head>
	<title>AngularJs</title>
</head>
<body>
<script src="http://code.angularjs.org/1.2.11/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.11/angular-route.min.js"></script>
</body>
</html>
```

A directiva ***ng-app*** pode ser incluida no ```html``` ou ```body``` ou em uma ```div``` qualquer.

Ex com head:
```
<!DOCTYPE html>
<html ng-app>
<head>
	<title>AngularJs</title>
</head>
```
Ex com body:
```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body ng-app>
<script src="http://code.angularjs.org/1.2.11/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.11/angular-route.min.js"></script>
</body>
</html>
```
Ex com div

```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body>
<div ng-app></div>
<script src="http://code.angularjs.org/1.2.11/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.11/angular-route.min.js"></script>
</body>
</html>
```

A diferença entre a directiva no ```html``` ou no ```body``` não é significativa, em questão da directiva ser na ```div```, é que aplicação só será válida dentro da ```div```. Ou seja, se fizer algo fora da ```div``` não terá resultados.

# Olá Mundo

Para criarmos um Olá Mundo, iremos pegar a estrutura que foi usada anteriormente. Quando expliquei sobre handlebars, ficou muito vago em relação as váriaveis, mas agora chegou a hora.
A tag ```ng-model``` é a model da sua aplicação que faz comunicação direta com a variável, ela referência a variável na aplicação, vemos que dentro da ng-model existe o "nome" e dentro dos caracteres especiais ```{{}}``` (handlebars), existe a mesma coisa "nome". Quando digitarmos algo no input que contêm o ng-model, começará uma comunicação e dentro do handlebars aparecerá o que você digitou, 
por exemplo: Se digitarmos "Mundo", irá formar Olá Mundo.

```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body ng-app>
<input type="text" ng-model="nome">
<p>Olá {{nome}}</p>
<script src="http://code.angularjs.org/1.2.11/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.11/angular-route.min.js"></script>
</body>
</html>
```
<a href="http://codepen.io/nicholasess/pen/AslmG">Visualizar exemplo na prática</a>