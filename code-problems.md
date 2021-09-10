## shortLongShort

Write a function that takes in 2 strings and returns a string of the form short+long+short. with the shorter string on the outside and the longer string on the inside. The strings will not be the same length, but they may be empty ( zero length ).

For example
```js
function shortLongShort(string1, string2) {
  // write code here
}
```

```js
shortLongShort('boom', 'chick');
// => 'boomchickboom'

shortLongShort('vis', 'a')
// => 'avisa'
```

<details>
  <summary>Solution</summary>

  ```js
  function solution(string1, string2) {
    let longer = '';
    let shorter = '';

    if (string1.length > string2.length) {
      longer = string1;
      shorter = string2;
    } else {
      longer = string2;
      shorter = string1;
    }

    return `${shorter}${longer}${shorter}`;
  }
  ```
</details>

### Hungry for More

Have your function throw an error if the strings are the same length.

<hr>

## findIfInLove

Timmy & Sarah think they are in love, but around where they live, they will only know once they pick a flower each. If one of the flowers has an even number of petals and the other has an odd number of petals it means they are in love.

Write a function that will take the number of petals of each flower and return true if they are in love and false if they aren't.

For Example
```js
function findIfInLove(flower1, flower2) {
  // write code here
}
```

```js
findIfInLove(4, 5);
// => true

findIfInLove(8, 10);
// => false
```

<details>
  <summary>Solutions</summary>

  ```js
  function findIfInLove(flower1, flower2) {
    const flowerOneIsEven = flower1 % 2 === 0;
    const flowerTwoIsEven = flower2 % 2 === 0;

    if (flowerOneIsEven && !flowerTwoIsEven) {
      return true;
    } else if (!flowerOneIsEven && flowerTwoIsEven) {
      return true;
    } else {
      return false;
    }
  }
  ```

  ```js
  function findIfInLove(flower1, flower2) {
    const flowerOneIsEven = flower1 % 2 === 0;
    const flowerTwoIsEven = flower2 % 2 === 0;

    if (
      (flowerOneIsEven && !flowerTwoIsEven)
      || (!flowerOneIsEven && flowerTwoIsEven)
    ) {
      return true;
    }

    return false;
  }
  ```
</details>

### Hungry for More

Have your function throw an error if either of the inputs is not an integer number.

<hr>

## SmallestInt

<!-- [REPL](https://repl.it/@michaelpetty/smallestInt) -->

Given an array of integers your solution should find the smallest integer.

For example:
```
Given [34, 15, 88, 2] your solution will return 2
Given [34, -345, -1, 100] your solution will return -345
```

You can assume, for the purpose of this problem, that the supplied array will not be empty.

```javascript
function findSmallestInt(args) {
  // Happy coding!  
}
```

<hr>

## Solution

<details>
  <summary>Click here to reveal a possible solution.</summary>
  <p>

```javascript
// SOLUTION 1
function findSmallestInt(arrayOfNums) {

  // start with smallest being first number in array
  let smallestInt = arrayOfNums[0];

  // Loop through array of numbers
  for (let i = 0; i < arrayOfNums.length; i++) {
    if (arrayOfNums[i] < smallestInt) {
      smallestInt = arrayOfNums[i];
    }
  }

  return smallestInt;
}


///////////////////////////////////////////////////////
// SOLUTION 2
function findSmallestInt(array) {
  let smallestInt = null;

  // Loop through array
  array.forEach((int) => {
    if (smallestInt === null) {
      smallestInt = int;
    } else {
      // if number is smallest so far make it new smallest number
      if (int < smallestInt) {
        smallestInt = int;
      }
    }
  });
  // return the smallest number
  return smallestInt;
}

///////////////////////////////////////////////////////
// SOLUTION 3
function findSmallestInt(array) {
  return array.reduce((smallest, int) => {
    return int < smallest ? int : smallest;
  }, Infinity);
}

///////////////////////////////////////////////////////
// SOLUTION 4
function findSmallestInt(array) {
  return Math.min(...array);
}
```

</p>
</details>

<hr>

## Square Every Digit

<!-- [REPL](https://repl.it/@michaelpetty/SquareEveryDigit) -->

Write a function that takes in an integer number and squares every digit of integer. It should return a new integer of all the square numbers. Notice the function accepts an integer and returns an integer. You will have to think about how to get each digit individually.

For example
```js
function squareEveryDigit(digits) {
  // write code here
}
```

```js
squareEveryDigit(323);
// => 949

squareEveryDigit(9229);
// => 814481
```


<hr>

## Solution
<details>
<summary>Click here to reveal a possible solution.</summary>
<p>

```javascript
// SOLUTION 1 - Using a for loop
function squareEveryNumber(number) {
  // Convert number into an array of digits
  const digits = number.toString().split('');

  let result = '';
  // Loop through each digit
  for (let i = 0; i < digits.length; i++) {
    const square = parseInt(digits[i]) ** 2;

    result += square.toString();
  }

  return Number(result);
}



/////////////////////////////////////////////////////////
// SOLUTION 2 - using forEach
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

  return Number(result);
}


/////////////////////////////////////////////////////////
// SOLUTION 2 - Using map
function squareEveryNumber(number) {
  // Convert number into an array of digits
  const digits = number.toString().split('');

  // Get an array of squares as strings
  const squares = digits.map((digit) => {
    const square = parseInt(digit) ** 2;
    return square.toString();
  });

  // Join all the square strings together
  const resultString = squares.join('');

  return Number(resultString);
}

/////////////////////////////////////////////////////////
// SOLUTION 3
function squareDigits(num){
    var string = num.toString();
    var results = [];
    for (var i = 0; i < string.length; i++){
        results[i] = string[i] * string[i];
    }
    return Number(results.join(''));
};


/////////////////////////////////////////////////////////
// SOLUTION 4
function squareDigits(num){
  return Number(num.toString().split('').map(i => i * i).join(''));
}
```
</p>
</details>

<hr>


## Growth of a Small Town

<!-- [REPL](https://repl.it/@michaelpetty/GrowthSmallTown#index.js) -->

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
