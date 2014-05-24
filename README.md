
# Code Snippets for Visual Studio development of AngularJS and Breeze apps

A collection of JavaScript code snippets for Visual Studio development of Breeze/AngularJS applications. 

## Download

[Download v1.0](https://github.com/Breeze/breeze.angular.snippets.git/archive/master.zip) (.zip)

## Installation

1. [Download the **breeze.angular.snippets** folder](https://github.com/Breeze/breeze.angular.snippets.git/archive/master.zip) and all of its contents.
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

For example, the ReSharper Angular Live Template shortcuts "ngm*" conflict with our snippets and override them. You can disable those templates as follows:

1. Open the Resharper Template Explorer from the VS menu
1. Locate the JavaScript templates with shortcuts that start "ngm"
1. Uncheck those templates

<a name="use-snippets"></a>
# Use the Snippets

You can insert IntelliSense Code Snippets by **typing the shortcut name of the snippet and pressing Tab** or by using the **Insert Code Snippet Menu**.

## Snippet Shortcuts

- In the Code Editor, put the cursor where you want to insert the code snippet.

- Type the letters of the shortcut.

- Press the TAB key once to invoke the code snippet. 

For example:

Type" ngapp&lt;tab>ngmc&lt;tab> 

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

**Press ESC** to conclude templating. It could look like this:

    angular.module('app').controller('todoController',
      ['$scope', '$q', 'someService', todoController]);
    
    function todoController($scope, $q, someService) {
        var vm = this;
        //your code here
    }

**You're almost done** ... but not quite. You have to fix the annotations array because Angular wants an array of strings, not (the more convenient) comma-separated string.

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
 
 2. On the Edit menu, point to IntelliSense, and then click Insert Snippet.
 
 3. Right-click the mouse and then select the Insert Snippet command on the shortcut menu.

- Select the code snippet from the code snippet inserter and then press TAB or ENTER, or double-click the snippet.

# Snippet Listing
[not just yet]

# Credit

These code snippets are based on the [work of Tyson Benson](https://github.com/tyson-benson/AngularJS-Snippets/) and [angularjs-livetpls](https://github.com/angularjs-livetpls/angularjs-webstorm-livetpls). 

Tyson appears to have stopped maintaining this repo. That's OK because many snippets have been modified to match the style we *currently* prefer and to align with the technologies we're using regularly. 

Changes include:

* Dropped the HTML snippets because we defer to Web Essentials (restore them from [Tyson's github site](https://github.com/tyson-benson/AngularJS-Snippets/) "Tyson's snippet github repo") if you want them.)

* Renamed the Angular and Jasmine shortcuts

* Rewrote the Angular snippets to suit our tastes

* Updated to Jasmine 2.0, adding a few more snippets
