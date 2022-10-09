# Foreach Map Filter Reduce

## Foreach

El `método forEach()` ejecuta la función indicada una vez por cada elemento del array.

```js
let saluda = function (e, i) {
	console.log('Hola', e, i);
};

let nombres = ['Pepe', 'Luis', 'Juan'];
nombres.forEach(saluda);
```

## Map

La función `map` es un método que aplica sobre un array. Recibe como parámetro otra función (callback) y `transforma cada elemento del array en otro elemento`. Una propiedad del map es que devuelve el mismo número de elementos de salida que de entrada: no es posible hacer operaciones en su interior. El método `map` es útil, por ejemplo, para transformar un elemento en otro.

```js
let data = ['💁🏼‍♀️', '😎', '🤦🏻‍♂️', '🙂'];

let result = data.map(function (e, i) {
	console.log(e);
	return '✅';
});

console.log(result); //["✅", "✅", "✅", "✅"];
```

```js
let data = ['💁🏼‍♀️', '😎', '🤦🏻‍♂️', '🙂'];

let result = data.map(function (e, i) {
	console.log(e);
	if (e == '😎') {
		return '❌';
	}
	return '✅';
});

// No modifica el array original
console.log(data); // ['💁🏼‍♀️', '😎', '🤦🏻‍♂️', '🙂']
console.log(result); // ['✅', '❌', '✅', '✅']
```

```js
let data = ['🙂', '😎', '🙂', '🙂'];

let result = data.map(function (e, i) {
	if (e == '😎') {
		return '❌ ' + e;
	}
	return '✅ ' + e;
});

console.log(data); // ['🙂', '😎', '🙂', '🙂']
console.log(result); // ['✅ 🙂', '❌ 😎', '✅ 🙂', '✅ 🙂']
```

Vamos a calcular el `total de estrellas` de estos hoteles:

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Pensión Loli', stars: 2 },
];

let result = data.map(function (e) {
	return e.stars;
});

console.log(data); // [{…}, {…}, {…}, {…}]
console.log(result); // [5, 5, 2, 2]

// Ahora podemos calcular el total de estrellas
let sum = 0;
for (let i = 0; i < result.length; i++) {
	sum = sum + result[i];
	// sum += result[i];
}
console.log(sum);
```

```js
[1, 2, 3, 4].map((e) => e * 2); // [2,4,6,8]
```

## Filter

El método `filter` recibe como parámetro otra función (callback) y filtra: es decir, `su salida será la misma que el objeto de entrada salvo los que no cumplan una condición`. Los outputs serán los mismos que inputs salvo aquellos que no cumplan la condición dada.

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Zouk', stars: 2 },
];

let result = data.filter(function (e) {
	console.log(e.stars > 4);
	return e.stars > 4;
});

console.log('IN: ');
console.log(data);
console.log('OUT: ');
console.log(result);
```

Mismo ejemplo que el anterior pero empleando una `función hasNStars`:

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Zouk', stars: 2 },
];

function hasNStars(e) {
	return e.stars > 4;
}

let result = data.filter(hasNStars);

console.log('IN');
console.log(data);
console.log('OUT');
console.log(result);
```

> ATENCIÓN a la siguiente función.

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Zouk', stars: 2 },
];

// HIGH ORDER FUNCTION: una función que devuelve una función.
function hasMoreThanNStars(threshold) {
	function check(e) {
		return e.stars > threshold;
	}
	return check;
}

let result = data.filter(hasMoreThanNStars(3)); // hasMoreThanNStars es una función que devuelve una función y recibe un parámetro. la variable result alberga una función muy sencilla de leer y pasa a ser pura (independientemente del contexto, siempre funcionará).

console.log('IN');
console.log(data);
console.log('OUT');
console.log(result);
```

## Reduce

El método `reduce` recorre un array y lo reduce a un solo elemento (acumula). Es decir, colapsa un array en un único valor. `Si no definimos un acumulador por defecto JS establece el primer elemento del array como dicho acumulador`.

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Zouk', stars: 2 },
	{ name: 'Pension loli', stars: 1 },
];

let result = data.reduce(function (acc, e) {
	console.log('REDUCE', acc, e);
	return acc + e.stars; // Devuelve el valor acumulado por cada uno de los elementos del array
}, 0);

console.log('========');
console.log(data);
console.log('result', result);
```

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Zouk', stars: 2 },
	{ name: 'Pension loli', stars: 1 },
];

function reduceFN(acc, e) {
	console.log('REDUCE', acc, e);
	return acc + e.stars;
}

let result = data.reduce(reduceFN, 'a');

console.log('========');
console.log(data);
console.log('result', result);
```

## All together

```js
let data = [
	{ name: 'Eurobuilding', stars: 5 },
	{ name: 'Palace', stars: 5 },
	{ name: 'Pension Atocha', stars: 2 },
	{ name: 'Zouk', stars: 2 },
	{ name: 'Pension loli', stars: 1 },
];

// Suma las estrellas de los hoteles con más de 3 estrellas
data
	.map(function (e) {
		return e.stars;
	})
	.filter(function (e) {
		return e > 3;
	})
	.reduce(function (acc, e) {
		return acc + e;
	});
```

```js
let data = [1, 2, 3, 4];

/*
data.map(function(e){
  return e*2;
})
*/

// ARROW FUNCTIONS
//data.filter(e => e%2).map(e => e*2)
//data.filter(e => e==4).map(e => e*2)

let hoteles = [
	{ name: '4Seasons', stars: 5 },
	{ name: 'NH', stars: 4 },
	{ name: 'PensionPerez', stars: 2 },
];

console.log(hoteles.filter((e) => e.stars > 3).map((e) => `Hotel ${e.name}`));

hoteles
	.filter((e) => e.stars > 3)
	.map((e) => `Hotel ${e.name}`)
	.reduce((acc, e) => acc + ', ' + e);
```
