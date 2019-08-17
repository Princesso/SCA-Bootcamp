# Modern Javascript for React - ES6 and beyond

ES6 Introduces new features and syntax to javascript. A lot of the new syntax reduces the amount of code written.

## Some ES6 features

### Const and Let

Prior to ES6 there was the var keyword for declaring or holding variables.
The problem with the var keyword was that variables declared with var were availabe in to the global scope and therefore there was less control over these vaiables or what and where they are modified.


```
  var cupColor = 'Red'
  function changeCupColor() {
    cupColor = 'Yellow'
  }
  function updateCupColor() {
    cupColor = 'Orange'
  }
  updateCupColor()
  changeCupColor()
  console.log(cupColor)
```
Depending on the function called first, the value of `cupColor` varies

`Let` which is an ES6 feature ensures that variables created with the keyword are block scoped.

The code below would throw an error because the variable `cupColor` is only available in the `changeCupColor` block's scope.

```
 function changeCupColor() {
   let cupColor = 'Yellow'
 }

  console.log(cupColor)
```

`Note: When variables are created without any of the keywords, it is assumed by javascript to have a global scope.`
```
  function changeCupColor() {
   let cupColor = 'Yellow';
    console.log(cupColor);
  }

  function updateCupColor() {
    cupColor = 'Orange'
    console.log(cupColor);
  }

  changeCupColor();
  updateCupColor();

  console.log(cupColor)
```

The const keyword ensure that a variable is not reassigned after it has been created.

```
  const seatNumber = 23;
  seatNumber = seatNumber + 1;
  console.log(seatNumber)
```

### Arrow Functions and Template Strings

Arrow functions make code more readable. Template strings allow for string interpolation. Consider the ES5 code:

```
function printFullName(fname, mname, lname) {
  return "My full name is "+fname+" " + mname+" "+lname
}

printFullName("Oluebube", "Princess", "Egbuna")
```

In ES6 this function can be written as:
```
const printFullName = (fname, mname, lname) =>  "My full name is "+fname+" " + mname+" "+lname

printFullName("Oluebube", "Princess", "Egbuna")
```
For functions with one lines, the return statement can simply be removed. 

ES6 also does the string interpolation neatly. For example instead of using the `+` operator to concatenate strings we can simply use template strings

```
const printFullName = (fname, mname, lname) =>  `My full name is ${fname} ${mname} ${lname}`

printFullName("Oluebube", "Princess", "Egbuna")
```

### Classes

Prior to ES6 there were no classes in javascript. To implement object oriented programming characteristics, one would have to use objects and object prototypes. ES6 introduces the class keyword and better OOP behaviour for javascript.

To create a class, use the class keyword.
```
class House{
  constructor() {
  }
}
```

Using classes we can implement inheritance, encapsulation, and the characteristics of object oriented programming. A few examples of the object oriented properties are shown below.

```

class House {
  constructor(numberOfFloors, color) {
    this.numberOfFloors = numberOfFloors;
    this.color = color;
  }

  changeHouseColor() {
    this.color = 'Blue'
    console.log(this.color)
  }  
}

let House1 = new House(4, 'orange')
House1.changeHouseColor()
```
The code above demnstrates encapsulation.

Also see this:

```
class House {
  constructor(numberOfFloors, color) {
    this.numberOfFloors = numberOfFloors;
    this.color = color;
  }

  changeHouseColor() {
    this.color = 'Blue'
    console.log(this.color)
  }  
}

class Bungalow extends House {

  changeHouseColor() {
    console.log(this.color)
  }  
}

let bungalow = new Bungalow(4, 'orange')
bungalow.changeHouseColor()
```

The code above demonstrates inheritance.
`NB: Inheritance is the property of OOP in which a class can possess the attributes of another class`

### Destructuring

Destructuring enables individual values or a group of values to be unpacked from arrays and objects.

In ES5 to access values of arrays or objects we need to use the index of the element to be accessd or keys in the case of objects.

```
let names = ['Oluebube', 'Princess', 'Egbuna', 'Eucharia', 'Pearl'];

let sistersName = names[4]
let mothersName = names[3]

console.log(sistersName, mothersName);

```

ES6 version

```

let names = ['Oluebube', 'Princess', 'Egbuna', 'Eucharia', 'Pearl'];

let [,,,mothersName,sistersName] = names
console.log(sistersName, mothersName);
```

Unpacking Objects

ES5
```
 let userDetails = getUserDetails();
 let firstname = userDetails.firstName;
 let lastname = userDetails.lastName;

```

ES6

```
let { firstName, lastName } = getUserDetails();
```

### Default Parameters

ES6 adds the ability to give variables passed to functions a fail safe value in the case that they are not provided on function call.

ES5

```
function addNumbers(a, b, c) {
    if (a === undefined)
      a = 10;
    if (b === undefined)
      b = 20;
    if (c === undefined)
      c = 30;
    return a + b + c;
};
addNumbers()
```

ES6

```
function addNumbers (a=10, b=20, c=30) {
  return a+b+c;
}
addNumbers()

```

### Spread Operator

The spread operator allows an iterable type like an array or object to be poured out as individual elements.

To concat amn array in ES5
```
let sisters = [ "Pearl", "Joan"];
let brothers = ["Brian", "Paschal"]
let siblings = sisters.concat(brothers)
```

ES6 version
```
let sisters = [ "Pearl", "Joan"];
let brothers = ["Brian", "Paschal"]
let family = [...sisters, ...brothers, "Mother", "Father"]
console.log(family)
```

### Rest Operator

The rest operator aggregates the remaining or rest of the parameters of a function that is parameterised.

```
function restFunction(a, b, ...c) {
    return (a + b) * c.length
}
restFunction(10, 20, "Oluebube", "Princess", false, 50)
```

### Promises
A Promise object is simply a wrapper around a value that may or may not be
known when the object is instantiated and provides a method for handling
the value after it is known ʈalso known as resolved ʉ or is unavailable for a
failure reason ʈwe'll refer to this as rejected ʉ.
