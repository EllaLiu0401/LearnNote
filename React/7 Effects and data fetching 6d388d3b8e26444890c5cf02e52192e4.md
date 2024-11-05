# 7. Effects and data fetching

# 7.1 The component lifecycle

![Untitled](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Untitled.png)

# 7.2 First look at effects

**Side effect**: event handler or effect

![Screenshot 2024-07-11 at 4.27.44 PM.png](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Screenshot_2024-07-11_at_4.27.44_PM.png)

# 7.3 The example of useEffect async

```jsx
  useEffect(function () {
  // Write async function inside because useEffect is synchronized
    async function fetchMovies() {
      const res = await fetch(
        `http://www.omdbapi.com/?apikey=${KEY}&s=${query}`
      );
      const data = await res.json();
      setMovies(data.Search);
    }
    // Call the async function
    fetchMovies();
  }, []);
```

# 7.3 The useEffect dependency array

- Each time one of the **dependencies changes**, the effect will be executed **again**.
- Every **state variable** and **prop** used inside the effect **MUST be included** in the dependency array.

![Screenshot 2024-07-11 at 9.17.13 PM.png](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Screenshot_2024-07-11_at_9.17.13_PM.png)

- useEffect is a synchronization mechanism

![Screenshot 2024-07-11 at 9.18.20 PM.png](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Screenshot_2024-07-11_at_9.18.20_PM.png)

![Screenshot 2024-07-11 at 9.19.14 PM.png](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Screenshot_2024-07-11_at_9.19.14_PM.png)

- useEffect executed after browser paint.

![Screenshot 2024-07-11 at 9.19.31 PM.png](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Screenshot_2024-07-11_at_9.19.31_PM.png)

# 7.4 Cleanup function

![Untitled](7%20Effects%20and%20data%20fetching%206d388d3b8e26444890c5cf02e52192e4/Untitled%201.png)

```jsx
useEffect(
    function () {
      if (!title) return;
      document.title = `Movie | ${title}`;
      // cleanup function
      return function () {
        document.title = "usePopcorn";
      };
    },
    [title]
  );
```

# 7.5 Listening to a keypress

Don’t forget to **clear** the addeventlistener

```jsx
useEffect(
    function () {
      function callback(e) {
        if (e.code === "Escape") {
          onCloseMovie();
        }
      }
      document.addEventListener("keydown", callback);
      return function () {
        document.removeEventListener("keydown", callback);
      };
    },
    [onCloseMovie]
  );
```