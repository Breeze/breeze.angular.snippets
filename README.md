
# Code Snippets for development of Angular and Breeze apps in Visual Studio

A collection of JavaScript code snippets for Visual Studio development of Breeze/AngularJS applications. 

>Snippet listing
>
- [angular](#angular-snippets)
- [breeze](#breeze-snippets)
- [jasmine](#jasmine-snippets)
- [general](#general-snippets)
## Download

[Download v1.0](https://github.com/Breeze/breeze.angular.snippets/archive/master.zip) (.zip)

## Installation

1. [Download the **breeze.angular.snippets** folder](https://github.com/Breeze/breeze.angular.snippets/archive/master.zip) and all of its contents.
1. Extract the zip and drop the **breeze.angular.snippets** folder into the **Documents** > **Visual Studio 2013** > **Code Snippets** folder on your computer.
1. Delete the *.github* files (optional)
1. In Visual Studio, navigate to **Tools** > **Code Snippet Manager**.
1. Select language **JavaScript** from the language dropdown menu.
1. Select the **Add** button at the bottom.
1. Locate the *Documents/Visual Studio 2013/Code Snippets/breeze.angular.snippets* folder and click **Select Folder**.
1. You should now see **breeze.angular.snippets** in the listing of JavaScript snippets under the Code Snippet Manager.
1. Click **OK** to exit the Code Snippet Manager.
1. Restart Visual Studio  (snippets may not be available until you do)
1. Start [using the code snippets](#use-snippets)

## Shortcut conflicts

Some snippet shortcuts may conflict with angular-oriented shortcuts in other snippets or templates. You'll have to either change these shortcuts to suit yourself or disable the others.

For example, the ReSharper Angular Live Template shortcuts  that being "ngm\*" conflict with our snippets and override them. You can disable those templates as follows:

1. Open the Resharper Template Explorer from the VS menu
1. Locate the JavaScript templates with shortcuts that start "ngm"
1. Uncheck those templates

<a name="use-snippets"></a>
# Use the Snippets

You can insert IntelliSense Code Snippets by **typing the shortcut name of the snippet and pressing TAB** or by using the **Insert Code Snippet Menu**.

## Snippet Shortcuts

- In the Code Editor, put the cursor where you want to insert the code snippet.

- Type the letters of the shortcut.

- Press the TAB key once to invoke the code snippet. 

Let's try writing a controller. Begin by typing:

>ngapp&lt;tab>ngmc&lt;tab> 

You are hoping to see this:

    angular.module('app').controller('name', 
        ['$scope', name]);
    
    function name($scope) {
        var vm = this;
        //your code here
    }

The `name` and `$scope` and `//your code here` will be shaded to indicate these tokens are now alive. Your cursor is in the `name` token.

Enter "todoController" followed by TAB and all the `name` tokens are replaced.

Now the cursor is in the `$scope` token. Let's keep that one (we could delete it instead) and extend it with ", $q, someService". Then hit tab again. This time  both the inject annotation and the arguments to the "todoController" function are replaced.

Now the cursor is in the final `//your code here` token. 

**Press ESC twice** to conclude templating. It should look like this:

    angular.module('app').controller('todoController',
      ['$scope, $q, someService', todoController]);
    
    function todoController($scope, $q, someService) {
        var vm = this;
        //your code here
    }

**You're almost done** ... but not quite. You have to fix the annotations array because Angular wants an array of strings, not (the more convenient) comma-separated strings.

    ['$scope, $q, someService', todoController]);     // WRONG
    ['$scope', '$q', 'someService', todoController]); // RIGHT

Add the missing quotes in the annotations array to get this:

    angular.module('app').controller('todoController',
      ['$scope', '$q', 'someService', todoController]);
    
    function todoController($scope, $q, someService) {
        var vm = this;
        //your code here
    }

You are ready to start programming a controller that is annotated for safe Angular dependency injection.

## Insert Code Snippet Menu

- In the Code Editor, put the cursor where you want to insert the code snippet.

- Launch the Insert Code Snippet menu in one of three ways:

	1. Press CTRL+K, CTRL+X.
 
	1. On the Edit menu, point to IntelliSense, and then click Insert Snippet.
 
	1. Right-click the mouse and then select the Insert Snippet command on the shortcut menu.

- Select the code snippet from the code snippet inserter and then press TAB or ENTER, or double-click the snippet.

# Snippet Listing and examples
[Incomplete listing. Need to flesh it out.]

- [angular](#angular-snippets)
- [breeze](#breeze-snippets)
- [jasmine](#jasmine-snippets)
- [general](#general-snippets)


<a name="angular-snippets"></a>
## Angular module snippets

`ngapp` - reference the 'app' module

`ngmc` - controller

`ngmco` - module configuration

`ngmf` - factory

`ngmfi` - filter

`ngmod` - create a module

`ngmp` - provider

`ngmr` - reference to a module you can name

`ngms` - service 

###Examples (filled in)

    // ngmod
    angular.module('app', [
            'ngAnimate','ngRoute','ngSanitize',
            'breeze.angular'
    ]);

    // ngapp
    var app = angular.module('app');

    // ngmf
    app.factory('fooFac',
        ['$q', '$http', function (
          $q, $http) {
            console.log("fooFac defined");
            var fooFac = {
                //your code here
            }
            return fooFac;

        }]);

    // ngmc
    app.service('fooSvc',
        ['$window', 'fooFac', function (
          $window, fooFac) {
            this.foo = "have foo";

            console.log("fooSvc defined");
        }]);

    // ngmp
    app.provider('fooProv', function () {
        console.log("fooProProvider defined");
        var someConfig;
        this.useSomeConfig = function(value) { someConfig = value; };

        this.$get = ['fooSvc', fooProv];

        function fooProv(fooSvc) {
            console.log("fooPro defined; using someConfig="+someConfig);
        }

    });

    // ngmco
    app.config(['fooProvProvider',
      function (fooProvProvider) {
          console.log("fooProProvider configured");
          fooProvProvider.useSomeConfig("this config");

      }]);

    // ngmfi
    app.filter('fooFilt',
        [function () {
            console.log("fooFilter defined");
            return function (input, args) {

            }

        }]);

    // ngmc
    app.controller('GreetingController',
        ['common', 'datacontext', 'fooProv', 'fooFiltFilter', function (
          common, datacontext, fooProv, fooFilt) {
            var vm = this;
            vm.name = "Eileen";
            vm.greetings = [{ greeting: 'Hello' }, { greeting: 'Hola' }, { greeting: 'Bonjour' }];

        }]);

<a name="breeze-snippets"></a>
## Breeze Snippets
Snippets for Breeze are located in the *breeze* subdirectory.

`bze` - entityAspect with entityState as suggested property

`bzc` - create entity

`bzq` - EntityQuery with suggested callbacks

### Examples

    ^ - cursor when template ends

    //bzce
    manager.createEntity('type', {^});

    //bze – entityAspect with suggested 'entityState' property
    foo.entityAspect.entityState^

    //bzq – EntityQuery with callbacks (assumes $q available)
    EntityQuery.from(from)
      .using(manager).execute()
      .then(success).catch(fail);

    function success(data){
        ^
    }

    function fail(error){
        return $q.reject(error); // forward error to caller
    }

<a name="jasmine-snippets"></a>
## Jasmine Snippets

Snippets for Jasmine 2.0 specs are located in the *jasmine* subdirectory. 

They begin with **it** and **setup and teardown snippets**:

`aft` - after

`bef` - beforeEach

`befi`- beforeEach with ng-mock inject

`befm` - beforeEach with ng-mock module

`desc` - describe

`it` - 'it' spec

`iti` - 'it' with ng-mock inject

`ita` - async 'it' with 'done' function


**expectation snippets** are in the *expect* sub-sub-directory 

`xtb` - expect to be

`xtbct` expect to be close to

`xtbd` - expect to be defined

`xtbf` - expect to be falsey

`xtbgt` - expect to be greater than

`xtblt` - expect to be less than

`xtbn` - expect to be null

`xtbt` - expect to be truthy

`xtbu` - expect to be undefined

`xtc` - expect to contain

`xte` - expect to equal

`xthbc` - expect to have been called (spy)

`xthbcw` - expect to have been called with (spy)

`xtm` - expect to match

`xtth` - expect to throw

###Examples

    //desc
    describe('Jasmine code snippet samples', function () {

        //bef
        beforeEach(function () {

        });

        //befm
        beforeEach(module('app'));

        //befi
        beforeEach(inject(function (breeze, $q) {

        }));

        //aft
        afterEach(function () {

        });

        //it
        it('should expect true not to be false', function () {
            //xtb
            expect(true).not.toBe(false);

        });

        //iti
        it('should be defined', inject(function (breeze) {
            //xtbd
            expect(breeze).toBeDefined();

        }));

        //ita - async spec
        it('should call doit() after a delay', function (done) {
            var doit = jasmine.createSpy('doit');

            setTimeout(function () {
                doit();
                //xthbc
                expect(doit).toHaveBeenCalled();
                done();
            }, 10)
        });
    });

<a name="general-snippets"></a>
## General JS snippets

`fun`  - an anonymous function

`func` - a named function

`iife` - "immediately invoked function execution" boilerplate

`vma`  - ViewModel activate function (often in controllers)

### Examples

    ^ - cursor when template ends

    //fun
    function(parameters) {
        ^
    }

    //func
    function name(parameters) {
        ^
    }

    //iife
    ; (function(args){
        'use strict';

    ^

    }(dependencies));

    //vma
    vm.activate = activate;

    function activate() { 
        ^;
    }

# Credit

These code snippets are based on the [work of Tyson Benson](https://github.com/tyson-benson/AngularJS-Snippets/) and [angularjs-livetpls](https://github.com/angularjs-livetpls/angularjs-webstorm-livetpls). 

Tyson appears to have stopped maintaining this repo. That's OK because many snippets have been modified to match the style we *currently* prefer and to align with the technologies we're using regularly. 

Changes include:

* Dropped the HTML snippets because we defer to Web Essentials (restore them from [Tyson's github site](https://github.com/tyson-benson/AngularJS-Snippets/ "Tyson's snippet github repo") if you want them.)

* Renamed the Angular and Jasmine shortcuts

* Rewrote the Angular snippets to suit our tastes

* Updated to Jasmine 2.0, adding a few more snippets
