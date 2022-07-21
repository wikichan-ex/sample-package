# sample-package

## Step of create npm package

1. create package.json file

```
$ npm init --scope={YOUR_SCOPE_NAME}
```
e.g. npm init --scope=@wikichan-ex

2. create index.js file

e.g.
```
exports.sample = function() {
    console.log("This is sample package");
    return "This is sample package";
}
```

## Publish npm package (using Githun Package Register)

1. Create Access Token for publish the package

    - Access https://github.com/settings/tokens/new
    - Create a token with following permission
        - repo
        - read:packages
        - write:packages 

Ref:
https://docs.github.com/en/packages/learn-github-packages/about-permissions-for-github-packages#about-scopes-and-permissions-for-package-registries


2. Create .npmrc file

```
//npm.pkg.github.com/:_authToken=${NPM_PUBLISH_TOKEN}
```

3. set environment variable for .npmrc file

```
$ export NPM_PUBLISH_TOKEN={YOUR TOKEN}
```

4. login to npm
```
$ npm login --scope=@OWNER --registry=https://npm.pkg.github.com
```
e.g. npm login --scope=@wikichan-ex --registry=https://npm.pkg.github.com

If login is successful, it will show the following message
```
Logged in as XXXXX to scope @XXXXXX on https://npm.pkg.github.com/.
```

5. Edit package.json and set the following publishConfig

```
"publishConfig": {
  "registry":"https://npm.pkg.github.com"
}
```

6. Publish to npm

Execute the following command
```
$ npm publish
```

It will show the following result:
```
$ npm publish
npm notice
npm notice 📦  @wikichan-ex/sample-package@1.0.0
npm notice === Tarball Contents ===
npm notice 1.5kB README.md
npm notice 112B  index.js
npm notice 585B  package.json
npm notice === Tarball Details ===
npm notice name:          @wikichan-ex/sample-package
npm notice version:       1.0.0
npm notice filename:      @wikichan-ex/sample-package-1.0.0.tgz
npm notice package size:  1.0 kB
npm notice unpacked size: 2.2 kB
npm notice shasum:        XXXXXXXXXXXXX
npm notice integrity:     XXXXXXXXXXXXX
npm notice total files:   3
npm notice
npm notice Publishing to https://npm.pkg.github.com/
+ @wikichan-ex/sample-package@1.0.0
```