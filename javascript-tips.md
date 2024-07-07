# Allow only Number from input field using javascript


### Make a method in javascript

```
function isNumber(evt) {
    evt = (evt) ? evt : window.event;
    var charCode = (evt.which) ? evt.which : evt.keyCode;
    const inputValue = evt.target.value;

    // Allow decimal point (.)
    if (charCode === 46 && inputValue.indexOf('.') !== -1) {
        return false;
    }
    
    // Allow only numbers (0-9)
    if (charCode > 31 && (charCode < 48 || charCode > 57) && charCode !== 46) {
        return false;
    }

    return true;
}

```

### Use this method on input field using onkeypress event

```
<input type="text" name="input_name" onkeypress="return isNumber(event)" required />
```