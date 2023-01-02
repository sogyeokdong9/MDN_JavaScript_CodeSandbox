🔗 https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat

# Array.prototype.concat()

The `concat()` method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

<!-- `concat()` 메서드는 두 개 또는 그 이상의 배열들을 병합하는데 사용합니다. 이 메소드는 기존 배열을 변경하지 않습니다.
그러나 대신에 새로운 배열을 반환합니다. -->

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
concat(value0, value1, /* … ,*/ valueN)
```

### Parameters

`valueN` _Optional_

Arrays and/or values to concatenate into a new array. If all `valueN` parameters are omitted, concat returns a [shallow copy](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy) of the existing array on which it is called. See the description below for more details.

<!-- 새로운 배열에 연결할 배열과(또는) 값이다. 만약, 모든 `valueN` 매개변수가 생략되었다면, concat은 호출된 기존 배열의 얕은 복사본을 반환한다. 자세한 사항은 아래 설명을 참조하시오. -->


### Return value

A new [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) instance.

## Descriptiond

The `concat` method creates a new array. The array will first be populated by the elements in the object on which it is called. Then, for each argument, its value will be concatenated into the array — for normal objects or primitives, the argument itself will become an element of the final array; for arrays or array-like objects with the property [`Symbol.isConcatSpreadable`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/isConcatSpreadable) set to a truthy value, each element of the argument will be independently added to the final array. The concat method does not recurse into nested array arguments.

<!-- `concat` 메소드는 새로운 배열을 만든다. 배열은 먼저 호출되어 객체의 요소에 의해 채워진다. 그리고 나서, 각 인수의 값들은 배열에 연결될 것이다. 일반 객체 또는 원시 객체의 경우, 인수 그 자체가 최종 배열의 요소가 될 것이다. `Symbol.isConcatSpreadable` 속성이 truthy 값으로 설정된 배열 또는 유사 배열 객체의 경우 각 인수의 각 요소가 독립적으로 최종 배열에 추가 될 것이다. `concat` 메소드는 중첩된 배열 인수로 반복되지 않습니다. -->

The `concat()` method is a [copying method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#copying_methods_and_mutating_methods). It does not alter `this` or any of the arrays provided as arguments but instead returns a [shallow copy](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy) that contains the same elements as the ones from the original arrays.

<!-- `concat()` 메소드는 복사 메소드 입니다. 그것은 `this`를 변경하지 않고 또는 인수로 제공된 배열 중의 하나이지만, 원래의 배열로부터 동일한 하나의 요소를 포함하여 얕은 복사본을 반환한다. -->

The `concat()` method preserves empty slots if any of the source arrays is [sparse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays).

<!-- `concat()` 메소드는 만약 소스 배열이 희소한 경우 빈 슬롯을 유지한다. -->

The `concat()` method is [generic](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods). The `this` value is treated in the same way as the other arguments (except it will be converted to an object first), which means plain objects will be directly prepended to the resulting array, while array-like objects with truthy `@@isConcatSpreadable` will be spread into the resulting array.

<!-- `concat()` 메소드는 포괄적이다. `this` 값은 다른 인수처럼 동일하게 처리되고(단, 먼저 객체로 변환될 경우 제외.), 즉 일반 객체는 결과 배열에 직접적으로 추가(전제)되는 반면, `@@isConcatSpreadable` truthy 값을 가진 배열과 유사 배열 객체는 결과 배열에 전파될 것이다. -->

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

<!-- `Symbol.isConcatSpreadable`을 사용하여 유사 배열 객체 연결 -->

`concat` does not treat all array-like objects as arrays by default — only if `Symbol.isConcatSpreadable` is set to a truthy value (e.g. `true`).

<!-- `concat`는 `Symbol.isConcatSpreadable`이 truthy value(예: `true`)으로 설정된 경우에만 기본적으로 모든 유사 배열 객체는 처리하지 않습니다. -->

```javascript
const obj1 = { 0: 1, 1: 2, 2: 3, length: 3 };
const obj2 = { 0: 1, 1: 2, 2: 3, length: 3, [Symbol.isConcatSpreadable]: true };
console.log([0].concat(obj1, obj2));
// [ 0, { '0': 1, '1': 2, '2': 3, length: 3 }, 1, 2, 3 ]
```

### Using concat() on sparse arrays

<!-- 희소 배열에서 concat() 사용 -->

If any of the source arrays is sparse, the resulting array will also be sparse:

```javascript
console.log([1, , 3].concat([4, 5])); // [1, empty, 3, 4, 5]
console.log([1, 2].concat([3, , 5])); // [1, 2, 3, empty, 5]
```

### Calling concat() on non-array objects

<!-- 배열이 아닌 개체에서 concat() 호출 중 -->

If the `this` value is not an array, it is converted to an object and then treated in the same way as the arguments for `concat()`. In this case the return value is always a plain new array.

<!-- 만약 `this`값이 배열이 아니라면, 그것은 객체로 변현된 다음에 `concat()`에 대한 인수와 같은 방식으로 처리될 것이고, 이 경우 반환 값을 항상 새로운 배열이다. -->

```javascript
console.log(Array.prototype.concat.call({}, 1, 2, 3)); // [{}, 1, 2, 3]
console.log(Array.prototype.concat.call(1, 2, 3)); // [ [Number: 1], 2, 3 ]
const arrayLike = { [Symbol.isConcatSpreadable]: true, length: 2, 0: 1, 1: 2 };
console.log(Array.prototype.concat.call(arrayLike, 3, 4)); // [1, 2, 3, 4]
```

## See also

- [Polyfill of `Array.prototype.concat` in `core-js` with fixes and implementation of modern behavior like `Symbol.isConcatSpreadable` support](https://github.com/zloirock/core-js#ecmascript-array)
- [`push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) / [`pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) — add/remove elements from the end of the array
- [`unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) / [`shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) — add/remove elements from the beginning of the array
- [`splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) — add/remove elements from the specified location of the array
- [`String.prototype.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat)
- [`Symbol.isConcatSpreadable`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/isConcatSpreadable) — control flattening.
