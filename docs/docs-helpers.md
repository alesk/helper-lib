
### Special


### README Helpers

#### authors
TODO...

### Travis CI

#### travis
Creates a "full" Travis CI link in markdown format.
Params: `branch`
Type: `String`
Usage: `{{travis [branch]}}`

Example using default: `{{travis}}`

``` md
# [helper-lib v2.0.0](https://github.com/assemble/helper-lib)[![Build Status](https://travis-ci.org/assemble/helper-lib.png)](https://travis-ci.org/assemble/helper-lib)
```

Example with branch: `{{travis 'master'}}`

``` md
# [helper-lib v2.0.0](https://github.com/assemble/helper-lib)[![Build Status](https://travis-ci.org/assemble/helper-lib.png?branch=master)](https://travis-ci.org/assemble/helper-lib)
```

#### travis-badge
Creates a Travis CI link in markdown format.
Params: `none`
Usage: `{{travis-badge}}`

Example:

``` md
[![Build Status](https://travis-ci.org/assemble/helper-lib.png)](https://travis-ci.org/assemble/helper-lib)
```

#### changelog
A few convenience helpers that read data in YAML format, and do interesting things with the data. Well... they "do things" with the data. Anyway I guess only nerds like me find it interesting. 

**NOTE**: These helpers will throw an error if the source files are not  valid YAML format, using the following conventions:

A couple things to keep in mind about YAML:

* YAML is picky, so don't be surprised if the parser throws an error from improperly placed quotation marks.
* Seriously, don't be surprised. If you even come onto the issues and act surprised when it happens, an automated message will tell you to read the first bullet.

Here is an example of the format to follow in your `CHANGELOG` file:

``` yaml
v0.1.2
  date: "2014-04-09"
  changes:
    - The future sucks.
    - This is my third and last commmit from the future.
v0.1.1
  date: "2014-04-08"
  changes:
    - Second commit from the future.
    - The future is more boring that I thought it would be.
v0.1.0
  date: "2014-03-07"
  changes:
    - First commit... from the future. Yes!
```
Of coure, you are under no obligation to make your changelog entries as interesting as these, and you may record your entries at any point in whatever timeline you prefer, but whatever you write must be valid YAML when you do it.

The output will look like this:

``` md
* 2013-03-15    v0.1.2    Update README.md with documentation, examples.
* 2013-03-06    v0.1.0    First commit.
```

* More info here: [js-yaml](https://github.com/nodeca/js-yaml)
* See the tests here: [test/helpers/special_test.js](test/helpers/special_test.js)



### Other

#### formatPhoneNumber
_Output a formatted phone number_
Credit: [Treehouse Blog](http://blog.teamtreehouse.com/handlebars-js-part-2-partials-and-helpers)
```js
phoneNumber: 4444444444
```
``` handlebars
{{formatPhoneNumber phoneNumber}}
```
Result:
```
(444) 444-4444
```


### Strings
#### hyphenate
_Replace spaces in string with hyphens._
<br>Parameters: `none`
``` handlebars
{{hyphenate "make this all hyphenated"}}

// Result 
make-this-all-hyphenated
```

#### dashify
_Same as `hyphenate`, but replaces dots in string with hyphens._
<br>Parameters: `none`
``` handlebars
{{dashify "make.this.all.hyphenated"}}

// Result
make-this-all-hyphenated
```

#### lowercase
_Turns a string to lowercase._
<br>Parameters: `none`
``` handlebars
{{lowercase "MAKE THIS ALL LOWERCASE"}}

// Result
make this all lowercase
```

#### uppercase
_Turns a string to uppercase. Opposite of `{{lowercase}}`._
<br>Parameters: `none`
``` handlebars
 {{uppercase "make this all uppercase"}}

// Result
MAKE THIS ALL UPPERCASE
```

#### capitalizeFirst
_Capitalizes the first word in a string._
<br>Parameters: `none`
``` handlebars
{{capitalizeFirst "capitalize first word in this sentence"}}

// Result
Capitalize first word in this sentence
```

#### capitalizeEach
_Capitalizes each word in a string._
<br>Parameters: `none`
``` handlebars
{{capitalizeEach "capitalize EACH word in this sentence"}}

// Result
Capitalize EACH Word In This Sentence
```

#### titleize
_Capitalizes all words within a string. Taken from the templating library [Walrus](https://github.com/jeremyruppel/walrus) by [Jeremy Ruppel](https://github.com/jeremyruppel)._
<br>Parameters: `none`
``` handlebars
{{titleize "capitalize EACH word in this sentence"}}

// Result
Capitalize Each Word In This Sentence.
```

#### sentence
_Capitalizes the first word of each sentence in a string and converts the rest of the sentence to lowercase._
Parameters: `none`
``` handlebars
{{sentence "capitalize the FIRST word in each sentence. but make the OTHER words lowercase."}}

// Result
Capitalize the first word in each sentence. But make the other words lowercase.
```

#### reverse
_Reverses a string._
<br>Parameters: `none`
``` handlebars
{{reverse "bender should NOT be allowed on TV."}}

// Result
.VT no dewolla eb TON dluohs redneb
```

#### truncate
_Truncates a string given a specified `length`, providing a custom string to denote an `omission`._
<br>Parameters: 

* length: `int`- The number of characters to keep (Required). 
* omission: `string` - A string to denote an omission (Optional). 

``` handlebars
{{truncate "Bender should not be allowed on tv." 31 "..."}}

// Result
Bender should not be allowed...
```

#### center
_Centers a string using non-breaking spaces._
<br>Parameters: spaces: `int` - The number of spaces. (Required)
``` handlebars
{{center "Bender should not be allowed on tv." 10}}

// Result:
|              Bender should not be allowed on tv.              |
```

#### nl2br
_Convert new lines (`\r\n`, `\n\r`, `\r`, `\n`) to line breaks_
<br>Parameters: `none`
``` handlebars
{{nl2br <br>description}}

// Result: 
<br>
```



### Collections
#### first
_Returns the first item in a collection._
<br>Parameters: `none`
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]

```
``` html
// Template
{{first collection}}

// Result:
Amy Wong
```

#### withFirst
_Use the first item in a collection inside a block._
<br>Parameters: `none`
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{#withFirst collection}}
  <p>{{this}} is smart.</p>
{{/withFirst}}

// Result:
<p>Amy Wong is smart.</p>
```

#### last
_Returns the last item in a collection. Opposite of `first`._
<br>Parameters: `none`
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{last collection}}

// Result:
Scruffy
```

#### withLast
_Use the last item in a collection inside a block. Opposite of `withFirst`._
<br>Parameters: `none`
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{#withLast collection}}
  <p>{{this}} is lazy.</p>
{{/withLast}}

// Result:
<p>Scruffy is lazy.</p>
```

#### after
_Returns all of the items in the collection after the specified count._
<br>Parameters: count `int` - How many items to omit from the beginning. (Required)
```
// Date
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{after collection 5}}

// Result:
Leela, Professor Farnsworth, Scruffy
```

#### withAfter
_Use all of the items in the collection after the specified count inside a block._
<br>Parameters: count `int` - How many items to omit from the beginning. (Required)
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{#withAfter collection 5}}
    {{titleize this}}
{{/withAfter}}

// Result:
Leela Professor Farnsworth Scruffy
```

#### before
_Returns all of the items in the collection before the specified count. Opposite of `after`._
<br>Parameters: count `int` - How many items to omit from the end. (Required)
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{before collection 5}}

// Result:
Amy Wong, Bender, Dr. Zoidberg
```

#### withBefore
_Use all of the items in the collection before the specified count inside a block. Opposite of `withAfter`._
<br>Parameters: count `int` - How many items to omit from the end. (Required)
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{#withBefore collection 5}}
    {{reverse this}}
{{/withBefore}}

// Result:
gnoW ymA redneB grebdioZ .rD
```

#### join
_Joins all elements of a collection into a string using a separator if specified._
<br>Parameters: separator `string` - A string to use as a separator between the items. (Optional)
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{join collection " & "}}

// Result:
Amy Wong & Bender & Dr. Zoidberg & Fry & Hermes Conrad & Leela & Professor Farnsworth & Scruffy
```

#### sort
_Returns the collection sorted._
Parameters: `none`
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]
```
``` html
// Template
{{sort collection}}

// Result:
Amy Wong, Bender, Dr. Zoidberg, Fry, Hermes Conrad, Leela, Professor Farnsworth, Scruffy
```

#### withSort
_Uses the sorted collection inside the block._
<br>Parameters: field `string` - String name of the field or property to sort by. (Optional)
``` js
// Data
collection = [
  name: 'Leela'
  deliveries: 8021,

  name: 'Bender'
  deliveries: 239,

  name: 'Fry'
  deliveries: -12
]

```
``` html
// Template
{{#withSort collection "deliveries"}}
    {{name}}: {{deliveries}} <br>
{{/withSort}}

// Result:
Fry: -12
Bender: 239
Leela: 8021
```

#### length
_Returns the length of the collection._
<br>Parameters: `none`
``` js
// Data
collection = [
  'Amy Wong', 
  'Bender', 
  'Dr. Zoidberg', 
  'Fry', 
  'Hermes Conrad', 
  'Leela', 
  'Professor Farnsworth', 
  'Scruffy'
]

```
``` html
// Template
{{length collection}}

// Result:
8
```

#### lengthEqual
_Conditionally render a block based on the length of a collection._
<br>Parameters: length `int` - The value to test against. (Required)
``` js
// Data
collection = [
  name: 'Leela'
  deliveries: 8021,

  name: 'Bender'
  deliveries: 239,

  name: 'Fry'
  deliveries: -12
]
```
``` html
// Template
{{#lengthEqual collection 3}}
        There are 3 people in Planet Express.
{{else}}
        This is not Planet Express.
{{/lengthEqual}}

// Result:
There are 3 people in Planet Express.
```

#### empty
_Conditionally render a block if the collection is empty._
<br>Parameters: `none`
``` js
// Data
collection = []
```
``` html
// Template
{{#empty collection}}
        Good news everyone!
{{else}}
        Bad news everyone!
{{/empty}}

// Result:
Good news everyone!
```
#### any
_Conditionally render a block if the collection isn't empty. Opposite of `empty`_
<br>Parameters: `none`
``` js
// Data
collection = ['Professor Farnsworth']
```
``` html
// Templates
{{#any collection}}
        Good news everyone!
{{else}}
        Bad news everyone!
{{/any}}

// Result:
Good news everyone!
```

#### inArray
_Conditionally render a block if a specified value is in the collection._
<br>Parameters: value `string|int` - A value to test against. (Required)
``` js
// Data
collection = ['Professor Farnsworth', 'Fry', 'Bender']
```
``` html
// Templates
{{#inArray collection "Fry"}}
        I'm walking on sunshine!
{{else}}
        I'm walking on darkness.
{{/any}}

// Result:
I'm walking on sunshine!
```

#### eachIndex
_Current implementation of the default Handlebars loop helper {{#each}} adding index (0-based index) to the loop context._
<br>Parameters: `none`
``` js
// Data
collection = ['Professor Farnsworth', 'Fry', 'Bender']
```
``` html
// Templates
{{#eachIndex collection}}
    {{this}} is {{index}}
{{/eachIndex}}

// Result:
Professor Farnsworth is 0, Fry is 1, Bender is 2
```

#### eachProperty
_Loop through an objects properties_
<br>Parameters: `none`
``` js
// Data
TODO...
```
``` html
// Templates
{{#eachProperty object}}
    {{property}}: {{value}}<br/>
{{/eachProperty }}

// Result
TODO...
```


### Math
#### add
_Returns the sum of two numbers._
<br>Parameters: value `int` - The number to add to the expression. (Required)
``` js
// Data
value = 5
```
``` html
// Template
{{add value 5}}

// Result:
10
```

#### subtract
_Returns the difference of two numbers. Opposite of `add`_
<br>Parameters: value `int` - The number to subtract from the expression. (Required)_
``` js
// Data
value = 5
```
``` html
// Template
{{subtract value 5}}

// Result:
0
```

#### divide
_Returns the division of two numbers._
<br>Parameters: value `int` - The number to divide the expression. (Required)
``` js
// Data
value = 5
```
``` html
// Template
{{divide value 5}}

// Result:
1
```

#### multiply
_Returns the multiplication of two numbers._
<br>Parameters: value `int` - The number to multiply the expression. (Required)
``` js
// Data
value = 5

```
``` html
// Template
{{multiply value 5}}

// Result:
25
```

#### floor
_Returns the value rounded down to the nearest integer._
<br>Parameters: `none`
``` js
// Data
value = 5.6
```
``` html
// Template
{{floor value}}

// Result:
5
```

#### ceil
_Returns the value rounded up to the nearest integer._
<br>Parameters: `none`
``` js
// Data
value = 5.6
```
``` html
// Template
{{ceil value}}

// Result:
6
```

#### round
_Returns the value rounded to the nearest integer._
<br>Parameters: `none`
``` js
// Data
value = 5.69
```
``` html
// Template
{{round value}}

// Result:
6
```

#### sum
_Returns the sum of multiple numbers. Similar to `{{#add}}` block helper but accepts multiple arguments._
<br>Parameters: `none`
``` js
// Data
value = {
  a: 1,
  b: 2,
  c: 3
}
```
``` html
// Template
{{sum value.a value.b value.c}}

// Result:
6
```


### Numbers
#### toFixed
_Returns exactly `digits` after the decimal place. The number is rounded if necessary, and the fractional part is padded with zeros if necessary so that it has the specified length._
<br>Parameters: digits `int` - The number of digits to appear after the decimal point. (Optional)
``` js
// Data
value = 5.53231
```
``` html
// Template
{{toFixed value 3}}

// Result:
5.532
```

#### toPrecision
_Returns the number in fixed-point or exponential notation rounded to `precision` significant digits._
<br>Parameters: precision `int` - The number of digits. If omitted, it returns the entire number (without any formatting). (Optional)
``` js
// Data
value = 555.322
```
``` html
// Template
{{toPrecision value 4}}

// Result:
555.3
```

#### toExponential
_Returns the number in exponential notation with one digit before the decimal point, rounded to `fractions` digits after the decimal point._
<br>Parameters: fractions `int` - An integer specifying the number of digits after the decimal point. (Optional)
``` js
// Data
value = 5

```
``` html
// Template
{{toExponential value 5}}

// Result:
5.00000e+0
```

#### toInt
_Returns an integer._
<br>Parameters: `none`
``` js
// Data
value = '22.2abc'
```
``` html
// Template
{{toInt value}}

// Result:
22
```

#### toFloat
_Returns a floating point number._
<br>Parameters: `none`
``` js
// Data
value = '22.2abc'
```
``` html
// Template
{{toFloat value}}

// Result:
22.2
```

#### toAbbr
_Returns the number in abbreviation formats based on a value. The number is rounded to a particular decimal place._
<br>Parameters: digits `int` - The number of digits to appear after the decimal point. (Optional)
<br>Default: `2`
``` js
// Data
value = 123456789

```
``` html
// Template
{{toAbbr value}}

// Result:
123.457m
```

#### addCommas
_Adds commas to a number._
<br>Parameters: `none`
``` js
// Data
value = 2222222

```
``` html
// Template
{{addCommas value}}

// Result:
2,222,222
```


### Comparisons: Equal
#### is
_Conditionally render a block if the condition is true (if x = y)._

Parameters: `string|int` (the value to test against)
Default: `undefined`

Example #1:
``` js
// Data
---
number = 5
---
```
``` html
// Template
{{#is number 5}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/is}}

// Result:
Kiss my shiny metal ass!
```

Example #2:

If you are using [Assemble](https://github.com/assemble/assemble), data from _YAML front matter_ or any specified `JSON` and/or `YAML` source files will get passed through to the context in your templates.

``` yaml
--- # YAML Front Matter
page:
  title: About Us
---
```
``` html
{{#is page.title "home"}}
    <h1> About Us </h1>
{{else}}
    Never mind :(
{{/is}}
```
Result:
```
<h1> About Us </h1>
```

#### if_eq
**Same as `is`, consider consolidating**
_Conditionally render a block if the condition is true (If x = y)._
Parameters: `none`
``` handlebars
{{#if_eq x compare=y}} ... {{/if_eq}}
```

#### isnt
_Conditionally render a block if the condition is false. Opposite of `is`._
<br>Parameters: value `string|int` - the value to test against.
``` js
// Data
number = 5
```
``` html
// Template
{{#isnt number 5}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/isnt}}

// Result:
Never mind :(
```

#### or
_Conditionally render a block if one of the values is truthy._
<br>Parameters: values `string|int` - the values to test against.
``` js
great = no
magnificent = true
```
``` html
// Template
{{#or great magnificent}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/or}}

// Result:
Kiss my shiny metal ass!
```

#### and
_Conditionally render a block if both values are truthy._
<br>Parameters: values `string|int` - the values to test against.
``` js
// Data
great = true
magnificent = true
```
``` html
// Template
{{#and great magnificent}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/and}}

// Result:
Kiss my shiny metal ass!
```

#### unless_eq
**Same as `isnt`, consider consolidating**
_Conditionally render a block if the condition is false (Unless x = y). Opposite of `is`._
Parameters: `none`
``` handlebars
{{#unless_eq x compare=y}} ... {{/unless_eq}}
```



### Comparisons: Greater Than
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


### Comparisons: Less Than
#### lt
_Conditionally render a block if the value is less than a given number. Opposite of `gt`._
<br>Parameters: value `string|int` - the value to test against.
``` js
number = 5
```
``` html
{{#lt number 3}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/lt}}

// Result:
Never mind :(
```

#### lte
_Conditionally render a block if the value is less or equal than a given number. Opposite of `gte`._
<br>Parameters: value `string|int` - the value to test against.
``` js
number = 5
```
``` html
// Template
{{#lte number 5}}
    Kiss my shiny metal ass!
{{else}}
    Never mind :(
{{/lte}}

// Result:
Kiss my shiny metal ass!
```

#### unless_lt 
_Render block, unless value is less than a given number (Unless x < y)_
Parameters: `none`
``` handlebars
{{#unless_lt x compare=y}} ... {{/unless_lt}}
```

#### unless_lteq 
_Render block, unless value is less than or equal to a given number (Unless x <= y)_
Parameters: `none`
``` handlebars
{{#unless_lteq x compare=y}} ... {{/unless_lteq}}
```



### Dates
#### formatDate
_Formats a date into a string given a format. Accepts any value that can be passed to `new Date()`. This helper is a port of the [formatDate-js](http://https://github.com/michaelbaldry/formatDate-js) library by [Michael Baldry](https://github.com/michaelbaldry)._
<br>Parameters: format `string`, `required`
The format string, according to these tokens: [strftime](http://www.ruby-doc.org/core-1.9.3/Time.html#method-i-strftime)
``` js
// Data
date = new Date()
```
``` html
// Template
{{formatDate date "%m/%d/%Y"}}
{{formatDate date "%I:%M%p"}}
{{formatDate date "%F"}}
{{formatDate date "%Y%m%dT%H%M%S%z"}}

// Result:
07/26/2012
11:38PM
2012-07-26
20120726T233805-0004
```

#### now
_Returns the current date._
<br>Parameters: format `string` - The format string, according to these tokens: [http://www.ruby-doc.org/core-1.9.3/Time.html#method-i-strftime]() (Optional)
``` html
// Template
{{now}}
{{now "%m/%d/%Y"}}

// Result:
Thu Jul 26 2012 23:41:02 GMT-0400 (AST)
07/26/2012
```

#### timeago
_Returns a human-readable time phrase from the given date._
<br>Parameters: `none`
``` js
// Data
date = 'Thu Jul 22 2012 23:41:02 GMT-0400 (AST)'
```
``` html
// Template
{{timeago date}}

// Result:
4 days ago
```



### Inflections
#### inflect
_Returns the plural or singular form of a word based on a count._
<br>Parameters:
* singular `string` - The singular form of the word. (Required)
* plural `string` - The plural form of the word. (Required)
* include `boolean` - whether or not to include the count before the word. (Optional)
``` js
// Data
enemies = 0
friends = 1
```
``` html
// Template
{{inflect enemies "enemy" "enemies"}}
{{inflect friends "friend" "friends" true}}

// Result:
enemies
1 friend

#### ordinalize
_Turns a number into an ordinal string. Taken from the templating library [Walrus](https://github.com/jeremyruppel/walrus) by [Jeremy Ruppel](https://github.com/jeremyruppel)._
<br>Parameters: `none`
``` html
// Template
{{ordinalize 3}}
{{ordinalize 1}}
{{ordinalize 22}}

// Result:
3rd
1st
22nd
```


### HTML
#### gist
_Embed public GitHub Gists by adding only the Id of the Gist. The helper also accepts an optional second parameter for targeting a specific file on the Gist.._

Parameters: `String`
Default: `undefined`
Usage: `{{ gist [id] }}`

Example:
``` hbs
{{gist '5193239'}}
```
Output:
``` html
<script src="https://gist.github.com/5193239.js"></script>
```

#### embed
_Embed Code Snippets_

Embed code snippets from any file with the `embed` variable. You can also pass in a second parameter to force syntax highlighting for a specific language.

Parameters: `String|String (optional)` 
Default: `undefined`
Syntax: `{{ embed [filename] [syntax] }}`

Example:
``` hbs
{{ embed 'src/test.json' }}
```

Forced highlighting:
``` hbs
{{ embed 'src/test.json' 'javascript' }}
```
In the second example, highlighting was forced as `javascript` instead of `json`.


#### blockquote (planned...)
_Create a blockquote_

Outputs a string with a given attribution as a quote

``` hbs
{{#blockquote '@doowb' 'http://github.com/source/for/your/quote' 'This is the title' }}
  This is your quote.
{{/blockquote}}
```
Output:

``` html
<blockquote>
  <p>This is your quote.</p>
  <footer> 
    <strong>@doowb</strong>
    <cite> 
      <a href="http://github.com/source/for/your/quote">This is the title</a>
    </cite>
  </footer>
</blockquote>
```
   
#### stripes
_Iterates through an array, letting the contents know whether to add an even or odd row._

Parameters:

* `array` to iterate over, 
* `string`: CSS class name for even rows 
* `string`: CSS class name for odd rows

Credit: [treehouse blog](http://blog.teamtreehouse.com/handlebars-js-part-2-partials-and-helpers)

Usage:
``` handlebars
{{#stripes myArray "even" "odd"}}
  <div class="{{stripeClass}}">
    ... code for the row ...
  </div>
{{else}}
  <em>There aren't any people.</em>
{{/stripes}}
```

#### timeline (planned...)
_Iterates through an array, letting the contents know whether a timeline entry belongs in the left or right column._

Parameters: 

* `array` to iterate over, 
* `string`: CSS class name for left columns
* `string`: CSS class name for right columns

Credit: by [@jonschlinkert](http://github.com/jonschlinkert), and based on striped helper from [treehouse blog](http://blog.teamtreehouse.com/handlebars-js-part-2-partials-and-helpers)

Usage:
``` handlebars
<div class="timeline">
 {{#timeline myArray "left" "right"}}
 <div class="{{columnClass}}">
   {{> entry}}
 </div>
 {{else}}
   <em>There aren't any entries.</em>
 {{/timeline}}
</div>
```

#### ul
_Creates an unordered list._

Parameters: `Hash|HTML attributes`, `Optional`

HTML attributes to use on the `ul` element. 
``` js
// Data
collection = [
  name: 'Leela'
  deliveries: 8021,
  name: 'Bender'
  deliveries: 239,
  name: 'Fry'
  deliveries: 1
]
```
Template:
``` handlebars
{{#ul collection class="deliveries-list"}}
  {{name}} - {{inflect deliveries "delivery" "deliveries" true}}
{{/ul}}
```
``` html
// Output:
<ul class="deliveries-list">
  <li> Leela - 8021 deliveries </li>
  <li> Bender - 239 deliveries </li>
  <li> Fry - 1 delivery </li>
</ul>
```
#### ol
_Same as the `ul` helper but creates and ordered list. Returns `<br>` tags based on a count._

Parameters: `Hash`, `HTML attributes`, `Optional`

HTML attributes to use on the `ol` element. 
``` js
// Data
collection = [
  name: 'Leela'
  deliveries: 8021,
  name: 'Bender'
  deliveries: 239,
  name: 'Fry'
  deliveries: 1
]
```

Template:
``` handlebars
{{#ol collection class="deliveries-list"}}
  {{name}} - {{inflect deliveries "delivery" "deliveries" true}}
{{/ol}}
```
``` html
// Output:
<ol class="deliveries-list">
  <li> Leela - 8021 deliveries </li>
  <li> Bender - 239 deliveries </li>
  <li> Fry - 1 delivery </li>
</ol>
```

#### br
_Renders `<br>` elements in the output, based on the number given as a parameter. Not really recommended for general use, but it's here if you need it._

Parameters: `Integer|Count`, `Optional`

The number of `br` elements to render. 

`template.hbs`
``` handlebars
{{br 5}}
```
renders to:
``` html
`<br><br><br><br><br>`
```


### Logging
#### log
_Simple `console.log()`_
<br>Parameters: `none`
``` html
// Template
{{log "Hi console :)"}}

// Result:
Hi console :)
```

#### debug
_Simple `console.debug()` that shows the current context._
<br>Parameters: `none`
``` js
// Data
collection = [
  name: 'Leela'
  deliveries: 8021,
  name: 'Bender'
  deliveries: 239,
  name: 'Fry'
  deliveries: 1
]
```
``` html
// Template
{{#withFirst collection}}
   {{debug name}}
{{/withFirst}}

// Result:
Context: { deliveries: 8021, name: "Leela" }
Value: Leela
```


### Miscellaneous
#### default
_Provides a default or fallback value if a value doesn't exist._
<br>Parameters: defaultValue `string|int` - The default value to use. `title = ''`

``` html
// Template
{{default title "No title available."}}

// Result:
Not title available.
```

#### include 
_Provides an easy way to register and use partials inside your templates._

This helper only works if you define your templates as common.js modules, since it uses the common.js `require` function to find and register your templates with `Handlebars.registerPartial`. 

<br>Pattern: `{{include [name] [data]}}`
<br>Parameters:

* name (required): `[string]` - The name or path of the file in which your template is defined. (Required)
* data (optional): `[int|string|collection]` - Data you want to use inside the include. 

Data (collection): `planet-express.json`

``` js
[
  "Professor Farnsworth", 
  "Fry", 
  "Bender"
]
```

Include (partial to be "included"): `planet-express.hbs`
``` html
{{sort this}}
```

Template:
``` html
<p>{{include "planet-express.hbs" data}}</p>
```

Result:
``` html
<p>Bender, Fry, Professor Farnsworth</p>
```


