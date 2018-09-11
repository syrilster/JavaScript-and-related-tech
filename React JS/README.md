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
* const and let are new keywords in ES6 used to create constants and variables. let is similar to var with only few differences. Ex:
    ```
    function ES6Example() {
    //tuce is *not* visible out here

    for( let tuce = 0; tuce < 5; tuce++ ) {
        //tuce is only visible in here (and in the for() parentheses)
        //and there is a separate tuce variable for each iteration of the loop
    }

    //tuce is *not* visible out here
    }

    function ES5Example() {
        //nish *is* visible out here

        for( var nish = 0; nish < 5; nish++ ) {
            //nish is visible to the whole function
        }

        //nish *is* visible out here
    }
    ```

## Outputting Dynamic Content
* Using a single braces unlike angular and Vue js as HTML in react is rendered in JS code. Example below:
    ```
    const name = 'Syril';
    const element = <p> {name} </p>
    ReactDOM.render(element, document.querySelector('#demoApp'));
    ```
## Handling events and updating the DOM
* DOM updations are tricky without the use of components. The example below code does not change the name on click of the button inspite of no errors in the console:
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
## React Component
* Two ways to create a component:
    * Write a function as a component with props and React will do the object mapping. Here props.name is set automatically by react.
        ```
        function App(props){
            return (
            <div>
                <p>{props.name}</p>
                <button>Change Me</button>
            </div>
        );
        }

        const element = 
        ReactDOM.render(<App name="Syril"/>, document.querySelector('#demoApp'));
        ```
    * Using ES6 classes to take leverage of state which can be changed inside the component. render() is the method where the JSX code needs to be present. The props is a property provided by the class and hence this.props.
       ```
       class App extends React.Component {
            render(){
                return (
                <div>
                    <p>{this.props.name}</p>
                    <button>Change Me</button>
                </div>
            );	
          }
        }
        const element = 
                    ReactDOM.render(<App name="Syril"/>, document.querySelector('#demoApp'));
       ```
## Using state in React JS
* Example to change the state using onClick event:
    ```
        class App extends React.Component {

        constructor(props){
            super(props);
            this.state = {
                name: props.name
            };
        }

        changeName() {
            this.setState({
                name: 'Anju'
            });
        }

        render(){
            return (
            <div>
                <p>{this.state.name}</p>
                <button onClick={this.changeName.bind(this)}>Change Me</button>
            </div>
        );	
        }
    }


    const element = 
                ReactDOM.render(<App name="Syril" />, document.querySelector('#demoApp'));
    ```
