# 3. State, Event, and Forms: Interactive components

# 3.1 Handling Events the React Way

- Don’t call a function in `onClick` effect.

# 3.2 What is the state?

![Untitled](3%20State,%20Event,%20and%20Forms%20Interactive%20components%2044525dac3720495d8bed1d439012a431/Untitled.png)

- Don’t set and update state manully.

![Untitled](3%20State,%20Event,%20and%20Forms%20Interactive%20components%2044525dac3720495d8bed1d439012a431/Untitled%201.png)

![Untitled](3%20State,%20Event,%20and%20Forms%20Interactive%20components%2044525dac3720495d8bed1d439012a431/Untitled%202.png)

![Untitled](3%20State,%20Event,%20and%20Forms%20Interactive%20components%2044525dac3720495d8bed1d439012a431/Untitled%203.png)

# 3.3 Update state

Use **callback** function to update state.

```jsx
const [isOpen, setIsOpen] = useState(true);
  function handlePrevious() {
    if (step > 1) setStep((s) => s - 1);
  }
```

# 3.4 State guidelines

- Each component has and manages its **own state**, no matter how many times we render the same component.
- If you want to change the way a component looks, or the data it displays, update its state.
This usually happens in an event handler function.
- For data that should not trigger **component re-renders**, **don’t use state**. Use a regular variable instead.

# 3.5 Date Counter

- 尽量减少组件之间传递和变量命名
- 计数器从1开始计数

# 3.6 State VS. Props

![Untitled](3%20State,%20Event,%20and%20Forms%20Interactive%20components%2044525dac3720495d8bed1d439012a431/Untitled%204.png)