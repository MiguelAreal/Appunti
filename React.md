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
