## react-2024

1.  Functional Component Structure
2. Array Function
3. Export , Import Component
4. Map, Filter, Reduce, Sort
5. Condional Operator - && and ternary
6. useState
7. setState - array,object,array of object,variable
8. useEffect
9. Axios / Fetch
10. Synthetic Event
11. Conditional rendering
12. Input , Dropdown - onChange
13. Button - onClick
14. Spread Operator
15. Props
16. Changing Parent State from child
17. Router
18. Redux
    
------------
## Functional Component 

Exampel 1 :
```

const App = () => {
// javascript logics will be written here
  let data = [1,2,3,4];

  function print(){
    console.log("print")
  }

// JSX logics will be written inside render
  return (
    <div>
      <p>Hello World</p>
    </div>
  );

};
```
Example 2 :
Writing JSX - should be written inside { } curly brackets.
```
const App = () => {

  const data = [1, 2, 3, 4];

  return (
    <div>
      {data.map((d) => <p>Hello World</p>)}
    </div>
  );

};
```
