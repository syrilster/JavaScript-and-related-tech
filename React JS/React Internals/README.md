## Component lifecycle
* Only available in stateful components. i.e a component using the ES6 syntax Class.
* Lifecycle steps executed in the below given order:
  * constructor() - call super(props) and then set the state. Do not make calls to a web server API.
  * componentWillMount() - Defined by React. Not really used often and it is mostly used for last minute optimizations ans state updations.
  * render() - This is called to prepare and structure the JSX code. Calling this does not mean that the browser DOM is updated. This will work with the React virtual DOM.
  * componentDidMount() - 
