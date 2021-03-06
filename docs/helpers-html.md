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