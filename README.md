# AngularJS: features and capabilities

AngularJS provides a variety of commands and features that help in building dynamic and interactive web applications. Below are some of the core features along with code snippets for each:

1. Modules
Modules are the basic building blocks of an AngularJS application. They contain different parts of the application such as controllers, services, filters, directives, etc.

javascript
Copy code
// Define a module
var app = angular.module('myApp', []);
2. Controllers
Controllers are JavaScript functions that are used to build the business logic of the application.

javascript
Copy code
// Define a controller
app.controller('myController', function($scope) {
  $scope.message = "Hello, World!";
});
html
Copy code
<!-- Use the controller in HTML -->
<div ng-app="myApp" ng-controller="myController">
  {{ message }}
</div>
3. Directives
Directives are special tokens in the markup that tell the library to do something to a DOM element (e.g., add behavior to an element).

html
Copy code
<!-- ng-model Directive -->
<div ng-app="myApp" ng-controller="myController">
  <input type="text" ng-model="name">
  <p>Hello, {{ name }}!</p>
</div>
4. Services
Services are singleton objects that are used to organize and share code across your app.

javascript
Copy code
// Define a service
app.service('myService', function() {
  this.sayHello = function() {
    return "Hello, Service!";
  };
});

// Use the service in a controller
app.controller('myController', function($scope, myService) {
  $scope.greeting = myService.sayHello();
});
5. Filters
Filters format the value of an expression for display to the user.

html
Copy code
<!-- Use a built-in filter -->
<div ng-app="myApp" ng-controller="myController">
  {{ price | currency }}
</div>
javascript
Copy code
// Define the data in the controller
app.controller('myController', function($scope) {
  $scope.price = 1234.56;
});
6. Two-Way Data Binding
Two-way data binding is a feature that synchronizes the model and the view.

html
Copy code
<!-- Example of two-way data binding -->
<div ng-app="myApp" ng-controller="myController">
  <input type="text" ng-model="name">
  <p>Hello, {{ name }}!</p>
</div>
7. ng-repeat
The ng-repeat directive repeats a set of HTML for each item in a collection.

html
Copy code
<!-- Example of ng-repeat -->
<div ng-app="myApp" ng-controller="myController">
  <ul>
    <li ng-repeat="item in items">{{ item }}</li>
  </ul>
</div>
javascript
Copy code
// Define the items in the controller
app.controller('myController', function($scope) {
  $scope.items = ['Item 1', 'Item 2', 'Item 3'];
});
8. ng-if
The ng-if directive conditionally includes a template based on the value of an expression.

html
Copy code
<!-- Example of ng-if -->
<div ng-app="myApp" ng-controller="myController">
  <p ng-if="showMessage">This is a conditional message.</p>
  <button ng-click="showMessage = !showMessage">Toggle Message</button>
</div>
javascript
Copy code
// Define the condition in the controller
app.controller('myController', function($scope) {
  $scope.showMessage = true;
});
9. ng-click
The ng-click directive specifies a custom behavior when an element is clicked.

html
Copy code
<!-- Example of ng-click -->
<div ng-app="myApp" ng-controller="myController">
  <button ng-click="incrementCounter()">Click Me!</button>
  <p>Clicked {{ counter }} times.</p>
</div>
javascript
Copy code
// Define the function and counter in the controller
app.controller('myController', function($scope) {
  $scope.counter = 0;
  $scope.incrementCounter = function() {
    $scope.counter++;
  };
});
10. Routing
AngularJS's routing mechanism allows you to create single-page applications with multiple views.

html
Copy code
<!-- Include the AngularJS route module -->
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.3/angular-route.js"></script>

<!-- Configure routes -->
<script>
var app = angular.module('myApp', ['ngRoute']);
app.config(function($routeProvider) {
  $routeProvider
    .when('/', {
      templateUrl: 'home.html',
      controller: 'HomeController'
    })
    .when('/about', {
      templateUrl: 'about.html',
      controller: 'AboutController'
    });
});
app.controller('HomeController', function($scope) {
  $scope.message = "Welcome to the Home Page";
});
app.controller('AboutController', function($scope) {
  $scope.message = "Welcome to the About Page";
});
</script>

<!-- Define the views -->
<div ng-view></div>
html
Copy code
<!-- home.html -->
<h1>{{ message }}</h1>

<!-- about.html -->
<h1>{{ message }}</h1>
11. Custom Directives
Custom directives allow you to create your own HTML tags with specific behavior.

javascript
Copy code
// Define a custom directive
app.directive('myDirective', function() {
  return {
    template: '<h1>Custom Directive!</h1>'
  };
});
html
Copy code
<!-- Use the custom directive -->
<div ng-app="myApp">
  <my-directive></my-directive>
</div>
These snippets cover the fundamental features of AngularJS. Each example illustrates a core concept and provides a base for you to build more complex applications. If you have any specific questions or need further details on any feature, feel free to ask!
