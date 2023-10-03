# Diving Deep into Functions

## Function Statement aka Function Declaration

```
function a(){
    console.log("a Called")
}
```

- The function statement declares a function. A declared function is "saved for later use", and will be executed later, when it is invoked (called).

- In JavaScript, functions are objects, and they have both properties and methods.

- Function Statements can be hoisted.

## Function Expression

```
var b = function () {
    console.log("b Called")
}
```

- The function keyword can be used to define a function inside an expression. 

- A function expression is very similar to, and has almost the same syntax as, a function declaration. The main difference between a function expression and a function declaration is the function name, which can be omitted in function expressions to create anonymous functions.

- Function expressions in JavaScript are not hoisted.

## Anonymous Function

```
function () {

}
```

Anonymous functions don't have any identity. So the above code is a sysntaxError because `A function statement requires a name`.

So Anonymous functions are used in places where funcitons are used as values.

```
var b = function () {
    console.log("b Called")
}
```

The above code demonstrates an anonymous function.

## Named Function Expression

It is similar to Anonymous function but with a name.

```
var b = function xyz() {
    console.log("b Called")
}
```

The above code is completely valid. The only thing is that we can call the b variable as a function but if we call xyz() then we will get a reference error that xyz is not defined. This is because the scope of xyz is local and not global so we can call it only inside b function.

## Difference between Parameters & Arguments

While creating a functions whatever we take as input in the function declaration are called Parameters. 

Whereas, the arguments that we pass while calling the function are called Arguments.

## First Class Functions

Functions can be assigned to any other variable or passed as an argument or can be returned by another function. JavaScript treat function as a first-class-citizens. This means that functions are simply a value and are just another type of object.

```
var b = function () {
    return function xyz() {

    }
}

console.log(b())
```

If we run the above code, we will get the xyz function as the output. This ability of a function to be passed as an argument or be returned from a function is known as First Class Function/Citizen.