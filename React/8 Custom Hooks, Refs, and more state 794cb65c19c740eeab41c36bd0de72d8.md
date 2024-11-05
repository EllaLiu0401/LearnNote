# 8. Custom Hooks, Refs, and more state

# 8.1 React hooks

- Creating and accessing **state** from Fiber tree
- Registering **side effects** in Fiber tree.
- Manual DOM selections

**Rules of hooks:**

- Only call hooks at the **top level**.
- Only call hooks from **React functions**.

# 8.2 useState

## 8.2.1 Creating state

- **Simple:**
    
    ![Screenshot 2024-08-07 at 10.59.50 PM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-07_at_10.59.50_PM.png)
    
- **Based on function (lazy evaluation):**
    - pure function
    - no arguments
    - called only on initial render
    
    ![Screenshot 2024-08-07 at 11.01.12 PM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-07_at_11.01.12_PM.png)
    

## 8.2.2 Updating state

Make sure to **NOT mutate** objects or arrays, but to **replace** them.

- **Simple:**
    
    ![Screenshot 2024-08-07 at 11.01.49 PM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-07_at_11.01.49_PM.png)
    
- **Based on current state:**
    
    ![Screenshot 2024-08-07 at 11.02.21 PM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-07_at_11.02.21_PM.png)
    

# 8.3 useRef

![Screenshot 2024-08-09 at 9.46.58 PM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-09_at_9.46.58_PM.png)

![Screenshot 2024-08-09 at 9.47.09 PM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-09_at_9.47.09_PM.png)

# 8.4 ways to use ref

## 8.4.1 select DOM elements

**useRef to set input focus**

```jsx
function Search({ query, setQuery }) {
  const inputEl = useRef(null);
  useEffect(
    function () {
      function callback(e) {
        if (document.activeElement === inputEl.current) return;
        if (e.code === "Enter") {
          inputEl.current.focus();
          setQuery("");
        }
      }
      document.addEventListener("keydown", callback);
      return () => document.addEventListener("keydown", callback);
    },
    [setQuery]
  );
  return (
    <input
      className="search"
      type="text"
      placeholder="Search movies..."
      value={query}
      onChange={(e) => setQuery(e.target.value)}
      ref={inputEl}
    />
  );
}
```

## 8.4.2 Persist data between renders without re-rendering

# 8.5 Custom Hooks

![Screenshot 2024-08-20 at 12.07.38 AM.png](8%20Custom%20Hooks,%20Refs,%20and%20more%20state%20794cb65c19c740eeab41c36bd0de72d8/Screenshot_2024-08-20_at_12.07.38_AM.png)