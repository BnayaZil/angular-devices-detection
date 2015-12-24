# angular-devices-detection
Angular Devices Detector come with provider that identify the user device and let you choose between two options, identify by user-agent(default) or by viewport(the css way).

## Get Started

#### Install

1. Get Angular-devices-detector in one of the following ways:
* Clone this [repository](https://github.com/BnayaZil/angular-devices-detection).
* And using npm:

```
npm install --save angular-devices-detector
```

2. Include ```angular-devices-detector.js``` (or ```angular-devices-detector.min.js```) in your ```index.html```, after including Angular itself.

3. Add ```angular-devices-detector```  to your main module's list of dependencies, it's should look like this:

```
var myApp = angular.module('myApp', ['angular-devices-detector']);
```
4. Config ```angular-devices-detector``` look like this:

```
myApp.config(['devicesDetectorProvider', function(devicesDetectorProvider){
	devicesDetectorProvider.init({desktop: 'desktop', mobile: 'mobile'});
}]);
```

#### Used

* ```angular-devices-detector``` is provider and he can help you to config your routes for example:

```
.state('/', {
	url: '',
	templateUrl: 'app/templates/homePage_' + devicesDetectorProvider.deviceTitle() + '.html',
	controller: 'homeCtrl'
})
```
```devicesDetectorProvider.deviceTitle()``` function return you the device title that you config

* ```angular-devices-detector``` also help you to choose the right template/controller in directives for example:

```
myApp.directive('directiveExample', ['deviceDetector', function(deviceDetector) {
	var template = 'app/directives/directiveName/directiveName' + devicesDetectorProvider.deviceTitle + 'Template.html';
	var ctrl = 'controllerName' + devicesDetectorProvider.deviceTitle + 'Ctrl.html';
	return {
		replace: true,
		templateUrl: template,
		controller: ctrl
	};
}]);
```