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
 * Creates its own virtual DOM with the information provided. This is not the usual browser DOM.
 * Parses the virtual DOM for Vue commands like the {{ name }} and replaces it with valid html values. 
 * Render virtual DOM as a real DOM to be used by the browser.
    
