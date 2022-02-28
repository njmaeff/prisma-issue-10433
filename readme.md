# Repro

Re: Issue [https://github.com/prisma/prisma/issues/10433](https://github.com/prisma/prisma/issues/10433)

## Version

```txt
prisma                  : 3.10.0
@prisma/client          : 3.10.0
Current platform        : debian-openssl-1.1.x
Query Engine (Node-API) : libquery-engine 73e60b76d394f8d37d8ebd1f8918c79029f0db86 (at node_modules/@prisma/engines/libquery_engine-debian-openssl-1.1.x.so.node)
Migration Engine        : migration-engine-cli 73e60b76d394f8d37d8ebd1f8918c79029f0db86 (at node_modules/@prisma/engines/migration-engine-debian-openssl-1.1.x)
Introspection Engine    : introspection-core 73e60b76d394f8d37d8ebd1f8918c79029f0db86 (at node_modules/@prisma/engines/introspection-engine-debian-openssl-1.1.x)
Format Binary           : prisma-fmt 73e60b76d394f8d37d8ebd1f8918c79029f0db86 (at node_modules/@prisma/engines/prisma-fmt-debian-openssl-1.1.x)
Default Engines Hash    : 73e60b76d394f8d37d8ebd1f8918c79029f0db86
Studio                  : 0.458.0
Preview Features        : mongoDb

```

## Install
```bash
yarn install
yarn prisma generate
node repro.js
```

## Output

```txt
<projectDir>/server/client/runtime/index.js:40248
        throw e;
        ^

Error: ENOENT: no such file or directory, open '<projectDir>/.next/client/schema.prisma'
    at Object.openSync (node:fs:585:3)
    at Object.readFileSync (node:fs:453:35)
    at new LibraryEngine (<projectDir>/server/client/runtime/index.js:35459:41)
    at PrismaClient.getEngine (<projectDir>/server/client/runtime/index.js:40257:16)
    at new PrismaClient (<projectDir>/server/client/runtime/index.js:40232:29)
    at Object.<anonymous> (<projectDir>/repro.js:2:1)
    at Module._compile (node:internal/modules/cjs/loader:1101:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1153:10)
    at Module.load (node:internal/modules/cjs/loader:981:32)
    at Function.Module._load (node:internal/modules/cjs/loader:822:12) {
  errno: -2,
  syscall: 'open',
  code: 'ENOENT',
  path: '<projectDir>/.next/client/schema.prisma',
  clientVersion: '3.10.0'
}
```