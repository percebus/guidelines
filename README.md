#Motivation
After 10+ years of experience in the *IT* field with languages like *python*, *JavaScipt*, *C++*, *C#*, *T-SQL*, *ASP*, *PHP* and so on, like any other SoftWare Engineer I've accumulated my best practices.

#Inspirations
 - *PEP-8*
 - `undersore.js`
 - `code.airBnB` guidelines
 - *Visual Studio*'s *C#* default code style.

#Steps of to any feature
1. Make it work
2. Make it fast
3. Make it pretty
4. Make it better

#Linting
 - Max lines per file? usually around **400**
 - 80char limit? *Nah!* but I do JSHint for **120**
 - *Tabs* or *Spaces*: **SPACES**. 
  - -Ideally- tabs! they solve the problem at hand! Anybody could customize their gutter sizes to their own *IDE*s and need.
  - But in reality code ends up looking "off". When working on a multi-location, OS, IDE, etc; team, is just begging to ruin someone's evening.
  - So *spaces* it is;
  
 - Indentation columns: 2 or 4? **3**. *But 3 is not a pair number! HERECY!*... meh!
 
  - If the world is divided by 2 or 4, the solution must lie in a middle ground.
  - Avoids lots of additional indentation issues that *PEP-8* runs into.
  ```
  ....
      var fourSpaces = function() {
  //      return "return cannot go here, as it aligns with the function's name"
              return "This is too much!"
          }
  ..
    var twoSpaces = function() {
      return "This is too crunched!"
    }

  ...
     var threeSpaces = function () {
        return "This is about right :)"
     }
  ```

 - `id`, `Id`, or `ID`? **`ID`**. 
  - Just look how cool  `coolID`, looks!.
  - `coolId` reads like "cool aid".

 - *camelCase* or *snake_case*? **HYBRID**! `sportCar_userID` is more readable than `sportcarUserid` or `sportcar_userid`. 
 - `'quotes_single'` or `"quotes_double"`: **BOTH**
  - `'quotes_single'` are better than `"quotes_double"`
  - `"quotes_double"` are better than `'escaped\'s`. `"quotes_double"` are particularly useful for cases `console`s, `print`s, `alert`s and so on.
  - Examples:
  ```
  var str = 'this is a String';
  console.log(str, "I was'n sure if this is what you've asked!");
  ```
  

#Zen of programming
1. Readability is king

  - Beautiful is better than ugly
  - Flat is better than nested
  - Sparse is better than dense
  - Files bigger than 400 lines are messy
  - Lines longer than 120 characters are less readable

2. Explicit is better than implicit

  2.1. `Type`s are better than `var`

  2.2. `try/catch` are more explicit than `if/else`

   - Errors should never pass silently.
   - Unless explicitly silenced.
  ```
  // *** example of bad error handling
     if ( _.isNumber(x) ) {
        keepMoving(x)
     }
     else {
        // something went wrong
        keepMoving(0)
     }

  // *** exmaple
     var result;
     try {// this denotes that your code is willing to handle the code
        if ( !_.isNumber(x) ) {
           throw new TypeError('x not instanceof Number');
        }
        result = x;
     } catch(err) {// this denotes that your code is not thorough in handling the error
        console.error(err);
        result = 0;
     }
     keepMoving(result);
  ```

  2.3. `Enum`s are *good!*, way better than:
   - extensive `README` files.
   - `dynamic` *run-time* `String`s 


3. Simple is better than complex

   3.1. Avoid `if/else` when possible. Here are things that are better:
   
      - *defaults*. `x || y`
      - *ternaries* `isFoo ? a : b;`
      - `switch` 

   3.2. `function`s are better than *method*s.

   3.3. `field`s are better than `get`ers & `set`ers.



4. Complex is better than complicated

   - `promise`s are better than `callback`s.


#Naming types
- *Primitives* (`int`, `float`, `String`, `Number`)
   - *camelCase*
   - Examples:
     `int x = 123;`
     `int locationID = 123456789`

- `Collection`s (`Array`, `List`, `Enum`, `Dictionary`, `HashMap`, etc.)
   - *camelCase* (starting with lowerCase)
   - *ALWAYS* in **plural**
   - Example: `var griffins = ['Peter', 'Stewie', 'Brian']`;

- `class`es
  - *CamelCase* (starting with UpperCase)

- `Enum`s
   - *CamelCase*
   - `class`' name in plural. Note that each `type` should be its own `enum`, instead of simply attaching all the `CONSTANTS` to classes, like in the *Titanim Appcelerator API*.
   - `constant` properties in *UPPER_CASE*
   - Example: 
    ```
    var HttpStatuses = {OK:200, CREATED:201, ACCEPTED:202}
    
    x['2001']; // bad. is prone to Chubby-fingers-syndrome. 

    x[HttpStatuses.CREATD]; // good. Yields (in python or C#) `object Satuses does not contain element 'ACTIV'
    ```


- `instance`s
  - `oCamelCase` or `camelCase`
  - `Type`: 
   - minimum `interface` needed for that `scope` *Polymorphism*.
   - **AVOID `var foo = new Thing();`**

   **Pseudo C# example**
   ```
   IType oCoordinate = new Coordinate(x, y) // good
   
   var coordinate = new Coordinate(x, y) // bad
   
   var coord = new Coordinate(x, y) // worst
   
   var c = new Coordinate(x, y) // ridiculous
   ```

   
  - NOTES: Usually we only have 1 instance per `type` per `scope`. If there is only 1 instance, it is *way better* to say 
  
   **JavaScript example**
   ```
    /* oHTMLFormElement tells us right out of the bat that
     * the class is called HTMLFormElement
     * this class is either from the browser or within my project
     * by "googling" 'HTMLFormElement' I immediatly find the src: 
     * https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement
     */
    var oHTMLFormElement = document.getElementById('#field') // good

    var element = document.getElementById('#field') // bad

    var elm = document.getElementById('#field') // worst

    var e = document.getElementById('#field') // ridiculous
    ```

  - But what if my `class` name is an abomination like `SensorStationDirectionLaneType`? (real-life case actually *sigh*)
   - Put some thought before rushing into naming classes.
   - Also, you can use the minimum interface name.

   **Pseudo C# example**
   ```
   /* If in this scope I am not concerned with all the added functionality 
    * of HTMLFormElement < HTMLElement < Element
    * I can be more clear of what bit of code I intend to use in this scope
    */
   // good. This will blow up here if HTMLFormElement does not implement IElement
   IElement oElement = new HTMLFormElement(); 
   
   var elm = getElm(); // bad. This will blow up until run-time
   ```
