# 6. How React works behind the scenes

# 6.1 Components, instances, and elements.

## Component:

- Description of a piece of UI.
- A component is a **function** that returns **React elements**(element tree), usually written as JSX

## Component Instance:

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled.png)

## React Element:

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%201.png)

# 6.2 How components are **displayed** on the screen

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%202.png)

In React, rendering is **NOT** updating the DOM or display elements on the screen. Rendering on happens **internally** inside React, it does not **produce visual changes**.

# 6.3 Render is triggered

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%203.png)

The render process is triggered for the **entire** application.

# 6.4 Render Phase

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%204.png)

## Virtual DOM:

Tree of all React elements created from all **instances** in the component tree.

Rendering a component will **cause all of its child components to be rendered as well** (no matter if props changed or not) → Necessary because React doesn’t know whether children will be affected.

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%205.png)

## Reconciliation:

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%206.png)

## Fiber:

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%207.png)

Looks like **linked list**

## Reconciliation in action:

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%208.png)

# 6.5 Commit phase

- **React writes to the DOM**: insertions, deletions, and updates (list of DOM updates are ‘flushed’ to the DOM)
- **Committing is synchronous**: DOM is updated in one go, it can’t be interrupted.
- After the commit phase completes, the `workInProgress` fiber tree becomes the current tree **for the next render cycle**.

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%209.png)

# 6.6 Recap

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2010.png)

# 6.7 How diffing works

Diffing uses 2 fundamental assumptions(rules):

- Two elements of different types will **produce different trees**.
- Elements with a stable key prop **stay the same across renders**.

[https://whimsical.com/diffing-4Gq8SSM4VqqVRt6NmDVtD8](https://whimsical.com/diffing-4Gq8SSM4VqqVRt6NmDVtD8)

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2011.png)

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2012.png)

# 6.8 The key prop

- Special prop that we use to tell the **diffing algorithm** that an element is **unique**.
- All React to **distinguish** between multiple instances of the same component type.

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2013.png)

![Screenshot 2024-07-10 at 1.21.38 AM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_1.21.38_AM.png)

![Screenshot 2024-07-10 at 1.22.04 AM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_1.22.04_AM.png)

# 6.9 Rules for render logic: pure components

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2014.png)

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2015.png)

## Refresher:

- **Side effect**: Dependency on or modification of any **data outside** the **function scope**.
    - Example: mutating external variables, HTTP requests, wring to DOM.
    
    ![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2016.png)
    
- **Pure function**: a function that has no side effect.
    - Does **not** change any variables outside its scope.
    - Given the **same input**, a pure function always returns the **same output**.

![Untitled](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Untitled%2017.png)

# 6.10 State update batching

Renders are not triggered immediately, but scheduled for when the JS engine has some “free time”. There is also batching of multiple `setState` calls in event handlers.

![Screenshot 2024-07-10 at 5.01.06 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_5.01.06_PM.png)

![Screenshot 2024-07-10 at 5.01.34 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_5.01.34_PM.png)

![Screenshot 2024-07-10 at 5.02.04 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_5.02.04_PM.png)

# 6.11 How events work in react

![Screenshot 2024-07-10 at 5.29.49 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_5.29.49_PM.png)

![Screenshot 2024-07-10 at 5.30.01 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_5.30.01_PM.png)

![Screenshot 2024-07-10 at 5.30.12 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_5.30.12_PM.png)

# 6.12 The React ecosystem

![Screenshot 2024-07-10 at 11.59.24 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_11.59.24_PM.png)

![Screenshot 2024-07-10 at 11.59.35 PM.png](6%20How%20React%20works%20behind%20the%20scenes%208be88b2f3cbe4f9a92439a9e6d031e7c/Screenshot_2024-07-10_at_11.59.35_PM.png)

[https://whimsical.com/behind-the-scene-VCGXH17s6RcdEQhDXij33U@8ADn3nfZACaQkdsAofZEzMxLsY17SqLKGcgv](https://whimsical.com/behind-the-scene-VCGXH17s6RcdEQhDXij33U@8ADn3nfZACaQkdsAofZEzMxLsY17SqLKGcgv)