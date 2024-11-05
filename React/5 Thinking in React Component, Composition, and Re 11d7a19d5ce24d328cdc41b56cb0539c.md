# 5.  Thinking in React: Component, Composition, and Reusability

# 5.1 How to split a UI into components?

## The 4 criteria for splitting a UI into components:

1. Logical separation of content/layout
2. Reusability
3. Responsibility / complexity
4. Personal coding style

![Untitled](5%20Thinking%20in%20React%20Component,%20Composition,%20and%20Re%2011d7a19d5ce24d328cdc41b56cb0539c/Untitled.png)

## More guidelines:

- Be aware that creating a new component creates a **new abstraction**. Abstractions have a cost, because **more abstractions require more mental energy** to switch back and forth between components. So try not to create new components too early.
- Name a component according to **what it does** or **what it displays**. Don’t be afraid of using long component names.
- Never declare a new component **inside another component**.
- **Co-locate related components inside the same file**. Don’t separate components into different files too early.
- It’s completely normal that an app has components of **many different sizes**, including very small and huge ones.

# 5.2 Component categories

![Untitled](5%20Thinking%20in%20React%20Component,%20Composition,%20and%20Re%2011d7a19d5ce24d328cdc41b56cb0539c/Untitled%201.png)

# 5.3 Component composition

**Component composition**: combining different components using the **children prop** (or **explicitly defined props**)

- Create highly **reusable** and flexible components
- Fix **prop drilling** (great for layouts)

![Untitled](5%20Thinking%20in%20React%20Component,%20Composition,%20and%20Re%2011d7a19d5ce24d328cdc41b56cb0539c/Untitled%202.png)

```jsx
export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  return (
    <>
      <NavBar>
        <Search />
        <NumResults movies={movies} />
      </NavBar>
      <Main>
        <ListBox>
          <MovieList movies={movies} />
        </ListBox>
        <WatchedBox />
      </Main>
    </>
  );
}

function NavBar({ children }) {
  return (
    <nav className="nav-bar">
      <Logo />
      {children}
    </nav>
  );
}
```