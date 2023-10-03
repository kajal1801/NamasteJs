# Callbacks

```
function x(){
    console.log("x")
}

x(function y(){
    console.log("y")
})
```

In the above example, y is the callback function. We can consider this as we are giving the responsibility to call y on x and now it's called back later by x in the code.

## What is a Callback Function in Javascript?

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```
setTimeout(function () {
    console.log("Timer")
}, 5000)

function x(){
    console.log("x")
    y()
}

x(function y(){
    console.log("y")
})
```

setTimeout will store the function in a space and wait for 5sec before executing it. But by then Javascript will move on to execute other lines in the code as it never waits for anyone.

As we call x, it will do a console.log of x and then we call y inside x and y will be executed. After all this, as soon as 5 sec is passed the setTimeout function is executed.


> Javascript is a single synchronous and single-threaded language but using callback funcitons we can perform asynchronous operaitons.

## Blocking the main thread

Everything in Javascript is executed through CallStack so if any execution blocks this callstack that is known as blocking the main thread.

## Power of Callbacks?

Callbacks make sure that a function is not going to run before a task is completed but will run right after the task has completed. It makes our code asynchronous and saves us from errors and bugs.

If we are executing a code which takes 20-30 secs then the main thread is blocked and nothing else is executed for that period.

If Javascript did not have this first class function / ability to pass functions then we wouldn't have been able to implement asynchronous operations.

# Pre-Event Loop Part

## Deep about Event Listeners

```
document.getElementById('clickMe').addEventListener("click", function xyz(){
    console.log("Button Clicked")
})
```

The piece of code means, when Javascript executes this line, it will pick up the button "clickMe" and it will add the eventlistener `click` and call the callback function. and it automatically comes inside our callstack.

## Closures Demo with Event Listeners [IMP for Interviews]

Suppose we have to count the number of times a button is clicked. In that case, using a global variable won't be a good option.

So here, we'll use closure for data hiding and to count the number of clicks.

```
function attachEventListener(){
    let count = 0
    document.getElementById('clickMe').addEventListener("click", function xyz(){
        console.log("Button Clicked", ++count)
    })
}
```

The callback functions forms a closure with it's outer scope and it basically kind of remembers where this count is present. So we won't have any issues calculating the clicks. The xyz functions has access to the count variable due to it's lexical environment.

In the EventListener tab near console, we can see that there is a handler that stores the anonymous function that defines what will happen if the button is clicked.

## Garbage Collection & removeEventListeners

EventListeners are heavy so whenever we attach an EventListener, it stays there and the memory is never empty even if we haven't done anything. And if we have many callbacks and clicks and event listeners in our program then our application will become very heavy.

So, the good practice is to free up the memory which was held by closure(garbage collection).