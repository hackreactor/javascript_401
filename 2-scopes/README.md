# Part II: Scopes

*Note: Before getting started on these exercises, please be certain that you've read through the root [README.md](../README.md) file in this repository.*

To complete these exercises, you will need to download this repo and open this particular folder in a code editor.

# How to complete these exercises

#### It is your mission to go through the function.js file and change all the `'???'` in such a way that all the tests pass true.

### Let's get started...

Run the specrunner.html file in a web browser. This document will immediately show one passed test and a series of failing tests.

The **functions.js** file holds all the failing tests that are being displayed in **SpecRunner.html**. You will be editing the **functions.js** file and refreshing the **SpecRunner.html** to check your progress on making the tests pass. This is a regular JavaScript file, so note that you can use `console.log` to help debug and inspect these functions.

A test block starts with an `it` function. The `it` function takes two arguments. The first one is a statement describing the rule addressed by the test. The second is a function that will either evaluate to true or false using the `expect` function. The expect statement (`expect(ACTUAL === 'inner').to.be.true;`) will evaluate if the statement between the parens `ACTUAL === 'inner'` is true. You can almost read it like plain English. The expect statement below "expects that the variable ACTUAL equals the value 'inner' to be true".

#### Failing Test Example

      it('a function has access to its own local scope variables',

      function () {
        var fn = function () {
          var name = 'inner';
          ACTUAL = name;
        };
        fn();
        expect(ACTUAL === '???').to.be.true;
        //change '???' to what ACTUAL evaluates to.
      });

#### Passing Test Example

      it('a function has access to its own local scope variables',

      function () {
        var fn = function () {
          var name = 'inner';
          ACTUAL = name;
        };
        fn();
        expect(ACTUAL === 'inner').to.be.true;
        //changed '???' to 'inner'
        //(because we assigned ACTUAL, a global variable to name inside fn)
      });

### Don't forget..

You should thoroughly read all of code in front of you and aim to understand line-by-line what is happening.
