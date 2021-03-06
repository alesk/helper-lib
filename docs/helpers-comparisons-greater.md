#### if_gt
_Conditionally render a block if the value is greater than a given number (If x > y)._
Parameters: `none`
``` handlebars
{{#if_gt x compare=y}} ... {{/if_gt}}
```

#### gt
**Same as `if_gt`, consider consolidating**
_Conditionally render a block if the value is greater than a given number (If x > y)._
<br>Parameters: value `string|int` - the value to test against.
``` js
// Data
number = 5
```
``` html
// Template
{{#gt number 8}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/gt}}

// Result:
Never mind :(
```

#### unless_gt
_Unless greater than (Unless x > y)_
Parameters: `none`
``` handlebars
{{#unless_gt x compare=y}} ... {{/unless_gt}}
```

#### if_gteq
_Conditionally render a block if the value is greater or equal than a given number (If x >= y)._
Parameters: `none`
``` handlebars
{{#if_gteq x compare=y}} ... {{/if_gteq}}
```

#### gte
**Same as `if_gteq`, consider consolidating**
_Conditionally render a block if the value is greater or equal than a given number (If x >= y)._
<br>Parameters: value `string|int` - the value to test against.

``` js
number = 5
```
``` html
// Template
{{#gte number 5}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/gte}}

// Result:
Kiss my shiny metal ass!
```


#### unless_gteq
_Render block, unless given value is greater than or equal to._
Parameters: `none`
_Unless x >= y_
``` handlebars
{{#unless_gteq x compare=y}} ... {{/unless_gteq}}
```