# JS types primitives

Como cualquier otro lenguaje de programación, JS posee sus propios tipos de datos. Un tipo de dato en un lenguaje de programación define el `tipo de información` que se almacena en una variable.

JS tiene 7 tipos de datos:

- Primitivos: Number, String, Boolean, Undefined, NULL y Symbol.
- No primitivos: Object

1. `Number`: interger, floating point, exponential, `NaN` o `Infinity`.

```js
var a = 250; // integer value
var b = 25.5; // a number containing a decimal
var c = 10e4; //  an exponential value which evaluates to 10*10000;
var infinity = 5 / 0; // results in infinity
// The type of infinity is a number
typeof infinity; // returns number
// A ‘NaN’ results when we try to perform an operation on a number with a non-numeric value
‘hi’ * 5; // returns NaN
typeof(NaN);  // returns a number
```

2. `String`: conjunto de characters encapsulados en comillas simples o dobles.

```js
// This is a string primitive type or string literal
var str3 = `This is a string3`;
// The String() function is also used to convert a non-string value to a string.
String(4); // This statement will create a string ‘4’
```

3. `Boolean`: los booleanos sólo tienen 2 valores: true o false. A menudo empleados para comprobar condiciones lógicas.

```js
typeof true; // returns boolean
typeof false; // returns boolean

var a = 5;
var b = 6;
console.log(a === b); // false

if(a<b){
alert("a is a smaller number than b");
}

var mystring = ‘hi there’;
console.log(Boolean(mystring)); // This will result in true because the ‘mystring’ value exists.

```

4. `Undefined`: El tipo undefined indica una variable que no está definida. La variable está creada pero no contiene valor.

```js
var und_1;
console.log(und_1); // This will return undefined.

var und_2 = undefined; // possible but not recommended
console.log(und_2); // returns undefined
```

5. `Null`: Significa sin valor.

```js
var the_null = null;
console.log(the_null); // This returns null
console.log(typeof the_null); // This returns object
```

6. `Symbol`: The ‘symbol’ data type is new in es6. It is one of the new features of es6. The symbol data type defines a property of an object which is private to the object. It refers to the ‘key’ of the key-value pair of an object.

```js
var object1 = {
   name: ‘Shalini’,
   age: 25,
   city: ‘Mumbai’
}
var occupation=Symbol(‘engineer’);
```

The function Symbol() is used to create a new symbol. Here we have created a symbol ‘occupation’ with the value ‘engineer’ for the above object ‘object1’. Every symbol is unique. Two Symbols even with the same key values are not same. `occupation===occupation // returns false.` Thus both the above ‘occupation’ symbols are different. Each one is a unique property of the object. We cannot create a symbol object using the ‘new’ operator because the Symbol() cannot be used as a constructor.

7. `Object`: Los objetos son un tipo no-primitivo de dato en JS. `Arrays` y `Functions` pertenecen a este tipo.

```js
var obj1 = { a: 5, b: 6 };
typeof obj1; // will return the data type ‘object’.
```

- `Array`: Lista de datos donde cada elemento posee un index ordenado y único empezando desde cero.

```js
var arr1 = [1, 2, 3];
console.log(typeof arr1); // will return the data type ‘object’.
```

- `Functions`: JS se referirá a las mismas como un tipo de objeto especial.

```js
function fun() {}
console.log(typeof fun);
```

> ADVANCE
> En este caso, la variable `a es un único valor interger`. De manera concreta la variable a hace referencia a un `espacio reservado en memoria`. Si quieremos cambiar el valor de a tendremos que asignar a dicha variable un nuevo valor ya que `los datos de tipo primitivo en JS no son mutables`.
>
> Cuando creamos una variable estamos reservando un nuevo espacio de memoria. Cuando tratamos de alterar el valor de la variable indicando `var a = 6` no alteramos el valor original sino que estamos `creando una nueva variable` con el nuevo valor.
>
> Podemos asignar el valor de la variable a otra empleando `var a1 = a`. De esta manera `a1` se asigna al valor de `a`, no a su dirección en memoria. Si empleamos `a === a1` para verificar que el valor es el mismo y se devuelve `true`. En otras palabras, `cuando comparamos nuestras variables estamos comparando su valor, no su espacio de memoria.`
>
> Los `tipos no-primitivos de JS son objetos` que se componen de una referencia de una o varias key-values. Cuando nos referimos a un objeto nos estamos refieriendo a la dirección en memoria que contiene el par key-value. Cuando asignamos `object1` a `object2` estamos asignando la dirección del primer objeto al segundo en lugar del par key-value que posee en memoria el objeto 1.
>
> ```js
> var object1 = { a: 5, a1: 6 };
>
> var object2 = object1;
> ```
>
> En el código anterior estamos asignando la dirección del objeto 1 al objeto 2, no su valor. object1 y object2 se referirán al mismo espacio en memoria. `object1 === object2` devolverá true.
>
> ```js
> var object1 = { a: 5, a1: 6 };
>
> var object2 = { a: 5, a1: 6 };
> ```
>
> Si comparamos `object1 === object2` devolverá false porque son dos espacios de memoria distintos.
>
> Por lo tanto, los tipos primitivos de datos se refieren a un `single value` en una dirección de memoria mientras que los tipos de data no-primitivos se refieren ala dirección de memoria que contienen una única (o varios) pares key-value.

---

Si introducimos una cadena de texto en if, devuelve true siempre que su longitud sea > 0.

```js

// Ejemplo de comparación de variables
var a = 1;
var b = 1;
if (a === b) {
	console.log('correct');
} else {
	console.log('wrong');
}

// Strings
let data = ""; // false
let data = " "; // true

if (data) {
	console.log('correct');
} else {
	console.log('wrong');
}

//Length
let data = 10;
data.length //undefined

// Numbers
let data = 10; // Positive -> true
let data = -10; // Negative -> true
let data = 0; // Zero -> false

// Arrays
let data = ["a", "b", "c"]; // true
let data = []; // true

// Operations

if (a || 0 ) // true
if (a && 0 ) // false
"Code" == true; // false
"Code" == "code"; // false
[] == "code"; // false

// Undefined
undefined == true; // false
undefined == undefined; // true
undefined === undefined; // true

Double equal `==` vs triple equal `===` //con triple igual evitamos que JS convierta el tipo para hacer coincidir el if (a === b)

// Type comparision
3 == "3"; // true
3 === "3"; // false
```

## Opearator `+`: Suma vs concatena

```js
let a = 330; // Number
let b = '330'; // String

console.log(a + 1); // Se suma (el valor de a no varía porque no reasignamos su valor)
console.log(b + 1); // Se concatena (el valor de a no varía porque no reasignamos su valor)
```

## Conocer el tipo de una variable

```js
console.log(typeof 330); // number
console.log(typeof '330'); // string
console.log(typeof []); // object
```
