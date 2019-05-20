

Document is ready
```
document.addEventListener("DOMContentLoaded", function(event) { 
  //do work
});
```


Escaping
```
// Use the browser's built-in functionality to quickly and safely escape
// the string
function escapeHtml(str) {
    var div = document.createElement('div');
    div.appendChild(document.createTextNode(str));
    return div.innerHTML;
}

// UNSAFE with unsafe strings; only use on previously-escaped ones!
function unescapeHtml(escapedStr) {
    var div = document.createElement('div');
    div.innerHTML = escapedStr;
    var child = div.childNodes[0];
    return child ? child.nodeValue : '';
}
```
Ref: http://shebang.brandonmintern.com/foolproof-html-escaping-in-javascript/

Form object fn:
```
function objectifyForm(formArray) {//serialize data function

  var returnArray = {};
  for (var i = 0; i < formArray.length; i++){
    returnArray[formArray[i]['name']] = formArray[i]['value'];
  }
  return returnArray;
}
```