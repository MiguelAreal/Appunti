# React

#### Basic Elements
asdasd
Html class
``` JSX
<div className="container"></div>
```

#### useEffect
If we want to interact with those things outside react, such as using an API, we use the useEffect hook.
By using this Hook, you tell React that your component needs to do something after render. React will remember the function you passed (we’ll refer to it as our “effect”), and call it later after performing the DOM updates.

The second parameter is the Dependencies Array, it is optional. This is used to determine how many times the useEffect is run. If this second parameter isn't set, the useEffect will be run everytime the component is rendered (Example 1). If the Dependencies Array is set and empty (Example 2), the useEffect will be run only on the first render. If some variable are placed on the Dependencies Array, after every rendering of the page, the useEffect will be run only if any of the variables has changed since the last rendering (Example 3).

Usually the variables in the Dependencies Array are also used on the useEffect function. For example an API call is placed into the useEffect function and the API call also passes a parameter to the backend. The parameter needs to be placed on the Dependencies Array so whenever the parameter is updated, th API call is run  again to get updated data.

Unlike componentDidMount or componentDidUpdate, effects scheduled with useEffect don’t block the browser from updating the screen. This makes your app feel more responsive. The majority of effects don’t need to happen synchronously. In the uncommon cases where they do (such as measuring the layout), there is a separate useLayoutEffect Hook with an API identical to useEffect.

Example 1:
``` JSX
import { useEffect } from 'react';

// This will run on every single render
function MyComponent() {
   useEffect(() => {
     // perform effect here
   });
}
```
Example 2:
``` JSX
import { useEffect } from 'react';

// This will run only on the first render
function MyComponent() {
   useEffect(() => {
     // perform effect here
   },[]);
}
```

Example 3:
``` JSX
import { useEffect } from 'react';
const [count, setCount] = React.useState(0);

// This will run on the first rendering and then only if the variable count is changed
function MyComponent() {
   useEffect(() => {
     // perform effect here
   },[count]);
}
```

Since useEffect is run after the DOM Rendering, it can be used to listen to events such as a window resize. If we register an event listener inside the useEffect function, it will register a new event listener everytime the component is loaded. Even if the component is unmounted, the event listener will be on the DOM. This will eventually end up in a memory leak. A good practice is to clean up the useEffect function. 

Example 3:
``` JSX
import React from "react"

export default function WindowTracker() {
    // When the component is mounted, it sets the state with the windows width
    const [windowWidth, setWindowWidth] = React.useState(window.innerWidth)
    
    React.useEffect(() => {
        function watchWidth() {
            console.log("Setting up...")
            setWindowWidth(window.innerWidth)
        }
        
        //On windows resize it will call watchWidth()
        window.addEventListener("resize", watchWidth)
        
        //The return is called only when the component is removed (end of lifecycle)
        return function() {
            console.log("Cleaning up...")
            window.removeEventListener("resize", watchWidth)
        }
    }, []) //Run useEffect only on the first component load
    
    return (
        <h1>Window width: {windowWidth}</h1>
    )
}
```

#### useRef
useRef returns a mutable ref object whose .current property is initialized to the passed argument (initialValue). The returned object will persist for the full lifetime of the component. useRef can be used to keep a value stored no matter how may times the component is rendered. When the value of the ref object changes, the component won't re-render.

Example 1:
``` JSX
//Example code that keeps track of the number of times the component is render using useRef hook.

import React, {useState, useEffect, useRef} from "react"

export default function App(){
const [name, setName] = useState('')
const renderCount = useRef(1)

useEffect(() => {
   // Updating the useRef object current value
   renderCount.current = renderCount.current + 1;
   })
return(
<>
   <input value={name} on Change={e => setName(e.targetvalue)} /}
   <div> My name is {name} </div>
   <div> I rendered {renderCount.current} times </div>
<>
)}

```

useRef hook is also used as a better way to access the DOM. If you pass a ref object to React with `<div ref={myRef} />`, React will set its .current property to the corresponding DOM node whenever that node changes.


Example 2:
``` JSX
//Example code that focus an input element whenever a button was clicked.

import React, {useState, useEffect, useRef} from "react"

export default function App(){
  const inputRef = useRef(null)
  
  const focusInput = () => {
    inputRef.current.focus()
  }
  
  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  )
}

```
#### useMemo 
Memoization is essentially just caching. Imagine a complex function that is slow to run which takes a as an argument. In order to speed up this function, you can cache the results of running the function so that when the function is run with the same inputs you can use the cached value instead of recomputing the value. This is a very common problem in React since all the component logic is re-computed every time the component renders and could cause drastic slowdowns if the component logic is slow to compute. Because of this, many React applications use memoization libraries or custom code to make memoization possible, but with the introduction of hooks, React has built in its own memoization system which is incredibly easy to use.

...

#### Sending data from child to parent components
1. Create a callback function in the parent component. This callback function will get the data from the child component.
2. Pass the callback function in the parent as a prop to the child component.
3. The child component calls the parent callback function using props.

Example: 

``` JSX
// PARENT
import React from "react"

export default function Parent(){
  const [state, setState] = React.useState(0);
  
  handleCallback = (childData) =>{
        this.setState({data: childData})
  }
    
  return (
    <div>
        <Child parentCallback = {handleCallback}/>
        {data}
    </div>
  )
}

```
``` JSX
// CHILD
import React from "react"

export default function Child(){
     onTrigger = (event) => {
        this.props.parentCallback("Data from child");
        event.preventDefault();
    }
    
    return(
        <div>
            <form onSubmit = {this.onTrigger}>
                <input type = "submit" value = "Submit"/>
            </form>
        </div>
    )
}

```

#### Forms 

In most cases, it’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form.

Example 1 (Simple change handler):
``` JSX
// Note: not using Controlled COmponent. See next examples to get the right implementation
import React from "react"

export default function Form() {
    const [firstName, setFirstName] = React.useState("")
    
    console.log(firstName)
    
    function handleChange(event) {
        // event.target return the DOM Obj that called the function.
        setFirstName(event.target.value)
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
            />
        </form>
    )
}

```


Example 2 (Handle changes on many inputs):
``` JSX
// Instead of creating an handler for every input field, we use a unique handler that uses the name of the input field to update the right propriety inside an unique object placed in "formData" state.
// Note: not using Controlled COmponent. See next examples to get the right implementation
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {firstName: "", lastName: ""}
    )
    
    console.log(formData)
    
    function handleChange(event) {
        setFormData(prevFormData => {
            return {
                  // The prevFormData is used to keep older values iside the object with this obj update
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        })
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                name="firstName"
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name="lastName"
            />
        </form>
    )
}

```
###### Controller Component
Controller component: an input form element whose value is controlled by React. Controlled component shoud be used to make sure that the internal state of the input component has the same value of the webpage state. In simple words: the value prop of the input component should be set to match the page state.

Example 3 (Controller component):

``` JSX
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {firstName: "", lastName: "", email: ""}
    )
    
    function handleChange(event) {
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        })
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                name="firstName"
                value={formData.firstName}
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name="lastName"
                value={formData.lastName}
            />
            <input
                type="email"
                placeholder="Email"
                onChange={handleChange}
                name="email"
                value={formData.email}
            />
        </form>
    )
}


```
###### Input, textarea, checkbox, ....
Example 4:
``` JSX
```
