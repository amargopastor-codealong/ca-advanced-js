# Var let const hoisting

Concepto MUY importante digno de entrevista de trabajo:

```js
nombreDelGato('Maurizzio');

function nombreDelGato(nombre) {
	console.log('El nombre es ' + nombre);
}
```

En el caso anterior, de manera contraintuitiva podemos llamar una varibale declarada posteriormente.

Digamos que durante la normal ejecuión de un archivo JS existen `2 pasos`: primero se prepara todo el código y en el segundo se ejecuta. Antes de ejecutar el código, JS lo `compila`. En el caso de JS, el `compilardor` está escrito en C++ (también llamado código emsamblador) y convierte nuestro código JS en O´s y 1´s para que la CPU lo pueda entender.

A esto se le llama `HOISTING` e implica que todas nuestras funciones existen, independientemente del orden que pongamos en el código. En el primer paso se prepara todo el código y en el segundo se ejecuta. Digamos que JS lee todo el código y luego lo reordena.

De esta manera podemos concluir que `el HOISTING dice que las declaraciones se transladan al inicio de su propio contexto`.

Veamos el siguiente ejemplo. ¿Habrá un error o veremos el valor de la variable?. Obtenemos undefined

```js
console.log(nombre); // undefined
var nombre = 'Marcos';
```

El hoisting (o elevación) hace que `las variables declaradas con var` se separan de su inicialización (dar valor, en este caso el string Marcos) y se eleva al inicio de su scope (al inicio de la función o del scope general):

```js
var nombre;
console.log(nombre); // undefined
nombre = 'Marcos';
```

En el siguiente caso cuando ejecutamos nuestro código obtenemos `1 undefined`: esto es debido a que `la DECLARACIÓN y ASIGNACIÓN de las variables son dos procesos distintos`. Es decir, ambas variables están declaradas pero sólamente la X está inicializada.

```js
var x = 1; // Declara e inicializa la variable x a 1.
console.log(x + ' ' + y); //1 undefined
var y = 2; //  Declara e inicializa la variable y
```

Tanto el `orden como la declaración de variables` son muy importantes.

```js
var x = 1;
console.log(x, y); //1 undefined
var y = 2;
x = 10;
console.log(x, y); // 10 2
```

`IMPORTANTE`: Declaración de variable e inicialización (asignación de valor) son dos términos distintos, y JS los separa. Las asignación no se pueden reordenar.

El `HOSTING` separa la declaración de las variables. Ambas variables existen independientemente de donde pongamos el var. La y está declarada pero vale undefined porque `se le da valor a posteriori`. El orden es importante.

Declarar las variables con `var` hace que estas tengan un scope de función por lo que es posible que se nos presenten algunos errores involuntarios. En el siguiente ejemplo, estamos declarando con var funciones dentro de un bucle for a las que podemos acceder una vez finalizado. Pero si tuviéramos una `variable num anterior` estaríamos perdiendo su valor sin querer:

```js
function mitades(numeros) {
	var resultado = [];
	var num = 42;
	console.log('num', num); // num 42
	for (var i = 0; i < numeros.length; i++) {
		var num = numeros[i];
		var mitad = num / 2;
		resultado.push(mitad);
	}
	// Solo vemos el último resultado:
	console.log('num', num); // num 55 (perdemos 42)
	console.log('mitad', mitad); // mitad 27.5
	console.log('i', i); // i 5 (el número que hace que no se cumpla la condición del if)

	return resultado;
}

mitades([4, 7, 99, 5, 55]);
```

## LET

<img src="./img/img1.png" width=450/>

Si `declaramos una variable con let` esta no hace HOISTING: ¡DIFERENCIA CON `VAR`!. El declarar las varibales con let te impide que las uses antes de su declaración. Esto nos protege de cometer errores.

```js
let x = 1;
console.log(x); // 1
console.log(x + ' ' + y); // Uncaught ReferenceError: Cannot access 'y' before initialization
let y = 2;
```

Vemos en el siguiente for un ejemplo de esto mismo al `declarar i con LET`:

```js
for (let i = 0; i < 10; i++) {
	console.log(i);
}
console.log(i); // i no está definida ya que i se declara con un LET dentro del bucle for
```

Sin embargo, en el siguiente bucle i da 10 porque la var existe fuera del bucle gracias a `declarar la variable con VAR`:

```js
for (var i = 0; i < 10; i++) {
	console.log(i);
}
console.log(i);
```

Veamos un ejemplo más:

```js
var i = 5;
if (i < 10) {
	var z = 10; // declración con var
	let o = 10; // let sólo existe dentro de este bloque.
	console.log('El valor es', i);
}

console.log('Final', z); // Final 10
console.log('Final', o); // ERROR: Uncaught ReferenceError: o is not defined
```

Ver en detalle este caso: aunque no entremos en el if la variable `var z` queda inicializada aunque vale undefined. Si empleamos `let` z, dara error porque sólo existe en ese if.

```js
var i = 5;
if (i < 3) {
	var z = 10; // Declaración con var: existe fuera del bloque (declarada pero no inicializada porque no entramos en el bloque).
	let o = 10; // let sólo existe dentro de este bloque.
	console.log('El valor es', i);
}

console.log('Final', z); //Final undefined porque se inicializa al inicio del contexto de ejecución pero solo toma valor dentro del bloque if. Como no entramos en el bloque if, no llega a tomar valor.
console.log('Final', o); //ERROR!
```

Las variables declaras con `LET y CONST tendrán un alcance de bloque:` es decir serán vigentes solamente en la porción de código encerradas en {}. Siendo esto así, dado el caso anterior tenemos:

```js
function mitades(numeros) {
	let resultado = [];
	let num = 42;
	console.log('num', num); // num 42
	for (let i = 0; i < numeros.length; i++) {
		let num = numeros[i]; // declaramos
		let mitad = num / 2;
		resultado.push(mitad);
	}
	console.log('num', num); // num 42
	console.log('mitad', mitad); // Uncaught ReferenceError: mitad is not defined

	return resultado;
}

mitades([4, 7, 99, 5, 55]);
```

## CONST

`CONST` impide reasignar el valor de una varibale (es una `constante`). Cuando declaramos `una variable CONST siempre tiene que tener valor`.

```js
// var i = 5;
// let i = 5;
// const i = 5;

const a = 3;
console.log(a);
a = 1000; // ERROR!
console.log(a);
```

En el sigueinte ejemplo, como estamos empleando `LET` lo podemos reasignar a otro objeto.

```js
let objet = { name: 'Pepe' };
console.log(objet);
objet = { name: 'Juan' };
console.log(objet);
```

Si usamos `CONST`, no podemos reasignar.

```js
const objet = { name: 'Pepe' }; // esto es un objeto: contenedor con keys y values. El contenedor es constante pero el contenido puede cambiar.
console.log(objet);
object = { name: 'Juan' }; // ERROR: no podemos asignar tras declarar con const.
objet[name] = 'Juan'; // OK ya que cambiamos el contenido, no el contenedor.
objet.name = 'Juan'; // OK idem
objet.surname = 'Gomez'; // OK idem
console.log(objet); // correcto
```

- `Var`: Existe siempre. Hace HOISTING.
- `Let`: Solo existe en el bloque donde es definida. `Let no tiene HOISTING`.
- `Const`: El contenedor es constante: cambiamos el contenido pero el objeto no varía. Puede ser un objeto vacío y podemos ir añadiendole propiedades. `Const no tiene HOISTING`.

## SHADOWING

El `SHADOWING` implica que la declaración de x en un scope (el de la función) prevalece sobre la x definida fuera.

Ejemplo de `función AUTOEJECUTADA` para comprender diferencias y combinación de SHADOWING y HOSTING. En este caso, la `declaración de X en el contexto de la función prevalece sobre la declaración anterio`r.

```js
var x = 5;
(function () {
	console.log('x:', x); // x: undefined porque se hace SHADOWING de x al declarar x en la siguiente línea y el HOISTING hace que valga undefined
	var x = 10; // Si comentamos esta línea vemos justo el SHADOWING
	// x = 10 Si no definimos con var la función simplemente reasignamos la variable anteriormente declara de x.
	console.log('x:', x);
})();
```

En base al anterior ejemplo, si quitamos el var de la función declara dentro, ya no se hace shadowing y se coge la x declarada fuera:

```js
var x = 5;
(function () {
	console.log(x); // undefined
	x = 10;
	console.log(x);
})();
```

Por último, si empleamos let este tiene shadowing pero un console.log(x) anterior dará error porque no tiene hoisting:

```js
var x = 5;
(function () {
	console.log(x); // script.js:3 Uncaught ReferenceError: Cannot access 'x' before initialization
	let x = 10;
	console.log(x);
})();
```

## Which is better ?

> const > let > var

## References

- [var, let and const - What, why and how - ES6 JavaScript Features](https://www.youtube.com/watch?v=sjyJBL5fkp8&ab_channel=FunFunFunction)
- [Hoisting](https://developer.mozilla.org/es/docs/Glossary/Hoisting)
- [Fun Fun Function videos](https://www.youtube.com/c/funfunfunction/videos)
