# js-basico

# 1. Introducción
## 1.1. ¿Qué es JavaScript?
### ¿Cómo nace Javascript?
Nace con la necesidad de generar dinamismo en las páginas web y que a su vez los usuarios y las empresas pudieran interactuar unos con otros.
### ¿Qué es Javascript?
Es un lenguaje interpretado, orientado a objetos, débilmente tipado y dinámico.
### Débilmente tipado
Se pueden hacer operaciones entre tipos distintos de datos (enteros con strings, booleanos con enteros, etc). Ejemplo:

```javascript
4 + "7";    // RESULTADO: 47
4 * "7";    // RESULTADO: 28
2 + true;   // RESULTADO: 3
false - 3;  // RESULTADO: -3
```
### Dinámico
Corre directamente en la etapa de Runetime sin una etapa de compilación previa. Esto permite probar nuestro código inmediatamente; pero también es lo que hace que los errores se muestren hasta que se ejecuta el programa.
¿Realmente es Javascript un lenguaje interpretado?
Si, y la razón es que le navegador lee linea por linea nuestro código el cuál le indica lo que tiene que hacer, sin la necesidad de compilar. Todo esto es controlado por el motor de Javascript V8 del navegador
### Javascript es Basckwards Compatible
Todas las funciones nuevas que salen de Javascript no dañarán el trabajo ya hecho, pero no se podrá utilizar en nuestro entorno de trabajo inmediatamente. Para solucionar esto está Babel que permite utilizar las nuevas características del lenguaje pero lo transforma a una versión que el navegador pueda entender.

## 1.2. ¿Por qué JavaScript?
- JavaScript tiene una comunidad enorme de desarrolladores que te pueden ir ayudando a generar diferentes cosas.
- Si solo estuvieras interesado en trabajar **aplicaciones web** tienes muchos frameworks y librerías construidas en JavaScript que te van a ayudar a hacer proyectos de forma mucho mas rápida, eficiente y robusta **(Angular, View, React,entre otros)**.
- Si no quieres trabajar solo en aplicaciones Web puedes utilizar JavaScript con un framework que se llama **React Native** para poder construir aplicaciones nativas como **Android y IOS**.
- Puedes construir **aplicaciones de escritorio** con JavaScript, usando un framework llamado **Electron**, pueden correr en Mac o Windows.
- También puedes trabajar en la parte del **Back-end o IOT (Internet Od Things)** es un concepto que se refiere a una interconexion digital de objetos cotidianos con Internet. Esto con un Framework llamado **NodeJS**, el cual es un entorno de ejecución de JavaScript que corre directamente en el Back-end.

## 1.3. Variables
Dentro de JavaScript tenemos tres formas de declarar una variable las cuales son: **var, const y let**.
- **Var**: Era la forma en que se declaraban las variables hasta ECMAScript 5. Casi ya no se usa porque es de forma global y tiene las siguientes características:

    - Se puede reinicializar: osea todas las variables se inicializan, por ejemplo:
    ```javascript
    var pokemonType = "electric" // entonces reinicializar es:
    var pokemonType = "grass" // osea la misma variable con diferentes datos el último dato predomina.
    ```
    
    - Se puede reasignar: osea la variable ya inicializada le reasignamos otro valor por ejemplo: inicializamos la variable: Var pokemonType = ‘electric’ ahora la reasignamos pokemonType = ‘grass’ ya no va var
    - Su alcance es función global: osea inicializamos la variable, pero la podemos llamar desde cualquier bloque (una llave abierta y una cerrada "{}" ) pero hay que tener mucho cuidado con ello ya que puede haber peligro, no es recomendable usar VAR.

    const y let es la forma en que se declaran las variables a partir de ECMAScript 6,

- **const**: sirve para declarar variables que nunca van a ser modificadas:
    - No se puede reinicilizar: es una const única no puede haber otra inicializada con el mismo nombre. const pokemonType = ‘electric’ no puede haber:
    ```javascript
    const pokemonType = ‘grass’
    ```
    - No se pude re asignar: una vez que la hayamos inicializado no la podemos reasignar solo con su nombre: const pokemonType = ‘electric’ no puede ejecutarse:
    pokemonType = ‘grass’
    - No es inmutable: osea no puede cambiar con objetos:

- **Let**: Son variables que pueden ser modificadas, se pueden cambiar:
    - No se puede reinicilizar: es una const única no puede haber otra inicializada con el mismo nombre. let pokemonType = ‘electric’ no puede haber:
    ```javascript
    let pokemonType = ‘grass’
    ```
    - Se puede reasignar: Osea la variable ya inicializada le reasignamos otro valor por ejemplo: inicializamos la variable: let pokemonType = ‘electric’ ahora la reasignamos pokemonType = ‘grass’
    - Su contexto de es bloque: Solo funciona dentro de un bloque {}, fuera de ello no.

## 1.4. Funciones
Las funciones son las tareas que va a llevar a cabo el navegador. Existen 2 tipos de funciones
- **Declarativas**
- **De expresión**

```javascript
// declarativas
function miFuncion( param1, param2 ){
    //code
}

// De expresion y anonimas

const miFunction = function( param1, param2 ){
    // code
    return a + b;
}
```
Ambas pueden llevar parámetros, que son los datos que necesitan para ejecutarse.
Cada parámetro va separado por una coma.
Cada instrucción que tenga la función debe terminar con ;

Ejemplo
```javascript

function sumar( param1, param2 ){
    return param1 + param2;
}

const sumar = function( param1, param2 ) {
    return param1 + param2;
}
```

# 2. Bases de javascript
## 2.1. Scope
Basicamente el scope es un todo, es en todo el documento de js en donde tenemos a nuestra disposicion variables, funciones etc, pero existen sub-scope en donde las variables que se van a inicializar dentro no se van a poder ocupar afuera.

```javascript
var miNombre = "Oscar";

function nombreCompleto(){
    var miApellido = "Muñoz";
    console.log( miNombre + " " + miApellido );
}

nombreCompleto();           // VA A IMPRIMIR OSCAR MUÑOZ
console.log(miNombre);      // VA A IMPRIMIR OSCAR
console.log(miApellido);    // NOS INDICARA QUE LA VARIABLE NO EXISTE.

```

## 2.2. Hoisting.
Si tenemos el siguiente código, que lo va a imprimir por pantalla:
```javascript

console.log(nombre);
var nombre = "Oscar";

// undefine
```

Puesto que las variables inicializadas con **var** suben hasta lo mas alto del scope para inicializarce:
```js
var nombre;
console.log(nombre);
nombre = 'Oscar';
```
Lo mismo pasa con las funciones, es como javascript va a interpretar nuestro codigo:
```js

saludar("OSCAR");
function saludar(nombre){
    var saludo = "Hola " + nombre;
    console.log(saludo);
}
```
js lo interpreta de la siguiente manera:
```js
function saludar(nombre){
    var saludo;
    saludo = "Hola " + nombre;
    console.log(saludo);
}
saludar("OSCAR");
```
Actualmente en el ESC6 no ocurre el hoisting, puesto que este solo se ejecuta cuando ocupamos funcioens y variables inicializadas con var, actualmente se ocupan funciones anonimas y las varaibles se inicializan en let
```js
let nombre = "OSCAR";
let saludar = (nombre) => {
    console.log( "HOLA " + nombre );
}
saludar(nombre);
```

## 2.3. Coerción.

Coerción es la forma en la que podemos cambiar un tipo de valor a otro, existen dos tipos de coerción:
Coerción implícita = es cuando el lenguaje nos ayuda a cambiar el tipo de valor.
Coerción explicita = es cuando obligamos a que cambie el tipo de valor.

```js
4 + '7';    // 11
4 * '7';    // 28
2 + true;   // 3
false - 3;  // -3
```

## 2.4. Valores: Truthy y Falsy
Ejemplos en los que Boolean devuelve Falso:
```js
Boolean(0); //false
Boolean(null); //false
Boolean(NaN); //false
Boolean(undefined); //false
Boolean(false); //false
Boolean(""); //false
```
Ejemplos en los que Boolean devuelve verdadero:
```js
Boolean(1); //true para 1 o cualquier número diferente de cero (0)
Boolean("a"); //true para cualquier caracter o espacio en blanco en el string
Boolean([]); //true aunque el array esté vacío
Boolean({}); //true aunque el objeto esté vacío
Boolean(function(){}); //Cualquier función es verdadera también
```

## 2.5. Operadores
### Operadores de asignación

|Nombre|Operador abreviado|Significado
|--|--|--|
|Asignación|x = y|x = y
|Asignación de adición|x += y|x = x + y
|Asignación de resta|x -= y|x = x - y
|Asignación de multiplicación|x *= y|x = x * y
|Asignación de división|x /= y|x = x / y
|Asignación de residuo|x %= y|x = x % y
|Asignación de exponenciación|x **= y|x = x ** y
|Asignación de desplazamiento a la izquierda|x <<= y|x = x << y
|Asignación de desplazamiento a la derecha|x >>= y|x = x >> y
|Asignación de desplazamiento a la derecha sin signo|x >>>= y|x = x >>> y
|Asignación AND bit a bit|x &= y|x = x & y
|Asignación XOR bit a bit|x ^= y|x = x ^ y
|Asignación OR bit a bit|x |= y|x = x | y
|Asignación AND lógico|x &&= y|x && (x = y)
|Asignación OR lógico|x \|\|= y|x \|\| (x = y)
|Asignación de anulación lógica|x ??= y|x ?? (x = y)

### Operador de comparación
|Operador|Descripción
|--|--|
|Igual (==)|Devuelve true si los operandos son iguales.
|No es igual (!=)|Devuelve true si los operandos no son iguales.
|Estrictamente igual (===)|Devuelve true si los operandos son iguales y del mismo tipo. Consulta también Object.is y similitud en JS.|
|Desigualdad estricta (!==)|Devuelve true si los operandos son del mismo tipo pero no iguales, o son de diferente tipo.|
|Mayor que (>)|Devuelve true si el operando izquierdo es mayor que el operando derecho.|
|Mayor o igual que (>=)|Devuelve true si el operando izquierdo es mayor o igual que el operando derecho.|
|Menor que (<)|Devuelve true si el operando izquierdo es menor que el operando derecho.|
|Menor o igual (<=)|Devuelve true si el operando izquierdo es menor o igual que el operando derecho.|

### Operadores aritméticos
|Operador|Descripción|Ejemplo|
|--|--|--|
|Residuo (%)|Operador binario. Devuelve el resto entero de dividir los dos operandos.|12 % 5 devuelve 2.|
|Incremento (++)|Operador unario. Agrega uno a su operando. Si se usa como operador prefijo (++x), devuelve el valor de su operando después de agregar uno; si se usa como operador sufijo (x++), devuelve el valor de su operando antes de agregar uno.|Si x es 3, ++x establece x en 4 y devuelve 4, mientras que x++ devuelve 3 y , solo entonces, establece x en 4.|
|Decremento (--)|Operador unario. Resta uno de su operando. El valor de retorno es análogo al del operador de incremento.|Si x es 3, entonces --x establece x en 2 y devuelve 2, mientras que x-- devuelve 3 y, solo entonces, establece x en 2.|
|Negación unaria (-)|Operador unario. Devuelve la negación de su operando.|Si x es 3, entonces -x devuelve -3.|
|Positivo unario (+)|Operador unario. Intenta convertir el operando en un número, si aún no lo es.|+"3" devuelve 3. +true devuelve 1.|
|Operador de exponenciación (**)|Calcula la base a la potencia de exponente, es decir, base(exponente)|2 ** 3 returns 8. 10 ** -1 returns 0.1.|

# 3.Condicionales
## 3.1. Condicionales: If, Else, else if
Una sintaxis básica de if .. else, luce así
```js
if (condicion){
    // Código a ejecutar si la condición es verdadera.
}else {
    // Código a ejecutar si la condición es falsa.
}
```

Ademas para no anidar muchos if dentro del else, existe el else if:
```js
if (condicion1) {
    // Codigo a ejecutar si la condición es verdadera
} else if (condicion2) {
    // Código a ejecutar si la condición 1 es falsa y la condición 2 es verdadera
} else if (condicionN) {
    // Código a ejecutar si la condición 1 y 2 son falsas y la condición N es verdadera
} else {
    // Código a ejecutar si las condiciones son falsas.
}
```

## 3.1. Switch.
La declaración switch evalúa una expresión, comparando el valor de esa expresión con una instancia case, y ejecuta declaraciones asociadas a ese case, así como las declaraciones en los case que siguen.

```js
switch (expresión) {
  case valor1:
    //Declaraciones ejecutadas cuando el resultado de expresión coincide con el valor1
    break;
  case valor2:
    //Declaraciones ejecutadas cuando el resultado de expresión coincide con el valor2
    break;
  ...
  case valorN:
    //Declaraciones ejecutadas cuando el resultado de expresión coincide con valorN
    break;
  default:
    //Declaraciones ejecutadas cuando ninguno de los valores coincide con el valor de la expresión
    break;
}
```

Ejemplo:
```js
switch (expr) {
  case 'Naranjas':
    console.log('El kilogramo de naranjas cuesta $0.59.');
    break;
  case 'Manzanas':
    console.log('El kilogramo de manzanas cuesta $0.32.');
    break;
  case 'Platanos':
    console.log('El kilogramo de platanos cuesta $0.48.');
    break;
  case 'Cerezas':
    console.log('El kilogramo de cerezas cuesta $3.00.');
    break;
  case 'Mangos':
  case 'Papayas':
    console.log('El kilogramo de mangos y papayas cuesta $2.79.');
    break;
  default:
    console.log('Lo lamentamos, por el momento no disponemos de ' + expr + '.');
}

console.log("¿Hay algo más que te quisiera consultar?");
```

# 4. Arrays
Los arrays son objetos similares a una lista cuyo prototipo proporciona métodos para efectuar operaciones de recorrido y de mutación. Tanto la longitud como el tipo de los elementos de un array son variables. Dado que la longitud de un array puede cambiar en cualquier momento, y los datos se pueden almacenar en ubicaciones no contiguas, no hay garantía de que los arrays de JavaScript sean densos; esto depende de cómo el programador elija usarlos. En general estas características son cómodas, pero si, en su caso particular, no resultan deseables, puede considerar el uso de arrays con tipo.

Crear un Array
```js
let frutas = ["Manzana", "Banana"]

console.log(frutas.length)
// 2
```

Acceder a un elemento de Array mediante su índice
```js
let primero = frutas[0]
// Manzana

let ultimo = frutas[frutas.length - 1]
// Banana
```

Recorrer un Array
```js
frutas.forEach(function(elemento, indice, array) {
    console.log(elemento, indice);
})
// Manzana 0
// Banana 1
```

Existen muchos metodos más, como por ejemplo agregar un elemento al array, quitar un elemento, modificar un elemento, todo esto lo podemos ver en el [Siguiente enlace](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array)

