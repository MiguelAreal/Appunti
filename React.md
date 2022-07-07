# React

#### Basic Elements

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

Example:
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

