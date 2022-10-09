# Introducción a JS

## Introducción a la programamción

La programación es un proceso de que diseña, ordena e implementa un `algoritmo` a través de un `lenguaje de programación`.

`Algoritmo`: Secuencia de pasos ordenados que solucionan un problema.

Áreas de programación:

- Desarrollo Web
- Videojuegos
- Inteligencia Artificial
- Desarrollo Móvil
- Big Data
- Robótica
- (...)

`Lenguaje de programamción`: Sistema estructurado de comunicación, conformado por conjunto de palabras claves, símbolos y reglas sintácticas y semánticas que permiten un entendimiento entre el programador y la máquina.

Programar se traduce en crear un software fiable mediante la escritura, prueba, depuración, compilación o interpretación, y mantenimiento del código fuente de dicho programa informático. Podemos destacar los siguientes pasos:

- El `desarrollo lógico del programa` para resolver un problema en particular.
- `Escritura de la lógica del programa` empleando un lenguaje de programación específico (codificación del programa).
- `Compilación o interpretación` del programa hasta convertirlo en lenguaje de máquina.
- `Prueba y depuración` del programa.
- Desarrollo de la `documentación`.

`Sistema Operativo`: El conjunto de programas informáticos que permite la administración eficaz de los recursos de un ordenador. Estos programas comienzan a trabajar nada más arrancar nuestro ordenador, ya que gestiona el hardware desde los niveles más básicos y permite además la interacción con el usuario.

> `RUTINA POST`: Es la serie de comprobaciones que una computadora hace con sus dispositivos al iniciar el sistema. La encargada de hacer el POST es la BIOS. El procedimiento POST comprueba que los dispositivos como unidades de disco, las memorias y otros componentes, funcionen correctamente.

## JS intro

Para esta introducción a JS podemos emplear la KATA [Counting sheep](https://www.codewars.com/kata/54edbc7200b811e956000556).

Una lista o `array` es una secuencia ordenada de datos. Estos datos pueden ser de x tipos. Por ejemplo, datos `BOOLEANS`(true o false).

Una `función` es una sintaxis que usamos para encapsular un programa (entran unos datos y salen otros datos). `function` es una palabra reservada de javascript.

`Variable`: contenedor de información.

Un `array` posee `propiedades` . Una de ellas es la propiedad length. Las listas o arrays cuentan sus elementos por posición (0,1,2...). En JS las listas están `indexadas desde 0`.

Un `blucle` es una instrucción bajo una sintaxis muy concreta que indica al programa que debe reptir x acción en cada interación. El número de interacciones también queda definido en la sintaxis de nuestro bucle.

Un dato importante es que, en JS, `comenzamos a contar desde 0`. Es decir, contamos posiciones no valores.

Sintaxis de `comentarios`:

```js
// Comentario de línea
/* Comentario de bloque */
```

Un bucle `for(condition){action}` posee 3 partes:

- Inicialización: Se ejecuta `sólo al inicio del bucle`.
- Condición: se ejecuta en cada iteración del bucle.
- Acción final: se ejecuta al finalizar el bucle.

- Se pone i en bucle `for` por iteración (es una convenicón).
- Todo lo que hay dentro de `{}` pertenece al bucle for.
- Todo lo que hay dentro de `[]` indica elemento de nuestro array.

```js
for (let i = 0; arrayOfSheep.length; i++) {
	// console.log(i)
}
```

`console.log()`: Instrucción de salida por consola.

`==` es un `operador de condición`.
`=` es un `operador de asignación` (de valor).

En javascript hay 7 tipos de datos primarios:

- string
- number
- boolean
- null
- undefined
- (...)

En javascript `la ejecución del código es secuencial`, línea por línea.

```js
arrayOfSheep = [
	true,
	true,
	true,
	false,
	true,
	true,
	true,
	true,
	true,
	false,
	true,
	false,
	true,
	false,
	false,
	true,
	true,
	true,
	true,
	true,
	false,
	false,
	true,
	true,
];
let counter = 0;
function countSheep(arraySheep) {
	// Un bucle for se compone de 3 parámetros: instancia e inicialización de variable, condición que se comprueba en cada bluque y acción que se ejecuta al acabar el bucle (i++)
	for (let i = 0; i <= arraySheep.lenght; i++) {
		console.log(i);
		console.log(arrayShepp[i]);
		if (console.log(arrayShepp[i]) == true) {
			console.log(i, 'OVEJA');
			counter++;
		} else {
			console.log(i, 'NO OVEJA');
		}
		return counter;
	}
	console.log('A POSTERIORI', i);
}
console.log('Tenemos un total de ', counter, ' ovejas');

function countSheeps(arrayOfSheep) {
	// La función espera recibir un argumento.
	let contador = 0;
	for (let i = 0; i < arrayOfSheep.length; i++) {
		if (arrayOfSheep[i]) {
			contador++;
		}
	}
	return contador;
}

// Llamada a la función pasando como parámtero la variable previamente definida.
countSheeps(arrayOfSheep);
```

## TIP

- `Menos código no siginifica código más rápido`. Existen maneras de compactar la gramática y formas de escritura que facilitan la lectura del código pero nada tiene que ver con los tiempos de ejecución.

Diferencia entre `VAR` y `LET`: let te permite declarar variables limitando su alcance (scope) al bloque, declaración, o expresión donde se está usando. Lo anterior diferencia let de la palabra reservada var, la cual define una variable global o local en una función sin importar el ámbito del bloque.
