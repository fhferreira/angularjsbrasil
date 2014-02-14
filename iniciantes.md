# INICIANTES

<ol>
	<li>Introdução&#10004;</li>
	<li>AngularJs e Internet Explorer&#10004;</li>
	<li>MVC&#10004;</li>
	<li>DataBind</li>
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

## Rotas

Vamos começar com uma pergunta, o que seria rotas? <br>
Quando acessamos um site comum usando um servidor apache, o servidor redireciona para o diretório raiz da aplicação, "/", onde é configurado para buscar o arquivo index que pode ser de extensão .html,.php e etc. E se renomearmos o arquivo index para outro nome e atualizarmos o site, em vez de termos a página renderizada, aparecerá o diretório do site, pois o servidor não encontrou o index. Para se configurar de fato as rotas do servidor apache, é um pouco complicado, usando a partir do arquivo .htaccess. Geralmente, se criarmos arquivo .php sem .htaccess iremos chamar os arquivos que contêm o conteúdo do html ou da aplicação. Por exemplo, digamos que temos os arquivos index.php e sobre.php, no site ```www.exemplo.com.br``` buscamos o index através da url padrão que é ```www.exemplo.com.br``` ou ```www.exemplo.com.br/index.php```, para o sobre.php buscamos ```www.exemplo.com.br/sobre.php```. Com .htaccess iremos buscar ```www.exemplo.com.br``` ou ```www.exemplo.com.br/index``` e com sobre ```www.exemplo.com.br/sobre```.

No AngularJs é um pouco mais fácil, as rotas ficam idênticas ao .htacces no servidor apache, podemos criar um arquivo separado as rotas ou no mesmo arquivo do módulo "central", vamos a prática.

```
O ensinamento será passo a passo para vocês entenderem e no final terá a função pronta.

Primeiro declaramos o module do angular
var app = angular.module('app',[]);

Depois criamos uma função chamada config, onde será passado um parametro chamado $routeProvider, responsável por fazer as rotas da aplicação.
app.config(function($routeProvider){});

Dentro dessa função chamamos o $routeProvider e .when que será responsável por indicar ou melhor dizendo, routiar as rotas da aplicação. O significado é "quando", então, quando indicarmos uma url na aplicação o $routeProvider vai procurar as rotas que estão configuradas com ele.
app.config(function($routeProvider){
	$route.when();
});

Dentro do .when, vamos indicar a rota a ser configurada entre aspas e dentro de uma estrutura json vamos indicar a url da página que será chamada através do campo templateUrl. Dentro das aspas temos a url, 'views/home.html', que indica a pasta views e o arquivo html que irá conter informações relevantes a home da aplicação.
app.config(function($routeProvider){
	$route.when('/', 
	{
	    templateUrl: 'views/home.html'
	});
});

No final ficamos assim:
var app = angular.module('app',[]);
app.config(function($routeProvider){
	$route.when('/', 
	{
	    templateUrl: 'views/home.html'
	});
});
```
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
<div ng-controller="MainCtrl">
<p>Olá {{nome}}</p>
</div>
<script src="http://code.angularjs.org/1.2.1/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.1/angular-route.min.js"></script>
<script type="text/javascript">
function MainCtrl($scope){
	$scope.nome = "Mundo";
}
</script>
</body>
</html>

``` 

Podemos criar através do módulo em um arquivo js e referenciamos a controller em outro arquivo.

```
<!DOCTYPE html>
<html>
<head>
	<title>AngularJs</title>
</head>
<body ng-app="App">
<div ng-controller="MainCtrl">
<p>Olá {{nome}}</p>
</div>
<script src="http://code.angularjs.org/1.2.1/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.1/angular-route.min.js"></script>
<script src="app.js"></script>
<script src="controller.js"></script>
</body>
</html>

```

No arquivo app.js fica assim:

```
var App = angular.module('App',['Controller']);
```

No arquivo controller.js fica assim:

```
var Ctrl = angular.module('Controller',[]);
Ctrl.controller('MainCtrl', function($scope){
	$scope.nome = "Mundo";
});
```

Ou podemos fazer com rotas que daria o mesmo resultado.
Primeiro vamos criar arquivo html que ficará a aplicação e outro arquivo html que será referenciado pela rota.

index.html
```
<!DOCTYPE html>
<html>
<head>
<title>AngularJs</title>
</head>
<body ng-app="App">
<div ng-view></div>
<script src="http://code.angularjs.org/1.2.1/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.1/angular-route.min.js"></script>
<script src="app.js"></script>
<script src="controller.js"></script>
</body>
</html>

```

home.html
```
<p>{{nome}}</p>
```

No arquivo app.js fica assim:

```
var App = angular.module('App',['Controller']);
App.config(['$routeProvider',function($routeProvider){
 $routeProvider.when('/', 
 {
     templateUrl: 'home.html',
     controller: 'MainCtrl'
 });
)]);
```

No arquivo controller.js fica assim:

```
var Ctrl = angular.module('Controller',[]);
Ctrl.controller('MainCtrl', function($scope){
	$scope.nome = "Mundo";
});
```
