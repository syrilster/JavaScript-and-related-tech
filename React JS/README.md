## What is React?
* A Javascript library to build user interfaces using components.
* Helps to write easy and maintainable piece of code which generates the HTML for the browser.
* Helps to build two types of applications:
  * Single Page Application - Only one HTML page, content is (re) rendered on the client. Typically only one ** ReactDOM.render() call.
  * Multi Page Application - Multiple HTML pages and content is rendered on the server. ReactDOM.render() call per widget.

## How React JS and JSX works
* JSX is an extension to JavaScript which is enabled by React and it allows HTML like code to be included in JS files.
* JSX is just syntactic sugar for JavaScript, allowing you to write HTMLish code instead of nested React.createElement(...) calls.
* The HTML is converted to something else by Babel transpiler. Example:
    ```
    ReactDOM.render(<p> Hello World !!</p>, document.querySelector('#demoApp'));
    (or)
    Syntax is: React.createElement('one HTML wrapping element', props, One or Many children of the HTML element)
    const element = React.createElement('p', null, 'Hello Syril')
    ReactDOM.render(element, document.querySelector('#demoApp'));
    ```
## JSX Restrictions
* Some words of HTML can't be used. In the below example: className is being used instead of class keyword for CSS class as class is a reserved keywprd in JS.
   ```
   <div className='someClassName'>
   </div>
   ```
* The render() method can have only one root element and can't have multiple root elements returned. This is also a best practice so that one root element per component.


## Outputting Dynamic Content
* Using a single braces unlike angular and Vue js as HTML in react is rendered in JS code. Example below:
    ```
    const name = 'Syril';
    const element = <p> {name} </p>
    ReactDOM.render(element, document.querySelector('#demoApp'));
    ```
* **props.children** => used to ouput the child element dynamically passed with an element. For example: The hobby part can be rendered using the children property.
	```
	<Person name='Anju' age={20}>My hobby is: Knitting</Person>
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
    * Write a function as a component with props and React will do the object mapping. Here props.name is set automatically by react. **Have no access to state and life cycle hooks.**
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
* Note: Do not use state to manipulate the state of elements in all the components. The best practice is to have state changes in the container component i.e. App.js
* Example: To change the state using onClick event: **this.changeName.bind(this)** is used as the 'this' keyword in the context of onClick event refers to the event listener component at run time and not the App class by react and hence the binding is required.
* **this.setState** informs react about the change in property and it will be rendered again.
* **Function is stateless and class is a stateful component.** i.e. only in a React class you will be able to work with state.
* https://jsfiddle.net/syrilster/152v73az/1/
    ```
     class App extends React.Component {
        // A normal constructor to set the props in super and the initial state.
        constructor(props){
            super(props);
            this.state = {
                name: props.name
            };
        }

        // JS function to reset the state on click on a button
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

    const element = ReactDOM.render(<App name="Syril" />, document.querySelector('#demoApp'));
    ```
## Passing Method References between components
* Example Below: The pattern is to use props to pass the method and parms to the component and access it on an event like shown below. **this.switchHandler.bind(this, 'pass the arg here')**
  ```
  Person.js
  ---------
  const person = (props) => {
    return (
        <div>
        <p onClick={props.clickhandler}>This user's name is {props.name} aged {props.age}!!</p>
        <p>{props.children}</p>
        </div>
    );
  }

  export default person;
  
  App.js
  ------
  switchHandler = (newName) => {
    this.setState({
      persons: [
        {name: newName, age: 28}
      ]
     }
    )
  };

  render() {
    return (
      <div className="App">
        <Person name={this.state.persons[1].name} clickhandler={this.switchHandler.bind(this, 'Anju Ravindran')} 
                age={this.state.persons[1].age}>My hobby is: Knitting</Person>
      </div> 
    );
  }
  ```
## Rendering conditional content
* using an if condition and the logic required: https://jsfiddle.net/syrilster/vru72sg6/2/
    ```
    render(){
		let updateParagraph = '';
		if(this.state.name != this.props.name){
			updateParagraph = <p> Name has been updated </p>;
		}
		return (
		<div>
			<p>{this.state.name}</p>
			{updateParagraph}
			<button onClick={this.changeName.bind(this)}>Change Me</button>
		</div>
		);	
      }
    }
   ```
## Outputting Lists
* Example below: https://jsfiddle.net/syrilster/9mh2wqpL/1/
	```
	class App extends React.Component {

	constructor(props){
		super(props);
		this.state = {
			name: props.name,
			elements: []
		};
	}
	
	changeName() {
		this.setState({
		  name: 'Anju'
		});
	}
	
	addElements() {
	const oldElements = this.state.elements;
		this.setState({
		  elements: oldElements.concat(oldElements.length + 1)	
		});
	}
	
	render(){
		let updateParagraph = '';
		let list = this.state.elements.map(
		  (el) => {
		     return <li key={el}>{el}</li>;
		  }
		);
		
		if(this.state.name != this.props.name){
		  updateParagraph = <p> Name has been updated </p>;
		}
		
		return (
		<div>
		<p>{this.state.name}</p>
		{updateParagraph}
		<button onClick={this.changeName.bind(this)}>Change Me</button><br></br>
		<button onClick={this.addElements.bind(this)}>Add Element</button>
		<ul>{list}</ul>
		</div>
		);	
	     }
	  }


	const element = ReactDOM.render(<App name="Syril" />, document.querySelector('#demoApp'));
	```
## Setting styles dynamically
* Adding style to the above example:
  ```
    let list = this.state.elements.map(
	(el) => {
	const liStyle = {
	  backgroundColor: el % 2 == 0 ? 'blue' : 'green'
	};
	return <li key={el} style ={liStyle}>{el}</li>;
      }
   );
  ```
## User input and Two way Data binding
```
changeInputMessage(event){
  this.setState({
    message: event.target.value
  });	
}

<input type="text" value={this.state.message} onChange={this.changeInputMessage.bind(this)}></input>
<p>{this.state.message}</p>
```
## Using multiple components
* https://jsfiddle.net/syrilster/x7wr4ohk/
* Creating component using a function way has a benefit as it brings in immutability. The props can't or usually not changed in this case unlike the setState option in the class way of creating the component.

## Assignment Solution
* https://jsfiddle.net/syrilster/Lhkp9ax6/

## Returning Adjacent Element
* React render() method needs one and only one wrapping HTML element. For this reason we usually have a <div> and put all the child elements in there. This can be avoided as shown below.
* Using a Higher Order Function:
  ```
  Aux.js
  -------
  const aux = (props) => props.children;
  export default aux;
	
  In render method:
  -----------------
  render(){
  	<Aux>
	  //Child HTML elements here without the need of a <div>
	</Aux>
  }
  ```
