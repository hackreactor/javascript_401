# Part I: Hoisting (Solutions)

### Two Forms of Functions

```js
// function declaration
function square(x) {
  return x * x;
}

// function expression
var square = function(x) {
  return x * x;
};
```

## Exercises

### Basic Requirements

#### Rewrite Functions

Rewrite the following *function declarations* using a *function expression*:

 ```js
 // 1.
 function cube(x) {
   return x * x * x;
 }

 // 2.
 function fullName(first, last) {
   return first + " " + last;
 }

 // 3.
 function power(base, exp) {
   if (exp === 0) {
     return 1;
   }
   return base * power(base, exp - 1);
 }

 // 4.
 function sumCubes(numbers) {
   var total = 0;
   for (var i = 0; i < numbers.length; i++) {
     total = total + cube(numbers[i]);
   }
   return total;
 }
 ```

**FIXED:**
 ```js
 // 1.
 var cube = function(x) {
   return x * x * x;
 }

 // 2.
 var fullName = function(first, last) {
   return first + " " + last;
 }

 // 3.
 var power = function(base, exp) {
   if (exp === 0) {
     return 1;
   }
   return base * power(base, exp - 1);
 }

 // 4.
 var sumCubes = function(numbers) {
   var total = 0;
   for (var i = 0; i < numbers.length; i++) {
     total = total + cube(numbers[i]);
   }
   return total;
 }
 ```

#### Mechanics of Hoisting

Type out your best answers to the following questions:

1. Why does JavaScript output `undefined` instead of throwing an error in the following code?

  ```js
  console.log(message);

  var message = 'Hi there!';
  ```

  **ANSWER:** JavaScript's engine hoists the variable `message` prior to the `console.log()` invocation. At the time of hoisting, the variable `message` has a value of `undefined` until it is assigned a value of `Hi there!` immediately following the `console.log()` invocation. Since the variable exists at the time `console.log()` is invoked, there is no error message, but the value `undefined` is logged to the console.

2. Why does JavaScript throw an error instead of logging `undefined` in the following code?

    ```js
    console.log(message);

    let message = 'Hi there!';
    ```

    **ANSWER:** JavaScript's ES6 version (released in 2015) came with two new keywords for declaring variables, `let` and `const`. These keywords can be leveraged in JavaScript for numerous purposes. One motivation for using `let` over `var` is that JavaScript will disallow a premature reference to a variable declared using `let`. In the above code, JavaScript's engine will throw an error instead of yielding `undefined` (as was demonstrated by the previous code in this section).

3. Explain precisely what happens when the following code is executed.

    ```js
    console.log(showMessage());

    var showMessage = function(){
      return 'Hi there!';
    };
    ```
    **ANSWER:** JavaScript's engine will throw an error yielding that `showMessage` is not a function. This is a result of the hoisting of `showMessage`, which, at the time of its attempted invocation, maintains a value of `undefined`. JavaScript's engine doesn't recognize `undefined` as a function, and throws an error accordingly.


4. Why does JavaScript *not* throw any errors when the following code is executed?

  ```js
  console.log(showMessage());

  function showMessage(){
    return 'Hi there!';
  }
  ```

  **ANSWER:** JavaScript's engine hoists function declarations differently than it does variables. Variables are hoisted but their respective values aren't assigned until the interpreter reaches the line of code where the variable was defined at author-time. Function declarations behave similarly but also hoist the associated function value. This renders function declarations usable on the first line of code in any JavaScript program, irrespective of where it is defined at author-time.

#### Code Restructuring

Restructure the following instances of code to work correctly:

 ```js
 // 1.
 for(var i = 0; i < values.length; i++){
   console.log(values[i]);
 }

 var values = [10, 20, 30];
 ```

 **FIXED:**
 ```js
 // 1.
 var values = [10, 20, 30];

 for(var i = 0; i < values.length; i++){
   console.log(values[i]);
 }
 ```

 ```js
 // 2.
 console.log(welcome('Charlie', 'Munger'));

 function welcome(first, last) {
   return `Welcome, ${first} ${last}! You last logged in on ${lastLogin}.`
 };

 var lastLogin = '1/1/1970';
 ```

 **FIXED:**
 ```js
 // 2.
 var lastLogin = '1/1/1970';

 console.log(welcome('Charlie', 'Munger'));

 function welcome(first, last) {
   return `Welcome, ${first} ${last}! You last logged in on ${lastLogin}.`
 };
 ```
