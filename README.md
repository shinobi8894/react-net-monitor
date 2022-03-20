# React Net Monitor

### It's using Semantic UI
```
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/semantic-ui@2.4.2/dist/semantic.min.css"/>
```
### How to check net status
```
import {useEffect, useState} from "react";

export default () => {
    const [online, networkStatus] = useState(navigator.onLine);

    useEffect(() => {
        if (window.addEventListener) {
            window.addEventListener("online", () => networkStatus(true), false);
            window.addEventListener("offline", () => networkStatus(false), false);
        } else {
            document.body.ononline = () => networkStatus(true);
            document.body.onoffline = () => networkStatus(false);
        }
    }, []);

    return online;
}
```
### App.js
```
import useOnline from "./onlinestatus";

import "./App.css";

function App() {
  const online = useOnline();

  return (
    <div className="App">
      <h3 class="ui center aligned icon header">
        <i class="circular plug icon"></i>
        React network Monitor
      </h3>

      <div class="ui two column centered grid">
        <span>
          {online ? (
            <div className="ui green message">
              {" "}
              <i class="wifi icon"> </i> Congrats you are ONLINE
            </div>
          ) : (
            <div className="ui red message">
              {" "}
              <i class="meh icon"> </i> please check your network connection
            </div>
          )}
        </span>{" "}
      </div>
    </div>
  );
}

export default App;
```
### Result
![network](https://user-images.githubusercontent.com/92864027/159155893-d9aae5ba-2b29-4ecd-b450-872218e06f82.jpg)
