# Javascript

Loop over array

```html
if ( json instanceof(Array) ){
    for (let i = 0; i < json.length; i++){}; // for arrays make sure to do < instead of <= 
}
```



Check for 0:

```


buttonCounts[buttonId] ??= 0;

if (buttonCounts[buttonId] === undefined) {
buttonCounts[buttonId] = 0;
}

buttonCounts[buttonId] = buttonCounts[buttonId] ?? 0;

buttonCounts[buttonId] = buttonCounts[buttonId] || 0;
```
