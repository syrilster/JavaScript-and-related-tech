## Component lifecycle
* Only available in stateful components. i.e a component using the ES6 syntax Class.
* Lifecycle steps executed in the below given order:
  * constructor() - call super(props) and then set the state. Do not make calls to a web server API.
  * **componentWillMount()** - Defined by React. Not really used often and it is mostly used for last minute optimizations ans state updations.
  * render() - This is called to prepare and structure the JSX code and also to render child components. Calling this does not mean that the browser DOM is updated. This will work with the React virtual DOM.
  * render child components.
  * **componentDidMount()** - Component was successfully mounted. AJAX requests should go in the componentDidMount lifecycle event. Do not update the state of the components as it will trigger render().
* componentWillUnmount() - There also is one Lifecycle method which gets executed (when implemented) right before a Component is removed from the DOM.
* shouldComponentUpdate(nextProps, nextState) - Let's the user to return false if the update process needs to be cancelled and the DOM won't show the updated elements as the render method is not called by React.

## React's DOM updating strategy
* React keeps 2 copies of the virtual DOM(old and the recent virtual DOM) and applies a diffing algorithm to check and render the parts which changed and not the entire DOM.
* After the virtual DOM has the latest and greatest changes have been identified this is then merged to the real browser DOM. For example if a button text has changed then React will only update this change in the real browser DOM.
* More about the diffing process here: https://reactjs.org/docs/reconciliation.html
