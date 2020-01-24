# Lesson Plan - Thinking in react

- [Thinking the react way](https://reactjs.org/docs/thinking-in-react.html)
  - What was initial problem react solves?
  
- Components
  - Understanding the component model
    - Break down a site into components
  - Reusable blocks of JavaScript & HTML
  - Each component instance can be given different data
  - Can display JavaScript values in the HTML, using the { } symbols
  - Class component vs. functional component
  - Always returns HTML (in the form of JSX)
  - Render an array in `.map`
  - [Exercise](#working-with-component-trees)

- JSX
  - A way to write dynamic HTML code with JavaScript
  - It is a more intuitive version of the function createElement()
    - show https://babeljs.io/repl write <div></div> converted to `"use strict"; React.createElement("div", null);`
  - A component should always return JSX
  - These are the parts that will build the DOM structure
  - `ReactDOM.render`

- Props
  - Props is short for property (like a regular HTML attribute)
  - It is (dynamic) data that can be given to child components
  - Passed down using an identifier, a self-defined attribute name
  - Can be given to multiple instances of components
  - [Code inspiration](#userlist-components-jsx-and-props)
  - [Exercise](#useritemexpanded)

- State
  - State holds all the dynamic data of the app
  - State can only be defined in class-based and functional components with hooks
  - Initialization of state in constructor
  - [Code inspiration](#counter-example)
  - [Exercise](#counter)


Teacher suggestion: 
- Make a jquery app first and then change it to use react instead

### Get started with react

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Get started with React</title>
</head>
<body>
    <div id="root">Loading...</div>

    <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
    
    <script type="text/babel">
        // Write react code with JSX here
    </script>
</body>
</html>

```
### Get started with React and parcel.js
- https://github.com/senner008/react-min-boilerplate-parcel

## Coding inspiration

### UserList (Components, jsx and props)

https://codesandbox.io/s/name-age-simple-react-dz32o

```js
  import React from "react";
  import ReactDOM from "react-dom";

  function UserItem (props) {
    
    return (
        <li>
          <h3>
            {props.name}: {props.age}
          </h3>
        </li>
    );
  }
    
  function UserList (props)  {
      
    return (
        <ul>
            {
              props.users.map(user => {
                return <UserItem name={user.name} age={user.age} key={user.id} />;
              });
            }
        </ul>
    );
  }
    
  const users = [
    {
      id : 0,  
      name: "Benjamin",
      age: 32,
    },
    {
      id : 1,
      name: "Peter",
      age: 43
    }
  ];

  ReactDOM.render(
      <UserList users={users} />, 
      document.getElementById("root")
  );


```

### Counter example

https://codesandbox.io/s/simple-counter-wvgxr

```js
import React, { useState } from "react";
import ReactDOM from "react-dom";

function Counter () {
    
    const [counterState, setCounterState] = useState(0);
  
    const increment = () => {
      setCounterState(prev => prev +1)
    };
  
    return <button onClick={increment}>{counterState}</button>;  
}

ReactDOM.render(<Counter />, document.getElementById("root"));

```

## Exercises

### Working with component trees
Write the component tree for these two sites. NO CODE!
- [www.youtubecom](https://www.youtube.com/)
- https://github.com/HackYourFuture-CPH

Example:
```
<FancyHeader>
    <Logo src="logoPath" />
    <Navigation links={arrayOfLinks}>
</FancyHeader> 
```

### UserItemExpanded
Create a new component called `UserItemExpanded`. Render these user attributes as well:

- Fullname
- Adress
- Gender
- Age
- Height
- Spoken languages

### Counter
Expanding the Counter example, Add two new buttons:
1. Reset button. Clicking this button will reset the counter
2. Increment double. Clicking this button will double the counter. 

