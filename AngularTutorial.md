# Codevolution Angular 5 Tutorial

[Youtube Link](https://www.youtube.com/watch?v=0eWrpsCLMJQ&list=PLC3y8-rFHvwhBRAgFinJR8KHIrCdTkZcZ)

[Github Link](https://www.youtube.com/redirect?q=https%3A%2F%2Fgithub.com%2Fgopinav&redir_token=4qOBqon9qk1YpzwfftzVX-bbTz18MTUyMzA4NDk2OUAxNTIyOTk4NTY5&event=video_description&v=0eWrpsCLMJQ)

## Angular CLI Commands

####Generate a new App

Run `ng new app-name` to generate a new app in the current folder.

####Launch the App

Run `ng serve` to  launch the app.

Run `ng serve --proxy-config proxy.conf.json` to launch the app and connect to the server specified in proxy.conf.json

Server config in proxy.conf.json can look like this:
    
    {
      "/api": {
	    "target": "http://localhost:12345/",
	    "secure": false
      }
    }

This connection can be used in a service like:

    this.baseUrl = baseUrl ? baseUrl : '/api';		<--- access the 'api' connection

	return this._http.get(baseUrl+"/data);			<--- fetch data

####Generate Components

Run `ng generate component component-name` to generate a new component.
 
Run `ng g c component-name` to generate a new component.

You can also use `ng generate directive/pipe/service/class/module`.

Notes:

* Components are created in a subdirectory be default - the subdirectory name is the component name. The filenames are <componentname>.component.ts/html/css.
* Services and Pipes are *not* created/scaffolded in a subdir by default, see below. 

####Generate Services and Models

To create a service in a subdirectory do the following:

	mkdir services
	ng g s services\myservice 

More examples:

	# typical folder structure
	mkdir services
	mkdir models

	ng g c models\user				# create a "User" model class
	ng g s services\user			# create a "UserService" service
	ng g s services\authentication 	# create a "AuthenticationService" service

## Building Blocks

### Modules
Every Module represents a feature area in the Application

e.g. User Module, Admin Module

Root Module = app-module

Every Module is made up of one or more Components and Services

#### Components 
Every Component controls a portion of the view - consisting of an HTML template and a TypeScript codebehind file that controls the logic of the view

e.g. Navigation Bar, Sidebar, Main Content

Root Component = app-component (tree structure - all other components are nested inside the root component)

The Component is declared by the Component Decorator, the 'templateUrl' and 'styleUrls' tell Angular where the HTML and CSS for this component are located. The 'selector' is the name to use in HTML Markup to declare this component.

    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })

A Component can be used in different ways, depending on the declaration of the selector:

`selector: 'app-componentname'`	will make the component available as an HTML element: `<app-componentname></app-componentname>`

`selector: '.app-componentname'`	will make the component available as a class name: `<div class="app-componentname"></div>`

`selector: '[app-componentname]'`	will make the component available as an attribute: `<div app-componentname"></div>`

#### Services
A Service is a class that contains the business logic of the Application


## Connecting the view to data

###Interpolation - works only with string values

Use `{{variable-name}}` to use the value of a variable in the HTML view

Can use `{{variable-name.member-name}}` (etc...) aswell

Can also use it with functions:

    {{2+2}}
    {{"Some String" + variable-name}}
    {{string-variable-name.length}}
    {{string-variable-name.toUpperCase}}
    {{string-variable-name.myCustomFunction}}

Can *NOT* assign variables 

    {{a=2+2}}
Can *NOT* access global javascript variables

    {{window.location.href}}
Use a variable in the component.ts for that:

    ----- component.ts ---------------------------------------------
    public siteUrl = window.location.href
    ----- component.html -------------------------------------------
    {{siteUrl}}

### Property Binding - can also work with boolean values

Attributes - Initial Values defined by HTML, read by using `(.getAttribute('value'))`

*Attributes initialize Properties with predefined values and then they are done. Their values cannot change once they are inizialized.*

Properties - Current Values defined by the DOM, read by using	`(.value)`

*Property values can change - they represent the current value.*


    ----- component.ts ---------------------------------------------
    public myId = "testId";
    ----- component.html -------------------------------------------
    <input [id]="myId" type="text" value="Vishwas">


binding a boolean Property like

    ----- component.html -------------------------------------------
    <input [disabled]="true" type="text" value="Vishwas">

using a boolean Variable like to make the view respond when the Variable value changes


    ----- component.ts ---------------------------------------------
    public isDisabled : boolean = true;

    ----- component.html -------------------------------------------
    <input [disabled]="isDisabled" type="text" value="Vishwas">

    ----- component.html (alternative syntax) ----------------------
    <input bind-disabled="isDisabled" type="text" value="Vishwas">

## CSS

### Class Binding

Instead of using static class declarations like `<h1 class="myHeadline"></h1>`

You can assign the class name to a property and bind the property to an html element using this syntax:

    ----- component.ts ----------------------------------
    public myClass = "myHeadline";

    ----- component.html --------------------------------
    <h1 [class]="myClass"></h1>

    ----- component.css ---------------------------------
    .myHeadline {
    	// ...
    }
    

Class Binding turns regular class assignments into dummy assignments, so only the bound classes will apply when using mixed syntax

    ----- component.html --------------------------------
    <h1 class="someClass" [class]="myClass"></h1>

In the example above, only myClass will apply

### Conditional Class Binding

####Single class

There is an alternative syntax that binds one class based on a truthy or falsy value. If true, the CSS is applied.

    ----- component.ts ----------------------------------
    public myClass = "myHeadline";
	public useCSS = true;

    ----- component.html --------------------------------
    <h1 [class.myClass]="useCSS"></h1>

    ----- component.css ---------------------------------
    .myHeadline {
    	// ...
    }

#### Multiple classes = ngClass Directive

To conditionally apply multiple classes, use the ngClass Directive. Assign the booleans in the typescript file to the class declarations.

    ----- component.ts ----------------------------------
    public messageClasses = {
		"text-success": !this.hasError,
		"text-danger": this.hasError,
		"text-special": this.isSpecial,
	}		

	public hasError = false;
	public isSpecial = true;

    ----- component.html --------------------------------
    <h1 [ngClass]="messageClasses"></h1>

    ----- component.css ---------------------------------
    .text-success {
    	// ...
    }
    .text-danger {
    	// ...
    }
    .text-special {
    	// ...
    }

## Parse JSON Data

There are several ways to parse JSON Objects into POCOs

###Observable Method

See YouTube for explanations

###"TryParse Method"

This method allows to parse an incoming object for the desired parameters, assign the values to the POCO if the parameters are found and assign default values to the POCO if the parameters are not found. Can be used in child classes aswell. 

    export class ParentClass
    {

      public name : string;
      public description : string;
      public address : number;
      public size : number;

	  public array_one ? : ChildClass[];

      static fromJS(data: any): ParentClass {
    		return new ParentClass(data);
      }
    
      constructor(data?: any) {
    
    if (data !== undefined) {
	      this.name = data["name"] !== undefined ? data["name"] : "No Name Specified";
	      this.description = data["description"] !== undefined ? data["description"] : "No Description";
	      this.address = data["address"] !== undefined ? data["address"] : 1;
	      this.size = data["size"] !== undefined ? data["size"] : 10;
	    
	      var parse_array = data["array_one"] !== undefined ? data["array_one"] : null;
	
	      this.array_one = new Array<ChildClass>();
	      for (let index = 0; index < parse_array.length; index++) {
		    const element = parse_array[index];
		    let newelement = new ChildClass(element);
		    this.array_one.push(newelement);
	      }
	    }   
      }
	}

    export class ChildClass
    {

      public childname : string;
      public childaddress : number;

      static fromJS(data: any): ParentClass {
    		return new ParentClass(data);
      }
    
      constructor(data?: any) {

      if (data !== undefined) {
	      this.childname = data["childname"] !== undefined ? data["childname"] : "No Child Name Specified";
	      this.childaddress = data["childaddress"] !== undefined ? data["childaddress"] : 0;
	  }
	}


The expression used here is evaluated as follows:

	      this.name = data["name"] !== undefined ? data["name"] : "No Name Specified";

*- if the json object has a property called "name" then assign its value to this.name*

*- if the json object does not have a property called "name" then assign "No Name Specified" to this.name*
		
## 08 Style Binding



## 09 Event Binding



## 10 Template Reference Variables



## 11 Two Way Binding



## 12 ngIf Directive



## 13 ngSwitch Directive



## 14 ngFor Directive



## 15 Component Interaction





 
