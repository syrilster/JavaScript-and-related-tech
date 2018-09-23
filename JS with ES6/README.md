## Understanding let and const
* const and let are new keywords in ES6 used to create constants and variables. 
* const is used when you need to store constant values and this cannot be re-assigned.
* let is similar to var with only few differences. Ex:
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
    
## Arrow Functions
* Solves the problem of using the **this keyword** within a function. It had issues with not keeping up with the right context at run time.
* Usage as follows when having to change the values:
    ```
    const printMyDetails = (name, age) => {
    console.log(name, age);
    }

    printMyDetails("Syril", 20);
    ```
* Usage when having to return a value:
    ```
    const multiply = (number) => {
    return number * 2;
    }
    
    or 
    
    const multiply = number => number * 2;

    console.log("Final Number ", multiply(10));
    
    ```
## Exports and Imports (Modules)
* Default export.
    ```
    Person.js
    ---------
    const person = {
        name: 'Max'
    }
    export default person
    
    App.js
    --------
    import person from './Person' 
    or
    import per from './Person' 
    ```
* Named export. Note the use of {} and same const name or use an alias.
    ```
    Utility.js
    ----------
    export const baseData = 10;
    export const clean = () => {...}
    
    App.js
    ------
    import {baseData} from './Utility'
    or 
    
    import {baseData as data} from './Utility'
    import {clean} from './Utility'
    
    or (Import all constants at once and have an alias)
    import * as bundled from './Utility' and then bundled.baseData can be used.
    ```
## Classes properties and methods
* Next generation ES7 changes for constructor shown below:
    ```
    ES6
    -----
    constructor() {
        this.myProperty = 'value';
    }
    
    ES7 (No need to put property in constructor method and no need to invoke super())
    ----
    myProperty = 'value';
    ```
* Next generation ES7 changes for method shown below:
    ```
    ES6
    ----
    myMethod() {
        // Some logic here
    }
    
    ES7 (Using the arrow function)
    ----
    myMethod() = () => {
        // Some logic here
    }
    ```
* Full Example below:
    ```
    class Human {
        gender = 'Male';

        printGender() = () => {
        console.log(this.gender);
        }
    }

    class Person extends Human {
      name = 'Syril';
      gender = 'Female';

      printDetails() = () =>{
        console.log(this.name);
      }

    }

    const person = new Person();
    person.printDetails();

    ```
## Spread and Rest operators
* Spread operator: Used to copy the desired array or object properties and add few extra elements/properties.
    ```
    1. Array demo:
    const numbers = [1,2,3];
    const newNumbers = [...numbers, 4];

    console.log(newNumbers);
    
    Output:
    -------
    [1, 2, 3, 4]
    
    2: Object Demo
    const person = {
      name: 'Syril'
    };

    const newPerson = {
      ...person,
      age: 25
    };

    console.log(newPerson);
    
    Output:
    -------
    {name: "Syril", age: 25}
    
* Rest operator: Used to accept multiple args like Java var args.
    ```
    const filterNumber = (...args) => {
        return args.filter(el => el === 1)
    }

    console.log(filterNumber(1,2,3));
    Output:
    -------
    [1]
    ```
## Destructuring
* Extract elements from the array or object and store them in variables. [] for Array and {} for Objects.
    ```
    Ex: Array Destructuring - To extract number 1 and 3 into different variables:
    const numbers = [1, 2, 3];

    const [numberOne, , numberThree] = [...numbers];
    console.log(numberOne, numberThree);
    Output:
    -------
    1
    3
    
    Ex: Object Destructuring
    const myObj = {
        name: 'Syril',
        age: 28
    }
    const {name} = myObj;
    console.log(name);
    
    Output:
    -------
    Syril
    ```

## Array Functions
* Iterate over the elements of an array using the map function
    ```
    const numbers = [1, 2, 3];

    const doubledNumbers = numbers.map( (number) => {
            return number * 2;
        }
    );

    console.log(doubledNumbers);
    output:
    -------
    [2. 4, 6]
    ```
