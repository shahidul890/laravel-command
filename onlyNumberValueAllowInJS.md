#### Create a simple function in javascript
```
function isNumber(evt) {
    evt = (evt) ? evt : window.event;
    var charCode = (evt.which) ? evt.which : evt.keyCode;
    if (charCode > 31 && (charCode < 48 || charCode > 57)) {
        return false;
    }
    return true;
}
```

#### HTML 
```
<input type="text" class="textfield" value="" id="extra7" name="extra7" onkeypress="return isNumber(event)" />
```