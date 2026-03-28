# Node.js Express

```
npm init -y
npm i express
npm i -D typescript @types/node @types/express
npm i -D @tsconfig/node24
npm i -D tsx
npm i -D prettier
npm i -D eslint
npm i -D vitest
```

change type to module:

`"type": "module",`

then run:

```
npx tsc --init
```



```
mkdir src
cd src
touch index.js
```

```
// index.js
import express from "express";
const app = express();
const port = "3000";

app.get("/", (req, res) => {
  res.send("Hello World!");
  console.log("Response sent");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```



```
npx tsc
npx tsx --watch src/index.ts
```









## Prettier

echo 'dist' > .prettierignore

echo '{}' > .prettierrc
