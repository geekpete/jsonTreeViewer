#jsonTreeViewer and jsonTree library

The library and the viewer released under the MIT license (LICENSE.txt).

###jsonTreeViewer

A simple json formatter/viewer based on [jsonTree library] (#jsontree-library) and [app.js] (https://github.com/summerstyle/app.js) framework.

Online: http://summerstyle.github.io/jsonTreeViewer

1. Load json: click on "load" button and load a json-string to opened form
2. Expand/collapse single nodes by click on properties names (recursively - by `SHIFT` + click)
3. Expand/collapse all tree nodes by click on "expand all" and "collapse all" buttons


###jsonTree library (JSON pretty-printer)

A simple lightweight pure-javascript library for drawing tree of json-nodes from json-object.
You can get json-object from json-string by `JSON.parse(str)` method.

The library includes 2 files - `libs/jsonTree/jsonTree.js` (18 KB) and `libs/jsonTree/jsonTree.css` (2 KB).

Demo: http://summerstyle.github.io/jsonTreeViewer

#####How to use:

html:
```html
<link href="libs/jsonTree/jsonTree.css" rel="stylesheet" />
<script src="libs/jsonTree/jsonTree.js"></script>
```
javascript:
```javascript
// Get DOM-element for inserting json-tree
var wrapper = document.getElementById("wrapper");

// Get json-data by javascript-object
var data = {
    "firstName": "Jonh",
    "lastName": "Smith",
    "phones": [
        "123-45-67",
        "987-65-43"
    ]
};

// or from a string by JSON.parse(str) method
var dataStr = '{ "firstName": "Jonh", "lastName": "Smith", "phones": ["123-45-67", "987-65-43"]}';
try {
    var data = JSON.parse(dataStr);
} catch (e) {}

// Create json-tree
var tree = jsonTree.create(data, wrapper);

// Expand all (or selected) child nodes of root (optional)
tree.expand(function(node) {
   return node.children.length < 2 || node.label === 'phoneNumbers';
}
```
You can create many trees on one html-page.

#####The aviable methods of each json tree:

* `loadData(jsonObj)` - Fill new data to current json tree
* `appendTo(domEl)` - Appends tree to DOM-element (or move it to new place)
* `expand()` - Expands all tree nodes (objects or arrays) recursively
* `expand(filterFunc)` - Expands only selected (by filter function) child nodes of root element
* `collapse()` - Collapses all tree nodes (objects or arrays) recursively
