## Demo Rails App for Sprockets Issue #349

Attempting to use sprockets dependency tree to prevent downstream JS files from double including files already included in dependent assets
see: https://github.com/sstephenson/sprockets/issues/349

### application.js
```javascript
//= require foo
```

### extension.js
```javascript
//= stub application
//= require foo
```

## Expected Result

The extension.js should *not* include `foo.js` since it is already provided by the dependent asset

## Steps to Reproduce:

* Startup rails app `rails s`
* load application.js asset: http://localhost:3000/assets/application.js
* load extension.js asset: http://localhost:3000/assets/extension.js
