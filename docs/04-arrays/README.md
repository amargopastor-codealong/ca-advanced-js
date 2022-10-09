# Arrays

## Iterate an array

```js
let data = [1, 2, 3, 4, 5];
for (let i = 0; i < data.length; i++) {
	console.log(i);
}
```

## Reverse iteration

A continuación veremos varios problemas de búsqueda que implican arrays y blucles.

> Dato importante: Accessing a not indexed position returns `undefined`.

One way:

```js
// El array contiene índides de 0 a 4
let data2 = [1, 2, 3, 4, 5];
for (let i = 0; i < data2.length; i++) {
	let element = data2[data2.length - i]; // UNDEFINED: no existe la posición 5
	let element = data2[data2.length - 1 - i]; // Correcto!
	console.log(element);
}
```

Another way:

```js
let data3 = [1, 2, 3, 4, 5];
for (let i = data3.length; i > 0; i--) {
	let element = data3[i]; // UNDEFINED: no existe la posición  5
	let element = data3[i - 1]; // Correcto!
	console.log(element);
}
```

Another way:

```js
let data3 = ['a', 'b', 'c', 'd', 'e'];
for (let i = data3.length; i > 0; i--) {
	let element = data3[i - 1]; // Ocurre igual que en el caso anterior.
	console.log(element);
}
```

## Find an element an array by using a loop and `break`

Los array son una de las estructuras primitivas de JS. Siempre que necesitos guardar una serie de datos (del mismo o distinto tipo) con un orden concreto. Es una estructura muy utilizada que nos obliga a dominar el concepto de los bucles. Dicho de otro modo: muy probablemente `si vemos un array tendremos que usar un bucle`.

La palabra reservada `break` permite la `interrupción del bucle` en el punto dónde nos encontremos y continua la ejecución normal del código. En el siguiente ejemplo es funcdamental para el `ahorro de recursos`.

```js
let names = ['Pepe', 'Luis', 'Juan', 'Code'];
let needle = 'Luis';

for (let i = 0; i < names.length; i++) {
	if (needle == names[i]) {
		console.log('Found ' + needle + ' at position ' + i);
		break; // En el momento en que encontremos el elemento búsqueda aplicamos un break (para ahorrar recursos).
	}
	console.log('test');
}
console.log('Fin');
```

## Our own find function

```js
names2 = ['Pepe', 'Luis', 'Juan', 'Code'];

function find(array, element) {
	for (let i = 0; i < array.length; i++) {
		if (element == array[i]) {
			return i;
		}
	}
	// return false
	return -1;
}

let result = find(names2, 'Pepe');
// if (result) { // Si hacemos que nuestra función find haga un return de 0 dará false.
// if (result != false) // Sigue dando error.
if (result >= 0) {
	// Correcto!
	console.log('Encontrado');
} else {
	console.log('No esta');
}
```

```js
let names1 = ['Pepe', 'Luis', 'Juan', 'Code'];
names1.includes('Code'); //Método por defecto de los array que devuelve true si existe.
```

## Filter an array

Vamos a generar una instrucción que muestre sólo los `números pares` de un array:

```js
let data = [22, 33, 56, 98, 105];
let result = []; // Generamos un array vacío que contendrá el resultado.

for (let i = 0; i < data.length; i++) {
	// Comprobamos si es número par
	if (data[i] % 2 == 0) {
		result.push(data[i]);
	}
}

console.log('el resultado es');
console.log(result);
```

## For... of

La herramienta `for ...of` ejeucta una determinda acción por cada uno de los elementos que podemos encontrar en un array. Es una forma abreviada de plantear un bluce for apra nuestros arrays:

```js
let iterable = [10, 20, 30];

for (let value of iterable) {
	value += 1;
	console.log(value);
}
// 11
// 21
// 31
```

## Métodos de array: `push`,`pop`,`shift` and `unshift`

- El método `push()` añade uno o más elementos al final de un array y devuelve la nueva longitud del array.
- El método `pop()` elimina el último elemento de un array y lo devuelve. Este método cambia la longitud del array.
- El método `shift()` elimina el primer elemento del array y lo retorna. Este método modifica la longitud del array.
- El método `unshift()` agrega uno o más elementos al inicio del array, y devuelve la nueva longitud del array.
- El método `join()` une todos los elementos de una matriz (o un objeto similar a una matriz) en una cadena y devuelve esta cadena. Añadirá coma (,) por defecto, a menos que definamos otro elemento entre paréntesis (por ejemplo: join("")).
- El método `reverse()` invierte el orden de los elementos de un array. El primer elemento pasa a ser el último y el último pasa a ser el primero.
- El método `split()` divide un objeto de tipo string en un array (vector) de cadenas mediante la separación de la cadena en subcadenas:

```bash
cadena.split([separador][limite])
```

Mención especial a los dos siguiente casos:

- El método `sort()` ordena los elementos de un arreglo (array) localmente y devuelve el arreglo ordenado. Por defecto, ordena alfabéticamente.
- El patrón `CALLBACK` es una función que recibe como argumento otra función y la ejecuta.

```js
let data = [];

data.unshift('Hola');
data.unshift('que');
data.unshift('tal');

console.log(data); // [ 'tal', 'que', 'Hola' ]
```

```js
let data = [];

data.push('Hola');
data.push('que');
data.push('tal');

console.log(data); // [ 'Hola', 'que', 'tal' ]
```

## Extract data

```js
let data = ['Hola', 'que', 'tal', 'estas'];

console.log(data);
let element = data.pop();
console.log(data);
console.log(element);
```

```js
let data = ['Hola', 'que', 'tal', 'estas'];

console.log(data);
let element = data.shift();
console.log(data);
console.log(element);
```

## `join()`, `split()`

```js
let data = ['Hola', 'que', 'tal', 'estas'];
console.log(data);
let str = data.join('🔥🔥');
console.log(str);
```

```js
let str = 'Hola, ¿que tal estás?';
console.log(str);
str.split(' '); // Para contar el número de palabras ya que el método nos devuelve un array.
```

## Sort data inside an array

El método sort ordena un array (de manera `alfabética`) y lo sobreescribe.

```js
let data = [9, 8, 4, 99, 10, 100, 1000];

data.sort(); // Si aplicamos este método sobre un array de números no devuelve de menor a mayor sino alfabéticamente.

function ordenaAsc(a, b) {
	return a - b;
}

// Usamos el PATRÓN CALLBACK para pasar función como parámetro de otra función. En este caso, pasamos una función que es el criterio de ordenación.
data.sort(ordenaAsc);

console.log(data);
```

> Ver vídeo [15 Sorting Algorithms in 6 Minutes](https://www.youtube.com/watch?v=kPRA0W1kECg&ab_channel=TimoBingmann).
