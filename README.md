# danger-web

## What you can not use

### Spread operator for `NodeList` IE, for example:

```javascript
const list = [ ...document.querySelectorAll('div') ]
```

This is because babel transpile this code to something with (related [issue](https://github.com/babel/babel/issues/7597)):

```javascript 
function _iterableToArray(iter) {
    if (Symbol.iterator in Object(iter) || Object.prototype.toString.call(iter) === "[object Arguments]")
        return Array.from(iter);
}
```

But, unfortunately, in IE:

```
(Symbol.iterator in document.querySelectorAll('div')) === false
```

You can use `Array.from(nodeList)` as workaround.
