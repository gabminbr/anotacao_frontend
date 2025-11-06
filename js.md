# Data types
- usaremos a palavra *let* para declarar variáveis em javascript:
```javascript
let numero = 90;
console.log(numero);
```
- usaremos a palavra reservada *const* para declarar constantes:
```javascript
const PI = 3.14159;
console.log(PI);
```
# Condicionais
- padrão de sempre, até o switch case.
- ternário:
```javascript
let result = condition ? value1 : value2;
```

# Funções
- para criar funções, usaremos a palavra chave *function*:
```javascript
function favoriteAnimal(animal){
  console.log("eu sou um" + animal);
}
```
- parametros "default": quando queremos que um parametro seja opcional numa função, usaremos ele, exemplo:
```javascript
function greeting(name = "No name given"){
  return "Hello, " + name;
}
console.log(greeting()); // vai printar "Hello, No name given"
```
## Functions Expressions
- como já foi mostrado, um jeito de declarar funções é usando a palavra reservada *function*, porém existem outros meios de declarar funções
- é chamada function expression, exemplo:
```javascript
let sayHi = function() {
  alert( "Hello" );
};
```
- note que não existe um nome para a função, apenas a palavra reservada *function*.
- podemos passar funções sem os parenteses para variaveis, o que vai ser copiado vai ser a funcao, exemplo:
```javascript
function sayHi(greeting, name){
  return greeting + ", " + name;
}

let say2 = sayHi;
console.log(say2); // note que nao usei os parenteses, logo vai printar o corpo da funcao.
```
## Arrow Functions
- é outra maneira de criar funções, até melhor que a anterior:
- estrutura: *let func = (arg1, arg2, ..., argN) => expression;*
- é o equivalente a:
```javascript
let func = function(arg1, arg2, ..., argN) {
  return expression;
};
```
