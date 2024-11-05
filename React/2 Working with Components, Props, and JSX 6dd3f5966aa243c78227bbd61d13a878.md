# 2.  Working with Components, Props, and JSX

# **2.1 Rendering the Root Component and Strict Mode**

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';

function App() {
  return <h1>Hello React</h1>;
}

// Render app in the Dom in React 18
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

# **2.2 Components as building blocks**

- react applications are entirely made out of **components**.
- **Building blocks** of user interfaces in React.
- Piece of UI that has its own **data, logic, and appearances**.
- We build complex UIs by **building multiple components** and **combining** them.
- Components can be **reused, nested** inside each other, and **pass data** between them.

# **2.3 What is JSX?**

- **Declarative** syntax to **describe** what components **look like** and **how they work**.
- Components must **return** a block of JSX.
- Extension of Javascript that allows us to **embed Javascript, CSS amd React components into HTML**.
- Each JSX element is **converted** to a React.createElement function call.
- We could use React **without JSX**.

![Untitled](2%20Working%20with%20Components,%20Props,%20and%20JSX%206dd3f5966aa243c78227bbd61d13a878/Untitled.png)

# **2.4 Passing and Receiving Props**

- the props can be `console.log`
- use js mode(`{}`) to prop numbers

```jsx
function Menu() {
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      <Pizza
        name="Pizza Spinaci"
        ingredients="Tomato, mozarella, spinach, and ricotta cheese"
        photoName="pizzas/spinaci.jpg"
        price={10}
      />
      <Pizza
        name="Pizza Funghi"
        ingredients="Tomato, mushrooms"
        photoName="pizzas/funghi.jpg"
        price={12}
      />
    </main>
  );
}
```

# **2.5 Props, immutability, and one-way data flow**

**Props:**

- Used to pass data from **parent components** to **child components**.
- read-only, **immutable**. Can only be updated by the parent component.

One-way data flow:

![Untitled](2%20Working%20with%20Components,%20Props,%20and%20JSX%206dd3f5966aa243c78227bbd61d13a878/Untitled%201.png)

# **2.6 Rules of JSX**

![Untitled](2%20Working%20with%20Components,%20Props,%20and%20JSX%206dd3f5966aa243c78227bbd61d13a878/Untitled%202.png)

# **2.7 Conditional rendering**

## 2.7.1 **Use `&&`**

- React will not render `true` or `falsy` value.

```jsx
function Menu() {
  const pizzas = pizzaData;
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      {pizzas && (
        <ul className="pizzas">
          {pizzas.map(pizza => (
            <Pizza pizzaObj={pizza} key={pizza.name} />
          ))}
        </ul>
      )}
    )
  }
```

## 2.7.2 **Use Ternaries**

```jsx
function Menu() {
  const pizzas = pizzaData;
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      {pizzas ? (
        <ul className="pizzas">
          {pizzas.map(pizza => (
            <Pizza pizzaObj={pizza} key={pizza.name} />
          ))}
        </ul>
      ) : null}
    </main>
  );
}
```

## **2.7.3 Multiple returns**

```jsx
function Footer() {
  const hour = new Date().getHours();
  const openHour = 12;
  const closeHour = 22;

  const isOpen = hour >= openHour && hour <= closeHour;
  if (!isOpen) return <p>CLOSED</p>;
  return (
    <footer className="footer">
      {isOpen && (
        <div className="order">
          <p>We're open untill {closeHour}:00. Come visit us or order online</p>
          <button className="btn">Order</button>
        </div>
      )}
    </footer>
  );
}
```

# **2.8 Destructuring  Props**

- Use `{}`
- Write parameter on them

```jsx
function Order(closeHour, openHour) {
  return (
    <div className="order">
      <p>
        We're open from {openHour} untill {closeHour}:00. Come visit us or order
        online
      </p>
      <button className="btn">Order</button>
    </div>
  );
}
```

# **2.9 React Fragments**

`<></>`: Group a list of children **without adding extra nodes** to the DOM.

- Difference between `<div>` and `<>`:
    - Use a `<div>` when you need an **actual DOM** element for **styling** or **layout** purposes.
    - Use a React fragment when you want to group components or elements **without adding extra nodes** to the DOM, which can be beneficial for **performance** and cleaner DOM structure.