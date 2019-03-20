# ts-node issue 797

Demo repository to reproduce https://github.com/TypeStrong/ts-node/issues/797.

The issue is fully resolved with ts-node 8.2.0 and TypeScript 3.5.1 (branch ts-node-8.2.0).
The information below is just there for historical reasons.

## Instructions

Run these commands:

```
yarn install --frozen-lockfile
cd packages/foo
yarn start
```

Actual result:

```
$ yarn start
yarn run v1.13.0
$ ts-node --files -P tsconfig.json src/index.ts

****/ts-node-issue-797/node_modules/ts-node/src/index.ts:343
        throw new TypeError(
              ^
TypeError: Unable to require `.d.ts` file.
This is usually the result of a faulty configuration or import. Make sure there is a `.js`, `.json` or another executable extension and loader (attached before `ts-node`) available alongside `index.ts`.
    at getOutput (****/ts-node-issue-797/node_modules/ts-node/src/index.ts:343:15)
    at Object.compile (****/ts-node-issue-797/node_modules/ts-node/src/index.ts:368:11)
    at Module.m._compile (****/ts-node-issue-797/node_modules/ts-node/src/index.ts:414:43)
    at Module._extensions..js (internal/modules/cjs/loader.js:700:10)
    at Object.require.extensions.(anonymous function) [as .ts] (****/ts-node-issue-797/node_modules/ts-node/src/index.ts:417:12)
    at Module.load (internal/modules/cjs/loader.js:599:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:538:12)
    at Function.Module._load (internal/modules/cjs/loader.js:530:3)
    at Module.require (internal/modules/cjs/loader.js:637:17)
    at require (internal/modules/cjs/helpers.js:22:18)
error Command failed with exit code 1.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```

Expected result (with ts-node 8.0.2):

```
$ yarn start
yarn run v1.13.0
$ ts-node --files -P tsconfig.json src/index.ts
I am bar
✨  Done in 1.10s.
```
