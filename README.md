# LOWBAR BREAK DOWN 

Below you will find a break down on how to implement all the lodash functions (without mock functions)

## _.identity

This function will return a given value.

**Arguments:**
- Value 

**Example:**
*Input*
```js
const value = "hello"
function _.identity(value)//invokes _.identity with value
```
*Output*
```js
//function _.identity => "hello"

```
**Possible tests:**
- Check value passed is the value returned 
- Check the value passed has not been changed 

***

## _.fromPairs

This function will take an array filled with other arrays consisting of two elements.
This function will return each of those two elements as key value pairs in an object


**Arguments:**
- Multi Dimensional Array

**Example:**
*Input*
```js
function _.fromPairs([['Cat', 'Tabby',],['Dog', 'Greyhound'], ['Bird', 'Pigeon']])
```
*Output*
```js
//function _.fromPairs => {Cat: "Tabby, Dog: "Greyhound, Bird: "Pigeon}
```

**Possible tests:**
- returns an empty Object when passed an empty array 
- return same number of key/val pairs as nested arrays args provided 
- returns obj with a single key/value pair
- returns obj with multiple key/val pairs when given multiple nested arrays
- does not mutate original array input

***

## _.times
This function will take a number and a iteretee function (it does not matter what this function returns), but this function will need to be invoked the same amount of times as the number given.  It Returns an array containing the output of the iteratee function.

**Arguments:**
- Number (times to iterate)
- Iteratee function

**Example:**
*Input*
```js
function iterateeFunc(){  //this iteratee function will return a cat every time it is invoked
    return '🐈';
}

function _.times(3, iterateeFunc) //_.times is invoked with the number and iteratee function
```

*Output*
```js
//function _.times => ['🐈', '🐈', '🐈'] 
```
**Possible tests:**
- When passed 0 does not invoke function
- invokes the iteratee n times
- returns an array with the results of the invocation
***

## _.map
This function will take a collection(Array or Object) and an iteratee function (it does not matter what this function does, but it will need to do something to **each** piece of data in the given collection - such as multiplying numbers, or only returning the values in an object) It will then return the functions output in a new Array.


**Arguments:**
- Collection (Array or Object)
- Iteratee function

**Example:**
*Input*
```js
const numberArr = [5, 10] //Array of numbers

function iterateeFunc(numbers){ //this iteratee function with multiply each number in the given numberArr array by itself and then push the result to a new array. 

const newArr = [];
for(let i = 0; i < numbers.length; i++){
newArr.push(numbers[i] * numbers[i]);
}
   return newArr;
}

function _.map(numberArr, iterateeFunc)//_.map is invoked with the numberArr and iteratee function
```

*Output*
```js
//function _.map => [25, 100]
```
**Possible tests:**
- If passed empty array or object - returns empty array
- Return array length is the same as either - array arg length or number of key/value pairs on obj arg
- Array: iteratte is called with Array
- Object: iteratte is called with Object 
- Should not mutate given collection
- Check iteratee is called with given argument (toHaveBeenCalledTimes, toHaveBeenCalledWith) 

***
## _.filter
This function will take a collection(Array or Object) and an iteratee function (it does not matter what this function does, but it will need to do something to **specified** pieces of data in the given collection - such as multiplying only odd numbers, or only returning specific values in an object) It will then return the functions output in a new Array.

**Arguments:**
- Collection (Array or Object)
- Iteratee function

**Example:**
*Input*
```js
const numberArr = [5, 10, 7, 12, 15] //array of numbers

function iterateeFunc(numbers){ //this iteratee function with multiply only even numbers in the numberArr array by itself and then push the result to a new array. 

const newArr = [];
for(let i = 0; i < numbers.length; i++){
    if(numbers[i] % 2 === 0){
newArr.push(numbers[i] * numbers[i]);
}
}
   return newArr;
}

function _.filter(numberArr, iterateeFunc)//_.filter is invoked with the numberArr and iteratee function
```

*Output*
```js
//function _.filter => [100, 144]
```
**Possible tests:**
- if passed empty array or object - returns empty array/object
- Check length of returned array is as desired
- Check return value is desired
- predicate function should be called on given array or object(toHaveBeenCalledTimes, toHaveBeenCalledWith)
- should correctly filter longer arrays or objects
- should not mutate given collection

***
## _.forEach
This function will take a collection(Array or Object) and an iteratee function (it does not matter what this function does, but it will need to do something to **each** piece of data in the given collection - such as +1 to each number or Capitalising each string) It will then return an amended version of the collection ** NO NEW ARRAY **

**Arguments:**
- Collection (Array or Object)
- Iteratee function 

**Example:**
*Input*
```js
const greetingArr = ['hi', 'hola', 'hello'] //array of strings

function iterateeFunc(arr){  //this iteratee function will turn each string in the greetingArr array to uppercase, it will then return the mutated array

for(let i = 0; i < arr.length; i ++){
 arr[i] = arr[i].toUpperCase()
}
return arr
}

function _.forEach(greetingArr, iterateeFunc)//_.forEach is invoked with the greetingArr and iteratee function
```

*Output*
```js
//function _.forEach => ["HI", "HOLA", "HELLO"]
```

**Possible tests:**
- If given empty array or object, should return empty array or object
- Should return the given collection type (Object returns Object, Array returns Array)
- Iteratee function should be called on given array or object(toHaveBeenCalledTimes, toHaveBeenCalledWith)
- Check return value is desired
- Check return value length is the same

***


## _.invert
This function will take an object, and return a **new** object where the values and keys have been swapped round. 

**Arguments:**
- Object

**Example:**
*Input*
```js
const obj = {1:'a', 2:'b', 3:'c'} //object 

function _.invert(obj)//_.invert is invoked with an object
```
*Output*
```js
//function _.invert => {'a': '1', 'b': '2', 'c': '3'}
```

**Possible tests:**
- Should return empty obj when given empty obj
- Should successfully invert obj with a single key/value pair
- Should successfully invert obj with multiple key/value pairs
- If object contains duplicate values, subsequent values overwrite property assignments of previous values
- should not mutate original object


***
## _.zip
This function will take multiple arrays and group them together by their indexes in a **new** Array.
It will then return this new Array. 

**Arguments:**
- Arrays

**Example:**
*Input*
```js
const arr1 = [1,2,3] //arrays 
const arr2 = [true, false, true]
const arr3 = ['cat', 'dog', 'mouse']

function _.zip(arr1, arr2, arr3)//_.zip is invoked with multiple Arrays
```

*Output*
```js
//function _.zip => [1, true, 'cat', 2, false, 'dog', 3, true, 'mouse']
```

**Possible tests:**
- Should return empty array when given empty array
- Should correctly group elements by their index (those are index 0, will be at the begining of the new array, followed by those at index 1 etc)
- Should correctly group when given two arrays
- Should correctly group when given multiple arrays
- Should not mutate original array

***
## _.fill
This function will take an array, a replacement value, a starting index and an ending index. It will then return the given array (mutated) where elements from the starting index to the ending index will be replaced with the given replacement value. 

**Arguments:**
- Array
- Replacement value
- Start index (number)
- End index (number)

**Example:**
*Input*
```js
const arr = [1,2,3,4,5,6,7]
const replacement = "A"
const startIndex = 0
const endIndex = 3

function _.fill(arr, replacement, startIndex, endIndex)//_.fill is invoked with 4 arguments
```
*Output*
```js
//function _.fill => ["A", "A", "A",4,5,6,7]
```
**Possible tests:**
- return an empty array when called with empty array and value
- fills an array with the given value
- fill takes a start index argument that gives the index at which to start the fill - defaults to zero
- fill takes a start index argument that gives the index at which to start the fill
- fill takes an end index argument that gives the index at which to end the fill - defaults to array length
- fill takes an end index argument that gives the index at which to end the fill
- SHOULD mutate the given array

***
## _.find

This function will take a collection (array or object), a predicate function (that returns only the **first instance** of data where the condition stated is true) and can also **optionally** take an index to start searching from. If the function finds relevevant data, it will return that data.

**Arguments:**
- Array or Object
- Predicate function
- Start index (**OPTIONAL**)

**Example:**
*Input*
```js
const arr = [1,2,3,4,5,6,7]

function predicateFunc(arg){ //this predicate function will take arr and return the first number in the array that is greater than 2
    for(let i = 0; i < arg.length; i++){
        if (arg[i] > 2){
            return arg[i]
        }
    }
}

function _.find(arr, predicateFunc)//_.find is invoked with an array and predicate function (can also take a starting index if desired)
```

*Output*
```js
//function _.find => 3
```

**Possible tests:**
- return undefined if given empty array or if no matching elements found
- predicate should be invoked with given array/object
- should only return one element/property (if predicate equates to true)
- should not mutate the given array/object
- return undefined if given empty object or if no matching elements found

***

## _.chunk
This function will take an array and a 'chunk' size, it will then return a **new** multi-dimensional array which contains arrays of the given chunk size.


**Arguments:**
- Array
- Chunk size (number)

**Example:**
*Input*
```js
const arr = [1,2,3,4,5,6,7] //given array
const chunkSize = 3 // how many elements should be in each array

function _.chunk(arr, chunkSize)//_.chunk is invoked with an array and chunk size
```

*Output*
```js
//function _.chunk => [[1,2,3],[4,5,6],[7]] // any remainders will be an array of their own
```
**Possible tests:**
- should return empty array when given empty array - no matter what number is given 
- inner array size should default to 1 when given no second arg
- should return array in chunks of length 1 when given number 1
- should return array in chunks of 2 which given number 2
- should return array in chunks > 2 depending on arg given
- should return correctly chunked arrays when elements cannot be split evenly
- inputted array should not be mutated
***
## _.remove

This function will take an array and a predicate function(that will give a condition that equates to true) Anything in the array that equates to *true* will be remove from the array. A mutated array will then be returned. 

**Arguments:**
- Array
- Predicate function

**Example:**
*Input*
```js
const arr = [1,2,7,2,3,4]

function predicateFunc(arg){ //this predicate function will take arr and return an array of all the numbers not less than 3



    for(let i = 0; i < arg.length; i++){
        if (arg[i] > 3){
            arg.splice(i, 1);
        }
    }
    return arg;
}

function _.remove(arr, predicateFunc)//_.remove is invoked with an array and predicate function
```

*Output*
```js
//function _.remove => [ 1, 2, 2, 3 ]
```
**Possible tests:**
- return empty array if given array is empty
- return unchanged array if predicate is always falsy
- should remove a single element from array if predicate returns truthy for it
- should remove multiple elements from an array if predicate returns truthy for them
- SHOULD mutate given array
***
## _.shuffle

This function will take an Array and return a **new** array of the data given, but the order now shuffled.

**Arguments:**
- Array

**Example:**
*Input*
```js
const arr = [1,2,3,4,5,6,7]

function _.shuffle(arr)//_.shuffle is invoked with an array it needs to shuffle
```
*Output*
```js
//function _.shuffle => [2,1,4,3,6,5,7]
```
**Possible tests:**
- should return given array when length <= 1
- should contain all the same elements after shuffling
- function should assign elements to random indices with Math.random
- should not mutate given array
***
## _.reduce
This function will take a collection (Array or object) and will use a iteratee function to return a reduced version of the given data. If given an object, Duplicate keys will be combined to one key and will contain an array of the values from said key. If an array of numbers are given, the numbers will be summed together, returning the sum. 

**Arguments:**
- Array or Object
- Inital value 
- Iteratee function

**Example:**
*Input*
```js
const numbers = [ 1, 2, 3, 4 ];// given array
const initalValue = numbers[0] // first value in array 

function iterateeFunc(array, inital){ // this iteratee function will add each element in the array to the inital value (first element in the array) and then return the sum

 for(let i = inital; i < array.length; i++){
            inital += array[i]
        }
        return inital

}

function _.reduce(numbers, initalValue, iterateeFunc)//_.reduce is invoked with 3 arguments
```

*Output*
```js
//function _.reduce => 10
```
**Possible tests:**
- iteratee function should be called with a given array or object + inital value
- accumulator should default to first item in collection
- accumulator should be updated with the result of the iteratee func
- should not mutate given collection

***
## _.intersection

This function will take two or more Arrays and will return a new array consisting of the intersection (the common elements in each array - same data and same index)

**Arguments:**
- Arrays

**Example:**
*Input*
```js
const arr1 = [1, 7, 9, 2, 3, 0]
const arr2 = [2, 7, 9, 2, 3, 8, 9]
const arr3 = [8, 2, 9, 2, 0]
function _.intersection(arr1, arr2, arr3)//_.intersection is invoked with all the arrays
```


*Output*
```js
//function _.intersection => [9,2]
```
**Possible tests:**
- if called with single array should return that array
- should return empty array if given empty arrays
- should return intersecting values of when called with two arrays
- should return intersecting values when called with >2 arrays
- original arrays should not be mutated

