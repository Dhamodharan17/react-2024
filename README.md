## react-2024

1.  Functional Component Structure
2.   useState
3. Array Function
4. Export , Import Component
5. Map, Filter, Reduce, Sort
6. Condional Operator - && and ternary
7.
8. setState - array,object,array of object,variable
9. useEffect
10. Axios / Fetch
11. Synthetic Event
12. Conditional rendering
13. Input , Dropdown - onChange
14. Button - onClick
15. Spread Operator
16. Props
17. Changing Parent State from child
18. Router
19. Redux
    
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
## Synthetic Event with onChange Event

```
onst App = () => {
  const [text,setText]= useState("");
  
  const onChangeText = (event)=>{
    setText(event.target.value);
  }
  
  return (
    <div>
      <input onChange = {onChangeText} placeholder='add todo'></input>    
    </div>
  );

};
```
## Passing Props to Child Component
```
import React, { useState } from "react";

const App = () => {
  const [text, setText] = useState("");

  const onChangeText = (event) => {
    setText(event.target.value);
  };

  return (
    <div>
      <input onChange={onChangeText} placeholder="add todo"></input>

      <Note name={text} />
    </div>
  );
};

export default App;

const Note = (props) => {
  return (
    <div>
      <p>{props.name}</p>
    </div>
  );
};

```
## Calling Parent method from child
step1: passing the method from parent
step2: call the method from child
```
import React, { useState } from "react";

const App = () => {
  const [text, setText] = useState("");

  const onChangeText = (event) => {
    setText(event.target.value);
  };

  const notify =()=>{
    alert("Called from child")
  }

  return (
    <div>
      <input onChange={onChangeText} placeholder="add todo"></input>

      <Note name={text} notify={notify} /> // step 1
    </div>
  );
};

const Note = (props) => {
  return (
    <div>
      <p>{props.name}</p>
      <button onClick={props.notify}>Notify</button> // step 2
    </div>
  );
};


export default App;
```
## Passing parameter from child to parent in method calling
```
import React, { useState } from "react";

const App = () => {
  const [text, setText] = useState("");

  const onChangeText = (event) => {
    setText(event.target.value);
  };

  const notify = (data) => {
    alert(data);
  };

  return (
    <div>
      <input onChange={onChangeText} placeholder="add todo"></input>

      <Note name={text} notify={notify} />
    </div>
  );
};

const Note = (props) => {
  return (
    <div>
      <p>{props.name}</p>
      <button onClick={() => props.notify(1)}>Notify</button>
    </div>
  );
};

export default App;

```
## useState Hook

a. Single Variable in useState

Only with setCount we can change the count state
```
const App = () => {

  const[count,setCount] = useState(0);

  const Inc = ()=>{
    setCount(count+1);
  }
  const Dec = ()=>{
    setCount(count-1);
  }

  return (
    <div>
      <p>{count}</p>
      <button onClick={Inc}>Increment</button>
      <button onClick={Inc}>Increment</button>
    </div>
  );

};
```
b. Array of objects in useState ( add, edit, delete, read)

Addig a new object
```
const App = () => {

  const[notes,setNotes] = useState([]);

  const [text,setText]= useState("");
  
  const onChangeText = (event)=>{
    setText(event.target.value);
  }
  
  const addNotes = ()=>{
    const newNote = {
      name:text,
      id:notes.length+1
    }
    setNotes(notes.concat(newNote));
  }

  return (
    <div>
      <input onChange = {onChangeText}placeholder='add todo'></input>
      <button onClick={addNotes}>Add</button>
    {notes.map((notes)=><p>{notes.name}</p>)}
    </div>
  );

};
```
Deleting a object
```
import React, { useState } from "react";

const App = () => {
  const [notes, setNotes] = useState([]);

  const [text, setText] = useState("");

  const onChangeText = (event) => {
    setText(event.target.value);
  };

  const addNotes = () => {
    const newNote = {
      name: text,
      id: notes.length + 1,
    };

    setNotes(notes.concat(newNote));
    console.log(notes)
  };

  const deleteNotes = (id) => {
    console.log(id)
    const newTodo = notes.filter((notes) => notes.id != id);
    setNotes(newTodo);
  };

  return (
    <div>
      <input onChange={onChangeText} placeholder="add todo"></input>
      <button onClick={addNotes}>Add</button>
      {notes.map((notes) => (
        <Note note={notes} deleteNote={deleteNotes} />
      ))}
    </div>
  );
};

export default App;

const Note = (props) => {
  return (
    <div>
      <p>{props.note.name}</p>
      <button onClick={() => props.deleteNote(props.note.id)}>Delete </button>
    </div>
  );
};
```


