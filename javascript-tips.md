1. The way to get last element in an array: `array[array.length - 1]`

```Javascript
const years = new Array(1998, 1999, 2000, 2001, 2002);
const age3 = calcAge(years[years.length - 1]);

```

2. Use `+` to concatenate every string values in an array.
3. `Object.entries()` is different from `.entries()`. `Object.entries()` makes an array of key and values, `.entries()` adds the index of array
4. Clever way to type coercion from number to string.

```Javascript
const str = number + '';
```

5. Good way to get page navigation:

- Put the ID of elements that want to scroll to in HTML href
- Add event listener to common parent element
- Determine what element originated the event
- Read the href in javascript, select the element wants to scroll to

6. Guard clause:

```Js
if (!clicked) return;
```

7. Add pad on date to implement standard date format.

```Js
const now = new Date();
const day = `${now.getDate()}`.padStart(2, 0);
const month = `${now.getMonth() + 1}`.padStart(2, 0);
```

8. When write function in class constructor, because this in simple function and eventlisners is different, we need to double check it. (Mapty App)

9. Method in constructor will be called immediately when an object is created. (Mapty App)

10. Try to write more small helper functions to help refactor code. (Mapty App)

11. Read more ducumentation. (Mapty App)
12. Object from local storage will not inherit all the methods, js object -> string -> js object will lose prototype. (Mapty App)

13. Access the first property of a js object: use `Object.keys()`

```Js
var obj = { first: 'someVal' };
obj[Object.keys(obj)[0]]; //returns 'someVal'
Object.values(obj)[0]; // returns 'someVal'
```

14. When use many promises, can chain them by return another function.

```Js
createImage('img/img-1.jpg')
  .then(img => {
    currentImg = img;
    console.log('Image 1 loaded');
    return wait(2);
  })
  .then(() => {
    currentImg.style.display = 'none';
    return createImage('img/img-2.jpg');
  })
  .then(img => {
    currentImg = img;
    console.log('Image 2 loaded');
    return wait(2);
  })
  .then(() => {
    currentImg.style.display = 'none';
  })
  .catch(err => console.error(err));
```
