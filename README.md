# React-Full-course
# Functional Based Components

components are the function same as in javascript but name of function must be capitalize and it must return jsx.

```javascript
function App() {
  return (
    <>
      <h1>Welcome to React World</h1>
    </>
  );
}
export default App;
```

# Class Based Components

```javascript
import { Component } from "react";
class App extends Component {
  render() {
    return (
      <>
        <h1>Class Based Component</h1>
      </>
    );
  }
}

export default App;
```

# JSX

jsx allows us to write HTML in React. jsx makes it easier to write and add HTML in React.

```javascript
function App() {
  return (
    <>
      <nav>
        <header>
          <ul>
            <li>Home</li>
            <li>About</li>
            <li>Product</li>
            <li>contact us</li>
          </ul>
        </header>
      </nav>
    </>
  );
}
export default App;
```

Here, These all tags `<nav><header><ul><li>` inside return is HTML tag. So Jsx allowed to wirte html code inside return.

# Rules for JSX

    1. There must be one parent inside return.
    2. All tags must be closed.
    3. Class is changed to className.
    4. for used in form tag is changed to HTMLFor.
    5. There must be no (space, _, -) between two words.
    For example background-color 👉 backgroundColor

# Creating different components

1. FirstComo.js

```javascript
export const FirstComo = () => {
  return <div>firstcomo</div>;
};
```

2. SecondComo.js

```javascript
export const SecondComo = () => {
  return <div>secondcomo</div>;
};
```

#### Calling both components

```javascript
import { FirstComo } from "./components/firstcomo";
import { SecondComo } from "./components/secondcomo";
function App() {
  return (
    <>
      <FirstComo />
      <SecondComo />
    </>
  );
}
export default App;
```

# Fragments

In return there must be only one parent, to use more than one parent we use Fragments.
`<></>` 👈 This is Fragment

```javascript
function App() {
  return (
    <>
      <header>Header</header>
      <article>Article</article>
      <section>Section</section>
    </>
  );
}
export default App;
```

# { Expressions in JSX }

The expression can be a `React variable, or property, or any other valid JavaScript expression` JSX will execute the expression and return the result.

```javascript
const Name = "Manoj";
const Add = (a, b) => a + b;
function App() {
  return (
    <>
      <h1>Name :{Name}</h1>
      <h1>7 + 5 = {Add(7, 5)}</h1>
    </>
  );
}
export default App;
```

# Lists

In React we use `map()` method to iterate throw list.

```javascript
function App() {
  const array = ["Home", "About", "Product", "Contact Us"];
  return (
    <>
      {array.map((navItems) => (
        <ul key={Math.random() * 10}>
          <li>{navItems}</li>
        </ul>
      ))}
    </>
  );
}
export default App;
```

#### Another Example itrating throw map function

```javascript
function App() {
  let object = [
    {
      Name: "Ramesh",
      Age: 21,
      Gender: "Male",
    },

    {
      Name: "Ajay",
      Age: 20,
      Gender: "Male",
    },
    {
      Name: "Suresh",
      Age: 25,
      Gender: "Male",
    },
  ];

  return (
    <>
      {object.map((data) => (
        <ul key={Math.random() * 10}>
          <li>Name :{data.Name}</li>
          <li>Age :{data.Age}</li>
          <li>Gender :{data.Gender}</li>
        </ul>
      ))}
    </>
  );
}

export default App;
```

# Props

    👉 To transver properties parent to child we use props
    👉 props are arguments passed into react components.
    👉 props are passed to components via HTML attributes

Example :

```javascript
const User = (props) => {
  return (
    <>
      <img src={props.img} alt="Image Not Found" />
      <h1>My Info :</h1>
      <h1>Name : {props.Name}</h1>
      <h1>Age : {props.Age}</h1>
    </>
  );
};
function App() {
  return (
    <>
      <User
        img="https://miro.medium.com/v2/resize:fit:834/1*XxOe72-YU1ASLQYgW4Rixg.jpeg"
        Name="Manoj"
        Age={21}
      ></User>
    </>
  );
}
export default App;
```

Breaking in files :

1. "./components/user"

```javascript
const User = (props) => {
  return (
    <>
      <img src={props.img} alt="Image Not Found" />
      <h1>My Info :</h1>
      <h1>Name : {props.Name}</h1>
      <h1>Age : {props.Age}</h1>
    </>
  );
};
export default User;
```

2. App.js

```javascript
import User from "./components/user";
function App() {
  return (
    <>
      <User
        img="https://miro.medium.com/v2/resize:fit:834/1*XxOe72-YU1ASLQYgW4Rixg.jpeg"
        Name="Manoj"
        Age={21}
      ></User>
    </>
  );
}
export default App;
```

# Props Destructuring

Example :

```javascript
const User = ({ img, Name, Age }) => {
  return (
    <>
      <img src={img} alt="Image Not Found" />
      <h1>My Info :</h1>
      <h1>Name : {Name}</h1>
      <h1>Age : {Age}</h1>
    </>
  );
};
function App() {
  return (
    <>
      <User
        img="https://miro.medium.com/v2/resize:fit:834/1*XxOe72-YU1ASLQYgW4Rixg.jpeg"
        Name="Manoj"
        Age={21}
      ></User>
    </>
  );
}
export default App;
```

👉 Here `props` is destructure to `{img,Name,Age}`

# children in props

When there is some data inside component tag then this data can be accesed by `children`.
`<Component>Data</Component>` 👉 Data accesed by `children`

Example :

```javascript
const User = ({ img, Name, Age, children }) => {
  return (
    <>
      <img src={img} alt="Image Not Found" />
      <h1>My Info :</h1>
      <h1>Name : {Name}</h1>
      <h1>Age : {Age}</h1>
      <p> children : {children}</p>
    </>
  );
};
function App() {
  return (
    <>
      <User
        img="https://miro.medium.com/v2/resize:fit:834/1*XxOe72-YU1ASLQYgW4Rixg.jpeg"
        Name="Manoj"
        Age={21}
      >
        <p>
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Magni neque
          porro repellat iusto pariatur, consequuntur quae eos nulla beatae
          illum omnis magnam fugit fuga fugiat aliquid rerum autem. Dolorum,
          laborum!
        </p>
      </User>
    </>
  );
}
export default App;
```

# Conditional Rednering

conditional rendering in React works the same way condition work in javascript. Use javascript operators like if or the conditional operator to create elements representing the current state and let React update the UI to match them.

Example :

```javascript
const ValidPassword = () => {
  return <h1>Valid Password</h1>;
};
const InvalidPassword = () => {
  return <h1>Invalid Password</h1>;
};

const Password = ({ isvalid }) => {
  if (isvalid) {
    return <ValidPassword />;
  } else {
    return <InvalidPassword />;
  }
};
function App() {
  return (
    <>
      <Password isvalid={true} />
    </>
  );
}
export default App;
```

# Applying CSS

### 1. Inline css

```javascript
function App() {
  return <h1 style={{ color: "blue" }}>This Text color will be blue</h1>;
}
export default App;
```

### 2. Style using Variable

```javascript
const Css = {
  backgroundColor: "black",
  color: "white",
};
function App() {
  return (
    <h1 style={{ backgroundColor: Css.backgroundColor, color: Css.color }}>
      Background color: Black & text color: white
    </h1>
  );
}
export default App;
```

### 3. Making Css file

#### Css file (style.css)

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
h1 {
  color: white;
  background-color: black;
}
```

#### App.js

```javascript
import "./style.css";
function App() {
  return <h1>Wroking with css in another file</h1>;
}
export default App;
```

### 4. installing bootstrap

Open terminal 👉 terminate (ctrl +c) 👉 enter 'y' and install bootstrap using this command `npm install react-bootstrap bootstrap`

### Steps:

1. Start your react server `npm start`
2. Import css using `import 'bootstrap/dist/css/bootstrap.min.css';`
3. Paste it on `index.js`
4. Copy code from `bootstrap` and paste it on `App.js`

### 5. Installing Talwind Css

1. `npm install -D tailwindcss`
2. `npx tailwindcss init`

# Uninstalling

1. bootstrap : `npm un bootstrap`
2. tailwind css :`npm un tailwindcss`

# React - Icon

`npm install react-icons --save`

Example : Youtube Icon

```javascript
import { FaYoutube } from "react-icons/fa";
function App() {
  return <FaYoutube />;
}
export default App;
```

# Events

1. Example : `onClick without perameter`

```javascript
let Button = () => {
  const handleClick = () => {
    console.log("Hello World");
    alert("why you are clicking me ?");
  };
  return <button onClick={handleClick}>Click Here</button>;
};
function App() {
  return (
    <>
      <Button />
    </>
  );
}
export default App;
```

2. Example: `onClick with perameter`

```javascript
let Button = () => {
  const handleClick = (a, b) => {
    alert("message");
  };
  return <button onClick={() => handleClick(7, 6)}>Click Here</button>;
};
function App() {
  return (
    <>
      <Button />
    </>
  );
}
export default App;
```

If we don't use arrow function inside onlick then before clicking on button content will render.
`<button onClick={handleClick(1,2)}>` content will render without clicking on button.

3. Example : `onCopy`

```javascript
const Copy = () => {
  let copyHandler = () => {
    alert("Please Do Not copy !");
  };
  return <p onCopy={copyHandler}>This is my content. please do not copy.</p>;
};
function App() {
  return <Copy />;
}
export default App;
```

4. Example : `onMouseMove`

```javascript
const Move = () => {
  let moveHandler = () => {
    console.log("Show Message : when you hover");
  };
  return (
    <p onMouseMove={moveHandler}>This is my content. please do not copy.</p>
  );
};
function App() {
  return <Move />;
}
export default App;
```

# State

The state is built in React object that is used to contain data or information about the component. A component's state can chage over time. Whenever it changes, the components re-renders.

# Hooks

Hooks are a new addition in React 16.8, They let you use state and other React features without writing a class.

# useState()

The React useState Hook allows us to track state in a function component. State generally refers to data or properties that need to be tracking in an application.

1. Example : `Counter`

```javascript
import { useState } from "react";
const Counter = () => {
  const [count, setCount] = useState(0);
  const increament = () => {
    setCount(count + 1);
  };
  const decrement = () => {
    setCount(count - 1);
  };
  return (
    <>
      <h1>{count}</h1>
      <button onClick={increament}>+</button>
      <button onClick={decrement}>-</button>
    </>
  );
};
function App() {
  return <Counter />;
}
export default App;
```

    To use useState() 👉 It must be import by react
    when we destructure useState() then first name and second name must be same, only difference is of "set".
    👉 For example const[count, setCount] = useState();

2. Example: `String Array in useState()`

```javascript
import { useState } from "react";
const List = () => {
  const [name, setName] = useState(["Ram ", "Radha ", "Sita "]);
  const add = () => {
    setName([...name, "krishna"]);
  };
  const remove = () => {
    setName(name.filter((n) => n !== "Sita "));
  };
  const update = () => {
    setName(name.map((m) => (m === "Radha " ? "Radha Rani " : m)));
  };
  return (
    <>
      {name.map((t) => (
        <li key={Math.random()}>{t}</li>
      ))}
      <button onClick={add}>Add</button>
      <button onClick={remove}>Remove</button>
      <button onClick={update}>Update</button>
    </>
  );
};
function App() {
  return (
    <>
      <List />
    </>
  );
}
export default App;
```

3. Example: `Object in useState`

```javascript
import { useState } from "react";
const Movie = () => {
  const [movie, setMovie] = useState({
    Movie: "Bahubali",
    Ratting: 5,
  });
  const changeRatting = () => {
    setMovie({ ...movie, Ratting: Math.round(Math.random() * 10) });
  };
  return (
    <>
      <h1>Movie Title : {movie.Movie}</h1>
      <p>Rating : {movie.Ratting}</p>
      <button onClick={changeRatting}>Change Ratting</button>
    </>
  );
};
function App() {
  return <Movie />;
}
export default App;
```

4. Example: `Array of OBJECTS`

```javascript
import { useState } from "react";
const StudentInfo = () => {
  const [student, setStudent] = useState([
    { RollNumber: 1, Name: "Jp", Age: 21 },
    { RollNumber: 2, Name: "Rahul", Age: 23 },
  ]);
  const changeName = () => {
    setStudent(
      student.map((m) => (m.Name === "Jp" ? { ...m, Name: "Manoj" } : m))
    );
  };
  return (
    <>
      {student.map((info) => (
        <li key={info.RollNumber}>{info.Name}</li>
      ))}
      <button onClick={changeName}>Change Name</button>
    </>
  );
};
function App() {
  return (
    <>
      <StudentInfo />
    </>
  );
}
export default App;
```

# Forms

When user did not fill complete data in that case we use `event.preventDefault()` show that submission of form will not be accepted.

1. Example : `link will not open`

```javascript
function handleClick(event) {
  event.preventDefault();
  console.log("Link click prevented!");
}

function App() {
  return (
    <a href="https://example.com" onClick={handleClick}>
      Click me
    </a>
  );
}
export default App;
```

2. Example : `input value`
   If we `provide value` to input box then we `cannot write` anything in web browser(input filed) to overcome this problem we use `event.target.value` 👉 Real-Time Data Capture: It allows you to capture the exact value the user has entered or selected in real-time.

```javascript
import { useState } from "react";
const Form = () => {
  const [data, setData] = useState("");
  const handleChange = (event) => {
    setData(event.target.value);
  };
  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`you type : ${data}`);
    setData("");
  };
  return (
    <>
      <h1>Your Name :</h1>
      <form onSubmit={handleSubmit}>
        <input type="text" value={data} onChange={handleChange}></input>
        <button>Submit</button>
      </form>
    </>
  );
};
function App() {
  return (
    <>
      <Form />
    </>
  );
}
export default App;
```

# useEffect()

The useEffect Hook allows you to perform side effects in your components. Some examples of side effects are: fetching data, directly updating the DOM.

```javascript
import { useEffect, useState } from "react";
const Counter = () => {
  const [value, setValue] = useState(0);
  useEffect(() => {
    console.log("calling for first Time");
    document.title = `My Website${value}`;
  });
  return (
    <>
      <h1>{value}</h1>
      <button onClick={() => setValue(value + 1)}>click here</button>
    </>
  );
};
function App() {
  return (
    <>
      <Counter />
    </>
  );
}
export default App;
```

### Uses of useEffect()

    1. Render content for the first time
    2. Any time we do side effect

# Dependecy list

```javascript
import { useEffect, useState } from "react";
const Counter = () => {
  const [value, setValue] = useState(0);
  useEffect(() => {
    console.log("calling for first Time");
    document.title = `My Website${value}`;
  }, [value]);
  return (
    <>
      <h1>{value}</h1>
      <button onClick={() => setValue(value + 1)}>click here</button>
    </>
  );
};
function App() {
  return (
    <>
      <Counter />
    </>
  );
}
export default App;
```

`useEffect(() =>{ },[value])` 👈 here useEffect is depended on `value` until `value` does not change it will not render or do not show side effect. `But it will render for the first time.`

# Pop drilling

passing of props from one component to another component and so on is known as pop drilling.

Example : `Transfering data from App.js to third.js`

App.js

```javascript
import First from "./first";
function App() {
  const name = "Manoj";
  return (
    <>
      <h1>This is just simple text</h1>
      <First name={name} />
    </>
  );
}
export default App;
```

first.js

```javascript
import Second from "./second";

const First = ({ name }) => {
  return (
    <>
      <Second life={name}></Second>
      <h1>This is also simple text but written by {name}</h1>
    </>
  );
};

export default First;
```

second.js

```javascript
import Third from "./third";
function Second({ life }) {
  return (
    <>
      <Third name={life} />
    </>
  );
}
export default Second;
```

third.js

```javascript
function Third({ name }) {
  return (
    <>
      <h1>heading 1 </h1>
      <h2>heading 2 </h2>
      <h2>name : {name} </h2>
    </>
  );
}
export default Third;
```

# context API

    1. Import {createContext} from "react";
    2. Creating instance of createContext
    Example : export const Data = createContext();
    3. Wrap our component into provider Component

```javascript
<Data.Provider value={name}>
  <ComponentZ />
</Data.Provider>
```

Example :

1. App.js

```javascript
import First from "./first";
import { createContext } from "react";
export const Data = createContext();
function App() {
  const name = "Manoj";
  return (
    <>
      <Data.Provider value={name}>
        <First />
      </Data.Provider>
      <h1>This is just simple text</h1>
    </>
  );
}
export default App;
```

2. first.js

```javascript
import { Data } from "./App";
const First = () => {
  return (
    <>
      <Data.Consumer>
        {(name) => {
          return <h1>My Name : {name}</h1>;
        }}
      </Data.Consumer>
    </>
  );
};

export default First;
```

# Problem in context Api

When want to `share multiple data` from parent to child then we `have to use multiple arrow function And that's make code to long`

Example :
`App.js`

```javascript
import { createContext } from "react";
import ComponentA from "./ComponentA";

// 2. Creating instance of (createContext)
export const Data = createContext();
export const Data1 = createContext();

const App = () => {
  const name = "Manoj";
  const age = 19;

  return (
    <>
      <Data.Provider value={name}>
        <Data1.Provider value={age}>
          <ComponentA />
        </Data1.Provider>
      </Data.Provider>
    </>
  );
};

export default App;
```

`ComponentA.js`

```javascript
import { Data, Data1 } from "./App";

const ComponentA = () => {
  return (
    <>
      {/* 4. Consuimg/Accessing Data */}
      <Data.Consumer>
        {(name) => {
          return (
            <Data1.Consumer>
              {(age) => {
                return (
                  <h1>
                    My name is: {name} and I'm {age} years old.
                  </h1>
                );
              }}
            </Data1.Consumer>
          );
        }}
      </Data.Consumer>
    </>
  );
};

export default ComponentA;
```

# Multiple props (overcome to problem)

Example :
`App.js`

```javascript
import First from "./first";
import Second from "./second";

function App() {
  const Name = "Manoj";
  const Age = 21;
  return (
    <>
      <First Name={Name} />
      <Second Age={Age} />
    </>
  );
}
export default App;
```

`first.js`

```javascript
function First({ Name }) {
  return (
    <>
      <h1>my name is {Name} </h1>
    </>
  );
}
export default First;
```

`second.js`

```javascript
function Second({ Age }) {
  return (
    <>
      <h1>And Age is {Age}</h1>
    </>
  );
}
export default Second;
```

# useContext()

`Solution for createContext`

React Context is a way to manage state globally it can be used together with the useState Hook to share state between deeply nested components more easily than with useState alone.

`App.js`

```javascript
import { createContext } from "react";
import ComponentA from "./ComponentA";

// 2. Creating instance of (createContext)
export const Data = createContext();
export const Data1 = createContext();

const App = () => {
  const name = "Manoj";
  const age = 19;

  return (
    <>
      <Data.Provider value={name}>
        <Data1.Provider value={age}>
          <ComponentA />
        </Data1.Provider>
      </Data.Provider>
    </>
  );
};

export default App;
```

`Component.js`

```javascript
import { useContext } from "react";
import { Data, Data1 } from "./App";

const ComponentA = () => {
  const name = useContext(Data);
  const age = useContext(Data1);
  return (
    <>
      <h1>
        My name is {name} and i am {age} years old.
      </h1>
    </>
  );
};
export default ComponentA;
```

# useReducer()

useReducer is a hook in React that is similar to useState, but it is designed for more complex state objects or state transition that involve multiple sub-values. It allows you to manage state in a functional, immutable way.

Example :
`App.js`

```javascript
import { useReducer } from "react";

const App = () => {
  const [count, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      <h1>Count: {count}</h1>
      <button onClick={() => dispatch({ type: "increment" })}>Increment</button>
      <button onClick={() => dispatch({ type: "decrement" })}>Decrement</button>
    </>
  );
};

export default App;
```

`reducer.js`

```javascript
const initialState = 0;

const reducer = (state, action) => {
  switch (action.type) {
    case "increment":
      return state + 1;
    case "decrement":
      return state - 1;
    default:
      return state;
  }
};

export default reducer;

```
framer motion 👉 animation library 

```javascript
import { motion } from "framer-motion";

const App = () => {
  return (
    <>
      <motion.h1>Count: {count}</motion.h1>
      <motion.button 
      whileHover={{ scale: 1.1 }}
      whileTap={{ scale: 0.9 }}
      
      onClick={() => dispatch({ type: "increment" })}>Increment</motion.button>
      <motion.button 
      whileHover={{ scale: 1.1 }} 
      whileTap={{ scale: 0.9 }}
      onClick={() => dispatch({ type: "decrement" })}>Decrement</motion.button>
    </>
  );
};

export default App;
``` 
So this is the basic use of useReducer() and framer motion.