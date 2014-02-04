O foco dessa série é ensinar AngularJs e criar situações que o AngularJs possa ser a solução.

<ol>
	<li>Introdução</li>
	<li>Iniciando uma aplicação</li>
	<li>Olá Mundo com AngularJs</li>
	<li>Scope</li>
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
AngularJs é um framework JavaScript MVC/MVVM, fácil de ser aprendido e a curva de aprendizado é pequena em relação a outros frameworks. Como toda a linguagem, no começo é fácil, mas conforme vai se aprofundando, é necessário um pouco mais de atenção, mas não irá desanimar. O AngularJs é uma ferramenta essencial para quem deseja criar sistemas (web apps) com facilidade e ter todo controle do lado client side.

# Iniciando uma aplicação

Para iniciar uma aplicação no corpo HTML é necessário inserir as referências do AngulaJS nos scripts.

```html
<html>
<head>
	<title>AngularJs</title>
</head>
<body>
<script src="http://code.angularjs.org/1.2.11/angular.min.js"></script>
<script src="http://code.angularjs.org/1.2.11/angular-route.min.js"></script>
</body>
</html>
```html

O primeiro script é referente ao Angular e segundo script é referente as rotas, que irei explicar mais adiante.

Após ter incluido os arquivos, é necessário inserir directivas do Angular para que ele consiga identificar no corpo do HTML que o arquivo é uma aplicação angular, como fazemos?

A directiva principal do angular é a ***ng-app***, é ela que dirá ao angular para que comece a trabalhar naquele HTML.




