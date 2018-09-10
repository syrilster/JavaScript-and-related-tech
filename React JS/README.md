## How React JS and JSX works
* JSX is an extension to java script which is enabled by React and it allows HTML like code in JS.
* The HTML is converted to something else by Babel transpiler. Example:
    ```
    ReactDOM.render(<p> Hello World !!</p>, document.querySelector('#demoApp'));
    (or)
    Syntax is: React.createElement('one HTML wrapping element', props, One or Many children of the HTML element)
    const element = React.createElement('p', null, 'Hello Syril')
    ReactDOM.render(element, document.querySelector('#demoApp'));
    ```
* const and let are new keywords in ES6 used to create constants and variables.

## Outputting Dynamic Content
* Using a single braces unlike angular and Vue js as HTML in react is rendered in JS code. Example below:
    ```
    const name = 'Syril';
    const element = <p> {name} </p>
    ReactDOM.render(element, document.querySelector('#demoApp'));
    ```
## Handling events and updating the DOM
* DOM updations are tricky without the use of components. The example below does not change the name on click of the button inspite of no errors:
* https://jsfiddle.net/syrilster/40gfL7ey/5/
    ```
        let name = "Syril";
        function changeMe(){
            name = 'Anju';
        }

        const element = (<div>
            <p>{name}</p>
            <button onClick={changeMe}>Change Me</button>
        </div>
        )
        ReactDOM.render(element, document.querySelector('#demoApp'));
    ```
