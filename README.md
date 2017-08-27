# Notes-for-Angular-course

Open-source client-side JavaScript framework
Developed in 2009, mainetained by Google.
Actively developed and supported. 

Angular extend and adapt HTML vocabulary with additional declarations that are useful for web application.

AngularJS's design goals:
1. Separate DOM manipulation and application logic.
2. Decouple the client side of an application from the server side.
3. Provide structure for building app (UI designe, business logic, testing)

Features:
1. Two-way databinding
2. MVC/MVVM pattern, also include other parts.
3. Custom directives.
4. Form Validation.
5. Dependency Injection

Conceptual overview (https://docs.angularjs.org/guide/concepts)
Templates (file with HTML markup) -> compiler -> view
https://docs.angularjs.org/img/guide/concepts-databinding1.png
All variables live in sertain scope.
`ng-model` directive allow stores/updates the value of the input field into/from a variable.

Frameworks vs Libraries
Libraries are collection of utility classes/methods your code calsl upon to get some functionality. 
Frameworks, on the other hand, contain some functionality or flow and calls your code to extend or make the flow a specific one.

AngularJS modules
Roles:
1. Associate and app with a region of an HTML document (ng-app, by hand)
2. Help orginize the code and components in application.

angular.module
Params:
1. name (string)
2. requires (array of string)
3. config (callback)

Examples:
<html ng-app='app'></html>
angular.element(document).ready(()=>{ angular.bootstrap(document, ["app"]) });

angular.module(...) => module object
1. name
2. requires
3. controller
4. directive
5. component
6. filter
7. factory
8. service
9. provider
10. constant
11. value
12. decorator
13. config
14. run
15. animation

module.controller()
Params:
- name
- factory function
Params of factory function (do not depends from declared order)
- $scope
- any service

<div ng-controller="Company">

File naming
company-list.controller.js

Examples live


module.directive()
Types:
- built-in
- custom
Params:
- name
- factory function
Params of factory function (do not depends from declared order)
- $scope
- any service

function myDir(){
return {}; configuration object or function
}
Simple example

module.filter()
Params:
- name
- factory function that returns a Worker Function
Params of Worker function
- input data
- additional data

function myFilter(){
return function(input){ ... };
}

{{ expr | filterName: filterParam}}
$filter('filterName')
filterNameFilter

angular.service
angular.factory
angular.provider
angular.value
angular.const

Services are singleton objects
Built-in Services
- $filter
- $http
- $resource
Custom Services
Create your own

.service('myService', function(){ this.value = 5; });
.value('myVar', 10);
.constant('PI', 3.14);

Orginizing code: modules, files
One module, few modules
Files: 
- all together
- by type
- by feature
- by subfeatures

Minification-safe code
angular.module('app')
.controller('CompanyList', CompanyList);
function CompanyList($location){ ... };


angular.module('app')
.controller('CompanyList', CompanyList);
function CompanyList(e){ ... };

angular.module('app')
.controller('CompanyList', ["$location", CompanyList]);
function CompanyList(e){ ... };

angular.module('app')
.controller('CompanyList', CompanyList);
CompanyList.$inject = ['$location'];
function CompanyList(e){ ... };

angular.module('app')
.controller('CompanyList', CompanyList);
/*@ngInject*/
function CompanyList(e){ ... };

Module life cycle
- module.config()
- module.run()

angular.module('app')
.constant('KEY', '007');
.config(function($routeProvider){
  $routeProvider.when("/", {constroller: "Welcome", template: "welcome.html" });
})
.config(function(ConnectionProvider, KEY){
  ConnectionProvider.setKey(KEY);
});





