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