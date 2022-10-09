# JS Advanced

## Operador IN

El operador `in` devuelve true o false si la propiedad está en el objeto especificado o su prototipo:

```js
if (letras[i] in cuenta) {
	// nuestro código
}
```

Vamos a crear nuestro propio `contador de vocales` para ver el ejemplo de in:

```js
let voc = ['a', 'e', 'i', 'o', 'u'];
let frase =
	'Bienvenidos a la semana 3 de programación, ahora más azúcar sintáctico que nunca';
let letras = frase.toLowerCase().split('');
let cuenta = {};

for (e in letras) {
	if (voc.includes(letras[e])) {
		if (letras[e] in cuenta) {
			cuenta[letras[e]]++;
		} else {
			cuenta[letras[e]] = 1; // Cada vez que encuentra una vocal crea una key en el objeto
		}
	}
}

console.log(cuenta); // { i: 2, e: 7, o: 4, a: 7, u: 2 }
```

## Single Purpose Functions

Es importante comprender porqué las funciones deben ser de un `único propósito`. De esta manera podremos ser más eficientes y generar código de mayor calidad. En el siguiente ejemplo hemos dividido la función anterior en una función que recorre una lista y una segunda que saluda:

```js
let recorreArray = function (a, fn) {
	for (let i = 0; i < a.length; i++) {
		fn(a[i]);
	}
};

let saluda = function (m) {
	console.log('Hola', m);
};

let frase = 'Hola que tal, bienvenido a estas clases de programación';
let letras = frase.toLowerCase().split('');
recorreArray(letras, saluda); // Paso como parámetro el string frase y la función saluda.
```

Si hacemos funciones de un único propósito `el código es mucho más mantenible` y podemos reutilizarlo las veces que queramos.

## Arrow functions

Los arrow function son `atajos sintácticos` que nos permiten escribir código de manera más rápida. Por ejemplo, nuestra definición de función clásica:

```js
function saluda() {
	console.log('Hola Code Lover');
}
```

Es lo mismo que:

```js
const saluda = () => console.log('Hola Code Lover');
```

```js
// OJO! Returns undefined because console.log
saluda();
```

```js
// Returns is implicit: the expression is evaluated and retuned
const suma = (a, b) => a + b;
console.log(suma(5, 10)); // prints 15
```

- Facilita las operaciones rápidas como `forEach`,`map`,`reduce`,`filter`, `callbacks`, etc.
- Si tienes `parámetros`, los pasas a la función dentro de los paréntesis.
- Si la función posee solo una acción y esta devuelve un valor, podemos `eliminar las llaves y la palabra return`.
- Si tenemos sólo un parámetro, podemos quitar los paréntesis también.
- Siempre son anóminas y quedan asignadas a una variable o se pasan como callback

```js
let say = () => {
	return 'hello';
};
let say = (m) => {
	return 'Hello ' + m;
};
let say = (m) => 'Hello ' + m;
let say = (m) => 'Hello ' + m;
```

# High order functions

Una `higher-order function` es una función que acepta funciones como parámetros y/o que devuelve una función.

```js
function suma(a) {
	function inner(b) {
		return a + b;
	}
	return inner;
}

let a = 6;
let b = 4;

let resultado = suma(a)(b);
console.log(resultado);
```

## Composition

```js
suma(suma(3))(6);
```

# Callback pattern

El `patrón callback o función callback` es una función que es pasada a otra función como argumento. Esta función puede ser invocada durante la ejecución en su higher order function.

```js
let recorreArray = function (a, fn) {
	for (let i = 0; i < a.length; i++) {
		fn(a[i]);
	}
};

let saluda = function (m) {
	console.log('Hola', m);
};

let nombres = ['Pepe', 'Luis', 'Juan'];
recorreArray(nombres, saluda);
```

```js
let voc = ['a', 'e', 'i', 'o', 'u']; // Definimos array

let saluda = (p) => 'Hello ' + p; // Definimos fn saluda que devuelve string

let recc = (a, fn) => {
	// Definimos función recc que recibe array y saluda() y pinta el resultado de la fn saluda();
	for (i in a) {
		console.log(fn(a[i]));
	}
};
let result = recc(voc, saluda);
console.log(result);
```
