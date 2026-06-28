# Node.js

```
pnpm init
pnpm add -D typescript
pnpm add -D @types/node
pnpm add fastify
pnpm add @fastify/swagger @fastify/swagger-ui
pnpm add @fastify/autoload
pnpm add @fastify/cors
pnpm add pg
```





```
{
  "compilerOptions": {
    "rootDir": "./src",
    "outDir": "./dist",
    "module": "NodeNext",

    "strict": false,
      //  "strict": true,
    "noUncheckedIndexedAccess": true,
    "noImplicitOverride": true,

    "lib": ["es2022"],

    "target": "es2022", // "target": "esnext",
    "moduleDetection": "force",
    "skipLibCheck": true,
    "verbatimModuleSyntax": true,
    "esModuleInterop": true,
    // "allowImportingTsExtensions":true
    "removeComments": true,
    "allowJs": true,
    "resolveJsonModule": true,
    "isolatedModules": true
  },
  "include": ["src/**/*"],
  "exclude": ["**/*.spec.ts", "**/old/**"]
}
```

```
{
  // Visit https://aka.ms/tsconfig to read more about this file
  "compilerOptions": {
    // File Layout
    // "rootDir": "./src",
    // "outDir": "./dist",

    // Environment Settings
    // See also https://aka.ms/tsconfig/module
    "module": "nodenext",
    "target": "esnext",
    "types": [],
    // For nodejs:
    // "lib": ["esnext"],
    // "types": ["node"],
    // and npm install -D @types/node

    // Other Outputs
    "sourceMap": true,
    "declaration": true,
    "declarationMap": true,

    // Stricter Typechecking Options
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,

    // Style Options
    // "noImplicitReturns": true,
    // "noImplicitOverride": true,
    // "noUnusedLocals": true,
    // "noUnusedParameters": true,
    // "noFallthroughCasesInSwitch": true,
    // "noPropertyAccessFromIndexSignature": true,

    // Recommended Options
    "strict": true,
    "jsx": "react-jsx",
    "verbatimModuleSyntax": true,
    "isolatedModules": true,
    "noUncheckedSideEffectImports": true,
    "moduleDetection": "force",
    "skipLibCheck": true,
  }
}

```

```
```





```
pnpm add -D tsx

pnpm install @asteasolutions/zod-to-openapi
pnpm add express zod swagger-ui-express 
pnpm install ts-node

pnpm install csv-parse

pnpm add -D @types/express @types/swagger-ui-express

pnpm i -D typescript
pnpm i -D prettier
pnpm i -D eslint

pnpm i -D tsx
```

```
npx tsc --init
```

```
pnpm exec tsc --init
```

```
pnpm config set ignore-scripts true
```

```
```















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
