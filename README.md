# AngularJS: commands and features

AngularJS provides a variety of **commands** and **features** that help in building dynamic and interactive web applications

Below are some of the core features along with code snippets for each:

## 1. Modules

Modules are the basic building blocks of an AngularJS application

They **contain different parts of the application** such as controllers, services, filters, directives, etc

```javascript
// Define a module
var app = angular.module('myApp', []);
```

## 2. Controllers

Controllers are JavaScript functions that are used to build the **business logic** of the application

```javascript
// Define a controller
app.controller('myController', function($scope) {
  $scope.message = "Hello, World!";
});
```

```html
<!-- Use the controller in HTML -->
<div ng-app="myApp" ng-controller="myController">
  {{ message }}
</div>
```

## 3. Directives

Directives are special tokens in the markup that tell the library to **do something to a DOM element** (e.g., add behavior to an element)

```html
<!-- ng-model Directive -->
<div ng-app="myApp" ng-controller="myController">
  <input type="text" ng-model="name">
  <p>Hello, {{ name }}!</p>
</div>
```

## 4. Services

Services are singleton objects that are used to organize and **share code** across your app

```javascript
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
```

## 5. Filters

Filters **format** the value of an expression for display to the user

```html
<!-- Use a built-in filter -->
<div ng-app="myApp" ng-controller="myController">
  {{ price | currency }}
</div>
```

```javascript
// Define the data in the controller
app.controller('myController', function($scope) {
  $scope.price = 1234.56;
});
```

## 6. Two-Way Data Binding

Two-way data binding is a feature that **synchronizes the model and the view**

```html
<!-- Example of two-way data binding -->
<div ng-app="myApp" ng-controller="myController">
  <input type="text" ng-model="name">
  <p>Hello, {{ name }}!</p>
</div>
```

## 7. ng-repeat

The ng-repeat directive **repeats a set of HTML** for each item in a collection

```html
<!-- Example of ng-repeat -->
<div ng-app="myApp" ng-controller="myController">
  <ul>
    <li ng-repeat="item in items">{{ item }}</li>
  </ul>
</div>
```

```javascript
// Define the items in the controller
app.controller('myController', function($scope) {
  $scope.items = ['Item 1', 'Item 2', 'Item 3'];
});
```

## 8. ng-if

The ng-if directive **conditionally includes a template** based on the value of an expression

```html
<!-- Example of ng-if -->
<div ng-app="myApp" ng-controller="myController">
  <p ng-if="showMessage">This is a conditional message.</p>
  <button ng-click="showMessage = !showMessage">Toggle Message</button>
</div>
```

```javascript
// Define the condition in the controller
app.controller('myController', function($scope) {
  $scope.showMessage = true;
});
```

## 9. ng-click

The ng-click directive specifies a **custom behavior when an element is clicked**

```html
<!-- Example of ng-click -->
<div ng-app="myApp" ng-controller="myController">
  <button ng-click="incrementCounter()">Click Me!</button>
  <p>Clicked {{ counter }} times.</p>
</div>
```

```javascript
// Define the function and counter in the controller
app.controller('myController', function($scope) {
  $scope.counter = 0;
  $scope.incrementCounter = function() {
    $scope.counter++;
  };
});
```

## 10. Routing

AngularJS's routing mechanism allows you to create **single-page applications with multiple views**

```html
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
```

**home.html**

```html
<h1>{{ message }}</h1>
```

**about.html**

```html
<h1>{{ message }}</h1>
```

## 11. Custom Directives

Custom directives allow you to create your own HTML tags with specific behavior

```javascript
// Define a custom directive
app.directive('myDirective', function() {
  return {
    template: '<h1>Custom Directive!</h1>'
  };
});
```

Here are some **more advanced features of AngularJS**, along with code snippets for each capability:

## 12.  Custom Services

AngularJS allows you to create custom services that can be reused across your application

```javascript
// Define a custom service
app.service('MathService', function() {
  this.add = function(a, b) {
    return a + b;
  };
  this.subtract = function(a, b) {
    return a - b;
  };
});
```

```javascript
// Use the custom service in a controller
app.controller('CalcController', function($scope, MathService) {
  $scope.addNumbers = function() {
    $scope.result = MathService.add($scope.number1, $scope.number2);
  };
  $scope.subtractNumbers = function() {
    $scope.result = MathService.subtract($scope.number1, $scope.number2);
  };
});
```

```html
<!-- HTML to use the controller -->
<div ng-app="myApp" ng-controller="CalcController">
  <input type="number" ng-model="number1">
  <input type="number" ng-model="number2">
  <button ng-click="addNumbers()">Add</button>
  <button ng-click="subtractNumbers()">Subtract</button>
  <p>Result: {{ result }}</p>
</div>
```

##  13. Custom Filters

Custom filters allow you to create new ways to display data in your application

```javascript
// Define a custom filter
app.filter('reverse', function() {
  return function(input) {
    return input.split('').reverse().join('');
  };
});
```

```html
<!-- Use the custom filter in HTML -->
<div ng-app="myApp" ng-controller="myController">
  <p>Original: {{ message }}</p>
  <p>Reversed: {{ message | reverse }}</p>
</div>
javascript
Copy code
// Define the data in the controller
app.controller('myController', function($scope) {
  $scope.message = "Hello, World!";
});
```

## 14. Custom Directives with Isolated Scope

Custom directives can have an isolated scope, making them reusable and self-contained components

```javascript
Copy code
// Define a custom directive with isolated scope
app.directive('myCustomer', function() {
  return {
    restrict: 'E',
    scope: {
      customerInfo: '='
    },
    template: 'Name: {{ customerInfo.name }}<br> Address: {{ customerInfo.address }}'
  };
});
```

```html
<!-- Use the custom directive in HTML -->
<div ng-app="myApp" ng-controller="myController">
  <my-customer customer-info="customer"></my-customer>
</div>
```

```javascript
// Define the data in the controller
app.controller('myController', function($scope) {
  $scope.customer = {
    name: 'John Doe',
    address: '123 Main St'
  };
});
```

## 15. Promises with $q Service

The $q service helps you run functions asynchronously and use their return values when they are done processing

javascript
Copy code
// Define a service using $q
app.service('AsyncService', function($q) {
  this.fetchData = function() {
    var deferred = $q.defer();
    setTimeout(function() {
      deferred.resolve('Data received!');
    }, 2000);
    return deferred.promise;
  };
});
javascript
Copy code
// Use the service in a controller
app.controller('AsyncController', function($scope, AsyncService) {
  $scope.getData = function() {
    AsyncService.fetchData().then(function(response) {
      $scope.data = response;
    });
  };
});
html
Copy code
<!-- HTML to use the controller -->
<div ng-app="myApp" ng-controller="AsyncController">
  <button ng-click="getData()">Get Data</button>
  <p>{{ data }}</p>
</div>
5. Form Validation
AngularJS provides robust form validation mechanisms to handle user input and display validation messages.

html
Copy code
<!-- Form validation example -->
<div ng-app="myApp" ng-controller="myController">
  <form name="userForm">
    <input type="text" name="username" ng-model="username" required>
    <span ng-show="userForm.username.$dirty && userForm.username.$invalid">
      Username is required.
    </span>
    <br>
    <input type="email" name="email" ng-model="email" required>
    <span ng-show="userForm.email.$dirty && userForm.email.$invalid">
      Valid email is required.
    </span>
    <br>
    <button ng-disabled="userForm.$invalid">Submit</button>
  </form>
</div>
6. Dependency Injection
AngularJS uses dependency injection (DI) to achieve Inversion of Control. It allows you to inject dependencies directly into your controllers, services, and other components.

javascript
Copy code
// Define a service
app.service('GreetingService', function() {
  this.greet = function(name) {
    return "Hello, " + name + "!";
  };
});

// Inject the service into a controller
app.controller('GreetingController', function($scope, GreetingService) {
  $scope.name = 'John';
  $scope.greet = function() {
    $scope.message = GreetingService.greet($scope.name);
  };
});
html
Copy code
<!-- HTML to use the controller -->
<div ng-app="myApp" ng-controller="GreetingController">
  <input type="text" ng-model="name">
  <button ng-click="greet()">Greet</button>
  <p>{{ message }}</p>
</div>
7. Custom Events
AngularJS allows communication between controllers through custom events using $emit, $broadcast, and $on.

javascript
Copy code
// Define a controller to emit an event
app.controller('ParentController', function($scope) {
  $scope.broadcastEvent = function() {
    $scope.$broadcast('customEvent', 'Hello from Parent!');
  };
});

// Define a child controller to listen for the event
app.controller('ChildController', function($scope) {
  $scope.$on('customEvent', function(event, message) {
    $scope.receivedMessage = message;
  });
});
html
Copy code
<!-- HTML to use the controllers -->
<div ng-app="myApp" ng-controller="ParentController">
  <button ng-click="broadcastEvent()">Broadcast Event</button>
  <div ng-controller="ChildController">
    <p>{{ receivedMessage }}</p>
  </div>
</div>
8. Routing with Parameters
AngularJS routing can handle parameters, making it possible to create dynamic views.

html
Copy code
<!-- Include the AngularJS route module -->
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.3/angular-route.js"></script>

<!-- Configure routes with parameters -->
<script>
var app = angular.module('myApp', ['ngRoute']);
app.config(function($routeProvider) {
  $routeProvider
    .when('/user/:userId', {
      templateUrl: 'user.html',
      controller: 'UserController'
    });
});
app.controller('UserController', function($scope, $routeParams) {
  $scope.userId = $routeParams.userId;
});
</script>

<!-- Define the view with parameter -->
<div ng-view></div>
html
Copy code
<!-- user.html -->
<h1>User ID: {{ userId }}</h1>
9. Custom Decorators
Decorators allow you to modify or extend the behavior of services.

javascript
Copy code
// Define a decorator for a service
app.config(function($provide) {
  $provide.decorator('$log', function($delegate) {
    var originalLog = $delegate.log;
    $delegate.log = function(message) {
      message = 'Decorated: ' + message;
      originalLog.apply($delegate, arguments);
    };
    return $delegate;
  });
});
javascript
Copy code
// Use the decorated service in a controller
app.controller('LogController', function($scope, $log) {
  $log.log('Hello, World!');
});
html
Copy code
<!-- HTML to use the controller -->
<div ng-app="myApp" ng-controller="LogController"></div>
10. Animations
AngularJS supports animations via the ngAnimate module.

html
Copy code
<!-- Include the AngularJS animate module -->
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.3/angular-animate.js"></script>

<!-- Add ngAnimate to your module dependencies -->
<script>
var app = angular.module('myApp', ['ngAnimate']);
app.controller('AnimateController', function($scope) {
  $scope.show = true;
});
</script>

<!-- Define animations in CSS -->
<style>
.my-animation.ng-enter {
  transition: 0.5s linear all;
  opacity: 0;
}
.my-animation.ng-enter.ng-enter-active {
  opacity: 1;
}
.my-animation.ng-leave {
  transition: 0.5s linear all;
  opacity: 1;
}
.my-animation.ng-leave.ng-leave-active {
  opacity: 0;
}
</style>

<!-- Use ngAnimate in HTML -->
<div ng-app="myApp" ng-controller="AnimateController">
  <button ng-click="show = !show">Toggle</button>
  <div ng-if="show" class="my-animation">Animate me!</div>
</div>
These advanced features help you build more sophisticated and powerful applications with AngularJS.

```html
<!-- Use the custom directive -->
<div ng-app="myApp">
  <my-directive></my-directive>
</div>
```

These snippets cover the **fundamental features of AngularJS**

Each example illustrates a core concept and provides a base for you to build more complex applications


