# Node.js

```
pnpm init
pnpm i -D typescript
pnpm i -D prettier
pnpm i -D eslint

pnpm i -D tsx
```

```
npx tsc --init
```





***



[https://medium.com/@gabrieldrouin/node-js-2025-guide-how-to-setup-express-js-with-typescript-eslint-and-prettier-b342cd21c30d](https://medium.com/@gabrieldrouin/node-js-2025-guide-how-to-setup-express-js-with-typescript-eslint-and-prettier-b342cd21c30d)

```
npm init -y
npm i -D typescript @types/node @types/express
npm i -D @tsconfig/node24
npm i -D tsx
npm i -D prettier
npm i -D eslint
npm i -D vitest

npm i express
npm i -D @types/express
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





## Postgres

```
npm install pg
npm i -D @types/pg
```







## Package manager

|      |                 |                  |
| ---- | --------------- | ---------------- |
| npm  | built in        |                  |
| pnpm | less redownload | current favorite |
| yarn |                 |                  |







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
