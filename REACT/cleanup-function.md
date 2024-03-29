# Cleanup Function
> 개발자가 원치않는 동작을 방지

```javascript
import { useState, useEffect } from "react";

function Hello(){

  function byeFn(){
    console.log("bye ;(");
  }
  
  function hiFn(){
    console.log("created :)");
    // hiFn이 실행되지 않으면 byFn return
    return byeFn;
  }
  
  // Cleanup function
  useEffect(hiFn,[]);
  return <h1>Hello</h1>
}

function App() {
  const [showing, setShowing]=useState(false);
  const onClick=()=>setShowing((prev)=>!prev)
  return (
  <div>
    {showing ? <Hello /> : null}
    <button onClick={onClick}>{showing ? "Hide" : "Show"}</button>
  </div>
  );
}

export default App;
```

## Simply
```javascript
import { useState, useEffect } from "react";

function Hello(){
  useEffect(()=>{
    console.log("hi :)")
    return () => console.log("by :(");
  },[]);
  return <h1>Hello</h1>
}

function App() {
  const [showing, setShowing]=useState(false);
  const onClick=()=>setShowing((prev)=>!prev)
  return (
  <div>
    {showing ? <Hello /> : null}
    <button onClick={onClick}>{showing ? "Hide" : "Show"}</button>
  </div>
  );
}

export default App;
```
