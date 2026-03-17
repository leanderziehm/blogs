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



### NestJS Framework

```
npm install -g @nestjs/cli

nest new projectName
cd button-api
```



```
npm install @nestjs/swagger swagger-ui-express class-validator class-transformer
```



```
npm run start
```

```
npm run start:dev
```











