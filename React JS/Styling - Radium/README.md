## Using Radium
* To use advance styles such as hover, other pseudo selectors and media queries.
* npm install --save radium to install radium
* import radium in the desired component file and enclose the component like show below:
    ```
    export default Radium(App);
    ```
* Example of using an hover shown below:
  ```
    const buttonStyle = {
        backgroundColor: "green",
        color: "white",
        font: "inherit",
        border: "1px solid blue",
        padding: "8px",
        cursor: "pointer",
        ":hover": {
          backgroundColor: "lightGreen",
          color: "black"
        }
      };
  ```
* Change the sytle using syntax below:
    ```
    buttonStyle[":hover"] = {
        backgroundColor: "salmon",
        color: "black"
    };
    ```
## Using Media Queries using Radium
* Import StyleRoot named export from radium and wrap the entire html element in the render()
    ```
    import Radium, { StyleRoot } from "radium";
    ```
* Define the style as below:
    ```
    let style = {
        "@media (min-width: 500px)": {
          width: "450px"
        }
    };
    ```
    
## Enabling and using CSS modules
* With CSS modules, you can write normal CSS code and make sure, that it only applies to a given component.
* This simply automatically generate unique CSS class names for you. 
* Example:
    ```
    Post.css
    --------

    .Post {
        color: red;
    }
    
    In Post Component
    -----------------

    import classes from './Post.css';

    const post = () => (
        <div className={classes.Post}>...</div>
    );
    ```
