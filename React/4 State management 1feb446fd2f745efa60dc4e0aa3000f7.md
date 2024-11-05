# 4. State management

# 4.1 Thinking react process

![Untitled](4%20State%20management%201feb446fd2f745efa60dc4e0aa3000f7/Untitled.png)

![Untitled](4%20State%20management%201feb446fd2f745efa60dc4e0aa3000f7/Untitled%201.png)

# 4.2 Local state vs global state

![Untitled](4%20State%20management%201feb446fd2f745efa60dc4e0aa3000f7/Untitled%202.png)

# 4.3 State: when and where?

![Untitled](4%20State%20management%201feb446fd2f745efa60dc4e0aa3000f7/Untitled%203.png)

# **4.5 Event Object and Parameter Passing**

- **Event Object**: In an event handler function, when an event (such as click or submit) occurs, the browser **automatically passes an event object** to the handler. This is the standard behavior of DOM events.
- **Parameter Passing**: When you need to pass custom parameters to the event handler function, you must use an arrow function or another method to ensure that the **parameters are passed** when the event occurs, not immediately during rendering.
    
    `<button *onClick***=**{() **=>** onDeleteItem(item**.***id*)}>❌</button>`
    

# **4.6 Derived state**

- state that is computed from an **existing** piece of **state** or from **props**
- Just use regular variables, no useState.
- Works because **re-rendering** component will **automatically re-calculated** derive state.

![Untitled](4%20State%20management%201feb446fd2f745efa60dc4e0aa3000f7/Untitled%204.png)

# **4.7 The Children prop**

- The children prop allow us to **pass JSX into an element** (beside regular props)
- Essential tool to make **reusable** and **configurable** components (especially component content)
- Really useful for **generic** components that **don’t know their content** before being used.(e.g. modal)

![Untitled](4%20State%20management%201feb446fd2f745efa60dc4e0aa3000f7/Untitled%205.png)