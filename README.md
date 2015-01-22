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
 - Tabs or Spaces: *SPACES*. -Ideally- tabs! they solve the problem at hand! but in reality code ends up looking off. So use spaces;
 - Indentation columns: 2 or 4? *3*. Avoids lots of additional indentation issues that *PEP-8* runs into.

#Zen of programming
1. Readability is king

2. Explicit is better than implicit

   2.1. `Enum`s are better than `README`s
   
   2.2. `Type`s are better than `var`
   
   2.3. `try/catch` are more explicit than `if/else`

3. Simple is better than complex

   3.1. Avoid `if/else`. Here are things that are better:

      - *defaults*

      - *ternaries*

      - `switch` 

   3.2. `function`s are better than *method*s

4. Complex is better than complicated

   4.1. Files bigger than 400 lines are messy

   4.2. Lines longer than 120 characters are less readable

#Naming types
- *Primitives* (`int`, `float`, `String`, `Number`)
   - *camelCase*
   - Examples:
     `int x = 123;`
     `int locationID = 123456789`

- `Collection`s (`Array`, `List`, `Enum`, `Dictionary`, `HashMap`, etc.)
   - *camelCase*
   - Alwas in plural
   - Example: `var griffins = ['Peter', 'Stewie', 'Brian'];

- `Enum`s
   - *CamelCase*
   - `Object`'s name in plural
   - `constant` properties in *UPPER_CASE*
   - Example: `var HttpStatuses: {OK:200, CREATED:201, ACCEPTED:202}`

Examples
`IType oCoordinate = new Coordinate(x, y)` is better than `var coord = new Coordinate(x, y)`
