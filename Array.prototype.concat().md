π https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat

# Array.prototype.concat()

The `concat()` method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

<!-- `concat()` λ©μλλ λ κ° λλ κ·Έ μ΄μμ λ°°μ΄λ€μ λ³ν©νλλ° μ¬μ©ν©λλ€. μ΄ λ©μλλ κΈ°μ‘΄ λ°°μ΄μ λ³κ²½νμ§ μμ΅λλ€.
κ·Έλ¬λ λμ μ μλ‘μ΄ λ°°μ΄μ λ°νν©λλ€. -->

## Try it

JavaScript Demo: `Array.concat()`

```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array1);
console.log(array2);
console.log(array3);

// Array ["a", "b", "c"]
// Array ["d", "e", "f"]
// Array ["a", "b", "c", "d", "e", "f"]
```

## Syntax

```javascript
concat()
concat(value0)
concat(value0, value1)
concat(value0, value1, /* β¦ ,*/ valueN)
```

### Parameters

`valueN` _Optional_

Arrays and/or values to concatenate into a new array. If all `valueN` parameters are omitted, concat returns a [shallow copy](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy) of the existing array on which it is called. See the description below for more details.

<!-- μλ‘μ΄ λ°°μ΄μ μ°κ²°ν  λ°°μ΄κ³Ό(λλ) κ°μ΄λ€. λ§μ½, λͺ¨λ  `valueN` λ§€κ°λ³μκ° μλ΅λμλ€λ©΄, concatμ νΈμΆλ κΈ°μ‘΄ λ°°μ΄μ μμ λ³΅μ¬λ³Έμ λ°ννλ€. μμΈν μ¬ν­μ μλ μ€λͺμ μ°Έμ‘°νμμ€. -->


### Return value

A new [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) instance.

## Descriptiond

The `concat` method creates a new array. The array will first be populated by the elements in the object on which it is called. Then, for each argument, its value will be concatenated into the array β for normal objects or primitives, the argument itself will become an element of the final array; for arrays or array-like objects with the property [`Symbol.isConcatSpreadable`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/isConcatSpreadable) set to a truthy value, each element of the argument will be independently added to the final array. The concat method does not recurse into nested array arguments.

<!-- `concat` λ©μλλ μλ‘μ΄ λ°°μ΄μ λ§λ λ€. λ°°μ΄μ λ¨Όμ  νΈμΆλμ΄ κ°μ²΄μ μμμ μν΄ μ±μμ§λ€. κ·Έλ¦¬κ³  λμ, κ° μΈμμ κ°λ€μ λ°°μ΄μ μ°κ²°λ  κ²μ΄λ€. μΌλ° κ°μ²΄ λλ μμ κ°μ²΄μ κ²½μ°, μΈμ κ·Έ μμ²΄κ° μ΅μ’ λ°°μ΄μ μμκ° λ  κ²μ΄λ€. `Symbol.isConcatSpreadable` μμ±μ΄ truthy κ°μΌλ‘ μ€μ λ λ°°μ΄ λλ μ μ¬ λ°°μ΄ κ°μ²΄μ κ²½μ° κ° μΈμμ κ° μμκ° λλ¦½μ μΌλ‘ μ΅μ’ λ°°μ΄μ μΆκ° λ  κ²μ΄λ€. `concat` λ©μλλ μ€μ²©λ λ°°μ΄ μΈμλ‘ λ°λ³΅λμ§ μμ΅λλ€. -->

The `concat()` method is a [copying method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#copying_methods_and_mutating_methods). It does not alter `this` or any of the arrays provided as arguments but instead returns a [shallow copy](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy) that contains the same elements as the ones from the original arrays.

<!-- `concat()` λ©μλλ λ³΅μ¬ λ©μλ μλλ€. κ·Έκ²μ `this`λ₯Ό λ³κ²½νμ§ μκ³  λλ μΈμλ‘ μ κ³΅λ λ°°μ΄ μ€μ νλμ΄μ§λ§, μλμ λ°°μ΄λ‘λΆν° λμΌν νλμ μμλ₯Ό ν¬ν¨νμ¬ μμ λ³΅μ¬λ³Έμ λ°ννλ€. -->

The `concat()` method preserves empty slots if any of the source arrays is [sparse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays).

<!-- `concat()` λ©μλλ λ§μ½ μμ€ λ°°μ΄μ΄ ν¬μν κ²½μ° λΉ μ¬λ‘―μ μ μ§νλ€. -->

The `concat()` method is [generic](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods). The `this` value is treated in the same way as the other arguments (except it will be converted to an object first), which means plain objects will be directly prepended to the resulting array, while array-like objects with truthy `@@isConcatSpreadable` will be spread into the resulting array.

<!-- `concat()` λ©μλλ ν¬κ΄μ μ΄λ€. `this` κ°μ λ€λ₯Έ μΈμμ²λΌ λμΌνκ² μ²λ¦¬λκ³ (λ¨, λ¨Όμ  κ°μ²΄λ‘ λ³νλ  κ²½μ° μ μΈ.), μ¦ μΌλ° κ°μ²΄λ κ²°κ³Ό λ°°μ΄μ μ§μ μ μΌλ‘ μΆκ°(μ μ )λλ λ°λ©΄, `@@isConcatSpreadable` truthy κ°μ κ°μ§ λ°°μ΄κ³Ό μ μ¬ λ°°μ΄ κ°μ²΄λ κ²°κ³Ό λ°°μ΄μ μ νλ  κ²μ΄λ€. -->

## Examples

### Concatenating two arrays

The following code concatenates two arrays:

```javascript
const letters = ["a", "b", "c"];
const numbers = [1, 2, 3];

const alphaNumeric = letters.concat(numbers);
console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```

### Concatenating three arrays

The following code concatenates three arrays:

```javascript
const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [7, 8, 9];

const numbers = num1.concat(num2, num3);

console.log(numbers);
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Concatenating values to an array

The following code concatenates three values to an array:

```javascript
const letters = ["a", "b", "c"];

const alphaNumeric = letters.concat(1, [2, 3]);

console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```

### Concatenating nested arrays

The following code concatenates nested arrays and demonstrates retention of references:

```javascript
const num1 = [[1]];
const num2 = [2, [3]];

const numbers = num1.concat(num2);

console.log(numbers);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);

console.log(numbers);
// results in [[1, 4], 2, [3]]
```

### Concatenating array-like objects with Symbol.isConcatSpreadable

<!-- `Symbol.isConcatSpreadable`μ μ¬μ©νμ¬ μ μ¬ λ°°μ΄ κ°μ²΄ μ°κ²° -->

`concat` does not treat all array-like objects as arrays by default β only if `Symbol.isConcatSpreadable` is set to a truthy value (e.g. `true`).

<!-- `concat`λ `Symbol.isConcatSpreadable`μ΄ truthy value(μ: `true`)μΌλ‘ μ€μ λ κ²½μ°μλ§ κΈ°λ³Έμ μΌλ‘ λͺ¨λ  μ μ¬ λ°°μ΄ κ°μ²΄λ μ²λ¦¬νμ§ μμ΅λλ€. -->

```javascript
const obj1 = { 0: 1, 1: 2, 2: 3, length: 3 };
const obj2 = { 0: 1, 1: 2, 2: 3, length: 3, [Symbol.isConcatSpreadable]: true };
console.log([0].concat(obj1, obj2));
// [ 0, { '0': 1, '1': 2, '2': 3, length: 3 }, 1, 2, 3 ]
```

### Using concat() on sparse arrays

<!-- ν¬μ λ°°μ΄μμ concat() μ¬μ© -->

If any of the source arrays is sparse, the resulting array will also be sparse:

```javascript
console.log([1, , 3].concat([4, 5])); // [1, empty, 3, 4, 5]
console.log([1, 2].concat([3, , 5])); // [1, 2, 3, empty, 5]
```

### Calling concat() on non-array objects

<!-- λ°°μ΄μ΄ μλ κ°μ²΄μμ concat() νΈμΆ μ€ -->

If the `this` value is not an array, it is converted to an object and then treated in the same way as the arguments for `concat()`. In this case the return value is always a plain new array.

<!-- λ§μ½ `this`κ°μ΄ λ°°μ΄μ΄ μλλΌλ©΄, κ·Έκ²μ κ°μ²΄λ‘ λ³νλ λ€μμ `concat()`μ λν μΈμμ κ°μ λ°©μμΌλ‘ μ²λ¦¬λ  κ²μ΄κ³ , μ΄ κ²½μ° λ°ν κ°μ ν­μ μλ‘μ΄ λ°°μ΄μ΄λ€. -->

```javascript
console.log(Array.prototype.concat.call({}, 1, 2, 3)); // [{}, 1, 2, 3]
console.log(Array.prototype.concat.call(1, 2, 3)); // [ [Number: 1], 2, 3 ]
const arrayLike = { [Symbol.isConcatSpreadable]: true, length: 2, 0: 1, 1: 2 };
console.log(Array.prototype.concat.call(arrayLike, 3, 4)); // [1, 2, 3, 4]
```

## See also

- [Polyfill of `Array.prototype.concat` in `core-js` with fixes and implementation of modern behavior like `Symbol.isConcatSpreadable` support](https://github.com/zloirock/core-js#ecmascript-array)
- [`push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) / [`pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) β add/remove elements from the end of the array
- [`unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) / [`shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) β add/remove elements from the beginning of the array
- [`splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) β add/remove elements from the specified location of the array
- [`String.prototype.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat)
- [`Symbol.isConcatSpreadable`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/isConcatSpreadable) β control flattening.
