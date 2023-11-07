# Event Loop

## Web APIs

These are some functions that we think are a part of Javascript but instead they are a part of the Browser.

- setTimeout()
- DOM APIs
- fetch()
- localStorage
- console
- location `[url]`
- many more...

Browsers give JS the ability to use these functions using the keyword window.

For example, `window.localStorage` / `window.console`.

## What is Callback Queue?

The Callback queue is a data structure that operates on the FIFO (first-in-first-out) principle. Callback functions that need to be asynchronously executed, are pushed onto the callback queue.

These are later pushed to the Call stack to be executed (when the event loop finds an empty call stack).

## What is an Event Loop?

An event loop is an endless loop, which waits for tasks, executes them, and then sleeps until it receives more tasks. It executes tasks from the event queue only when the call stack is empty i.e. there is no ongoing task.
The event loop allows us to use callbacks and promises.

## Need for Callback Queue / Task Queue

Suppose user clicks on a button several times and the allback function enters the queue several times and all the functions are waiting to be executed and the Event loop will check if the call stack is empty or not. Then it executes all the functions one by one. This is the reason we need callback queue because we have only one call stack and we need all the callback functions be executed at some point.

## What is a Micro Task Queue?

This queue is similar to Callback queue but it has higher priority. API calls goes inside the micro task queue. The Event Loop checks this queue before the callback queue and executes the functions in this queue, if any. Then it moves on to callback queue.

All callbackk functions whch come through Promises will go inside this Micro Task Queue. Also, the `MutationObserver` (interface that provides the ability to watch for changes being made to the DOM tree) can also be put in the Micro Task Queue.

Suppose the 2nd task in the microtask queue creates another microtask and that microtask creates another microtask, then the task in the callback function will end up in starvation.