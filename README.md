This is guide for day 4 of component library build 

## Add testing

```
npm i -D @types/react
npm i -D jest ts-jest @types/jest @testing-library/jest-dom @testing-library/react identity-obj-proxy
```

Copy from RAW

```
jest.config.js
jest.setup.js
tsconfig.json
```

Add `src` folder

Alter test script in package.json to 

```
"test": "jest —passWithNoTests"
```

Add to scripts 

```
"test:watch": "jest --passWithNoTests --watchAll",
```

Now run `npm run test` (if run fails, close code and restart)
Now run (in another terminal) `npm run test:watch` - keep this running and restart it if you have to restart 

## Add build

```
npm i -D @babel/core @rollup/plugin-commonjs @rollup/plugin-node-resolve babel-loader babel-preset-react-app rollup rollup-plugin-copy rollup-plugin-peer-deps-external rollup-plugin-sass rollup-plugin-typescript2 sass-loader
```

Add to package.json

```
"module": "build/index.esm.js",
  "files": [
    "build"
  ],
```

Add to scripts

```
"build": "rollup -c",
```

Copy file from RAW

```
rollup.config.js
```

Add empty `index.ts` in src folder

Now run `npm run build` (if run fails, close code and restart)

## Add storybook & static

```
npm i -D @storybook/react 
```

Create folder `.storybook`

Copy file from RAW

```
main.js
```

Add to scripts

```
    "storybook": "start-storybook -p 6006",
    "storybook:export": "build-storybook",
```

Add to .gitignore

```
storybook-static/
```

Now run `npm run storybook` (if run fails, close code and restart)
Now run `npm run storybook:static`

## Now add util generate

Copy over util folder (and check each file and save) from RAW

Add to scripts

```
"generate": "node ./util/create-component"
```

Copy files from RAW to src

```
typography.scss
variables.scss
```

## Now create a component

Now run `npm run generate TestButton1`

** the code created does not meet slinging rules we have decided upon, so the temp[lates should be changed at this stage)

Change index.ts to

```
import TestButton1 from './TestButton1/TestButton1';

export { TestButton1 };
```

Tests should continue to run and pass

Now run `npm run storybook`

## Now add npm package registration and pipelines

Copy files from RAW

```
.npmrc
azure-pipelines.yml
```

Add to package.json

```
"peerDependencies": {
    "react": "^16.13.1",
    "react-dom": "^16.13.1"
  },
```

pipelines file maybe needs to be changed (not sure)

test piublishing and building/deploying - sorry dont know instructions
