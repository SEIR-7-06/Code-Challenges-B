# Square Every Digit

[REPL](https://repl.it/@michaelpetty/SquareEveryDigit)

Welcome. In this problem, you are asked to square every digit of a number.

For example, if we run 9119 through the function, 811181 will come out, because 9^2 is 81 and 1^2 is 1.

Note: The function accepts an integer and returns an integer

<hr>

## Solution
<details>
<summary>Click here to reveal a possible solution.</summary>
<p>

```javascript
// SOLUTION 1
function squareEveryNumber(number) {
  // Convert number into an array of digits
  const digits = number.toString().split('');

  let result = '';
  // Loop through each digit
  digits.forEach((digit) => {
    // get the square of each digit
    const square = parseInt(digit) ** 2;
    // add square to end of string
    result += square.toString();
  });

  return result;
}

// SOLUTION 2
function squareEveryNumber(number) {
  // Convert number into an array of digits
  const digits = number.toString().split('');

  // Get an array of squares as strings
  const squares = digits.map((digit) => {
    const square = parseInt(digit) ** 2;
    return square.toString();
  });

  // Join all the square strings together
  return squares.join('');
}

// SOLUTION 3
function squareDigits(num){
    var string = num.toString();
    var results = [];
    for (var i = 0; i < string.length; i++){
        results[i] = string[i] * string[i];
    }
    return Number(results.join(''));
};


// SOLUTION 4
function squareDigits(num){
  return num.toString().split('').map(i => i * i).join('');
}
```
</p>
</details>

<hr>

# Regex PIN Validator

[REPL](https://repl.it/@michaelpetty/RegexPINValidator#index.js)

ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.

If the function is passed a valid PIN string, return true, else return false.

eg:
```javascript
validatePIN("1234") === true
validatePIN("12345") === false
validatePIN("a234") === false
```

<hr>

## Solution
<details>
<summary>Click here to reveal a possible solution.</summary>
<p>
  
  ```javascript
  // a solution, but nothing special 
  function validatePIN(pin) {
    //return true or false
    var n = pin.length;
    if( n != 4 && n != 6)
        return false;
    for (var i in pin)
        if (pin[i] > '9' || pin[i] < '0')
            return false;
    return true;
  }
  
  // good solution
  function validatePIN(pin) {

    var pinlen = pin.length;
    var isCorrectLength = (pinlen == 4 || pinlen == 6);
    var hasOnlyNumbers = pin.match(/^\d+$/);

    if(isCorrectLength && hasOnlyNumbers){
      return true;
    }

    return false;

  }
  
  // cleanest solution
  function validatePIN(pin) {
    return /^(\d{4}|\d{6})$/.test(pin)
  }
  ```
</p>
</details>

<hr>

# Growth of a Small Town

[REPL](https://repl.it/@michaelpetty/GrowthSmallTown#index.js)

In a small town the population is 1000 at the beginning of a year (p0). The population regularly increases by 2 percent per year and in addition to that, 50 new inhabitants per year come to live in the town. How many years will it take for the town to see its population greater or equal to 1200 inhabitants?

```
At the end of the first year there will be: 
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be: 
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (number of inhabitants is an integer)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years.
```

<!-- More generally given parameters: -->

<!-- `p0`, `percent`, `aug` (inhabitants coming or leaving each year), `p` (population to surpass)

The function `nb_year` should return n number of entire years needed to get a population greater or equal to `p`.

`aug` is an integer, `percent` a positive or null number, `p0` and `p` are positive integers (`> 0`) -->

Write a function that takes in the starting population, the rate of population growth, the number of new inhabitants, and the population limit. The function should return the number of years it will take to reach or surpass the population limit.

Examples:
```javascript
calcYears(startingPop, growthRate, newcomers, limit) {
  // Calculate years here
}

calcYears(1500, 5, 100, 5000) -> 15
calcYears(1500000, 2.5, 10000, 2000000) -> 10
```

Note: Don't forget to convert the `percent` parameter as a percentage in the body of your function: if the parameter `percent` is `2` you have to convert it to `0.02`.

<hr>

## Solution
<details>
<summary>Click here to see the solution</summary>
<p>
  
  ```javascript
  // good and readable solution
  function calcYears(startingPop, growthRate, newComers, limit) {
    let population = startingPop;
    let year = 0;

    // Increment the population and the year while the population is under
    // the limit.
    while (population <= limit) {
      population = population + (population * growthRate / 100) + newComers;
      year++;
    }

    return year;
  }
  
  // nice use of recursion
  function calcYears(p0, percent, aug, p) {
      // your code
      if (p0 >= p) {
        return 0;
      }

      return 1 + calcYears(p0 + p0 * percent / 100 + aug, percent, aug, p);
  }
  
  // clever, but not best practice
  function calcYears(p0, percent, aug, p, years = 0) {
    return p0 < p ? calcYears(p0 + p0 * percent / 100 + aug, percent, aug, p, years + 1) : years; 
  }
  ```
</p>
</details>
