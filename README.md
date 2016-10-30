# angular-form-validator
> Angular validation directive with many validation rules and custom error messages.
> Validation rules are simmilar to mongoose validation rules!



## 1. Installation
`npm install angular-form-validator`



## 2. Description
This is angular module which gives you angular directive for HTML form validation.
- easy to integrate in your existing angular 1.4+ project
- many default validation rules inspired by [mongoose validation](http://mongoosejs.com/docs/validation.html)
- validation on almost all [jQuery events](https://api.jquery.com/category/events/): 'change', 'keyup', 'click', 'blur' ...etc
- developer can create custom validation rules
- developer can define custom error messages
- not dependant on any CSS framework (Bootstrap, Foundation, Material, ...etc) or any JS library like jQuery
- 100% native angular

It's not only validator but corrector. For example if you put type:'number' it will automatically convert string into JS number format.

DEMO: [https://smikodanic.github.io/angular-form-validator/](https://smikodanic.github.io/angular-form-validator/)<br>
DEMO CODE: [https://github.com/smikodanic/angular-form-validator/blob/master/index.html](https://github.com/smikodanic/angular-form-validator/blob/master/index.html)


## 3. Integration

### If you use browserify in your angular project

```javascript
require('angular-form-validator');

var clientApp = angular.module('clientApp', [
    'ngFormValidator'
]);
```

### If you use compiled version (/dist/ folder) include it in HTML file

```html
<script src="... /angular-form-validator/dist/js/ngFormValidator.js"></script>
```

##### Also don't forget to include CSS file.
```html
<head>
	<link rel="stylesheet" type="text/css" href="./dist/css/ngFormValidator.css">
</head>
```


## 4. Angular Directive
Directive is **ngformValidator** and must be applied as a tag attribute.
Config (rules and error messages) are defined inside **config** object.

```html
<input type="text" list="countrylist" class="form-control"
	ng-model="firstName"
	ngform-validator="{type: 'number', min: ['Number must be min 45', 45]}"
	ngform-validator-options="{validateOn: 'keyup'}">

<p class="help-block" ng-cloak>{{errMsg.firstName}}</p> <!-- error output -->
```



## 5. Validation rules

#### TYPE VALIDATORS
- **string** - accepts any string value
- **number** - accepts integer or float numbers (12 , 12.23, 1.2e-21)
- **date** - accept valid date formats mm/dd/yy , mm/d/yyy hh:mm:ss , m.d.yy , mm.dd.hh and converts it automatically

#### MIN, MAX, BETWEEN
- **min** - If type:'number' then it will compare two numbers (input >= number). If type:'string' will validate number of characters.
- **max** - If type:'number' then it will compare two numbers (input <= number). If type:'string' will validate number of characters.
- **between** - If type:'number' (number1 <= input <= number2). If type:'string' will validate number of characters.

#### MISC
- **email** - Validate inserted email
- **sameAs** - compare two input fields (for example 'Password' and 'Repeat password')
- **emptySpaces** - clear empty spaces in a string (validator and corrector)
- **regex** - test input against regular expression
- **enum** - limit input string to offered values
- **url** - check if input is valid URL
- **price** - must be Number (type:'Number'), round number to 2 decimals

*(You are wellcome to make pull request and add extra validator functions.)*



## 6. Options

```html
ngform-validator-options="{validateOn: 'keyup'}"
```

- ***validateOn:*** 'change' | 'keyup' (or any other [jQuery event](https://api.jquery.com/category/events/) ) defines on which JS event field validation will take effect


*Notice: 'required' validation is onBlur by default and can't be changed.*



## 7. Disabling form fields and buttons
Submit button or input field can be disable on specific form field errors.

```html
//submit button is disable only when 'eml' or 'maxstr' have bad validations. Use ng-disabled dirctive.
<button type="button" class="btn btn-primary" ng-click="mySubmit()" ng-disabled="errMsg.eml || errMsg.maxstr">Submit</button>
```



## 8. Reseting form
To reset whole form and clear all errors use **ngform-validator-reset** directive. Reset will be activted on click.

```html
<button type="button" class="btn btn-warning" ngform-validator-reset>Reset</button>
```




## 9. Licence
*Copyright (c) 2016 Saša Mikodanić*

Licensed under [MIT](https://github.com/smikodanic/angular-form-validator/blob/master/LICENSE) .

*(Freely you received, freely give. , Mt10:8)*


