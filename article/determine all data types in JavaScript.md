How do determine all data types in JavaScript?
Newly, I saw an interview question:  the For all the basic data types in JavaScript, how could we write a function to detect the type of arbitrary data.
original data types: Boolean、Number、Undefined、Null、String、Symbol、BigInt
reference data types: Array、Object、Function
The most common methods to determine data types is
1、typeof : it's only use to determine the original data type, but the reference and Null the result is 'object'.

```
console.log(typeof 1) // number
console.log(typeof '1') // string
console.log(typeof true) // boolean
console.log(typeof undefined) // undefined
console.log(typeof null) // object
console.log(typeof Symbol()) // symbol
console.log(typeof {}) // object
console.log(typeof []) // object

```

2、instanceof: it's use to determine the reference data types, it's return value is true or false.

```
console.log(1 instanceof Number) // false
console.log('1' instanceof String) // false
console.log({a: 1} instanceof Object) // true
console.log([1,2,3] instanceof Array) // true

```

3、Object.prototype.toString.call(): it's refer to all types of determine test. returning data format on Object Protypes. It's result value is '[object Xxxx]

```
function determineType (data) {
    return Object.prototype.toString.call(data).slice(1, -1).split(' ')[1].toLowerCase()
}
console.log(determineType(1)) // number
console.log(determineType(true)) // boolean
console.log(determineType(Symbol())) // symnol
console.log(determineType('1')) // string
console.log(determineType(null)) // null
console.log(determineType(undefined)) // undefined
console.log(determineType({})) // object
console.log(determineType([])) // array
console.log(determineType(new Date())) // date
console.log(determineType(new RegExp('ab+c'))) // regexp
```

4、Array.isArray： it's use to determine array types:

```
console.log(Array.isArray([])); //true
console.log(Array.isArray(1)); // false
console.log(Array.isArray({})); // false


```


**Overall, use specific judgments based on one's own situation.**

Thank you for your time and hope you get something out.
