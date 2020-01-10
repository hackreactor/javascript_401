# Part II: Higher-Order Functions

*Note: Before getting started on these exercises, please be certain that you've read through the root [README.md](../README.md) file in this repository.*

In order to complete these exercises, open [repl.it](https://repl.it/), choose JavaScript, and then write your code in the left-hand panel. You can run your code using the "Run" button.

## Exercises

### Basic Requirements

#### Iterating Over Arrays Using `each`

1. Write `each` as seen below in your code editor.

   ```js
   function each(array, func) {
     for (var i = 0; i < array.length; i++) {
       func(array[i]);
     }
   }
   ```

2. Finish the implementation of `sumSquares` below (using above `each` function):

   ```js
   function sumSquares(numbers) {
     var total = 0;
     // ...
     return total;
   }
   ```

3.  Rewrite `sumCubes` using `each`:

    ```js
    function sumCubes(numbers) {
      var total = 0;
      for (var i = 0; i < numbers.length; i++) {
        total = total + cube(numbers[i]);
      }
      return total;
    }
    ```

3.  Write a function called `product` that calculates the product of an array of
    numbers using a `for` loop; then, refactor it to use `each`.

4.  Write a function called `cubeAll` that cubes each number in an array, and
    returns an array of all the numbers *cubed* using a `for` loop; then,
    refactor it to use `each`.

5.  Write a function called `odds` that accepts an array as a parameter and
    returns an array of just the odd numbers.

### More Practice

#### Summations

1.  Write a function `sumByAllElementsMultipliedByFour` that takes an array as an
    argument and returns the sum of all elements multiplied by four.

2.  Observe that `sumByAllElementsMultipliedByFour` is a terrible name for a
    function &#x2013; you should also notice that `sumByAllElementsMultipliedByFour`
    looks a lot like `sumCubes` and `sumSquares`.

    Write a function `sumBy` that accepts two arguments: an array of numbers and
    a *function*. The function will be invoked upon each element in the array,
    and its result will be used to compute the sum.

    ```js
    function sumBy(numbers, f) {
      // ...
    }
    var numbers = [1, 2, 3, 4];
    sumBy(numbers, square); // => 30
    sumBy(numbers, cube); // => 100
    sumBy(numbers, function(number) {
      return number * 4;
    });
    // => 40
    ```

3.  How can you use `sumBy` to compute the sum of an array of
    numbers (just the plain sum)?

4.  Write a function `productBy` that works like `sumBy`, but for **products**.

#### Refactoring

*If you've attended prior lessons:* As an extended exercise, run back through your code from the past lessons and look for opportunities to refactor your use of `for` loops using
`each`, `map` and `filter`.

### Advanced

#### Finding Patterns: Mapping

1.  Write a function `doubleAll` that takes an array of numbers as a parameter
    and returns an array of all of those numbers *doubled*:

    ```js
    function doubleAll(numbers) {
      // ...
    }
    doubleAll([1, 3, 10, 4, 7]); // => [2, 6, 20, 8, 14]
    ```

2.  Write a function `halveAll` that takes an array of numbers as a parameter and
    returns an array of all of those numbers *halved* (divided by two).

3.  Write a function `uppercaseAll` that takes an array of **strings** as a
    parameter, and returns an array of all of those strings, but transformed to
    *upper case*. You can use `toUpperCase` to convert a string to upper case.

    ```js
    "hello, world".toUpperCase(); // => "HELLO, WORLD"
    ```


4.  You should at this point notice a similarity between all of the above
    functions, as well as the `cubeAll` function from the warmup. These functions
    all define what we call **mappings**; that is, they *map* from one value to
    another.

    ```js
    // doubleAll maps from an array of numbers to an array of doubled numbers
    // [1, 2, 3, 4] => [2, 4, 6, 8]

    // halveAll maps from an array of numbers to an array of halved numbers
    // [1, 2, 3, 4] => [0.5, 1, 1.5, 2]
    ```

5.  Write a function `map` that takes two parameters: an array and a *function*
    that, when applied to a single element, produces a new element. `map` should
    return an *array* of all elements in the input array transformed using the
    input function. Your function should work like this:

    ```js
    function map(array, f) {
      // ...
    }
    map([1, 2, 3, 4], function(x) {
      return x * 2;
    });
    // => [2, 4, 6, 8]
    ```

6.  Complete the invocations of `map` below to produce the desired output (you'll
    need to replace `???` with a function):

    ```js
    map(["hello", "world"], ???); // => ["HELLO", "WORLD"]
    map(["HelLo", "WorLD"], ???); // => ["hello", "world"]
    map(["the", "quick", "brown", "fox", "jumped"], ???); // => [3, 5, 5, 3, 6]
    var people = [
      {name: "Alyssa P. Hacker", age: 26},
      {name: "Ben Bitdiddle", age: 34},
      {name: "Eva Lu Ator", age: 19},
      {name: "Lem E. Tweakit", age: 40}
    ];
    map(people, ???); // => ["Alyssa P. Hacker", "Ben Bitdiddle", "Eva Lu Ator", "Lem E. Tweakit"]
    map(people, ???);
    // => ["Alyssa P. Hacker is 26", "Ben Bitdiddle is 34", "Eva Lu Ator is 19", "Lem E. Tweakit is 40"]
    ```

#### Finding Patterns: Filtering

1.  Write a function called `evens` that takes an array of **numbers** as a
    parameter, and returns **an array of only the even numbers** in the parameter.

2.  Write a function called `multiplesOfThree` that takes an array of **numbers** as a
    parameter, and returns an array of only the numbers that are multiples of
    three.

3.  Write a function called `positives` that takes an array of **numbers** as a parameter, and
    returns an array of only the numbers that are positive.

4.  Write a function called `evenLength` that takes an array of **strings** and
    returns an array of only the strings with an even length.

5.  At this point, you should notice a pattern; write a function called `filter`
    that takes two parameters: an array and a **function** that, when invoked with
    an argument, will return `true` or `false`. `filter` should return a *new
    array* of only the elements for which the function returns `true`:

    ```js
    function filter(array, f) {
      // ...
    }
    filter([1, 2, 3, 4], function(x) {
      return x % 2 === 0; // x is even?
    }); // => [2, 4]
    ```

6.  Use `filter` to write/rewrite:
    -   `odds`
    -   `positives`
    -   `negatives`
    -   `evenLength`
    -   `largerThanSix` (given an array of numbers, returns those larger than 6)

7.  Using `filter`, write a function `startsWithChar` that accepts two
    parameters: an array of strings, and a character (*e.g.* "a"), and returns an
    array of only the strings that start with that character:

    ```js
    function startsWithChar(strings, character) {
      // ...
    }
    var words = "the quick brown fox jumps over the lazy dog".split(" ");
    startsWithChar(words, "q"); // => ["quick"]
    startsWithChar(words, "t"); // => ["the", "the"]
    ```
