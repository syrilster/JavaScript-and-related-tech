## Understanding let and const
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
