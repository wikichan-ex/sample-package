# sample-package

## Step of create npm package

1. create package.json file

```
$ npm init --scope={YOUR_SCOPE_NAME}
```
e.g. npm init --scope=@wikichan

2. create index.js file

e.g.
```
exports.sample = function() {
    console.log("This is sample package");
    return "This is sample package";
}
```