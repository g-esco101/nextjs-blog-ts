# Nextjs Blog TS

A sample website created with React using TypeScript. It is a blog that displays articles concerning prerendering in Nextjs.

This project is the result of completing the [Create a Next.js App](https://nextjs.org/learn/basics/create-nextjs-app) course on the Nextjs site and converting it to use TypeScript. It concerns the following: frontend development concepts; react; the basics of Nextjs; the basics of the Develop, Preview, Ship workflow in Vercel; and how to set up Next.js with TypeScript, use Next.js specific types, and convert the blog app to TypeScript.

Currently it is deployed on Vercel:
_____

## Technology

- Node.js version 18
- React
- Next.js

## Getting Started

1. Install [Node 18](https://nodejs.org) (I recommend using nvm - node version manager - to switch between versions of node)
2. Clone this repository

```
git clone https://github.com/g-esco101/nextjs-blog-ts.git
```

3. Change to root directory

```
cd nextjs-blog
```

4. Install node packages with dependencies

```
npm install
```

5. Run the app

```
npm run dev
```

## Building the app for production

1. Build the app

```
npm run build
```

2. Run the app

```
npm run start
```


## Setup Nextjs to use TypeScript

- Create an empty tsconfig.json file in the root of your project:
```
touch tsconfig.json
```
If you run the dev server ('npm run dev' or 'yarn dev') it will tell you which packages to install. 

- Install the required packages to use TypeScript:
```
npm install --save-dev typescript @types/react @types/node
```
Now when you run the dev server, Nextjs will populate the tsconfig.json file (you may customize this file) and create the next-env.d.ts file, which ensures Next.js types are picked up by the TypeScript compiler. You should not modify this file.

- Add the "moduleResolution": "node" to tsconfig.json:
```
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "moduleResolution": "node",
    "allowJs": true,
    "skipLibCheck": true,
    "strict": false,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "incremental": true,
    "esModuleInterop": true,
    "module": "esnext",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve"
  },
  "include": [
    "next-env.d.ts",
    "**/*.ts",
    "**/*.tsx"
  ],
  "exclude": [
    "node_modules"
  ]
}
```
Module resolution is the process the compiler uses to figure out what an import refers to. 

- You can now use TypeScript for your Next.js app.

## Next.js Specific Types

### Static Generation and Server-side Rendering
```
import { GetStaticProps, GetStaticPaths, GetServerSideProps } from 'next';

export const getStaticProps: GetStaticProps = async (context) => {
  // ...
};

export const getStaticPaths: GetStaticPaths = async () => {
  // ...
};

export const getServerSideProps: GetServerSideProps = async (context) => {
  // ...
};
```

### API Routes
```
import { NextApiRequest, NextApiResponse } from 'next';

export default (req: NextApiRequest, res: NextApiResponse) => {
  // ...
};
```

### Custom App
You can convert pages/_app.js into pages/_app.tsx and use the built-in type AppProps, like so:
```
import { AppProps } from 'next/app';

function App({ Component, pageProps }: AppProps) {
  return <Component {...pageProps} />;
}

export default App;
```
