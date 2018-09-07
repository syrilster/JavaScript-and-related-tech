## Overview
* Embed the html in a div like below:
  ```
  <div id="appName">
    {{ name }}
  </div>
  ```
* Having an instance of Vue to take control of some part of HTML code. 
  * el is a reserved keyword which take a CSS selector to gain control over the HTML part. 
  * The **data property** to takes a javascript object which can work inside this view instance.
      
    ```
    new Vue({
      el: '#appName',
      data: {
        name: 'Syril',
        age: ''
      }
    });
    ```
    
## How Vue.js works
* Creates its own virtual DOM with the information provided in the Vue instance. This is not the usual browser DOM.
* Parses the virtual DOM for Vue commands like the {{ name }} and replaces it with valid html values. 
* Render virtual DOM as a real DOM to be used by the browser.
 
## Handling events and updating the DOM
* By Vue events on html tags such as below:
  ```
  // HTML code
  <button v-on:click="methodName">Change Name</button>
  
  //JS Code:
  new Vue({
      el: '#appName',
      methods: {
        methodName: function(){
          this.name = "newname";
        }
      }
    });
  ```
* Note that the method cannot be any javascript function outside of the Vue instance. It should be a method name matching the methods tag inside a Vue instance.
* Access variables, objects inside Vue instance using the this keyword. Ex: this.name from the data tag name field.

## Render content Conditionally
* v-if directive for conditional rendering of DOM element. Example:
  ```
  <p v-if="name == 'Syril'">Name Changed !!</p>
  ```

## Outputting Lists
* Adding new elements dynamically as shown below:
  ```
  <button v-on:click="addElement">Add Element</button>
  <ul>
    <li v-for="element in elements"> Element {{ element }}</li>
  </ul>
  
  //JS Code:
  new Vue({
      el: '#appName',
      data: {
        elements: []
      },
      methods: {
        addElement: function(){
          this.elements.push(this.elements.length + 1);
        }
      }
    });
  
  ```
## Binding HTML Attributes and property to data
* Using the v-bind:attributeName to generate dynamic id attribute.
  ```
  <li v-for="element in elements"
      v-bind:id="'element ' + element"> Element {{ element }}</li>
      
  //Will generate HTML
  <li id="element 1">Element 1</li>
  ```
## Styling elements dynamically
* Using the **v-bind:style**. For example to set background color based on the element order. i.e even number or odd
  ```
  <li v-for="element in elements"
      v-bind:id="'element ' + element"
      v-bind:style="{backGroundColor: getColor(element)}"> Element {{ element }}</li>
      
  //JS Code:
  new Vue({
      el: '#appName',
      data: {
        elements: []
      },
      methods: {
        getColor: function(number){
          return number % 2 ==0 ? 'green' : 'red';  
        }
      }
    });
   ```
* Note that the backGroundColor attribute is in camel case and the getColor is a method in the Vue instance.
    
## Setting CSS classes dynamically
* Using the **v-bind:class**. Below example to change the css of the name displayed when a condition is met.
  ```
  <p v-bind:class="{updated: name == 'Syril'}"> {{ name }}</p>
  
  // CSS Code
  .updated {
    color: black,
    background-color: red
  }
      
  ```
## Shorthands for v-bind and v-on
* There are shorthands you can use for these common directives though.
* v-bind:PROPERTY  =>  :PROPERTY. Example: v-bind:style="..."  => :style="..." 
* v-on:EVENT  => @EVENT. Example: v-on:click="..."  => @click="..." 

## Limitations of multiple Vue instances
**Multiple Vue instances can be used to control different parts of the HTML.**
* Vue instances can only control the first occurance of the selector and then ignore the second one. Example: The below code is going to print the output as 
  * Syril
  * {{username}}
  ```
  <div class="username"> {{username}} </div>
  <div class="username"> {{username}} </div>

  //JS Code
  new Vue({
      el: '.username',
      data: {
        username: 'Syril'
      }
    });
  ```
## Creating and using components
* Example to register a component below: This will print the username twice.
* Fiddle: https://jsfiddle.net/syrilster/h2rsgb7j/
  ```
  <script src="https://unpkg.com/vue"></script>
  <div id="app">
  <app-username></app-username>
  <app-username></app-username>
  </div>


  
  Vue.component('app-username', {
    data: function() {
      return {
        username: 'Syril'
      }
    },
    template: '<p>{{username}}</p>'
  });
  
  new Vue({ el: '#app' });
 
  ```
## Passing data into components
* Using the props inside the Vue component.
* https://jsfiddle.net/syrilster/j7cufe1a/
  ```
  <script src="https://unpkg.com/vue"></script>
  <div id="app">
  <app-username v-bind:username="'Syril'"></app-username>
  <app-username v-bind:username="'Anju'"></app-username>
  </div>
  
  Vue.component('app-username', {
	props: ['username'],
  data: function() {
    return {
      //username: 'Syril'
    }
  },
  template: '<p>{{username}}</p>'
  });

  new Vue({ el: '#app' });
  ```
