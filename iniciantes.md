# INICIANTES

<ol>
	<li>Introdução&#10004;</li>
	<li>AngularJs e Internet Explorer&#10004;</li>
	<li>MVC&#10004;</li>
	<li>MVVM</li>
	<li>HandleBars&#10004;</li>
	<li>Iniciando uma aplicação&#10004;</li>
	<li>Olá Mundo&#10004;</li>
	<li>Module&#10004;</li>
	<li>Scope</li>	
	<li>Routers</li>
	<li>Controllers</li>
	
	
</ol>


## Introdução
	
O AngularJs surgiu em meados de 2009, foi criado por dois funcionários da Google e após um tempo a Google
adotou o projeto, e hoje existe uma equipe focada somente no AngularJs.
AngularJs é um framework JavaScript MVC/MVVM, fácil de ser aprendido e a curva de aprendizado é pequena em relação a outros frameworks. Como toda a linguagem, no começo é fácil, mas conforme vai se aprofundando, é necessário um pouco mais de atenção, mas não irá desanimar. O AngularJs é uma ferramenta essencial para quem deseja criar sistemas (web apps) com facilidade e ter todo controle do lado client (Front).

## AngularJs e Internet Explorer

Não é recomendado que o IE6 e IE7 sejam usados em aplicações AngularJS. A falta de suporte a tags personalizadas e eventos por mudança de hash tornam a aplicação em si muito inchada e lenta. Apesar de termos algum suporte a eles, o AngularJS é recomendado somente para ser usado com navegadores de qualidade como (Chrome, Firefox, IE8+, Safari e Opera). Esforce em evitar o uso do AngularJS com IE6 e IE7 e tudo vai estar bem.

AngularJS menciona que o uso de tags personalizadas é suportada no IE8 e é notado que o Angular trabalha bem com IE8 quando usado qualquer tag personalizada. Eu não creio completamente que o IE8 respeita tags personalizadas visto que um arquivo especial HTML5 é necessário para fazer tags HTML5 funcionarem no IE8. Portanto você vai precisar de definir cada uma das tags personalizads que vai usar no início do seu arquivo (document.createElement('ng-pluralize'), document.createElement('ng-view'), etc...). Então se você quiser trabalhar usando tags personalizadas ou se você quiser evitar IE8 também, então somente continue usando as tags HTML/HTML5 regulares e tudo funcionará bem.

## MVC

O MVC é uma abreviatura de Model, View, Control, uma pattern (padrão) que é conhecida por todos. Serve para padronizar o desenvolvimento/arquitetura de sistemas e facilitar o controle de informações.
Vamos entender melhor como funciona:

***Model*** - É a parte do sistema onde é recebido as informações do banco de dados/webservice e etc. Para tratar essas informações no front, eventualmente usamos o ```$.ajax (XHR - XMLHttpRequest)``` para jQuery, no AngularJs usamos o ```$http```, essas funções tem o intuito de enviar e receber informações através dos métodos [GET,POST,PUT,DELETE] no formato JSON. A model conversa com a Control no momento em que a Control envia ou busca informações. Abaixo segue uma estrutura JSON.

```
{
    "users": [{
        "name": "Nicholas Eduardo",
        "id": "9999"
    }]
}

```


***View*** - As informações que o usuário visualiza nos sites através do HTML, é renderizado a partir do momento em que a Control envia informações para View. As informações estáticas inseridas no HTML no momento do desenvolvimento é diferente das informações que são inseridas dinâmicamente. O angular trabalha com as informações dinamicas.

***Control*** - O nome já diz, controla as informações que vem da Model e renderiza na View.

Ex: Em um cadastro de produto, os campos para serem preenchidos são a View, a partir do momento que você envia as informações do produto para serem cadastradas, essas informações passam pela Control, que verifica campos preenchidos, formatos e etc. E após isso conversa com a Model para enviar as informações ao banco de dados.

Nota: JSON, um acrônimo para "JavaScript Object Notation", é um formato leve para intercâmbio de dados computacionais. JSON é um subconjunto da notação de objeto de JavaScript, mas seu uso não requer JavaScript exclusivamente  - <a href="http://pt.wikipedia.org/wiki/JSON" target="_blank">Wikipedia</a>

## HandleBars

O handlebars são os caracteres especiais ```{{algumacoisa}}```, eles que fazem a renderização das informações de variáveis do AngularJs, porém isso fica muito vago na explicação. No ***Olá Mundo***, explicarei melhor.

## Iniciando uma aplicação

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

A directiva ***ng-app*** pode ser incluida no ```<html>``` ou ```<body>``` ou em uma ```<div>``` qualquer.

Ex com ```<html>```:
```
<!DOCTYPE html>
<html ng-app>
<head>
	<title>AngularJs</title>
</head>
```
Ex com ```<body>```:
```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body ng-app>
<script src="http://code.angularjs.org/1.2.1/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.1/angular-route.min.js"></script>
</body>
</html>
```
Ex com ```<div>```

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

A diferença entre a directiva no ```html``` ou no ```body``` não é significativa, em questão da directiva ser na ```div```, é que aplicação só será válida dentro da ```div```. Ou seja, se criarmos algo fora da ```div``` não terá resultados.

## Olá Mundo

Para criarmos um Olá Mundo, iremos pegar a estrutura que foi usada anteriormente. A tag ```ng-model``` é a model da sua aplicação que faz comunicação direta com a variável, ela referência a variável na aplicação, vemos que dentro da ng-model existe o "nome" e dentro dos caracteres especiais ```{{}}``` (handlebars), existe a mesma coisa "nome". Quando digitarmos algo no input que contêm o ng-model, começará uma comunicação e dentro do handlebars aparecerá o que você digitou, 
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
<script src="http://code.angularjs.org/1.2.1/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.1/angular-route.min.js"></script>
</body>
</html>
```

<a href="http://codepen.io/nicholasess/pen/AslmG" target="_blank">Visualizar exemplo na prática</a>

## Module

O AngularJs é composto por módulo, como assim?<br>
Para cada módulo se cria um arquivo, assim fica melhor para gerir o sistema. 
Digamos que o sistema tem os arquivos [app.js, controller.js], o app.js referência ao módulo "central" do AngularJs, onde estará ligado ao HTML, é nele que definimos quais módulos conversarão com o módulo "central" e definiremos as rotas. No arquivo controller.js ficará as controllers que iremos definir nas rotas ou controllers avulsas.

Para se criar um módulo "central", onde referenciará ao arquivo app.js, temos que nomear esse módulo de forma que quando o AngularJs ler o arquivo HTML, o mesmo consiga acessar o arquivo necessário para se manter a comunicação.
Na prática fica assim:

```
A primeira coisa a se fazer é criar uma variável e depois nomear o módulo.

var App = angular.module('App',[]);

A função "angular.module();", como já é alto declarável, cria um módulo.
O parametro 'App' é a nomeação do módulo e fará a comunicação no HTML, na directiva ng-app,
será inserido o parametro 'App' para a comunicação.

Ficando desse jeito <html ng-app="App">

Dentro dos couchetes ficam as referências de outros módulos, digamos que tem o módulo de controllers,
então fica assim:

var App = angular.module('App',['Controllers']);

```
Obs: Somente o módulo "central" será referenciado no HTML, o restante será interligado nos couchetes.

## Scope

Em construção

## Routers

Em construção

## Controllers

Vamos aprofundar mais um pouco!
A explicação de controllers (Control) já foi feita, em relação ao AngularJs, funciona da seguinte maneira. 
Temos duas formas de criar controllers:
A primeira inserimos diretamente no html e referimos a controller pela diretiva ```ng-controller```, dentro da directiva indicamos o nome da controller. E no código javascript escrevemos o que a controller irá fazer.

```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body ng-app>
<div ng-controller="Ctrl">
<p>Olá {{nome}}</p>
</div>
<script src="http://code.angularjs.org/1.2.1/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.1/angular-route.min.js"></script>
<script type="text/javascript">
function Ctrl($scope){
	$scope.nome = "Mundo";
}
</script>
</body>
</html>

``` 

