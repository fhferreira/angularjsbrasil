O foco dessa série é ensinar AngularJs e criar situações que o AngularJs possa ser a solução.

<ol>
	<li>Introdução</li>
	<li>MVC</li>
	<li>MVVM</li>
	<li>Iniciando uma aplicação</li>
	<li>Olá Mundo com AngularJs</li>
	<li>Scope</li>
	<li>Injeção de Dependências</li>
	<li>Controllers</li>
	<li>Routers</li>
	<li>RootScope</li>
	<li>Services</li>
	<li>Filters</li>
	<li>Directives</li>
</ol>


# Introdução
	
O AngularJs surgiu em meados de 2009, foi criado por dois funcionários da Google e após um tempo a Google
adotou o projeto e hoje existe uma equipe focada somente no AngularJs.
AngularJs é um framework JavaScript MVC/MVVM, fácil de ser aprendido e a curva de aprendizado é pequena em relação a outros frameworks. Como toda a linguagem, no começo é fácil, mas conforme vai se aprofundando, é necessário um pouco mais de atenção, mas não irá desanimar. O AngularJs é uma ferramenta essencial para quem deseja criar sistemas (web apps) com facilidade e ter todo controle do lado client.

# MVC

# MVVM

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

A directiva ***ng-app*** pode ser incluida no ```head``` ou ```body``` ou em uma ```div``` qualquer.

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

A diferença entre a directiva no ```head``` ou no ```body``` não é significativa, em questão da directiva ser na ```div```, é que aplicação só será válida dentro da ```div```. Ou seja, se fizer algo fora da ```div``` não terá resultados.

