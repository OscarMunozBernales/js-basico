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

## 1.5. Scope
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

## 1.6. Hoisting.
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

