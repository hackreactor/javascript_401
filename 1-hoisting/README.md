# Part I: Hoisting

*Note: Before getting started on these exercises, please be certain that you've read through the root [README.md](../README.md) file in this repository.*

In order to complete these exercises, open [repl.it](https://repl.it/), choose JavaScript, and then write your code in the left-hand panel. You can run your code using the "Run" button.

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
#### Mechanics of Hoisting

Type out your best answers to the following questions:

1. Why does JavaScript output `undefined` instead of throwing an error in the following code?

  ```js
  console.log(message);
 // because the declaration of the varuble is after the console log so message of console log is undefind
 //When declering a var the output is undefind 
  var message = 'Hi there!';
  ```

2. Why does JavaScript throw an error instead of logging `undefined` in the following code?

    ```js
    console.log(message);
      // because has already been declared and let value is usssed only once
    let message = 'Hi there!';
    ```

3. Explain precisely what happens when the following code is executed.

    ```js
    console.log(showMessage());
//It will be an error because the code will be read frm the top and the consol will stop at the first line because showMessage is not a function yeet
    var showMessage = function(){
      return 'Hi there!';
    };
    ```

4. Why does JavaScript *not* throw any errors when the following code is executed?

  ```js
  console.log(showMessage());
// because the function has allredy been declaired and it is stored
  function showMessage(){
    return 'Hi there!';
  }
  ```

#### Code Restructuring

Restructure the following instances of code to work correctly:

 ```js
 // 1.
 function getValues(values){
  var array=[]
 for(var i = 0; i < values.length; i++){
   array.push(values[i]);
 }
    return array;
}

 var values = [10, 20, 30];
 ```
 ```js
 // 2.
 console.log(welcome('Charlie', 'Munger'));

 function welcome(first, last) {
   var welc= `Welcome, ${first} ${last}! You last logged in on ${lastLogin}.`;
   return welc
 };

 var lastLogin = '1/1/1970';
 ```
