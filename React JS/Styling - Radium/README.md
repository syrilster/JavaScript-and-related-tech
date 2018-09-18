## Using Radium
* To use advance styles such as hover, media queries and other pseudo selectors.
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
