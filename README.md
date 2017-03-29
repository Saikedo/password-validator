[![logo][logo-image]][logo-url]

[![build status][travis-image]][travis-url]
[![npm version][npm-image]][npm-url]
[![npm downloads][downloads-image]][npm-url]

## Install
`npm install password-validator`

## Usage
```js
var passwordValidator = require('password-validator');

// Create a schema
var schema = new passwordValidator();

// Add properties to it
schema
.isMin(8)           // Minimum length 8
.isMax(100)         // Maximum length 100
.has().uppercase()  // Must have uppercase letters
.has().lowercase()  // Must have lowercase letters
.has().digits()     // Must have digits
.not().spaces();    // Should not have spaces

// Validate against a password string
console.log(schema.validate('validPASS123'));
// => true
console.log(schema.validate('invalidPASS'));
// => false

// Get a full list of rules which failed
console.log(schema.validate('joke', { list: true }));
// => [ 'isMin', 'uppercase', 'digits' ]

```

## Rules
Rules supported as of now are:

|     Rules      |               Descriptions                                       |
|:---------------|:-----------------------------------------------------------------|
|**digits()**    | specifies password must include digits                           |
|**letters()**   | specifies password must include letters                          |
|**lowercase()** | specifies password must include lowercase letters                |
|**uppercase()** | specifies password must include uppercase letters                |
|**symbols()**   | specifies password must include symbols                          |
|**spaces()**    | specifies password must include spaces                           |
|**isMin(len)**  | specifies minimum length                                         |
|**isMax(len)**  | specifies maximum length                                         |
|**not()**       | inverts the result of validations applied next                   |
|**has([regex])**| inverts the effect of _**not()**_ and applies a regex (optional) |

## Options
The following options can be passed to `validate` method:
* `list` - If set, validate method returns a list of rules which failed instead of true/false.

## Resources
* [API Reference](https://tarunbatra.github.io/password-validator/PasswordSchema.html)
* [Wiki](https://github.com/tarunbatra/password-validator/wiki)
* [Changelog](https://github.com/tarunbatra/password-validator/blob/master/CHANGELOG.md)

## License
[MIT License](http://choosealicense.com/licenses/mit/)


[logo-image]: http://res.cloudinary.com/tbking/image/upload/v1490803400/password-validator/logo.png
[logo-url]: http://tarunbatra.github.io/password-validator
[npm-image]: https://img.shields.io/npm/v/password-validator.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/password-validator
[travis-image]:https://img.shields.io/travis/tarunbatra/password-validator.svg?style=flat-square
[travis-url]:https://travis-ci.org/tarunbatra/password-validator
[downloads-image]: https://img.shields.io/npm/dt/password-validator.svg?style=flat-square
