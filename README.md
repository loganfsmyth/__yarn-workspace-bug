
This repo demonstrates an issue with Yarn Workspace's behavior for repos that are self-hosting with older versions of themselves.

e.g.
```
// Root package.json has dep on:
babel-core@7.0.0-alpha.18
babel-cli@7.0.0-alpha.18
```
and
```
// Packages:
packages/babel-core@7.0.0-alpha.19
packages/babel-cli@7.0.0-alpha.19 depending on babel-core@7.0.0-alpha.19
```

Actual Result:
```
node_modules/
    babel-core@7.0.0-alpha.18
    babel-cli@7.0.0-alpha.18
```

Expected Result:
```
node_modules/
    babel-core@7.0.0-alpha.18
    babel-cli@7.0.0-alpha.18
packages/babel-cli/node_modules/
    babel-core@7.0.0-alpha.19 -> ../../babel-core
```
