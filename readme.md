# Python and Javascript Syntax Comparison


## Table of Contents

- [Hello World](#hello-world)
- [Comments](#comments)
- [Data types](#data-types)
- [Variable declaration int](#variable-declaration-int)
- [Variable declaration float](#variable-declaration-float)
- [Variable declaration None](#variable-declaration-none)
- [Strings](#strings)
- [Boolean](#boolean)
- [Arithmetic Operators](#arithmetic-operators)
- [Comparison Operators](#comparison-operators)
- [Logical Operators](#logical-operators)
- [Getting Input](#getting-input)
- [Bitwise Operators](#bitwise-operators)
- [Increment](#increment)
- [Arrays and Lists](#arrays-and-lists)
- [Conditional Statement](#conditional-statement)
- [Loops](#loops)
- [Instantiation](#instantiation)
- [Functions](#functions)
- [Higher order functions](#higher-order-functions)
- [Hash Tables / Dictionaries / Objects](#hash-tables)
- [Destructuring](#destructuring)
- [Spread Operator](#spread-operator)
- [Rest parameters/*args/*kwargs](#rest-parameters)
- [Class](#class)
- [Importing Libraries](#importing-libraries)
- [Type Conversions](#type-conversions)
- [Find Data Type](#find-data-type)
- [String Concatenation](#string-concatenation)
- [JSON](#json)
- [Program Entry Point](#program-entry-point)
- [Swapping values](#swapping-values)
- [Error Handling](#error-handling)
- [Custom Error](#custom-error)
- [Asynchronous](#asynchronous)
- [Math](#math)
- [Date and Time](#date-and-time)
- [Access modifier](#access-modifier)
- [File System](#file-system)
- [Iterators](#iterators)
- [Generators](#generators)
- [Fetching Web Data](#fetching-web-data)
- [Enum](#enum)
- [Language Specific](#language-specific)


## Hello World

### python 3

```python
print("Hello World")  # "Hello World\n"
print("Hello", "World", sep="/")  # "Hello/World"
print("Hello World", end="")  # "Hello World"
```

### javascript

```javascript
console.log("Hello World"); // "Hello World"
console.log("Hello", "World"); // "Hello World"
```

[back to top](#table-of-contents) ⬆️


## Comments

### python 3

```python
# Single line comment

"""
multi-line comments
"""
```

### javascript

```javascript
// Single line comment

/*
multi-line comments
*/
```

[back to top](#table-of-contents) ⬆️


## Data types

### python 3

#### 8 main data types

- Text type
  - `str`, `x = "Hello World"	`, `x = str("Hello World")`
- Numeric types
  - `int`, `x = 20	`, `x = int(20)`
  - `float`, `x = 20.5`, `x = float(20.5)`
  - `complex`, `x = 1j`, `x = complex(1j)`
- Sequence types
  - `list`, `x = ["apple", "banana", "cherry"]`, `x = list(("apple", "banana", "cherry"))`
  - `tuple`, `x = ("apple", "banana", "cherry")`, `x = tuple(("apple", "banana", "cherry"))`
  - `range`, `x = range(6)`, `x = range(6)`
- Mapping type
  - `dict`, `x = {"name" : "John", "age" : 36}`, `x = dict(name="John", age=36)`
- Set types
  - `set`, `x = {"apple", "banana", "cherry"}`, `x = set(("apple", "banana", "cherry"))`
  - `frozenset`, `x = frozenset({"apple", "banana", "cherry"})`,  `x = frozense(("apple", "banana", "cherry"))`
- Boolean type
  - `bool`, `x = True`, `x = False`, `x = bool(5)`
- Binary types
  - `bytes`, `x = b"Hello"`, `x = bytes(5)`
  - `bytearray`, `x = bytearray(5)`, `x = bytearray(5)`
  - `memoryview`, `x = memoryview(bytes(5))`, `x = memoryview(bytes(5))`
- None type
  - `None`, `x = None`


### javascript

#### 1 primitive structural root

- null
  - unknown values – a standalone type that has a single value null

#### 2 Structual types

- object
  - for more complex data structures
  - new Object, new Array, new Map, new Set, new WeakMap, new Date, new ...

#### 6 basic primitive data types

- number
  - **for numbers of any kind**: integer or floating-point, integers are limited by ±(2^53-1) === ±9007199254740991
  - contain
    - regular numbers
      ```javascript
      let n = 123;
      ```
    - floats
      ```javascript
      let n = 1.23;
      ```
    - special numeric values
      - Infinity
        ```javascript
        let n = 1 / 0;
        let n2 = Infinity;
        ```
      - -Infinity
      - NaN
        ```javascript
        let n = "not a number" / 2; // NaN
        ```
- bigiInt
  - no maximum limit to a BigInt
  ```javascript
  let bigInt = 1234567890123456789012345678901234567890n; // ends with n
  ```
- string
  - may have zero or more characters, there’s no separate single-character type
- boolean
  - true / false (lowercase)
- undefined
  - **unassigned values** – a standalone type that has a single value undefined

- symbol
  - for unique identifiers

  ```javascript
  // id is a new symbol
  let id = Symbol();

  // can give symbol a description (also called a symbol name), mostly useful for debugging purposes
  let _id = Symbol("id2");

  // symbol in an object literal
  let obj = {
    [_id]: 123, // not "id": 123
  };

  // guaranteed to be unique
  let id1 = Symbol("id");
  let id2 = Symbol("id");
  console.log(id1 == id2); // false

  // convert symbol to string
  id1.toString(); // "Symbol(id)"

  // get symbol description
  id1.description; // "id"
  ```

  - Symbols allow us to create “hidden” properties of an object, that no other part of code can accidentally access or overwrite

  ```javascript
  let user = {
    // belongs to another code
    name: "John",
  };

  let id = Symbol("id");
  user[id] = 1;
  console.log(user[id]); // 1
  console.log(user); // { name: 'John', [Symbol(id)]: 1 }
  ```

  - **benefit of using symbol over string**
    - objects belongs to another code, and that code also works with them, we shouldn’t just add any fields to it
    - symbol cannot be accessed accidentally, the third-party code probably won’t even see it
  - Symbols are skipped by for...in loop

  ```javascript
  let id = Symbol("id");
  let user = {
    name: "John",
    age: 30,
    [id]: 123,
  };

  for (let key in user) console.log(key); // name age undefined
  ```

  - Symbol can be cloned with Object.assign

  ```javascript
  let id = Symbol("id");
  let user = {
    [id]: 123,
  };

  let clone = Object.assign({}, user);
  console.log(clone); // { [Symbol(id)]: 123 }
  ```

  - global symbols
    - use if want same-named symbols to be same entities

  ```javascript
  // get symbol by name
  let id1 = Symbol.for("id");
  let id2 = Symbol.for("id");

  console.log(id1 === id2); // true

  // get name by symbol, can only use for global symbol
  console.log(Symbol.keyFor(id1)); // "id"
  ```

[back to top](#table-of-contents) ⬆️

## Variable declaration int

- integer ...-2, -1, 0, 1, 2...

### python 3

```python
integer_name = 123
```

### javascript ES5

```javascript
// method 1
var integer_name;
integer_name = 123; // accessible within the function

// method 2
var integer_name = 123;
```

### javascript ES6

```javascript
// method 1
let integer_name;
integer_name = 123; // accessible only within the block {}

// method 2
let integer_name = 123;

// method 3
const integer_name = 123; // variable value cannot be reassigned
```

[back to top](#table-of-contents) ⬆️

## Variable declaration float

- float, double

### python 3

```python
float_name = 1.123
float_name = 0.1123e1  # equals to 1.123
float_name = 0.1123E1  # equals to 1.123
float_name = 1123e-3  # equals to 1.123
float_name = 1123E-3  # equals to 1.123
```

### javascript ES5

```javascript
var float_name = 1.123;
```

### javascript ES6

```javascript
let float_name = 1.123;
const float_name = 1.123;
```

[back to top](#table-of-contents) ⬆️

## Variable declaration None

### python 3

```python
variable_name = None

# nan in python
import math
math.inf - math.inf  # nan
```

### javascript

```javascript
// undefined is reserved for variables whose values have not yet been set.
let variable_name; // undefined

//null is reserved for variables whose values are explicitly nothing — instead of just “not yet defined.”
let variable_name2 = null;

// NaN is a special numeric value meaning “Not a Number”
let variable_name3 = NaN;
```

[back to top](#table-of-contents) ⬆️

## Strings

### python 3

```python
string_name = "string"
string_name = 'string'
# back slash not required, but will produce a new line if not given
string_name = """multi-line \
string\
"""

# raw strings (ignore escape characters)
string_name = r"\n raw string"  # "\n raw string"

len(string_name)  # 6

# Character unicode point
# only accepts 1 character
ord("b")  # 98

# reverse string
string_name = string_name[::-1]  # "gnirts"

string_name = "Gnirts"
string_name = string_name.swapcase()  # "gNIRTS"
string_name = string_name.upper()  # "GNIRTS"
string_name = string_name.lower()  # "gnirts"

# capitalize string
string_name_caps = "test me"
string_name_caps.title()  # "Test Me"
string_name_caps.capitalize()  # "Test me"

# Replace string in string, string_name.replace(old, new, max)
string_name = string_name.replace("g", "xxx")  # "xxxnirts"
string_name = string_name.replace("x", "g", 1)  # "gxxnirts"

# Find character or string in string and return the index of the 1st character, return -1 if not found
string_name.find("x")  # 1
string_name.find("v")  # -1

# string slicing
# extract characters from a string, from start position to but not including end position
new_string_name = string_name[1:4]  # "xxn"

# Split strings, string_name.split(separator, max)
string_name = string_name.split()  # ["gxxnirts"]  only works for string without spaces
string_name = "test string"
string_name1 = string_name.split()  # ["test", "string"]
string_name2 = string_name.split("s")  # ["te", "t ", "tring"]
string_name3 = string_name.split("s", 1)  # ["te", "t string"]

# Split string into an array of letters
string_name4 = list(string_name)  # ['t', 'e', 's', 't', ' ', 's', 't', 'r', 'i', 'n', 'g']

# Remove empty spaces
string_name = "    string    "
# remove all left spaces
string_name1 = string_name.lstrip()  # "string    "
# remove all right spaces
string_name2 = string_name.rstrip()  # "    string"
# remove all spaces
string_name3 = string_name.strip()  # "string"

# Check if string has alphabet and integer characters
string_name3.isalnum()  # False
string_name = "123"
string_name.isalnum()  # True
string_name = "s 123"
string_name.isalnum()  # False
string_name = "s123"
string_name.isalnum()  # True

# Check if string has all alphabet characters
string_name3.isalpha()  # True
string_name = "A e"
string_name.isalpha()  # False
string_name = "a2"
string_name.isalpha()  # False

# Check if string has all digit characters
string_name = "123"
string_name.isdigit()  # True
string_name = "12 3"
string_name.isdigit()  # False
string_name = "12d"
string_name.isdigit()  # False

# Join an array of string elements
arr = ["a", "b"]
"_".join(arr)  # "a_b"
```

### javascript ES5

```javascript
var stringName = "string";
var stringName = "string";
// back slash required
var stringName =
  "multi-line \
string";

stringName.length; // 6

// Character unicode point
string.charCodeAt(stringIndex);
"abc".charCodeAt(1); // 98

// reverse string
stringName.split("").reverse().join(""); // "gnirts"

stringName = stringName.toUpperCase(); // "GNIRTS"
stringName = stringName.toLowerCase(); // "gnirts"

// capitalize string
stringName = stringName.charAt(0).toUpperCase() + stringName.slice(1); // "Gnirts"

// replace 1 string occurance with string, stringName.replace(old, new)
stringName = stringName.replace("G", "xxx"); // "xxxnirts"

let stringName0 = "test_test_123";
// replace all string occurances with string, stringName.replaceAll(old, new)
stringName0 = stringName0.replaceAll("_", " "); // "test test 123"

// extract characters from a string, from start position to but not including end position
newStringName = stringName.substring(1, 4); // "xxn"

// Split string into arrays
stringName = "test string";
stringName1 = stringName.split(); // ["test string"]
stringName2 = stringName.split(""); // ['t', 'e', 's', 't', ' ', 's', 't', 'r', 'i', 'n', 'g']
stringName3 = stringName.split("s"); // ["te", "t ", "tring"]
```

### javascript ES6 // Almost all of ES5 are included in ES6

```javascript
// back slash not required, but will produce a new line if not given
var stringName = `multi-line \
string`;
let stringName = "string";
const stringName = "string";

// raw strings (ignore escape characters)
String.raw`\n raw string`; // "\n raw string"
```

[back to top](#table-of-contents) ⬆️

## Boolean

### python 3

```python
boolean_name = True
boolean_name = False
not True  # False
not False  # True
```

### javascript ES5

```javascript
var boolean_name;
boolean_name = true;
var boolean_name = false;
!true; // false
!false; // true
```

- truthy: "xxx", 1, -1, 2.5, true
- falsey: false, 0, "", null, undefined, NaN

### javascript ES6

```javascript
let boolean_name;
boolean_name = true;
let boolean_name = false;
const boolean_name = true;
```

[back to top](#table-of-contents) ⬆️

## Arithmetic Operators

### python 2

- addition: `+`
- subtraction: `-`
- multiplication: `*`
- division: `3.0/2  # output 1.5, 3/2 output 1`
- modulus: `%`
- exponent: `**`
- floor division: `3//2  # output 1`

### python 3

- division: `3/2  # output 1.5`
- floor division: `3//2  # output 1`

### javascript

- addition: `+`
- subtraction: `-`
- multiplication: `*`
- division: `3/2  // output 1.5`
- modulus: `%`
- exponent: `**`
- floor division: `Math.floor(3/2)  // output 1`

[back to top](#table-of-contents) ⬆️

## Comparison Operators

### python 3

- `==` (double equal) condition is True if both operand have equal contents

```python
list1 = []
list2 = []
list1 == list2  # True
```

- `is` condition is True if both operand points to the same identical object

```python
list1 = []
list2 = []
list1 is list2  # False

list1 = None
list2 = None
list1 is list2  # True
```

- `!=` condition is True if both operand do not have equal contents
- `is not` condition is True if both operand do not points to the same identical object
- `>` condition is True if right operand is less than left operand
- `<` condition is True if left operand is less than right operand
- `>=` condition is True if right operand is less than or equal to left operand
- `<=` condition is True is left operand is less than or equal to right operand

### javascript

- `==` **not type-safe**, e.g.: string or int will be automatically converted before comparison, **only checks the value**

```javascript
var x = 5;
x == 5; // is true
x == "5"; // is also true
```

- `===` string or int will NOT be converted before comparison, **checks both the value and type**
  - NaN and NaN comparison are not equal
  - +0 and -0 are equal

```javascript
var x = 5;
x === 5; // is true
x === "5"; // is false
```

- `Object.is(var1, var2);` similar to `===`
  - NaN and NaN comparison are equal
  - +0 and -0 are not equal
- `!=`
- `!==`
- `>`
- `<`
- `>=`
- `<=`
- `??` Nullish coalescing operator: returns right-hand side operand when left-hand side operand is null or undefined, and otherwise returns its left-hand side operand

```javascript
const foo = null ?? "default string";
console.log(foo);
// expected output: "default string"

const baz = 0 ?? 42;
console.log(baz);
// expected output: 0
```

[back to top](#table-of-contents) ⬆️

## Logical Operators

### python 3

- `and`
- `or`
- `not`

### javascript

- `&&` and
- `||` or
- `!` not
- truthy and falsey examples
  - `truthy1 && truthy2` truthy2
  - `falsey && truthy` falsey
  - `truthy && falsey` falsey
  - `falsey1 && falsey2` falsey1
  - `truthy1 || truthy2` truthy1
  - `truthy || falsey` truthy
  - `falsey1 || falsey2` falsey2

[back to top](#table-of-contents) ⬆️

## Getting Input

### python 3

```python
input("What's your name?")
```

### javascript

```javascript
// install readline-sync package locally via npm i readline-sync
var readlineSync = require("readline-sync"); // import package
var getInput = readlineSync.question("What's your name?");
```

[back to top](#table-of-contents) ⬆️

## Bitwise Operators

### python 3

```python
# Each digit is 1 bit, all bitwise operators converts to signed 32-bit integers, except for zero-fill right shift which results to unsigned 32 bit integer
a = 60  # 60 = ...0011 1100
b = 13  # 13 = ...0000 1101
c = 9  # 9 = ...0000 1001

# & is binary AND, return 1 if both a and b are 1
a & b  # 12 = ...0000 1100

# | is binary OR, return 1 if either a and or b HAVE a 1
a | b  # 61 = ...0011 1101

# ^ is binary XOR, return 1 if both a and b are not 1 or 0
a ^ b  # 49 = ...0011 0001

# ~ is binary ones complement, invert everything, 1 change to 0 and vice versa
~a  # -61 = ...1100 0011

# << is binary left shift, shift everything to the left by n digit(s)
a << 2  # 240 = ...1111 0000

# >> is binary right shift, shift everything to the right by n digit(s)
a >> 2  # 15 = ...0000 1111
c >> 2  # 3 = ...0000 0010, count the 1s
c = -9  # -9 = ...1111 0111
c >> 2  # -3 = ...1111 1101, count the 0s

# Zero fill right shift, shift everything to the right by n digits(s), leftmost will add n 0s
def zero_fill_right_shift(val, n):
    return (val >> n) if val >= 0 else ((val + 0x100000000) >> n)
zero_fill_right_shift(9, 2)  # 2 = ...0000 0010, count the 1s
c = -9  # -9 = ...1111 0111
zero_fill_right_shift(-9, 2)  # 1073741821 = 0011...1111 1101, count the 0s
```

### javascript

```javascript
// Each digit is 1 bit, all bitwise operators converts to signed 32-bit integers, except for zero-fill right shift which results to unsigned 32 bit integer
let a = 60; // 60 = ...0011 1100
let b = 13; // 13 = ...0000 1101
let c = 9; // 9 = ...0000 1001
// & is binary AND, return 1 if both a and b are 1, count the 1s
a & b; // 12 = ...0000 1100

// | is binary OR, return 1 if either a and or b HAVE a 1
a | b; // 61 = ...0011 1101

// ^ is binary XOR, return 1 if both a and b are not 1 or 0
a ^ b; // 49 = ...0011 0001

// ~ is binary ones complement, invert everything, 1 change to 0 and vice versa, count the 0s
~a; // -61 = ...1100 0011

// << is binary left shift, shift everything to the left by n digit(s)
a << 2; // 240 = ...1111 0000

// >> is Sign-propagating right shift, a binary right shift, shift everything to the right by n digit(s)
a >> 2; // 15 = ...0000 1111
c >> 2; // 3 = ...0000 0010, count the 1s
c = -9; // -9 = ...1111 0111
c >> 2; // -3 = ...1111 1101, count the 0s

// >>> is Zero fill right shift, shift everything to the right by n digits(s), leftmost will add n 0s
c >>> 2; // 2 = ...0000 0010, count the 1s
c = -9; // -9 = ...1111 0111
c >>> 2; // 1073741821 = 0011...1111 1101, count the 0s
```

[back to top](#table-of-contents) ⬆️

## Increment

### python 3

- `x = x + 1` increment
- `x += 1`
- `+=, -=, *=`

### javascript

- `x = x + 1;` add 1 now
- `x += 1;` add 1 now
- `++x;` preincrement, add 1 now
- `x++;` postincrement, display without addition now then add 1 later when called again

[back to top](#table-of-contents) ⬆️

## Arrays and Lists

### python 3

```python
# Empty list
list_name = []
# List with elements
list_name = [1, "one", True]
# Nested lists
list_name = [1, ["two", 3]]

# Find list size
len(list_name)


# Get index of element, return ValueError if element does not exist
list_name.index(element)

# Add element to list (left to right)
list_name.append(element)


# Add element to list at index
list_name.insert(index, element)

# Extends list by appending elements from the iterable
list_name = [1, 2]
list_name.extend([3, 4])  # [1, 2, 3, 4]


# Access an element
list_name[index]

# Modify an element
list_name[index] = element


# Remove element from list (right to left)
list_name.pop()

# Remove element from list at index
list_name.pop(index)

# Remove any element from list at element
list_name.remove(element)

# Method 1: remove all elements
del list_name[:]
# Method 2: remove all elements
list_name = []
# Method 3: remove all elements, only in python 3
list_name.clear()


Slice notation
# items start through stop-1
list_name[start:stop]

# items start through the rest of the array
list_name[start:]

# items from the beginning through stop-1
list_name[:stop]

# a copy of the whole array
list_name[:]

# start through not past stop, by step
list_name[start:stop:step]
list_name = [1, 2, 3, 4, 5]
list_name[::2]  # [1, 3, 5]

# last item in the array
list_name[-1]

# last two items in the array
list_name[-2:]

# everything except the last two items
list_name[:-2]

# all items in the array, reversed
list_name[::-1]

# the first two items, reversed
list_name[1::-1]  # [2, 1]

# the last two items, reversed
list_name[:-3:-1]  # [5, 4]

# everything except the last two items, reversed
list_name[-3::-1]   # [3, 2, 1]


# Reverse an array
list_name.reverse()


# Merge 2 or more arrays together
new_list = list_name + list_name2


# Sort an array in ascending order
list_name = [2, 3, 1, 4]
# method 1
list_name2 = sorted(list_name)  # [1, 2, 3, 4]
# method 2
list_name.sort()  # [1, 2, 3, 4]

# sort an array of dictionaries in ascending order
dict_name = [{"key_name": value1}, {"key_name": value2}]
# sort by value
dict_name2 = sorted(dict_name, key=lambda k: k["key_name"])


# Sort an array in descending order
# method 1
list_name2 = sorted(list_name2, reverse=True)  # [4, 3, 2, 1]
# method 2
list_name.sort(reverse=True)  # [4, 3, 2, 1]

# sort an array of dictionaries in descending order
# sort by value
dict_name2 = sorted(dict_name, key=lambda k: k["key_name"], reverse=True)


# Join array into a string
list_name = ["a", "b", "c"]
x = ", ".join(list_name)
print(x)  # "a, b, c"


# Split string into an array
y = x.split(", ")
print(y)  # ['a', 'b', 'c']

```

### javascript

```javascript
// Method 1: empty list
var list_name = [];
// Method 2: empty list
var list_name = new Array();
// create list of empty elements
var list_name = new Array(3); // [undefined, undefined, undefined]
var list_name = Array.from({ length: 3});  // [undefined, undefined, undefined]
// List with elements
var list_name = [1, "one", true];
var list_name = new Array(3).fill("-") // ["-", "-", "-"]
// Nested lists
var list_name = [1, ["two", 3]];
var list_name = new Array(3).fill(new Array(2).fill("-")) // [["-", "-"], ["-", "-"], ["-", "-"]]


// Modify an element
list_name[index] = element;

// Access an element
list_name[index];


// Remove element from list (right to left)
list_name.pop();
// Remove element from list (left to right)
list_name.shift();
// Remove number of elements (left to right) from index and insert new elements (left to right)
list_name.splice(index, number_of_element);


// Add element to list (left to right)
list_name.push(element);
// Add element to list (right to left)
list_name.unshift(element);
// Add element to list at index (left to right)
list_name.splice(index, 0, new_element1, new_element2...);
// Add & Remove elements to & from list at index (left to right)
list_name.splice(index, number_of_element, new_element1, new_element2...);


// Return the selected elements in an array, as a new array object
list_name.slice();
// Return the elements starting at the given 1st argument,
// and ends at, but does not include, the given 2nd argument
list_name.slice(1, 3);
list_name.slice(1);  // if 1 argument is given, return all elements from array from the 1st argument index


// Find list size
list_name.length;
// Remove all elements
list_name = [];


// Merge 2 or more arrays together
list_name1 = [1, 2, 3];
list_name2 = [4, 5, 6];
new_list = list_name1.concat(list_name2);


// Get index of element, return -1 if not present
list_name = ["element1", "element2", "element1"]
list_name.indexOf("element1")  // returns index of 0
list_name.indexOf("element1", 1);  // returns index of 2
list_name.indexOf("element1", 2);  // also returns index of 2
list_name.indexOf("element1", 0);  // returns index of 0


// Sort array in ascending order
list_name = [2, 3, 1, 4];
list_name.sort();  // [1, 2, 3, 4]  work only only positive integers and strings

list_name = [2, -1, 4, 3];
list_name.sort((a, b) => a - b);  // [ -1, 2, 3, 4 ] work for negative and positive integers

// Sort array in descending order
list_name.sort((a, b) => (b - a));  // [4, 3, 2, 1] work for negative and positive integers
list_nameStr = ["b", "a", "c"];
// method 1: most optimal
list_nameStr.sort().reverse(); // ["c", "b", "a"]
// method 2
list_nameStr.sort((a, b) => (a > b ? -1 : 1));
// method 3
list_nameStr.sort((a, b) => b.localeCompare(a));


// Determine whether an array contains a specified element
list_name = ["a", "b", "c", "a"]
console.log(list_name.includes("b"))  // true

// Determine whether an array contains a specified element from starting index
console.log(list_name.includes("b", 2)  // false
console.log(list_name.includes("a", 2)  // true

// Flatten nested arrays
list_name = [1, 2, [3, 4]];
list_name.flat() // [1, 2, 3, 4]

// Check if all elements in array pass the conditional check
function helper(currentValue) {
 return currentValue < 3;
}
list_name = [1, 2, 3, 4];
list_name.every(helper); // false
list_name = [1, 2];
list_name.every(helper); // true
```

[back to top](#table-of-contents) ⬆️

## Conditional Statement

### python 3

```python
# If else statement
if condition_a:
    do_A
elif condition_b:
    do_B
else:
    do_something_else


# Ternary operator
do_A if condition_a else do_B


# Switch Statement is not available in python, but can create similar function
def switch(choice):
    case = {
        1: do_A,
        2: do_B,
    }
    case.get(choice, do_something_else)


# comparing between 2 objects (array, dictionaries, etc.) is allowed
x = [1, 2, 3]
y = [1, 2, 3]
x == y  # returns True
```

### javascript

```javascript
// If else statement
if (condition_a) {
  do_A;
} else if (condition_b) {
  do_B;
} else {
  do_something_else;
}

// Ternary operator
condition_a ? do_A : do_B;

// Switch statement
switch (choice) {
  case choice_A:
    do_A;
    break;
  case choice_B:
    do_B;
    break;
  default:
    do_something_else;
}

// comparing between 2 objects (array, object, etc.) is NOT allowed
var x = [1, 2, 3];
var y = [1, 2, 3];
x === y ? true : false; // returns false
// solution: use JSON.stringify()
JSON.stringify(x) === JSON.stringify(y) ? true : false; // return true
```

[back to top](#table-of-contents) ⬆️

## Loops

### python 2

```python
# While loop

# declare_initial_conditional_value
i = 0
# Set condition
while i<5:  # Start from 0 to 4
    do_this
    # Include condition_increment_or_decrement
    i += 1
    # Can use break, continue, and pass statements to add additional functionality, or not use any
    break  # Breaks out of the current closest enclosing loop
    continue  # Goes to the top of the closest enclosing loop
    pass  # Does nothing at all
```

### python 3

```python
# For loop

# Looping with range()
for i in range(5):  # Starts from 0 to (5 - 1)
    do_this
    # Can use break, continue, and pass statements to add additional functionality, or not use any
    break  # Breaks out of the current closest enclosing loop
    continue  # Goes to the top of the closest enclosing loop
    pass  # Does nothing at all

# Looping with range() and multiple parameters
for i in range(0, 5, 2):  # Start from 0 to 4 at every 2 steps (0,2,4)
    do_this

# Reverse loop
for i in range(4, -1, -1):  # Start from 4 to 0 at every -1 steps
    do_this


# Looping and getting each value
for value in list_name:  # [value1, value2, value3,...]
    print(value)


# Looping and getting index and value
for index, value in enumerate(list_name):
    print(index, value)  # output index, value


# Loops and getting both key and value of a dict
x = { "one": 1, "two": 2}
for k, v in x.items():
    print(f"k: {k}, v: {v}")
```

### javascript ES5

```javascript
// While loop

// declare_initial_conditional_value
var i = 0;
// Set condition
while (i < 5) {
  // Start from 0 to 4
  do_this;
  // Include condition_increment_or_decrement;
  i++;
  // Can use break or continue to add additional functionality, or not use any
  break; // Breaks out of the current closest enclosing loop
  continue; // Goes to the top of the closest enclosing loop
}

// Do While loop
var i = 0;
do {
  do_this;
  i++;
} while (i < 5);


// For loop

for (var i = 0; i < 5; i++) {
  // Start from 0 to 4
  do_this;
  // Can use break or continue to add additional functionality, or not use any
  break; // Breaks out of the current closest enclosing loop
  continue; // Goes to the top of the closest enclosing loop
}

// Reverse loop
for (var i = 4; i >= 0; i--) {
  // Start from 4 to 0
  do_this;
}

// forEach loop
// Looping through a list while calling a function
list_name.forEach(function (value, index, list) {
  // do not need to include all 3 parameters, but must be in order
  console.log(index, value, list); // outputs index value list
});
```

### javascript ES6: Use let in loops when declaring

```javascript
// For of loop
// Looping and getting each value
for (let value of list_name) {
  // [value1, value2, value3,...]
  console.log(value); // output value
}

// Looping and getting index and value
for (let index_and_value of list_name.entries()) {
  console.log(index_and_value); // output a list [index, value]
}

// For in loop
for (let index in list_name) {
  console.log(list_name[index]);
}

// For in loop normally used to get values from objects (hash table, dictionaries) than to arrays
// object = {key1:value1, key2:value2,...}
for (let key in object) {
  console.log(object[key]); // outputs value, normally calling this way will not output value from objects
}
```

[back to top](#table-of-contents) ⬆️

## Instantiation

### python 3

```python
t = Thing()  # everything
```

### javascript

```javascript
v = getValue(); // plain function
t = new Thing(); // instantiation
```

[back to top](#table-of-contents) ⬆️

## Functions

### python 3

- Function **returns None by default** if return statement is not declared

```python
# Normal function, use return to return values
def myFunction():
    do_something

# Normal function with parameters
def myFunction(a):
    do_something_with_a

# Default parameters
def myFunction(a=value):
    do_something_with_a
    return something

# Calling a function
result = myFunction(a=argument_value)

# Lambda function: a small anonymous function
# can take any number of arguments, but can only have 1 expression
myFunction = lambda a : do_something_with_a
myFunction = lambda a, b : do_something_with_a_and_b

# Function annotation (python 3)
def get_sum(num1: int, num2: int):
    return num1 + num2

# Function annotation with default parameters (python 3)
def get_sum(num1: int=1, num2: int=2):
    return num1 + num2
```

### javascript ES5

- Function **returns undefined by default** if return statement is not declared

```javascript
// Normal function, use return to return values
function myFunction() {
  do_something;
}
// Normal function with parameters
function myFunction(a) {
  do_something_with_a;
}

// Function expression
let myFunction = function () {
  do_something;
};

// Function expression with parameters
let myFunction = function (a) {
  return a**2
};
// Calling the function
myFunction(6)   // 36


// Arrow function: do not have their own "this" keyword
// 1 line arrow function
let myFunction = () => do_something; // () at (do_something) not necessary if on single line
// 1 line arrow function with arguments
let myFunction = (a) => do_something_with_a;

// arrow function, must use return keyword
let myFunction = () => {
  return do_something;
};

// arrow function with arguments
let myFunction = (num) => {
    return num**2
}
// Calling the function
myFunction(7)   // 49


// Immediately Invoked Function Expressions (IIFE)
// method 1
(function () {
  do_something;
})();
// method 2: parentheses placed outside instead of inside.
(function () {
  do_something;
}());
// method 3: no returning of value
!(function () {
  do_something;
})();
```

### javascript ES6

```javascript
// Default parameters
function myFunction(a = value) {
  do_something_with_a;
}
```

[back to top](#table-of-contents) ⬆️

## Higher order functions

### python 2

```python
# Map: applies a given function to each item of an iterable (list, tuple etc.) and returns a list of the results
# map(function, iterable, ...)
arr = [1, 2, 3]
def add(n):
    return n + n
map(add, arr)  # return <map object at 0x10473e518>
list(map(add, arr))  # return [2, 4, 6]


# Filter: filter and return a new array based on the conditions
# filter(function, iterable)
arr = [1, 2, 3]
def condition(n):
    if n < 3:
        return n
filter(condition, arr)  # return <filter object at 0x10473e550>
list(filter(condition, arr))  # return [1, 2]
```

### python 3

```python
# Zip: combines 2 arrays or tuples into an array of tuples
arr1 = [1, 2, 3]
arr2 = ["1", "2", "3"]
zip(arr1, arr2)  # return <zip object at 0x7f4ec1106100>
list(zip(arr1, arr2))  # [(1, '1'), (2, '2'), (3, '3')]
```

### javascript

```javascript
// Map: create a new array from a current array
// array.map(element, currentIndex, originalArray)
const companies = [
    {name: "company1", category: "industry1"},
    {name: "company2", category: "industry2"}
];
// callback method
const companyNames = companies.map(function(company) {
    return company.name;
}
// arrow function method
const companynames = companies.map((company) => company.name);


// Filter: creates a new array with all elements that pass the condition implemented by the provided function
// array.filter(element, currentIndex, originalArray)
const ages = [age1, age2, age3];
// callback method
const canDrink = ages.filter(function(age) {
    if (condition) {
        return true;
    }
}
// arrow function method
const canDrink = ages.filter(age => condition);


// Sort: sorts the elements of an array in place and returns the sorted array
// array.sort(compareFunction)
// if compareFunction is not used, all sorted elements will be sorted based on it's string value
let array = ["1", 30, 4, 21, 100000];
array.sort();  // returns ["1", 100000, 21, 30, 4]

// sort in ascending order
array.sort((a, b) => a - b);  // returns ["1", 4, 21, 30, 100000]

// sort in descending order
array.sort((a, b) => b - a);  // returns [100000, 30, 21, 4, "1"]

// Zip is not available in Javascript, use Maps instead
const arr1 = [1, 2, 3];
const arr2 = ["1", "2", "3"];
function zip(arrays) {
    return arrays[0].map(function(_,i){
        return arrays.map(function(array){return array[i]})
    });
}
zip([arr1, arr2]);  // [[1, '1'], [2, '2'], [3, '3']]
```

[back to top](#table-of-contents) ⬆️

## Hash Tables

- Hash Tables, Dictionaries, Objects

### python 3

```python
# Create dictionary
newDict = {}

# Create dictionary and assign key value pairs
# method 1
newDict = {
    "key1": "value1",
    "key2": 123,
    "key3": True,
    "key4": myFunction
}
# method 2
newDict = dict(key1="value1", key2="value2")

# Add or reassign key value pair
newDict["Key"] = "Value"  # method 1
newDict.update({"key": "value"})  # method 2

# Set multiple keys with a similar value
newKeys = ("key1", "key2", "key3")
newValue = value
newDict = dict.fromkeys(newKeys, newValue)

# Return value of the item with the specified key
# If the key does not exist, insert the key, with the specified value
newVariable = newDict.setdefault("key", "newValue")

# Get value
newDict["key"]  # method 1 # return KeyError if key does not exist
newDict.get("key")  # method 2 # return None if key does not exist

# Get list of keys
newDict.keys()  # dict_keys(['key1', 'key2', 'key3', 'key4'])
list(newDict.keys())  # ['key1', 'key2', 'key3', 'key4']

# Get list of values
list(newDict.values())

# Get list of key value tuples
list(newDict.items())

# Loop through Dictionary and get each key
# method 1
for key in newDict:
    print(key)
# method 2
for key in newDict.keys():
    print(key)

# Loop through Dictionary and get each value
# method 1
for key in newDict:
    print(newDict[key])
# method 2
for value in newDict.values():
    print(value)

# Loop through both keys and values
for key, value in newDict.items():
    print(key, value)

# Check if key exists
if "key" in newDict:
    return True

# Get dictionary length
len(newDict)

# Copy dictionary
# cannot copy just from dict2 = dict1 as it is just referencing to dict1
# method 1
newDict2 = newDict.copy()
# method 2
newDict2 = dict(newDict)

# Remove items
newDict.pop("key")  # method 1
del newDict["key1"]  # method 2

# Remove last inserted item
newDict.popitem()

# Delete entire dictionary
del newDict  # method 1
newDict.clear()  # method 2
```

### javascript ES5

```javascript
// Objects
// Create object
let newObj = new Object(); // method 1
let newObj = {}; // method 2, literal notation

// Create object and assign values
// keys can only be strings without quotes
let newObj = {
  key1: "stringValue",
  key2: 123,
  key3: true,
  key4: ["array", "array2"],
  key5: { anotherKey: anotherValue },
  key6: function (arg) {
    return do_something_with_arg;
  },
};

// dynamic key
let myKey = "emotion";
let newObj2 = {
  [myKey]: "Happy",
}; // key = "emotion"


// Creates a new object, using an existing object as the prototype of the newly created object
// method 1
newObj2 = Object.create(newObj); // copies the prototype of newObj, key value pairs will become inherited
let newObj2pt2 = Object.create(null, {
  // creates a new object but without default object properties, default object properties can't be used
  key1: value,
});
let newObj2pt3 = Object.create(null, {
  // set object configuration
  key: {
    value: "something",
    writable: true,
    enumerable: true,
    configurable: true,
  },
});
let newObj2pt4 = Object.create(Object.prototype, {
  // creates a new object with all default object properties
  key: {
    value: "something",
    writable: true,
    enumerable: true,
    configurable: true,
  },
});
// method 2: merge 2 object together
newObj2 = Object.assign(oldObj, newObj);


// Assign and Reassign values
newObj["key1"] = "newString"; // method 1, bracket notation
newObj.key1 = "newString2"; // method 2, dot notation

// Copy the values of all enumerable own properties from one or more source objects to a target object
// return the target object
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };
const newObj = Object.assign(target, source); // newObj, target = { a: 1, b: 4, c: 5 }

// Copy without mutating the target source
const target2 = { a: 1, b: 2 };
const source2 = { b: 4, c: 5 };
const newObj2 = Object.assign({}, target2, source2); // newObj2 = { a: 1, b: 4, c: 5 }, target2 = { a: 1, b: 2 }


// Get value
newObj["key1"]; // method 1
newObj.key1; // method 2

// Get an array of keys
Object.keys(newObj);

// Get an array of values
Object.values(newObj);

// Loop through all key value pairs
// must be (key, value)
for (let [key, value] of Object.entries(newObj)) {
  console.log(`Key: ${key}, Value: ${value}`);
}

// Defines a new property directly on an object, or modifies an existing property on an object, and returns the object
// Object.defineProperty(obj, propertyName, descriptor)
Object.defineProperty(newObj, "property1", {
  value: "123",
  writable: true,
  enumerable: true,
  configurable: false,
}); // newObj.property1 = 123

let descriptor = Object.getOwnPropertyDescriptor(newObj, "property1");
console.log(descriptor);
/*
{
  value: 123,
  writable: true,  // if false cannot reassign new primitive values, but can reassign values of an object
  enumerable: true,  // if false will skip this property when looping
  configurable: true,  // if false cannot delete and redefine property (except writable); once set to false, cannot change back to true
}
*/

// Seals an object
// prevent addition of properties, however defined properties still can be changed
Object.seal(newObj);

// Freeze an object
// makes the object immutable, meaning no change to defined property allowed, unless they are objects.
Object.freeze(newObj);
```

### javascript ES6

```javascript
// Merge 2 objects
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };
const newObj = { ...target, ...source }; // { a: 1, b: 4, c: 5 }

// Maps or Hash tables
// Create new Map or hash table
const newDict = new Map();

// Add key value pair data
// keys does not need to be strings, can be numbers, booleans, etc.
newDict.set(key1, value1);
newDict.set(key2, value2);

// Get all keys
newDict.keys();

// Get all values
newDict.values();

// Iterate over Maps to get each key
for (let key of newDict.keys()) {
  console.log(key);
}

// Iterate over Maps to get each value
for (let value of newDict.values()) {
  console.log(value);
}

// Get value
newDict.get(key);

// Get hash table size
newDict.size;

// Check if key value pair exist with key input
newDict.has(key);

// Loop through all key value pairs
// method 1, must be (value, key)
newDict.forEach((value, key) => console.log(`Key: ${key}, Value: ${value}`));
// method 2, must be (key, value)
for (let [key, value] of newDict.entries()) {
  console.log(`Key: ${key}, Value: ${value}`);
}

// Delete key value pair
newDict.delete(key);
// Delete all key value pairs
newDict.clear();

// WeakMap: similar to Map, but all keys must be objects
// Create new weak map
const newDict = new WeakMap();

// Add key value pair data
// key MUST be and Object
newDict.set(obj1, value1);
newDict.set(obj2, value2);

// Get value
newDict.get(obj);

// Delete key value pair
newDict.delete(obj);

// Check if key value pair exist with key input
newDict.has(obj);
```

[back to top](#table-of-contents) ⬆️

## Destructuring

### python 3

```python
# Tuples
xVariable, yVariable = (xValue, yValue)

# Arrays
xVariable, yVariable = [xValue, yValue]

# String
xVariable, yVariable = "xy"

# Dictionaries
xKey, yKey = {"xKey": xValue, "yKey": yValue}
```

### javascript ES6

```javascript
// Arrays
const [xVariable, yVariable] = [xValue, yValue];

// Objects
const obj = {
  xKey: xValue,
  yKey: yValue,
};
// declaring variables
const { xKey, yKey } = obj; // variable names must be the same as object key names

// assigning different variable names
const { xKey: xNewKey, yKey: yNewKey } = obj;

// Set default values if extracted variables does not exist
const { xKey, yKey, zKey = "test" } = obj;

// Use optional chaining for async code where data type will change
let data = null; // value before fetch
const { a = "", b = "" } = data?.[0] || []; // checks if data is undefined or null, then checks if there is value inside array
console.log(a); // ""

data = [{ a: "hello", b: "world" }]; // value after fetch
const { a = "", b = "" } = data?.[0] || []; // checks if data is undefined or null, then checks if there is value inside array
console.log(a); // "hello"
```

[back to top](#table-of-contents) ⬆️

## Spread Operator

### python 3

```python
# *args (splat)
# Takes an array and transform (unpacks) it into single values
# Must utitlize all of the element of the array to work
myFunction(a, b, c)  # normal method
myFunction(*Tuple)  # (a, b, c)
myFunction(*List)  # [a, b, c]
myFunction(*String)  # "abc"
myFunction(*Dict)  # {"a": value1, "b": value2}  only utilize the keys

# **kwargs
myFunction(**Dict) # {"a": value1, "b": value2}  utilize both keys and values
```

### javascript ES6

```javascript
// Takes an array and transform (unpacks) it into single values
// Must utitlize all of the element of the array to work
let arr = [a, b, c];
myFunction(a, b, c); // normal method
myFunction.apply(null, arr); // using the apply() method
myFunction(...arr); // spread method

// join multiple arrays together
let arr1 = ['a', 'b', 'c'];
let arr2 = [1, 2, 3];
let totalArr = arr1.concat(arr2); // concat method
let totalArr = [...arr1, ...arr2];  // ['a', 'b', 'c', 1, 2, 3]
```

[back to top](#table-of-contents) ⬆️

## Rest parameters

### python 3

```python
# *args
# Receive a couple of single values and transform them into tuple
def myFunction(*args):
    newArr = args  # args is tuple of arugments

# **kwargs
# Receive a couple of keys and values and transform them into a dictionary
def myFunction(**kwargs):
    newDict = kwargs  # kwargs is a dictionary of keys and values
# calling example
myFunction(var1=value1, var2=value2)
```

### javascript ES6

```javascript
// Receive a couple of single values and transform them into an array
function myFunction(...args) {
  let argsArr = args; // args is an array of arguments
}
```

[back to top](#table-of-contents) ⬆️

## Class

### python 2

```python
class MathClass:
    def __init__(self, arg1, arg2):
        self.arg1 = arg1
        self.arg2 = arg2
        self.total = self.outterAdd(arg1, arg2)

    def innerAdd(self, arg3):
        return self.arg1 + self.arg2 + arg3

    # Static method knows nothing about the class and just deals with the parameters
    def outterAdd(number1, number2):
        return number1 + number2
    outterAdd = staticmethod(outterAdd)


test = MathClass(2, 4)
print (test.total)  # 6
print (test.innerAdd(2))  # 8
print (test.outterAdd(3, 7))  # 10
print (MathClass.outterAdd(4, 5)  # 9
```

### python 3

```python
class MathClass:
    def __init__(self, arg1, arg2):
        self.arg1 = arg1
        self.arg2 = arg2
        self.total = self.outterAdd(arg1, arg2)

    def innerAdd(self, arg3):
        return self.arg1 + self.arg2 + arg3

    # Static method knows nothing about the class and just deals with the parameters
    @staticmethod
    def outterAdd(number1, number2):
        return number1 + number2


test = MathClass(2, 4)
print(test.total)  # 6
print(test.innerAdd(2))  # 8
print(test.outterAdd(3, 7))  # 10
print(MathClass.outterAdd(4, 5))  # 9


# Using classmethod: method 1
class Person:
    name = "Default name"

    @classmethod
    def change_name(clas, new_name):
        cls.name = new_name


person1 = Person()
print(person1.name)  # Default name
person1.change_name("New name")
print(person1.name)  # New name


# Using classmethod: method 2
class Person2:
    def __init__(self, name):
        self.name = name

    @classmethod
    def use_default_name(cls):
        return cls("Default name")


person2 = Person2("My name")
print(person2.name)  # My name
person3 = Person2.use_default_name()
print(person3.name)  # Default name


# Inheritance
class Employee:  # parent
    raise_amt = 1.04

    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.pay = pay

    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amt)


class Developer(Employee):  # child
    raise_amt = 1.1

    def __init__(self, first, last, pay, prog_lang):
        super().__init__(first, last, pay)  # method 1: implement parent class init method
        Employee.__init__(self, first, last, pay)  # method 2: implement parent class init method
        self.prog_lang = prog_lang


dev = Developer("abc", "xyz", 5000, "Python")
print(dev.pay)  # 5000
dev.apply_raise()
print(dev.pay)  # 5500
```

- python magic method guide
  - https://rszalski.github.io/magicmethods/

### javascript ES5

```javascript
// method 1
var MathClass = {
  arg1: 2,
  arg2: 0,

  get getTotal() {
    return this.arg1 + this.arg2;
  },

  set getTotal(arg2) {
    // can only have 1 parameter
    this.arg2 = arg2;
  },
};

MathClass.getTotal; // 2
MathClass.getTotal = 4;
MathClass.getTotal; // 6

// method 2
// Constructor
var MathClass = function (arg1) {
  this.arg1 = arg1;
  this.arg2 = 0;
};

// Instantiation
var test = new MathClass(2);

// Add method
MathClass.prototype.innerAdd = function (arg3) {
  return this.arg1 + this.arg2 + arg3;
};

test.innerAdd(4); // 6

// Add getter and setter
Object.defineProperty(MathClass.prototype, "getTotal", {
  get: function () {
    return this.arg1 + this.arg2;
  },
  set: function (arg2) {
    // can only have 1 parameter
    this.arg2 = arg2;
  },
});

var total = new MathClass(2);
total.getTotal; // 2
total.getTotal = 4;
total.getTotal; // 6

// inheritance
function Employee(first, last, pay) {
  this.raiseAmt = 1.04;
  this.first = first;
  this.last = last;
  this.pay = pay;
}

Employee.prototype.applyRaise = function () {
  this.pay = parseInt(this.pay * this.raiseAmt);
};

function Developer(first, last, pay, progLang) {
  Employee.call(this, first, last, pay);
  this.raiseAmt = 1.1;
  this.progLang = progLang;
}

Developer.prototype = Object.create(Employee.prototype);

Developer.prototype.constructor = Developer;

const dev = new Developer("abc", "xyz", 5000, "Javascript");
console.log(dev.pay); // 5000
dev.applyRaise();
console.log(dev.pay); // 5500
```

### javascript ES6

```javascript
// Case 1: normal javascript way
class MathClass {
  #privateVariable; // required if want to declare private variable

  constructor(arg1, arg2) {
    this.arg1 = arg1;
    this.arg2 = arg2;
    this.#privateVariable = "this is a real private variable"; // cannot be accessed directly
    this.total = this.constructor.outterAdd(arg1, arg2);
  }

  innerAdd(arg3) {
    return this.arg1 + this.arg2 + arg3;
  }

  // Static method knows nothing about the class and just deals with the parameters
  static outterAdd(number1, number2) {
    return number1 + number2;
  }

  get privateVariable() {
    return this.#privateVariable;
  }

  set privateVariable(newValue) {
    // can only have 1 parameter
    this.#privateVariable = newValue;
  }
}

const test = new MathClass(2, 4);
console.log(test.total); // 6
console.log(test.innerAdd(2)); // 8
console.log(test.constructor.outterAdd(3, 7)); // 10
console.log(MathClass.outterAdd(4, 5)); // 9

console.log(test.privateVariable); // "this is a real private variable"
test.privateVariable = "changed private variable value";
console.log(test.privateVariable); // "changed private variable value"

// Case 2: event handlers in React
class MathClass {
  constructor() {
    this.arg1 = 2;
    this.arg2 = 4;
    this.innerAdd = this.innerAdd.bind(this); // this is required to prevent TypeError
  }

  innerAdd(arg3) {
    return this.arg1 + this.arg2 + arg3;
  }
}
const test = new MathClass();
console.log(test.innerAdd(2)); // 8

// Inheritance
class Employee {
  // parent
  raiseAmt = 1.04;

  constructor(first, last, pay) {
    this.first = first;
    this.last = last;
    this.pay = pay;
  }

  applyRaise() {
    this.pay = parseInt(this.pay * this.raiseAmt);
  }
}

class Developer extends Employee {
  // child
  raiseAmt = 1.1;

  constructor(first, last, pay, progLang) {
    super(first, last, pay); // implement parent class init method
    this.progLang = progLang;
  }
}

const dev = new Developer("abc", "xyz", 5000, "Javascript");
console.log(dev.pay); // 5000
dev.applyRaise();
console.log(dev.pay); // 5500
```

[back to top](#table-of-contents) ⬆️

## Importing Libraries

### python 3

```python
# import module from libraries
import module_name  # must call module_name to use

# Using alias
import module_name as mn  # must call mn to use
import pandas as pd

# import class or function from a module
from module_name import function_name
from module_name import function_name1, function_name2  # multiple imports

# Absoute imports within the same project (file extensions not required)
from folder1 import module1  # example 1
from folder1.module2 import function1  # example 2
from folder2 import class1  # example 3
from folder2.subfolder1.module5 import function2  # example 4


# Relative imports (dot feature is similar to terminal)
from .module1 import class1  # example 1
from ..folder2 import function1 # example 2
from . import class2 # example 3
```

### javascript ES5

```javascript
// Before a module can be imported, it has to be exported first
var objectName.functionName = function();
module.exports = objectName;  // can be an object of functions
// alternative exports, import rules also change
exports.moduleName = objectName;  // preset a name to the module

// importing a module
// moduleName can be path too
var mn = require("moduleName");  // must call mn to use
var {function1, function2} = require("moduleName");  // importing multiple functions from a module
// import for alternative export
var mn = require("moduleName").moduleName;
```

### javascript ES6

```javascript
// Before a module can be imported, it has to be exported first
export default objectName; // exporting a single or nested functions or class

// {} must be used when importing
// method 1
export { functionName }; // export only 1 class or function (can be used for importing multiple functions or classes
// method 2, can be function, class, objects, etc.
export const functionName = () => {
  do_something;
};

// import class or function from module
import "moduleName"; // import module
import name from "moduleName"; // name can be anything if only have 1 export
import * as name from "moduleName"; // import multiple exports as name
import { function1 } from "moduleName"; // import a function from a module of multiple exports
import { function1 as f1 } from "moduleName"; // import a function with alias
import { function1, function2 } from "moduleName"; // import multiple functions
import name, { function1 } from "/modules/path/moduleName"; // function1 can be used directly or via name.function1
```

[back to top](#table-of-contents) ⬆️

## Type Conversions

### python 3

```python
# Convert to Integer, floats will round down
int(type_to_convert)

# Convert to floats
float(type_to_convert)

# Convert to strings
str(type_to_convert)

# Convert to arrays
list(type_to_convert)  # cannot be a number

# Convert to tuples
tuple(type_to_convert)  # cannot be a number

# Convert to sets
set(type_to_convert)  # cannot be a number
```

### javascript

```javascript
// number to string
let num = 123;
let str = String(num); // "123"

// number to bigInt
let bigNum = BigInt(num);  // "123n"

// bigInt to number
let bigInt = 1234n;
// method 1
num = parseInt(bigInt);  // 1234
// method 2
num = Number(bigInt);  // 1234

// string to integer (remove all non numbers automatically)
str = "12 kg";
num = parseInt(str); // 12

// string to float (remove all non number automatically)
str = "12.5 kg";
num = parseFloat(str) // 12.5

//string to integer or float (return NaN if non number in string)
str = "12"
num = Number(str) // 12
str = "12.5";
num = Number(str) // 12.5
str = "12.5 kg";
num = Number(str); // NaN
```

[back to top](#table-of-contents) ⬆️

## Find Data Type

### python 3

```python
# Get data type
num = 123
type(num)  # int

# Get boolean value
isinstance(num, int)  # True
isinstance(num, str)  # False

# check if all characters in string are uppercase
"abc".isupper()  # False
"Abc".isupper()  # False
"ABC".isupper()  # True
"AB1".isupper()  # True

# check if all characters in string are lowercase
"abC".islower()  # False
"abc".islower()  # True
"ab1".islower()  # True

# check if all characters in string are digits
"ab1".isdigit()  # False
"123".isdigit()  # True


# check if 2 objects are exactly the same even if they have the same value
# primitive values have the exact same objects
x = 1
y = 1
id(x)  # 4357474608
id(y)  # 4357474608

# reference type objects are different even if they have the same value
x = [1]
y = [1]
id(x)  # 4360090688
id(y)  # 4359972032
```

### javascript

```javascript
// Get data type: "number", "string", "boolean", "object", "undefined", "function"
// null and arrays are classified as object
// classes and methods are classfied as function
let num = 123;
typeof num; // "number"

let array = [1, 2, 3];
typeof array; // "object"

let variable1 = 10 / undefined; // NaN
Number.isNaN(variable1); // true
```

[back to top](#table-of-contents) ⬆️

## String Concatenation

### python 3

```python
string_name = "string1" + "string2"  # "string1string2"
# f string: python 3.6 and above
string1 = "string1"
string2 = "string2"
string_name = f"{string1} {string2}"  # "string1 string2"
```

- string formatting for numbers

```python
a = 8

# set number of digits
# add spaces to the right for missing digits
print(f"{a:<2}")  # "8 "
#add 0s (can only be number 0) to the right for missing digits
print(f"{a:<02}")  # "80"

# add spaces to the left for missing digits
print(f"{a:>2}")  # " 8"
# add 0s (can only be number 0) to the right for missing digits
print(f"{a:>02}")  # "08"
```

### javascript ES5

```javascript
// javascript allows data type mashups, numbers will be converted to strings when concatenated with a string.
let stringName = "string1" + "string2" + 123; // "string1string2123"
```

### javascript ES6

```javascript
let string1 = "string 1 value";
let string2 = "string 2 value";
let stringName = `${string1} ${string2} 123`; // "string 1 value string 2 value 123"
```

[back to top](#table-of-contents) ⬆️

## JSON

### python 3

```python
import json  # must import to use

# python objects that can be converted: dict, list, tuple, string, int, float, True, False, None
# Convert JSON to python
json.loads(json_object)

# Convert python to JSON
json.dumps(python_object)
```

### javascript

```javascript
// JSON (JavaScript Object Notation): a lightweight, text-based data format that's based on JavaScript.
// convert js to JSON
let objName = { title: "Black Panther" };
objName = JSON.stringify(objName);

// convert JSON to js
let objName = { title: "Black Panther" };
objName = JSON.parse(objName);
```

[back to top](#table-of-contents) ⬆️

## Program Entry Point

### python 3

```python
if __name__ == "__main__":
    # do something
```

### javascript

```javascript
// only works in node js
if (require.main === module) {
  // do something
}
```

[back to top](#table-of-contents) ⬆️

## Swapping values

### python 3

```python
a, b = 1, 2
# method 1
temp = a
a = b
b = temp

# method 2
a, b = b, a
```

### javascript ES5

```javascript
let a = 1;
let b = 2;
const temp = a;
a = b;
b = temp;
```

### javascript ES6

```javascript
[a, b] = [b, a];
```

[back to top](#table-of-contents) ⬆️

## Error Handling

### python 3

- try: lets you test a block of code for errors
- except: except block lets you handle the error
  - covers all error types
    > except:
  - define exception type (can write multiple except statements)
    > except NameError:
  - save error to variable e
    > except ValueError as e:
  - list of important error types
    - AssertionError, AttributeError, EOFError, FloatingPointError, GeneratorExit, ImportError, IndexError, KeyError
    - KeyboardInterrupt, MemoryError, NameError, NotImplementedError, OSError, OverflowError, ReferenceError, RuntimeError
    - StopIteration, SyntaxError, IndentationError, TabError, SystemError, TypeError, UnboundLocalError, UnicodeError
    - UnicodeEncodeError, UnicodeDecodeError, UnicodeTranslateError, ValueError, ZeroDivisionError
- else: code to be executed if no errors were raised
- finally: if specified, will be executed regardless if the try block raises an error or not
  - useful to close objects and clean up resources

```python
# similar to if else
try:  # must start with try
    do_something
except:  # must have to handle errors
    do_something_if_error_occurs
else:  # not required
    do_something_if_no_error
finally:  # not required
    do_something_when_try_&_except_or_else_is_completed
```

### javascript

- try: lets you test a block of code for errors
- catch: lets you handle the error
- finally: lets you execute code, after try and catch, regardless of the result

```javascript
try {
  doSomething;
} catch (error) {
  doSomethingIfErrorOccurs;
} finally {
  doSomethingWhenTryAndCatchIsCompleted;
}
```

[back to top](#table-of-contents) ⬆️
## Custom Error

### python 3

```python
# raise generic exception
raise Exception("custom message")

# raise specific exception
raise ValueError("custom message")
```

### javascript

```javascript
throw "custom message"; // throw a text

throw 123; // throw a number
```

[back to top](#table-of-contents) ⬆️
## Asynchronous

- Handling asynchronous code (making it synchronous)

### python

### javascript ES5

```javascript
var posts = [
  { title: "Post 1", body: "body of post 1" },
  { title: "Post 2", body: "body of post 2" },
];

// callback is required if need getPost to display data after createPost is called
// reason is because createPost takes longer time to complete compared to getPost
function createPost(post, callback) {
  setTimeout(() => {
    posts.push(post);
    callback();
  }, 2000);
}

// method 1
// callback function
function getPosts() {
  setTimeout(() => {
    var output = "";
    posts.forEach((post, index) => {
      output += post.title;
    });
    console.log(output);
  }, 1000);
}
createPost({ title: "Post 3", body: "body of post 3" }, getPosts);

// method 2:
// Using anonymous callback function can lead to callback hell if over used
createPost({ title: "Post 3", body: "body of post 3" }, function () {
  setTimeout(() => {
    var output = "";
    posts.forEach((post, index) => {
      output += post.title;
    });
    console.log(output);
  }, 1000);
});
```

### javascript ES6

```javascript
// Change createPost to return a Promise
function createPost(post) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (post) {
        posts.push(post);
        resolve();
      } else {
        reject("error");
      }
    }, 2000);
  });
}

// method 3
// use .then() instead of callback
createPost({ title: "Post 3", body: "body of post 3" })
  .then(getPosts) // can chain multiple promises by adding .then(do_something)
  .catch((error) => console.log(error));

// method 4
// use Promise.all
Promise.all([
  // can chain multiple promises
  createPost({ title: "Post 3", body: "body of post 3" }),
]).then((values) => {
  getPosts();
  console.log(values); // output array of results e.g [promise1_output, promise2_output, ...]
});
```

### javascript ES8

```javascript
// method 5
// use async / await when calling functions
async function init() {
  await createPost({ title: "Post 3", body: "body of post 3" });
  getPosts();
}
init();
```

- the difference between `process.nextTick` vs asynchronous / callback
  - process.nextTick() runs immediately after the current synchronous execution, before I/O and timers.
    - it is not part of the event loop phases! Instead, it uses the Next Tick Queue, which has the highest priority.
  - asynchronous code runs after the event loop finishes processing the current execution, in the Timer Queue.
- Order which comes first
  1.	Synchronous Code runs first. (take note that anything in a Promise constructor might come first based on sequential order whichever was called first)
	 2.	Next Tick Queue (process.nextTick()) runs immediately before moving to the event loop.
	 3.	Microtask Queue (Promise.then(), queueMicrotask()) runs after the Next Tick Queue before the event loop continues.
	 4.	Timer Queue (setTimeout(), setInterval()) runs in the Timers Phase of the event loop.

```javascript
async function example() {
    return new Promise((resolve) => {
        console.log("promise constructor");
        resolve();
    }).then(() => {
        console.log("promise");
    });
}

async function run() {
    console.log("start");

    setTimeout(() => console.log("timeout"), 0);

    example();

    process.nextTick(() => console.log("next tick"));

    console.log("end");
}

await run();
// start
// promise constructor ✅ (appears before next tick, because it runs immediately inside the Promise constructor. Unlike Promise.then() (which would defer execution), this runs synchronously)
// end
// next tick
// promise
// timeout
```

[back to top](#table-of-contents) ⬆️
## Math

### python 3

```python
import math

print("abs(-1) ", abs(-1))  # abs(-1)  1
print("max(5, 4) ", max(5, 4))  # max(5, 4)  5
print("min(5, 4) ", min(5, 4))  # min(5, 4)  4
print("pow(2, 2) ", pow(2, 2))  # pow(2, 2)  4
print("ceil(4.5) ", math.ceil(4.5))  # ceil(4.5)  5
print("floor(4.5) ", math.floor(4.5))  # floor(4.5)  4
print("round(4.5) ", round(4.5))  # round(4.5)  4
print("exp(1) ", math.exp(1))  # e**x  # exp(1)  2.718281828459045
print("log(e) ", math.log(math.exp(1)))  # log(e)  1.0
print("log(100) ", math.log(100, 10))  # Base 10 Log  # log(100)  2.0
print("sqrt(100) ", math.sqrt(100))  # sqrt(100)  10.0
print("sin(0) ", math.sin(0))  # sin(0)  0.0
print("cos(0) ", math.cos(0))  # cos(0)  1.0
print("tan(0) ", math.tan(0))  # tan(0)  0.0
print("asin(0) ", math.asin(0))  # asin(0)  0.0
print("acos(0) ", math.acos(0))  # acos(0)  1.5707963267948966
print("atan(0) ", math.atan(0))  # atan(0)  0.0
print("sinh(0) ", math.sinh(0))  # sinh(0)  0.0
print("cosh(0) ", math.cosh(0))  # cosh(0)  1.0
print("tanh(0) ", math.tanh(0))  # tanh(0)  0.0
print("asinh(0) ", math.asinh(0))  # asinh(0)  0.0
print("acosh(pi) ", math.acosh(math.pi))  # acosh(pi)  1.811526272460853
print("atanh(0) ", math.atanh(0))  # atanh(0)  0.0
print("hypot(0) ", math.hypot(10, 10))  # sqrt(x*x + y*y)  # hypot(0)  14.142135623730951
print("radians(0) ", math.radians(0))  # radians(0)  0.0
print("degrees(pi) ", math.degrees(math.pi))  # degrees(pi)  180.0

# infinity value
math.inf

import random
# random integer
random.randint(1, 3)  # any number from 1 to 3
```

### javascript

```javascript
Math.abs(-1); // 1

Math.pow(-4, 2); // 16, same as (-4) ** 2

// random integer from 0 to 9
Math.floor(Math.random() * 10);
// similar to
~~(Math.random() * 10);

// random integer from 0 to 10
Math.floor(Math.random() * 11);

// random integer from 0 to 10
Math.floor(Math.random() * 11);

// random integer from 1 to 10
Math.floor(Math.random() * 10) + 1;
```

[back to top](#table-of-contents) ⬆️
## Date and Time

### python3

```python
from datetime import date, datetime, timedelta
import calendar

# get today's date from the today method from the date class
today = date.today()
print("Today's date is ", today)  # Today's date is  2021-07-16

# print out the date's individual components
print("Date components: ", today.day, today.month,
      today.year)  # Date components:  16 7 2021

# retrieve today's weekday (0=Monday, 6=Sunday)
print("Today's weekday # is: ", today.weekday())  # Today's weekday # is:  4

# get today's date from the datetime class
today = datetime.now()
print("The current date and time is ", today)  # The current date and time is  2021-07-16 18:33:33.510322

# get the current time
t = datetime.time(datetime.now())
print(t)  # 18:34:40.676073

# Times and dates can be formatted using a set of predefined string control codes
now = datetime.now()
# Date formatting
# %y/%Y - year, %a/%A - weekday, %b/%B - month, %d - day of month
print(now.strftime("%a/%A, %d %D %b/%B, %y/%Y"))  # Fri/Friday, 16 07/16/21 Jul/July, 21/2021

# %c - locale's date and time, %x - locale's date, %X - locale's time
print(now.strftime("Locale date and time: %c"))  # Locale date and time: Fri Jul 16 18:47:27 2021
print(now.strftime("Locale date: %x"))  # Locale date: 07/16/21
print(now.strftime("Locale time: %X"))  # Locale time: 18:48:32

# Time formatting
# %I/%H - 12/24 hour, %M - minute, %S - second, %p - locale's AM/PM
print(now.strftime("Current time: %I:%M:%S %p"))  # Current time: 06:58:10 PM
print(now.strftime("24-hour time: %H:%M"))  # 24-hour time: 18:58

# construct a basic timedelta
print(timedelta(days=365, hours=5, minutes=1))  # 365 days, 5:01:00

# today's date
now = datetime.now()
print("today is: ", str(now))  # today is:  2021-07-16 19:05:19.744915

# today's date 1 year from now
print("one year from now it will be: ", str(now + timedelta(days=365)))  # one year from now it will be:  2022-07-16 19:06:45.299792

# create a timedelta that uses more than one argument
print("In 2 days and 3 weeks, it will be ",
      str(now + timedelta(days=2, weeks=3)))  # In 2 days and 3 weeks, it will be  2021-08-08 19:40:39.554060

# calculate the date 1 week ago, formatted as a string
t = datetime.now() - timedelta(weeks=1)
s = t.strftime("%A %B %d, %Y")
print("One week ago it was: ", s)  # One week ago it was:  Friday July 09, 2021

# How many days until April Fools' Day
today = date.today()  # 2021-07-16
afd = date(today.year, 4, 1)  # 2021-04-01
print((today - afd).days)  # 106
afd = afd.replace(year=today.year + 1)  # 2022-04-01

# calculate the amount of time until April Fool's day
time_to_afd = afd - today  # 259

# create a text calendar
# the day (SUNDAY) states the 1st day of the week in the calendar
c = calendar.TextCalendar(calendar.SUNDAY)
st = c.formatmonth(2017, 1, 0, 0)
print(st)
'''
    January 2017
Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29 30 31
'''

# create an HTML formatted calendar
hc = calendar.HTMLCalendar(calendar.SUNDAY)
st = hc.formatmonth(2017, 1)
print(st)  # bunch of html tags

# loop over the days of a month
# 0s mean that the day of the week is in an overlapping month
for i in c.itermonthdays(2017, 8):
    print(i)

# Calendar module provides useful utilities for the given locale
# such as the names of days and months in both full and abbreviated forms
for month_name in calendar.month_name:
    print(month_name)
for day_name in calendar.day_name:
    print(day_name)

# calculate all the first Fridays of every month
for m in range(1, 13):
    cal = calendar.monthcalendar(2018, m)
    weekone = cal[0]
    weektwo = cal[1]
    meetday = weekone[calendar.FRIDAY] if weekone[calendar.FRIDAY] != 0 else weektwo[calendar.FRIDAY]
    print("%10s %2d" % (calendar.month_name[m], meetday))
```

### javascript

[back to top](#table-of-contents) ⬆️
## File System

### python

- Modifying files

```python
# Open a file for writing and create file if it doesn't exist
# file will be rewritten if contents already exists
f = open("textfile", "w+")
for i in range(10):  # write some lines of data to the file
    f.write(f"this is line {str(i)}\r\n")
f.close()  # close file when done


# Open a file and append text to the end
f = open("textfile", "a")
for i in range(10):
    f.write(f"this is line {str(i)}\r\n")
f.close()


# Open and read file
f = open("textfile", "r")
if f.mode == "r":
    contents = f.read()  # reads the entire content
    print(contents)


f = open("textfile", "r")
if f.mode == "r":
    fl = f.readlines()  # reads per line
    for x in fl:
        print(x)
```

- path utilities

```python
import os
from os import path
import datetime
import time


print(os.name)  # get OS name

# check if file exist and file type
print(path.exists("textfile"))  # True
print(path.isfile("textfile"))  # True
print(path.isdir("textfile"))  # False

# get file paths
print(path.realpath("textfile"))  # /path/to/textfile
print(path.split(path.realpath("textfile")))  # ('/path/to', 'textfile')

# get modificaton time
t = time.ctime(path.getmtime("textfile"))  # method 1
print(t)  # Sun Jul 18 00:16:20 2021
t2 = datetime.datetime.fromtimestamp(path.getmtime("textfile"))  # method 2
print(t2)  # 2021-07-18 00:16:20.360159

# calculate how long ago file was modified
td = datetime.datetime.now() - datetime.datetime.fromtimestamp(
    path.getmtime("textfile")
)
print(td)  # 0:19:02.185160
print(td.total_seconds())  # 1142.18516
```

- copy and zip files

```python
import os
from os import path
import shutil
from shutil import make_archive
from zipfile import ZipFile


if path.exists("textfile"):
    src = path.realpath("textfile")  # get path of file in current directory
    dst = src + ".bak"  # create a backup copy by appending "bak"

    shutil.copy(src, dst)  # copy over only the the contents of file
    shutil.copytree(src, dst)  # copy over contents and all other metadata of file

    os.rename("textfile", "newtextfile")

    # zip files
    root_dir, tail = path.split(src)
    shutil.make_archive("archive", "zip", root_dir)  # zip all files in the folder

    with ZipFile("testzip.zip", "w") as newzip:  # zip only selected files
        newzip.write("textfile")
        newzip.write("textfile.bak")
```

### javascript

[back to top](#table-of-contents) ⬆️
## Access modifier

- use to hide the implementation details of a class

### python

### javascript


[back to top](#table-of-contents) ⬆️
## Iterators

### python

### javascript

```javascript
let i = [1, 2];

let iterator = i[Symbol.iterator]();

iterator.next(); // { value: 1, done: false }
iterator.next(); // { value: 2, done: false }
iterator.next(); // { value: undefined, done: true }
```

[back to top](#table-of-contents) ⬆️
## Generators

### python

```python
def generator_example():
    yield 1

x = generator_example():
next(x)  # 1

def infinite_maker():
    i = 0
    while True:
        yield i
        i += 1

x = infinite_maker()
next(x)  # 0
next(x)  # 1

# generator expression
y = (i for i in range(10))
print(next(y))  # 0
print(next(y))  # 1


# send, throw, close method
def generator_ex():
    num = 0
    while True:
        j = yield num
        if j is not None:
            num = j
        num += 1


x = generator_ex()
for i in x:
    print(i)  # prints out the yield result of num
    digits = len(str(i))
    if (i > 100):
        # method 1
        x.throw(ValueError("value is above 100"))
        # method 2
        x.close()  # raises StopIteration, an exception used to signal the end of a finite iterator
    # when a yield result is available, return the new value into the generator (eg.: j takes the new value)
    x.send(10 ** (digits))  # 0 12 102

```

### javascript

```javascript
function* generatorExample1() {
  yield 1;
  yield 2;
}

function* generatorExample2() {
  yield 1;
  yield 2;
}

let iterator1 = generatorExample1();
let iterator2 = generatorExample2();

iterator1.next(); // { value: 1, done: false }
iterator1.next(); // { value: 2, done: false }
iterator1.next(); // { value: undefined, done: true }

iterator2.next(); // { value: 1, done: false }
iterator2.next(); // { value: 2, done: false }
iterator2.next(); // { value: undefined, done: true }

// does not cause stackoverflow for infinite loops
function* infiniteMaker() {
  let i = 0;
  while (true) {
    yield i;
    i++;
  }
}

let iterator3 = infiteMaker();
iterator3.next(); // { value: 0, done: false }
iterator3.next(); // { value: 1, done: false }

// nested generators
function* nestedGenerator() {
  yield* generatorExample1(); // add * after yield to add another generator
  yield 3;
}

let iterator4 = nestedGenerator();
iterator4.next(); // { value: 1, done: false }
iterator4.next(); // { value: 2, done: false }
iterator4.next(); // { value: 3, done: false }
iterator4.next(); // { value: undefined, done: true }

// using return keyword will stop the generator
function* generatorWithReturn() {
  yield 1;
  return "hello"; // done will become true here
  yield 2;
}

let iterator5 = generatorWithReturn();
iterator5.next(); // { value: 1, done: false }
iterator5.next(); // { value: "hello", done: true }
iterator5.next(); // { value: undefined, done: true }
```

[back to top](#table-of-contents) ⬆️
## Fetching Web Data

### python

- fetching a webpage

```python
import urllib.request


response = urllib.request.urlopen("http://www.google.com")
print(response.getcode())  # get response status code

data = response.read()
print(data)  # google html tags
```

- fetching a json from an api

```python
import urllib.request
import json


def print_json(raw_data):
    get_json_data = json.loads(raw_data)  # load string data into a dictionary
    if "title" in get_json_data["metadata"]:
        print(get_json_data["metadata"]["title"])

    count = get_json_data["metadata"]["count"]
    print(count)

    for feature in get_json_data["features"]:
        print(feature["properties"]["place"])


api_url = "https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson"

# open the URL and read the data
response = urllib.request.urlopen(api_url)
status_code = response.getcode()

print(status_code)

if (status_code == 200):
    data = response.read()
    print_json(data)
else:
    print("Error")
```

- manipulate XML

```python
import xml.dom.minidom


doc = xml.dom.minidom.parse("samplexml.xml")  # parse the xml file
print(doc.nodeName)
print(doc.firstChild.tagName)

skills = doc.getElementsByTagName("skill")
print(f"%d skills: {skills.length}")
for skill in skills:
    print(skill.getAttribute("name"))

# create a new XML tag and add it into the document
new_skill = doc.createElement("skill")  # create a new skill tag
new_skill.setAttribute("name", "jQuery")
doc.firstChild.appendChild(new_skill)  # adds to memory but not persisted

skills = doc.getElementsByTagName("skill")
print(f"%d skills: {skills.length}")
for skill in skills:
    print(skill.getAttribute("name"))
```

### Javascript

[back to top](#table-of-contents) ⬆️
## Enum

### python 3

```python
from enum import Enum
```

```python
class Methods(Enum):
  GET = "GET_VALUE"

# get value
print(Method.GET.value)  # "GET_VALUE"
print(Method("GET_VALUE").value)  # "GET_VALUE"

# get key
print(Method.GET.name)  # "GET"
print(Method("GET_VALUE").name)  # "GET"

# check if value exist in Enum
print("GET_VALUE" in Methods._value2member_map_)  # True
print("GET" in Methods._value2member_map_)  # False

# check if name exist in Enum
print("GET_VALUE" in Methods._member_names_)  # False
print("GET" in Methods._member_names_)  # True
```

### Javascript

```javascript
const color = {
  Red: 1,
  Green: 2,
  Blue: 3,
};
```

[back to top](#table-of-contents) ⬆️
## Language Specific

### python

- Shebang line / hashbang
  - it is a common pattern for unix based systems
  - allows a script to be invoked from the command line
  - written on the first line in the python file
  - `#!` marks the shebang

```python
#!/usr/bin/env python3
```

```python
# List comprehension
# original method
arr = []
for i in range(5):
 arr.append(i)
print(arr)  # [0, 1, 2, 3, 4]

# List comprehension method
arr = [i for i in range(5)]
print(arr)  # [0, 1, 2, 3, 4]

# List comprehension with conditional statement
arr = [i for i in range(5) if i < 3]
print(arr)  # [0, 1, 2]

# Tuples (similar to list, but are immutable)
tuple1 = (1, 2, "3")

# Sets (only have unique values)
# create set
set1 = set([1, 2])  # method 1
set2 = {1, 2}  # method 2

# join 2 sets together
set3 = set1 | set2  # {1, 2}

# add element to set
set1.add(3)  # {1, 2, 3}

# add set2 to set1
set1 |= set2  # {1, 2, 3}

# remove element from set from element
set1.discard(2)  # {1, 3}

# Get intersection of 2 sets
set1.intersection(set2)  # {1}

# Get unique value from the 2 sets
set1.symmetric_difference(set2)  # {2, 3}

# Get values from set1 that set2 does not have
set1.difference(set2)  # {3}

# delete all values from set
set1.clear()  # set()

# Create a set that cannot be modified
set_fixed = frozenset([1, 2, 3])
```

```python
# modify global variable from local
var = "from global"

print(var)  # from global

def convert_local_to_global:
    global var  # without the keyword global, cannot modify global variable var locally unlike javascript
    var = "from local"

print(var)  # from local
```

```python
# undefine an existing variable
var = 123

print(var)  # 123

del var

print(var)  # NameError: name 'var' is not defined
```

```python
# find the sum of values that are True in an array
sum([True, False, True])  # 2
```

```python
# convert character to number
ord("a")  # 97

# convert number to character
chr(97)  # a
```

- function annotatins
- `int`, `float`, `bool`, `str`, `bytes`, `None`
- python 3.8 & earlier, `list`, `set`, `dict`, `tuple`
  - `list[int]`, `dict[float, str]`, `Tuple[int, ...]`
- python 3.9+
  - can import types from typing library

```python
from typing import List, Set, Dict, Tuple, Optional, Callable, Iterator, Union, Any, cast, Mapping, MutableMapping, Sequence, Match, AnyStr, IO

isValid: bool = True;

def foo(a:”int”, b:”float”=5.0)  -> ”int”:
    pass


x: Optional[str] = some_function()  # use Optional[] for values that could be None

x: Callable[[int, float], float] = f

# A generator function that yields ints is secretly just a function that
# returns an iterator of ints,
def g(n: int) -> Iterator[int]:
    i = 0
    while i < n:
        yield i
        i += 1

# can also split a function annotation over multiple lines
def send_email(address: Union[str, List[str]],
               sender: str,
               cc: Optional[List[str]],
               bcc: Optional[List[str]],
               subject='',
               body: Optional[List[str]] = None
               ) -> bool:

# An argument can be declared positional-only by giving it a name starting with two underscores:
def quux(__x: int) -> None:
    pass

quux(3)  # Fine
quux(__x=3)  # Error

# To find out what type mypy infers for an expression anywhere in
# your program, wrap it in reveal_type().  Mypy will print an error
# message with the type; remove it again before running the code.
reveal_type(1)  # -> Revealed type is "builtins.int"

# Use Union when something could be one of a few types
x: List[Union[int, str]] = [3, 5, "test", "fun"]

# Use Any if you don't know the type of something or it's too
# dynamic to write a type for
x: Any = mystery_function()

# If you initialize a variable with an empty container or "None"
# you may have to help mypy a bit by providing a type annotation
x: List[str] = []
x: Optional[str] = None

# This makes each positional arg and each keyword arg a "str"
def call(self, *args: str, **kwargs: str) -> str:
    request = make_request(*args, **kwargs)
    return self.do_api_query(request)

# Use a "type: ignore" comment to suppress errors on a given line,
# when your code confuses mypy or runs into an outright bug in mypy.
# Good practice is to comment every "ignore" with a bug link
# (in mypy, typeshed, or your own code) or an explanation of the issue.
x = confusing_function()  # type: ignore  # https://github.com/python/mypy/issues/1167

# "cast" is a helper function that lets you override the inferred
# type of an expression. It's only for mypy -- there's no runtime check.
a = [4]
b = cast(List[int], a)  # Passes fine
c = cast(List[str], a)  # Passes fine (no runtime check)
reveal_type(c)  # -> Revealed type is "builtins.list[builtins.str]"
print(c)  # -> [4]; the object is not cast

# If you want dynamic attributes on your class, have it override "__setattr__"
# or "__getattr__" in a stub or in your source code.
#
# "__setattr__" allows for dynamic assignment to names
# "__getattr__" allows for dynamic access to names
class A:
    # This will allow assignment to any A.x, if x is the same type as "value"
    # (use "value: Any" to allow arbitrary types)
    def __setattr__(self, name: str, value: int) -> None: ...

    # This will allow access to any A.x, if x is compatible with the return type
    def __getattr__(self, name: str) -> int: ...

a.foo = 42  # Works
a.bar = 'Ex-parrot'  # Fails type checking

# Use Iterable for generic iterables (anything usable in "for"),
# and Sequence where a sequence (supporting "len" and "__getitem__") is
# required
def f(ints: Iterable[int]) -> List[str]:
    return [str(x) for x in ints]

f(range(1, 3))

# Mapping describes a dict-like object (with "__getitem__") that we won't
# mutate, and MutableMapping one (with "__setitem__") that we might
def f(my_mapping: Mapping[int, str]) -> List[int]:
    my_mapping[5] = 'maybe'  # if we try this, mypy will throw an error...
    return list(my_mapping.keys())

f({3: 'yes', 4: 'no'})

def f(my_mapping: MutableMapping[int, str]) -> Set[str]:
    my_mapping[5] = 'maybe'  # ...but mypy is OK with this.
    return set(my_mapping.values())

f({3: 'yes', 4: 'no'})

# User-defined classes are valid as types in annotations
x: MyClass = MyClass()

# "typing.Match" describes regex matches from the re module
import re
x: Match[str] = re.match(r'[0-9]+', "15")

# Use IO[] for functions that should accept or return any
# object that comes from an open() call (IO[] does not
# distinguish between reading, writing or other modes)
def get_sys_IO(mode: str = 'w') -> IO[str]:
    if mode == 'w':
        return sys.stdout
    elif mode == 'r':
        return sys.stdin
    else:
        return sys.stdout
```

- Async await

```python
import asyncio

# A coroutine is typed like a normal function
async def countdown35(tag: str, count: int) -> str:
    while count > 0:
        print('T-minus {} ({})'.format(count, tag))
        await asyncio.sleep(0.1)
        count -= 1
    return "Blastoff!"
```

### javascript

- Set

```javascript
// Create a Set
const letters = new Set(["a", "b"]); // or new Set();

// Add Values to the Set
letters.add("c");

// size of set
letters.size; // 3

// check if value exist
letters.has("a"); // true

// delete an element
letters.delete("a");

// loop through a set, keys and values are the same
for (const letter of letters.keys()) {
  // similar to letters.values
  console.log(letter);
}

// loop through a set and get both keys and values
for (const letter of letters.entries()) {
  // similar to letters.values
  console.log(letter); // ["b", "b"]
}

// delete everything in the set
letters.clear();
```

```javascript
// convert character at index 0 to number
"a".charCodeAt(); // 97

// convert character at a specific index to number
"abc".charCodeAt(1); // 98

// convert number to character
String.fromCharCode(97); // "a"
```

- Explicit Binding
  - choose what we want the context of "this" to be by using call, apply or bind
  - by refering to the call, apply, or bind methods, you can determine the value of "this"
  - can only be used on FUNCTIONS

```javascript
/*
NAME OF METHOD  | PARAMETERS                | INVOKE IMMEDIATELY?
    CALL        |   thisArg,a,b,c,...       |       Yes
    APPLY       |   thisArg,[a,b,c,...]     |       Yes
    BIND        |   thisArg,a,b,c,...       |       No

CALL args can be set to anything and can have infinite arguments, function is immediately invoked
APPLY only takes 2 args, the 2nd arg is an array of infinite arguments, function is immediately invoked
BIND can have infinite arguments, and is a method that returns a function definition
*/
var foo = {
  firstName: "Foo",
  say: function() {
    return "Hi " + this.firstName;
  },
  add: function(a, b, c) {
    return this.firstName + " just calculated " + (a + b + c);
  }
}
var bar = {
  firstName: "Bar"
}
// Call: allow this to be referenced to bar instead of foo, all arguments must not be undefined
foo.say() // returns "Hi Foo"
foo.say.call(bar) // returns "Hi Bar"
foo.add.call(bar, 1, 2, 3); // returns "Bar just calculated 6"

// Apply: simlar to Call for the 1st argument, 2nd argument has to be an array of values, all arguments must not be undefined
foo.say.apply(bar) // returns "Hi Bar"
foo.add.apply(bar, [1, 2, 3]); // returns "Bar just calculated 6"

// Bind: returns the function, then requires it to be called
// all agruments need not be defined upfront, but must provide remaining arguments when calling
var say = foo.say.bind(bar);
say(); // returns "Hi Bar"
var add = foo.add.bind(bar, 1, 2);
add(3); // returns "Bar just calculated 6"

// Bind is commonly used when dealing with asynchronous code
var foo = {
  firstName: "Foo",
  say: function() {
    setTimeout(function() {
      console.log("Hi " + this.firstName;
    }.bind(this), 1000);
  }
}
foo.say(); // prints "Hi Foo", if without bind(this), prints "Hi undefined"
```

- Proxy
  - checks for the number of times the field in the object has been accessed
  - each time the field has been accessed, the defined logic will occur

```javascript
const target = {};
const handler = {
  get: function (targetObj, field) {
    if (field === "nextId") {
      // field name must be the same when called
      if (targetObj[field] === undefined) {
        targetObj[field] = 1;
        return targetObj[field];
      }
      targetObj[field]++;
      return targetObj[field];
    }
    return undefined;
  },
};

const proxy = new Proxy(target, handler);
console.log(proxy.nextId); // 1  (field name must be the same as when doing the conditional check)
console.log(proxy.nextId); // 2
console.log(proxy.nextId); // 3
```
[back to top](#table-of-contents) ⬆️