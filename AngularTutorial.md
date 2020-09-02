# 0. Table Of Contents

<!-- TOC -->

- [0. Table Of Contents](#0-table-of-contents)
- [1. About](#1-about)
- [2. To Do](#2-to-do)
- [3. Get the Prerequisites](#3-get-the-prerequisites)
    - [3.1. Get Node Package Manager (npm)](#31-get-node-package-manager-npm)
    - [3.2. Get Angular](#32-get-angular)
- [4. Angular CLI Commands](#4-angular-cli-commands)
    - [4.1. Configure CLI Output](#41-configure-cli-output)
    - [4.2. Generate a new App](#42-generate-a-new-app)
    - [4.3. Launch the App](#43-launch-the-app)
    - [4.4. Generate Components](#44-generate-components)
    - [4.5. Generate Services and Models](#45-generate-services-and-models)
- [5. Building Blocks](#5-building-blocks)
    - [5.1. Modules](#51-modules)
    - [5.2. Components](#52-components)
    - [5.3. Services](#53-services)
- [6. CSS](#6-css)
    - [6.1. Class Binding](#61-class-binding)
    - [6.2. Fluent Class Binding](#62-fluent-class-binding)
    - [6.3. Conditional Fluent Class Binding](#63-conditional-fluent-class-binding)
        - [6.3.1. Single class](#631-single-class)
        - [6.3.2. Multiple Classes (ngClass Directive)](#632-multiple-classes-ngclass-directive)
    - [6.4. Style Binding](#64-style-binding)
    - [6.5. Conditional Style Binding](#65-conditional-style-binding)
    - [6.6. Fluent Style Binding](#66-fluent-style-binding)
- [7. One Way Data Binding](#7-one-way-data-binding)
    - [7.1. Class to View](#71-class-to-view)
        - [7.1.1. Interpolation (only works with string values)](#711-interpolation-only-works-with-string-values)
        - [7.1.2. Property Binding (can also work with boolean values)](#712-property-binding-can-also-work-with-boolean-values)
    - [7.2. View to Class](#72-view-to-class)
    - [7.3. Pipes](#73-pipes)
        - [7.3.1. String Pipes](#731-string-pipes)
        - [7.3.2. Number Pipes](#732-number-pipes)
        - [7.3.3. Date & Time Pipes](#733-date--time-pipes)
- [8. Two Way Data Binding](#8-two-way-data-binding)
    - [8.1. Data Flow between View and Class](#81-data-flow-between-view-and-class)
    - [8.2. Two Way Binding a Boolean Value to two Radio Buttons](#82-two-way-binding-a-boolean-value-to-two-radio-buttons)
    - [8.3. Two Way Binding String Values to a Dropdown List](#83-two-way-binding-string-values-to-a-dropdown-list)
    - [8.4. Two Way Binding DateTime Values to a DatePicker](#84-two-way-binding-datetime-values-to-a-datepicker)
        - [8.4.1. Install ngx-bootstrap](#841-install-ngx-bootstrap)
        - [8.4.2. Install bootstrap 3 or 4](#842-install-bootstrap-3-or-4)
        - [8.4.3. Either reference the bootstrap stylesheet in your *.angular-cli.json*](#843-either-reference-the-bootstrap-stylesheet-in-your-angular-clijson)
        - [8.4.4. Or reference the bootstrap stylesheet in your *index.html*](#844-or-reference-the-bootstrap-stylesheet-in-your-indexhtml)
        - [8.4.5. Import the desired component into the *app.modules.ts* and add it to the *imports* Array](#845-import-the-desired-component-into-the-appmodulests-and-add-it-to-the-imports-array)
        - [8.4.6. Reference the Datepicker stylesheet in *.angular-cli.json*](#846-reference-the-datepicker-stylesheet-in-angular-clijson)
        - [8.4.7. Declare a Datepicker in your Application](#847-declare-a-datepicker-in-your-application)
        - [8.4.8. Customize the Component](#848-customize-the-component)
        - [8.4.9. Customize the Input Date Format (TBD)](#849-customize-the-input-date-format-tbd)
    - [8.5. Two Way Binding a Complex Object from a Dropdown to another Object](#85-two-way-binding-a-complex-object-from-a-dropdown-to-another-object)
    - [8.6. Adding an Item to an Array from the View by selecting it from a Dropdown](#86-adding-an-item-to-an-array-from-the-view-by-selecting-it-from-a-dropdown)
    - [8.7. Removing an Item from an Array from the View by clicking a Table Row](#87-removing-an-item-from-an-array-from-the-view-by-clicking-a-table-row)
- [9. Forms in Angular](#9-forms-in-angular)
    - [9.1. [Template Driven Forms](https://angular.io/guide/forms)](#91-template-driven-formshttpsangularioguideforms)
        - [9.1.1. Template Reference Variable](#911-template-reference-variable)
        - [9.1.2. Angular Form Directives](#912-angular-form-directives)
        - [9.1.3. The ngSubmit directive](#913-the-ngsubmit-directive)
    - [9.2. [Model Driven Forms (Reactive Forms)](https://angular.io/guide/reactive-forms)](#92-model-driven-forms-reactive-formshttpsangularioguidereactive-forms)
        - [9.2.1. Form Validation](#921-form-validation)
        - [9.2.2. Reactivate native validation](#922-reactivate-native-validation)
        - [9.2.3. Custom validation](#923-custom-validation)
- [10. Data Flow Between Components](#10-data-flow-between-components)
    - [10.1. Child to Parent](#101-child-to-parent)
    - [10.2. Parent to Child](#102-parent-to-child)
    - [10.3. Data Flow between components called by Router outlet](#103-data-flow-between-components-called-by-router-outlet)
- [11. Structural Directives (TBD)](#11-structural-directives-tbd)
    - [11.1. ngIf	*(If Statement)*](#111-ngif	if-statement)
    - [11.2. ngFor *(Foreach Statement)*](#112-ngfor-foreach-statement)
    - [11.3. ngSwitch *(Switch Case Statement)*](#113-ngswitch-switch-case-statement)
- [12. Angular Specific HTML Elements](#12-angular-specific-html-elements)
    - [12.1. ng-content	*(Allow other elements inside this element)*](#121-ng-content	allow-other-elements-inside-this-element)
- [13. Services and Dependency Injection](#13-services-and-dependency-injection)
    - [13.1. Define the Service](#131-define-the-service)
    - [13.2. Register the Service with the Injector](#132-register-the-service-with-the-injector)
    - [13.3. Declare the Service as a Dependency in the classes where it is needed](#133-declare-the-service-as-a-dependency-in-the-classes-where-it-is-needed)
- [14. HTTP Requests](#14-http-requests)
    - [14.1. Cross-Origin-Requests: using CORS (TBD)](#141-cross-origin-requests-using-cors-tbd)
    - [14.2. Cross-Origin Requests: using Browser Proxy](#142-cross-origin-requests-using-browser-proxy)
    - [14.3. GET](#143-get)
        - [14.3.1. Standard Method: Observables](#1431-standard-method-observables)
            - [14.3.1.1. Send HTTP Request](#14311-send-http-request)
            - [14.3.1.2. Get Observable from HTTP Response and cast it into an Array of Objects](#14312-get-observable-from-http-response-and-cast-it-into-an-array-of-objects)
            - [14.3.1.3. Subscribe to the Observable from the Components that need the Data](#14313-subscribe-to-the-observable-from-the-components-that-need-the-data)
        - [14.3.2. The Try Parse Method](#1432-the-try-parse-method)
    - [14.4. POST](#144-post)
        - [14.4.1. Preflight the HTTP POST Request (TBD)](#1441-preflight-the-http-post-request-tbd)
        - [14.4.2. Subscribe to the POST Observable](#1442-subscribe-to-the-post-observable)
- [15. Routing](#15-routing)
    - [15.1. Routing from a Button Click](#151-routing-from-a-button-click)

<!-- /TOC -->

# 1. About

I use this document as a reference for Angular development. All code examples are copy & paste-able. Some code Examples work with complex Objects that were Parts of Programs I created or from Tutorials that I watched, so they need to be adapted to your specific use case. Also, I don't bother with removing all the css classes assigned to my HTML elements when I copy & paste my code in here.

[Codevolution Angular 5 Tutorial - Youtube](https://www.youtube.com/watch?v=0eWrpsCLMJQ&list=PLC3y8-rFHvwhBRAgFinJR8KHIrCdTkZcZ)

[Codevolution Angular 5 Tutorial - Github](https://www.youtube.com/redirect?q=https%3A%2F%2Fgithub.com%2Fgopinav&redir_token=4qOBqon9qk1YpzwfftzVX-bbTz18MTUyMzA4NDk2OUAxNTIyOTk4NTY5&event=video_description&v=0eWrpsCLMJQ)

[Kudvenkat Angular CRUD Tutorial - Youtube](https://www.youtube.com/playlist?list=PL6n9fhu94yhXwcl3a6rIfAI7QmGYIkfK5)

[Blog: Angular in Depth](https://blog.angularindepth.com/)

# 2. To Do

**Find a working Markdown Table of Contents Generator!!!**

How to customize the input date for Datepicker

Add links to the structural directive documentations and other ng directives

Add item from select to Array

# 3. Get the Prerequisites

## 3.1. Get Node Package Manager (npm)

Download npm [here](https://www.npmjs.com/get-npm).

## 3.2. Get Angular

Installing Angular from npm is described [here](https://angular.io/guide/setup-local). This link also leads to the official documentation of Angular.

# 4. Angular CLI Commands

## 4.1. Configure CLI Output

Run `set DEBUG=express:*` to enable debug output

Run `set DEBUG=` to disable debug output

## 4.2. Generate a new App

Run `ng new app-name` to generate a new app in the current folder.

Run `ng serve --proxy-config proxy.conf.json` to launch the app and use the proxy route specified in proxy.conf.json

## 4.3. Launch the App

Run `ng serve` to  launch the app.

## 4.4. Generate Components

Run `ng generate component component-name` to generate a new component.
 
Run `ng g c component-name` to generate a new component.

You can also use `ng generate directive/pipe/service/class/module`.

Notes:

* Components are created in a subdirectory be default - the subdirectory name is the component name. The filenames are <componentname>.component.ts/html/css.
* Services and Pipes are *not* created/scaffolded in a subdir by default, see below. 

## 4.5. Generate Services and Models

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

# 5. Building Blocks

## 5.1. Modules

Every Module represents a feature area in the Application

e.g. User Module, Admin Module

Root Module = app-module

Every Module is made up of one or more Components and Services

## 5.2. Components 

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

## 5.3. Services

A Service is a class that contains the business logic of the Application

# 6. CSS

## 6.1. Class Binding

Single class:

    <h1 class="myHeadline">Headline</h1>

Multiple classes:

    <h1 class="myHeadline frontPage anotherClass">Headline</h1>

## 6.2. Fluent Class Binding

You can assign the class name to a property and bind the property to an html element using this syntax:

*component.ts*

    public myClass = "myHeadline";

*component.html*

    <h1 [class]="myClass">Headline</h1>

*component.css*

    .myHeadline {
    	color: red;
	}
    

Class Binding turns regular class assignments into dummy assignments, so only the bound classes will apply when using mixed syntax

*component.html*

    <h1 class="someClass" [class]="myClass">Headline</h1>

In the example above, only myClass will apply

## 6.3. Conditional Fluent Class Binding

### 6.3.1. Single class

There is an alternative syntax that binds one class based on a truthy or falsy value. If true, the CSS is applied.

*component.ts*

	public useCSS = true;

*component.html*

    <h1 [class.myHeadline]="useCSS">Headline</h1>

*component.css*

    .myHeadline {
    	color: blue;
    }

### 6.3.2. Multiple Classes (ngClass Directive)

To conditionally apply multiple classes, use the ngClass Directive. Assign the booleans in the typescript file to the class declarations.

*component.ts*

	public hasError = false;
	public isSpecial = true;

    public messageClasses = {
		"text-success": !this.hasError,
		"text-danger": this.hasError,
		"text-special": this.isSpecial,
	}		

*component.html*

    <h2 [ngClass]="messageClasses">Some Text</h2>

*component.css*

    .text-success {
    	color: green;
    }
    .text-danger {
    	color: red;
    }
    .text-special {
    	font-style: italic;
    }

		
## 6.4. Style Binding

Inline binding to a single style parameter works as follows:

    <h2 [style.color]="'orange'">Text</h2>

## 6.5. Conditional Style Binding

Conditional Style Binding looks like this: if *hasError* is true, then Text is red. Else it is green.

*component.ts*

    public hasError = false;
    
*component.html*

    <h2 [style.color]="hasError ? 'red' : 'green'">Text</h2>

## 6.6. Fluent Style Binding

If two styles are not enough for the desired application, it is possible to bind an element to a string value that can be changed at runtime.

*component.ts*

    public highlightColor = "orange";
    
*component.html*

    <h2 [style.color]="highlightColor">Text</h2>

# 7. One Way Data Binding

## 7.1. Class to View

### 7.1.1. Interpolation (only works with string values)

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

*component.ts*

    public siteUrl = window.location.href

*component.html*

    {{siteUrl}}

### 7.1.2. Property Binding (can also work with boolean values)

Attributes - Initial Values defined by HTML, read by using `(.getAttribute('value'))`

*Attributes initialize Properties with predefined values and then they are done. Their values cannot change once they are inizialized.*

Properties - Current Values defined by the DOM, read by using	`(.value)`

*Property values can change - they represent the current value.*


*component.ts*

    public myId = "testId";

*component.html*

    <input [id]="myId" type="text" value="Vishwas">


binding a boolean Property like

*component.html*

    <input [disabled]="true" type="text" value="Vishwas">

using a boolean Variable to make the view respond when the Variable value changes

*component.ts*

    public isDisabled : boolean = true;

*component.html*

    <input [disabled]="isDisabled" type="text" value="Vishwas">

*component.html (alternative syntax)*

    <input bind-disabled="isDisabled" type="text" value="Vishwas">

## 7.2. View to Class

To interact with the typescript class from the view, Angular offers Event Binding. Simply add the type of Event like "click" to the Element and assign the name of the function that should be called to it.

*component.ts*

	private onClick() {
	  console.log("onClick");
	}
	    
*component.html*

    <button (click)="onClick()" type="button">Click Me</button>


Angular can also pass information about the event to the function

*component.ts*

	private onClick(event) {
	  console.log(event);
	}
	    
*component.html*

    <button (click)="onClick($event)" type="button">Click Me</button>

Angular can also pass user inputs to the class

*component.ts*

	logMessage(message) {
	  console.log(message);
	}
	    
*component.html*

	<input #myInput type="text">
    <button (click)="logMessage(myInput.value)">Click Me</button>

Angular can also execute code manually right from the HTML

*component.ts*

	public sometext = "";

	private onClick() {
	  console.log(sometext);
	}
	    
*component.html*

    <button (click)="sometext='this text was changed inline directly from HTML'" type="button">Click Me</button>
	<button (click)="onClick()" type="button">And me afterwards</button>

## 7.3. Pipes

Pipes allow to transform the data before showing it in the view. The data is *only* transformed for the view. The values of the properties in the class do *not* change

### 7.3.1. String Pipes

*component.ts*

    name = "StringPipeTest";
	title = "this is the title";
	slice = "0123456789";
	person = {
		"firstName": "John",
		"lastName": "Doe"
	}

*component.html*

display the string in all lowercase or all uppercase

    <h2>{{ name | lowercase }}</h2>
	<h2>{{ name | uppercase }}</h2>

display the string with first letter of every word capitalized

	<h2>{{ title | titlecase }}</h2>

display part of the string, starting with (zero-based) index 3

	<h2>{{ slice | slice:3 }}</h2>

display part of the string, starting with (zero-based) index 3 up to index 4

	<h2>{{ slice | slice:3:5 }}</h2>

display the string in lowercase

	<h2>{{ person | json }}</h2>
	
### 7.3.2. Number Pipes

*component.html*

number pipe specifies the number of digits and decimal digits: 
'1.2-3' = shows 5.678 - minimum number of digits = 1 - decimal digits minimum 2, maximum 3

    <h2>{{ 5.678 | number:'1.2-3' }}</h2>

shows 05.6780

    <h2>{{ 5.678 | number:'2.4-5' }}</h2>

shows 005.68

    <h2>{{ 5.678 | number:'3.1-2' }}</h2>

turns a decimal into its percentage => shows 25%

	<h2>{{ 0.25 | percent }}</h2>

no currency code: default shows $0.25 (US Dollars)

	<h2>{{ 0.25 | currency }}</h2>

currency code 'EUR': shows €0.25 (Euro) check the [ISO Currency Code List](https://en.wikipedia.org/wiki/ISO_4217) for more currency codes
 
	<h2>{{ 0.25 | currency: 'EUR' }}</h2>
													//  
	<h2>{{ 0.25 | currency: 'EUR' : code }}</h2>	//  shows the code instead of the currency sign: shows EUR0.25

### 7.3.3. Date & Time Pipes

*component.ts*

    date = new Date();

*component.html*

	<h2>{{date}}</h2>
	<h2>{{date | date:'short'}}</h2>
	<h2>{{date | date:'shortDate'}}</h2>
	<h2>{{date | date:'shortTime'}}</h2>
	<h2>{{date | date:'medium'}}</h2>
	<h2>{{date | date:'mediumDate'}}</h2>
	<h2>{{date | date:'mediumTime'}}</h2>
	<h2>{{date | date:'long'}}</h2>
	<h2>{{date | date:'longDate'}}</h2>
	<h2>{{date | date:'longTime'}}</h2>

# 8. Two Way Data Binding 

## 8.1. Data Flow between View and Class  

When working with input elements, it is essential that the model (in the class) and the user input (in the view) are always in sync. For this purpose, Angular provides the ngModel directive. 

The basic syntax is a Mix between [Propery Binding] and (Event Binding):

*component.ts*

	public name = "";
	    
*component.html*

	<input [(ngModel)]="name" type="text>
	{{name}}

To use the ngModel directive, we need to import the FormsModule from '@angular/forms'

 *app.module.ts*
    
	...

    import { FormsModule } from '@angular/forms';
    
	...
    
    
    @NgModule({
      declarations: [
			...
      ],
      imports: [
		...,
    	FormsModule
      ],
      providers: [],
      bootstrap: [AppComponent]
    })
    export class AppModule { }

## 8.2. Two Way Binding a Boolean Value to two Radio Buttons

To bind two Radio Buttons to a Model that has a boolean value, these steps must be taken:

1.) Give both inputs the same `name` attribute, so they can not be triggered at the same time. 

2.) Bind the inputs to the same same property. In this case, its the *isPrivate* property of the *Insurance* object.

3.) The *value* has to be set with square braces (Property Binding) to *"true"* or *"false"*

*component.html*

	<form #insurancesForm="ngForm">
        <div class="row dualRadio">
            <div>
                <input type="radio" name="private" [(ngModel)]="Insurance.isPrivate" [value]="false"><label>false</label>
            </div>
            <div>
                <input type="radio" name="private" [(ngModel)]="Insurance.isPrivate" [value]="true"><label>true</label>
            </div>
        </div>
	</form>

*component.ts*

	Insurance = new Insurance();

## 8.3. Two Way Binding String Values to a Dropdown List

To bind the String Values selected in a Dropdown to a Model, these steps must be taken:

1. Give both the label and the select the same `name` attribute, so they are linked. 

2. Use the ngModel directive as usual to bind the value of the dropdown to the Property. In this case, it is the `gender` Property of the `Patient` Object.

3. The *value* has to be set with square braces (Property Binding) to *"true"* or *"false"*

*component.html*

	<label for="gender">Gender</label>
	<select id="gender" name="gender" [(ngModel)]="Patient.gender">
	  <option *ngFor="let gender of genders">{{gender}}</option>
	</select>

*component.ts*

	Patient = new Patient();
	
	private genders : string[] = [
		"male",
		"female",
		"not sure"
	];

## 8.4. Two Way Binding DateTime Values to a DatePicker

It is bad practice to use the browser built-in DatePicker, because the implementation varies from browser to browser in terms of layout and data format. To achieve the same function, look and feel across all browsers, it is recommended to use a custom DatePicker. This example will be using the [Datepicker](https://valor-software.com/ngx-bootstrap/#/datepicker) from [Valor Software's ngx-bootstrap](https://valor-software.com/ngx-bootstrap/#/)

The [Getting Started Guide](https://valor-software.com/ngx-bootstrap/#/getting-started) provides Information about this, except for the part how to install bootstrap 3 / 4.

### 8.4.1. Install ngx-bootstrap

	npm install ngx-bootstrap --save

### 8.4.2. Install bootstrap 3 or 4

	npm install bootstrap@3 --save

	npm install bootstrap@4 --save

### 8.4.3. Either reference the bootstrap stylesheet in your *.angular-cli.json*

Find the *"styles"* section in your *.angular-cli.json* file and add the following line.

      "styles": [
		...
		"../node_modules/bootstrap/dist/css/bootstrap.min.css",
        ...
      ],

### 8.4.4. Or reference the bootstrap stylesheet in your *index.html*

Add one of these lines to the index.html of your application, depending on which version of bootstrap you installed.

*index.html*

	<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
	
	<link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" rel="stylesheet">

### 8.4.5. Import the desired component into the *app.modules.ts* and add it to the *imports* Array

In this example, we import the Datepicker. The [Datepicker Documentation Page](https://valor-software.com/ngx-bootstrap/#/datepicker) contains the import commands that have to be included.

*app.module.ts*

	// RECOMMENDED (doesn't work with system.js)
	import { BsDatepickerModule } from 'ngx-bootstrap/datepicker';

	// or
	import { BsDatepickerModule } from 'ngx-bootstrap';
	
	@NgModule({
	  imports: [BsDatepickerModule.forRoot(),...]
	})
	export class AppModule(){}

### 8.4.6. Reference the Datepicker stylesheet in *.angular-cli.json*

Find the *"styles"* section in your *.angular-cli.json* file and add another line that points to the component you want to use.

      "styles": [
		...
		"../node_modules/ngx-bootstrap/datepicker/bs-datepicker.css",
        ...
      ],

### 8.4.7. Declare a Datepicker in your Application

Declare an *input* and set its type to "text" (NOT "date"!) and add the *bsDatepicker* directive to the element as shown in the example below. Then just use the *[(ngModel)]* directive to bind the Datepicker to the Model's Date value (e.g. Birthday). 

*component.html*

	<div class="input">
		<label>Birthday</label>
		<input [(ngModel)]="selectedPatient.birthday" name="birthday" #birthdayControl="ngModel" bsDatepicker type="text">
	</div>		

*component.ts*
	
	public selectedPatient : Patient = new Patient();

### 8.4.8. Customize the Component

Check the [Theme Reference](https://valor-software.com/ngx-bootstrap/#/datepicker#themes) of the Component to find a proper Theme. Then Import the Config Object into the Component that uses the Datepicker. Then create a Property to hold the values. Check the definition in *bs-datepicker.config.d.ts* (right-click => Go to Definition in VS Code) to find all the Properties it has. Use the Object.assign() Method to assign the desired configuration to the Element. Then Property Bind the *datePickerConfig* Object to the bsConfig Property of the Datepicker in the HTML Tag.

*component.ts*
	
	import { BsDatepickerConfig } from 'ngx-bootstrap/datepicker'

	datePickerConfig: Partial<BsDatepickerConfig>;

	constructor(private _patientService: PatientService) { 
	    this.datePickerConfig = Object.assign({}, { containerClass: 'theme-dark-blue', showWeekNumbers: true});
	}

*component.html*
	
	<div class="input">
		<label>Birthday</label>
		<input [(ngModel)]="selectedPatient.birthday" name="birthday" #birthdayControl="ngModel" bsDatepicker [bsConfig]="datePickerConfig" type="text">
	</div>		

### 8.4.9. Customize the Input Date Format (TBD)

I used the ngModel directive to bind the Datepicker to the Birthday Property of my Model. 
Now my Forms Model accepts the Value from the Datepicker just fine (View => Class). The Format looks like this: 

`"2018-04-19T08:35:25.000Z"`

But when I want the Datepicker to be set from the Property of the Model (Class => View), it sais 'Invalid date'. Then the Format looks like this: 

`"2018-04-17T00:00:00+02:00"`

This is of course not the desired behavior. The Datepicker be able to assign a value to the Patient Object, but it should also be able to show the initial value when the Patient is loaded and his / her Birthday has a different Format.

## 8.5. Two Way Binding a Complex Object from a Dropdown to another Object

The Data Types in this example are like a simple Web Shop would use them. An *Item* Object is bound to a *Customer* Object. To work with the *Item* Object-Oriented, it is insufficient to bind the ID of the Item (if it even has one...) or a string representation. The *Customer* has a Property e.g. MyItem, which is of Type Item, so the expected behavior is to bind an Item-Object to that Property. And this is the Syntax:

*component.html*

      <div class="form-group">
        <label for="singleItem">Dropdown for assigning a single Object</label>
        <select required id="singleItem"  class="form-control inputResize" #singleItemControl="ngModel" name="singleItem" [(ngModel)]="selectedCustomer.singleItem">
          <option *ngFor="let item of items" [ngValue]="item">{{item.description}}</option>
        </select>
      </div>

The [ngValue] directive is the key here. It is bound directly to the "item" from the **ngFor* directive, so it points to the object itself. Using [value]="item" isn't going to do the trick, it is just going to bind a string to the Property *selectedCustomer.singleItem*.

## 8.6. Adding an Item to an Array from the View by selecting it from a Dropdown

## 8.7. Removing an Item from an Array from the View by clicking a Table Row

Pass the index of the list view to an "onDelete" Method and delete the Object from the Array from there.

*component.html*

	<table class="listView" id="table">
		<tr>
		  <th>Delete Example</th>
		</tr>
		<tr *ngFor="let patient of patients; index as i" title={{patient.patientId}} (click)="onDeletePatient(i)">
		  <td>{{patient.lastName}}, {{patient.firstName}}</td>
		</tr>
	</table>

*component.ts*

	onDeletePatients(i: number) {
		this.patients.splice(i, 1);
	}

# 9. Forms in Angular

Most applications require some type of Form elements that the user can interact with to enter new data or change existing data. There are two different ways to create Forms in Angular. Template Driven Forms, which are used for simple Forms or Model Driven Forms (Reactive Forms), which allow for more complex Forms that use cross-field validation etc.

## 9.1. [Template Driven Forms](https://angular.io/guide/forms)

### 9.1.1. Template Reference Variable

`#employeeForm` is called the Template Reference Variable. Notice `ngForm` was assigned as the value for the Template Reference Variable `employeeForm`. So `employeeForm` variable holds a reference to the form. When Angular sees a form tag, it automatically attaches the `ngForm` directive to it. The `ngForm` directive supplements the form element with additional features. It holds all the form controls that we create with `ngModel` directive and name attribute, and monitors their properties like value, dirty, touched, valid etc. The form also has all these properties.

### 9.1.2. Angular Form Directives

This is an example for a Template Driven Form. It uses the `ngModel` directive for Two-Way Databinding, although there is not underlying Object in the TypeScript class yet. The `ngForm` Directive also creates a dummy Object to hold the values in this Form, so this Directive is predestined to use with Object Oriented Programming. The Object can be displayed in the view using Interpolation with *json* Pipe: `{{employeeForm.value | json}}`. The `ngSubmit` directive is called when the button with `type="submit"` is clicked and passes the whole Template Reference Variable to the `saveEmployee()` Method.

*component.html*

	 <form #employeeForm="ngForm" (ngSubmit)="saveEmployee(employeeForm)">
	  <div class="panel panel-primary">
	    <div class="panel-heading">
	      <h3 class="panel-title">Create Employee</h3>
	    </div>
	    <div class="panel-body">
	
	      <div class="form-group">
	        <label for="fullName">Full Name</label>
	        <input id="fullName" type="text" class="form-control"
	               name="fullName" [(ngModel)]="fullName">
	      </div>
	
	      <div class="form-group">
	        <label for="email">Email</label>
	        <input id="email" type="text" class="form-control"
	               name="email" [(ngModel)]="email">
	      </div>
	
	    </div>
	    <div class="panel-footer">
	      <button class="btn btn-primary" type="submit">Save</button>
	    </div>
	  </div>
	</form>

	{{employeeForm.value | json}}

*component.ts*

    onSave(employeeForm: NgForm) {
    	console.log(employeeForm.value);
    }



### 9.1.3. The ngSubmit directive 

... submits the form when we hit the enter key or when we click the Submit button. When the form is submitted, the *saveEmployee()* method is called and we are passing it the employeeForm. We do not have this method yet. We will create it in the component class in just a bit.

## 9.2. [Model Driven Forms (Reactive Forms)](https://angular.io/guide/reactive-forms)

### 9.2.1. Form Validation

Angular disables the browser native validation on forms by default. Since the validation messages appear different in every browser, it is better to use custom validation. 

### 9.2.2. Reactivate native validation

Use the ngNativeValidate directive in the opening tag of the form to re-enable browser built-in validation. The text field in the example is set to required using the HTML5 *required* attribute. If the text field is left empty and the Submit button is clicked, the form will not be submitted and the browser will display its built-in validation attribute. Else, the form will be submitted and the code in the *onSave()* method is executed, which logs the value of the text field to the console. For more information on HTML5 validation attributes, click [this Link](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Form_validation).

*component.html*

    <form #textForm="ngForm" ngNativeValidate (ngSubmit)="onSave(textForm)">

            <div class="input">
                <label>Text</label>
                <input required [(ngModel)]="text" name="text" #textControl="ngModel" type="text">
            </div>
    
            <div>
                <button class="inputButton" type="submit">Submit</button>
            </div>

    </form>

*component.ts*

    import { NgForm } from '@angular/forms/forms';



    export class CustomersComponent implements OnInit {
        
      private text = "";
    
	  ....
    
      onSave(textForm: NgForm) {
    	console.log(textForm.value);
      }

    }

### 9.2.3. Custom validation

Luckily, when using Two Way Data Binding, Form fields have six Properties that help with handling their State:

- Pristine: Field has not been changed (it is the same as the Property's initial value)
- Dirty: Field *has* been changed (it is different from the Property's initial value)
- Valid: The Validation Attributes set to this Form Element have been met by the Content
- Invalid: The Validation Attributes set to this Form Element have *NOT* been met by the Content
- Touched: This is set to *true* when the User even so much as activates a Control (Putting the Cursor in a Textbox or Tabbing over it is enough)
- Untouched: User hasn't even touched the Control

The Form itself has these six Properties, too. So it is possible to check if *any* Form Control is *invalid* or has been *touched* etc...

Using these Properties, Angular can build its own Validation Messages. This example shows the basic implementation of Custom Validation: The Textbox has the *required* Attribue, so leaving it empty will result in the *valid* Property being set to *false* and the *invalid* Property being set to *true*.  The [hidden] Property of the *div* that displays the Error Message is set to the input's *valid* Property, so it is only shown when the input is *invalid*. The "Save" Button at the Bottom of the Form has the *invalid* Property of the entire 

*component.html*

    <form #patientForm="ngForm" (ngSubmit)="onSave(patientForm)">
	    <div class="input form-group">
	        <label>First Name</label>
	        <input required [(ngModel)]="selectedPatient.firstName" class="form-control" name="firstName" #firstNameControl="ngModel" type="text">
	    </div>
	    <div [hidden]="firstNameControl.valid"
	      class="alert alert-danger inputResize">
	      Please Enter the Patient's First Name
	    </div>
	
	....

        <div>
            <button [disabled]="patientForm.invalid" class="inputButton btn btn-success" type="submit">Save</button>
        </div>

	</form>

The following HTML can be copy pasted into a Form and used to display the values of a Form or Form Element.

*component.html*
        <table border=1 style="border-collapse:collapse; font-family:Arial; table-layout: fixed">
          <tr style="background-color:red; font-weight: bold">
            <td colspan="3" style="padding:3px; white-space:nowrap; width:100%">
              <h4 style="margin:2px;">Validation Properties: patientForm</h4>
            </td>
          </tr>
          <tr style="background-color:salmon; font-weight: bold">
            <td style="padding:10px; white-space:nowrap; width:33%">
              <div>touched : {{ patientForm.touched }}</div>
              <div>untouched : {{ patientForm.untouched }}</div>
            </td>
            <td style="padding:10px; white-space:nowrap; width:33%">
              <div>pristine : {{ patientForm.pristine }}</div>
              <div>dirty : {{ patientForm.dirty }}</div>
            </td>
            <td style="padding:10px; white-space:nowrap; width:33%">
              <div>valid : {{ patientForm.valid }}</div>
              <div>invalid : {{ patientForm.invalid }}</div>
            </td>
          </tr>
        </table>

# 10. Data Flow Between Components

## 10.1. Child to Parent

To send data from a child component to its parent component, Angular provides an Output mechanism with the EventEmitter class. The syntax works like this:

Declare an instance of the EventEmitter class and put the Output decorator on it. Be sure to import them both. Have the emitter emit a value in the click event of a button for example.

*child.component.ts*

    import { ... , EventEmitter, Output } from '@angular/core';

	...

    @Output() public outputEventEmitter = new EventEmitter();
	
	...
    
	private onButtonClick() {
	  console.log("Button Clicked");
	  this.outputEventEmitter.emit('Value');
	}
	
*child.component.html*

	<button (click)="onButtonClick()" type="button">Click Me!</button>

Then, in the parent component, declare a variable to hold the value sent by the child component. Mark that variable with the input decorator (which needs to be imported aswell).

*parent.component.ts*

    import { ... , Input } from '@angular/core';

	...

    @Input() childData = "";
	
*parent.component.html*

    <app-child (outputEventEmitter)="childData=$event"></app-child>

## 10.2. Parent to Child

To pass data into a Child Component, declare a Variable of the 

*parent.component.ts*

    parentData = "some string or number or complex type whatever";

*child.component.ts*

    @Input() importedParentData = "";
	
	
*parent.component.html*

    <app-child [importedParentData]="parentData"></app-child>

## 10.3. Data Flow between components called by Router outlet

[Example on Stackblitz](https://stackblitz.com/edit/passing-data-between-components-in-router-outlet-to-outside)




# 11. Structural Directives (TBD)

## 11.1. ngIf	*(If Statement)*

## 11.2. ngFor *(Foreach Statement)*

## 11.3. ngSwitch *(Switch Case Statement)*

# 12. Angular Specific HTML Elements

## 12.1. ng-content	*(Allow other elements inside this element)*

ngcontent + ngif

# 13. Services and Dependency Injection

The TypeScript codebehind files in Angular are supposed to control the view *only*.To implement application logic and share data across components, Angular provides Services which can be injected into the classes with the built-in Dependency Injection.

There are a few steps to take:

## 13.1. Define the Service

- Use Angular CLI to create a new service
- Add the logic to the service. In this example, the service will only be used to return a static array of customer objects

*customer.service.ts*

    getCustomers(){
	    return [
		    {"id": 1, "firstname": "Max", "lastname": "Mustermann", "company": "Muster AG"},
		    {"id": 2, "firstname": "Erika", "lastname": "Mustermann", "company": "Muster AG"},
		    {"id": 3, "firstname": "Hans", "lastname": "Mustermann", "company": "Arbeitslos"},
		    {"id": 4, "firstname": "Tobias", "lastname": "Mustermann", "company": "Muster Holding GmbH"}
	    ]
    }


## 13.2. Register the Service with the Injector

The place where the Service is registered for Dependency Injection matters, because Angular uses a hierarchical DI system. The Components are organized in a tree structure, and registering a Service in a Component (or Module) means that it will only be available in its child Components. So the best solution is to register the service is the AppModule, which is the root of every Angular App.

So Import the Service and add it to the 'providers' Array

*app.module.ts*

	import { CustomerService } from './services/customer.service';


	@NgModule({
	  declarations: [...],
	  imports: [...],
	  providers: [CustomerService],
	  bootstrap: [...]
	})

## 13.3. Declare the Service as a Dependency in the classes where it is needed

Now add the Dependency in the Components that need the Service using Constructor Injection. Be sure to declare the Variable with a leading underscore (like  _*customerService* ), as this is a naming convention for variables injected with Dependency Injection. The Service can now be used to get the Customer Array. Again, this is a basic example with hardcoded data, in reality the Service would probably make an HTTP call to get some data or read the data from a database.

*customers.component.ts*

	import { CustomerService } from '../services/customer.service';

	...

	private customers : Customer[] = [];

	constructor(private _customerService: CustomerService) { }

	ngOnInit() {
		this.customers = this._customerService.getCustomers();
	}


# 14. HTTP Requests

[Angular-University.io - Guide for Old Http Module, but many things are still relevant](https://blog.angular-university.io/angular-http/)

The [Same-origin policy](https://en.wikipedia.org/wiki/Same-origin_policy) permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin. An origin is defined as a combination of URI scheme, host name, and port number. This policy prevents a malicious script on one page from obtaining access to sensitive data on another web page through that page's Document Object Model. So an Angular Application making the Request by itself will throw an Error like *"No 'Access-Control-Allow-Origin' header is present on the requested resource."*. There are two ways to handle the situation: [Enabling CORS](https://enable-cors.org/index.html), which requires Client & Server side Configuration, or using a Browser Proxy to make the Request for the Angular App, which requires Client side Configuration only.

## 14.1. Cross-Origin-Requests: using CORS (TBD)

[CORS Client Side](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

[CORS Server Side](https://developer.mozilla.org/en-US/docs/Web/HTTP/Server-Side_Access_Control)

## 14.2. Cross-Origin Requests: using Browser Proxy

The Browser can do the Request for the Angular Application, thus eliminating the need to configure the Server for Cross-Origin-Resource-Sharing. This Method only requires the Configuration of the Client. It makes use of a *.json* file to configure the Client.

- in the Application Main Folder (same Folder as .angular.cli.json), create a file for the proxy configuration, e.g. *proxy.conf.json*

- copy the following text into that file and configure the "target" parameter according to the target URL:

		{
			"/api": {
			    "target": "http://localhost:12345/",
			    "secure": false
			}
		}


This connection can now be used in a service like:

    this.baseUrl = baseUrl ? baseUrl : '/api';		<--- access the 'api' connection

	return this._http.get(baseUrl+"/data);			<--- fetch data from api endpoint "/data"

All requests to /api will be made to the URL specified as "target" and will 

Run `ng serve --proxy-config proxy.conf.json` to launch the app and use the proxy route specified in proxy.conf.json

## 14.3. GET

There are several ways to parse received Objects into [POCOs](https://en.wikipedia.org/wiki/Plain_old_CLR_object)

### 14.3.1. Standard Method: Observables

Angulars standard method for processing HTTP Responses is turning them into Observables (or Arrays of Observables). An Observable is a sequence of items that arrive asynchronously over time (when the HTTP call returns and HTTP response).

#### 14.3.1.1. Send HTTP Request
To send an HTTP Request, the Service needs to use the HttpClientModule. To use it, the Module needs to be added to the imports Array in add.module.ts. This makes it available to the service for Dependency Injection. It does not need to be added to the providers Array like e.g. a Service, the HttpClientModule does that by itself.

*app.module.ts*

	import { HttpClientModule } from '@angular/common/http';

	@NgModule({
	  declarations: [...],
	  imports: [HttpClientModule],
	  providers: [...],
	  bootstrap: [...]
	})

Inject the HttpClient into the Constructor of the Service. Depending on the Backend used, it may be desirable to configure the Service to work with JSON data as done in the Constructor here.

*patient.service.ts*

	import { HttpClient } from '@angular/common/http';

	constructor(private _http: HttpClient) {
		this.headers = new Headers();
		this.headers.append('Content-Type', 'application/json');
		this.headers.append('Accept', 'application/json');
	}

#### 14.3.1.2. Get Observable from HTTP Response and cast it into an Array of Objects

To cast the HTTP Response into an Array of Patient Objects, the Type Patient and an IPatient Interface need to be created first. For the sake of simplicity, the Type and Interface will be declared inside the Service file.

*patient.service.ts*

	@Injectable()
	export class PatientService {

	...

		getPatients(url : string): Observable<IPatient[]>{
	    	return this._http.get<IPatient[]>(url);
	  	}
	}

	export interface IPatient {
	  id : number;
	  firstname : string;
	  lastname : string;
	}
	
	export class Patient {
	  public id : number;
	  public firstname : string;
	  public lastname : string;
	}



#### 14.3.1.3. Subscribe to the Observable from the Components that need the Data

The Component that requires the Data fetched from the HTTP Server can now subscribe to the "getPatients()" Method. The Argument to the Subscribe Method is a Lambda Expression that tells the Subscribe Method to assign its data to the "customers" Array.


	export class PatientsComponent implements OnInit {
	
	private customers : Patient[] = [];
	
	....
	
		ngOnInit() {
			this._patientService.getPatients()
				.subscribe(data => this.patients = data);
		}
	}

### 14.3.2. The Try Parse Method

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

## 14.4. POST

*When working with an ASP.NET Web API & Entity Framework (like my PatientManagement Project), the Primary Key (in my case "patientId" must be set to 0 for a POST Request to work. The Api Controller will check the Value of the Primary Key and return a 400 Bad Request if the key is NULL!*

### 14.4.1. Preflight the HTTP POST Request (TBD)

### 14.4.2. Subscribe to the POST Observable

To save a newly created Object to the Backend, it is not enough to simply send a Patient Object to the PatientService and have the Service make a POST call. The HTTPClient in Angular will only execute that REST Call, if the Angular Application subscribes to the Observable that is returned by the HttpClient.post Method. To execute the call properly: have the Method in the Service that calls the HttpClient.post Method return the result of the HTTP call: `return this._http.post(this.baseUrl + "patients", body, this.httpOptions);`. Then, subscribe to the response (which is an Observable) in the Component Method: `this._patientService.postPatient(this.selectedPatient).subscribe(...);`. It is not necessary to assign the Response to a Variable, the *subscribe* Method can just make a console log for example.

*patient.component.ts*

	onSavePatient() {
	    this._patientService.postPatient(this.selectedPatient)
	                         .subscribe(() => console.log('patient saved successfully'),
	                         console.error
	                     );  
	  }

*patient.service.ts*
	
	postCustomer(patient: Patient) {
		let body = JSON.stringify(patient);
		return this._http.post(this.baseUrl + "patients", body, this.httpOptions);
	}

# 15. Routing

To navigate between views, Angular provides a Router. To use it, several steps are necessary.

***Please note**: This example was copied from a YouTube Tutorial. To copy & paste these examples, your Angular app requires a **customers** component and a **products** component. Otherwise, the code snippets need to be changed according to your actual application.*

In app.module.ts, import the RouterModule and Routes Object from @angular/router. Also declare an Array of type Routes that will hold the routes for the application. Now add the routes as shown below in the example for two components "customers" and "products". The last item in the example Array is used to configure what happens if the base URL of the application is called. In this case, the app will reroute the user to the customers route. Then add the Routermodule to the imports Array, passing the appRoutes Object using the forRoot method.

*app.module.ts*

    import { RouterModule, Routes } from '@angular/router';
    
    
    const appRoutes: Routes = [
      { path: 'customers', component: CustomersComponent },
      { path: 'products', component: ProductsComponent },
      { path: '', redirectTo: '/customers', pathMatch: 'full' }
    ];
    
	@NgModule({
	  declarations: [...],
	  imports: [
		...
	    RouterModule.forRoot(appRoutes),
	    ...
	  ],
	  providers: [...],
	  bootstrap: [...]
	})

## 15.1. Routing from a Button Click

In the app.component.html, create a nav bar that holds some buttons which will call the routes. Configure the routes that shall be called using the `routerLink` directive provided the by the RouterModule. The `<router-outlet></router-outlet>` component specifies where the components that were specified in the `appRoutes` Array will be shown.

*app.component.html*

	<nav class="navbar navbar-default">
		<ul class="nav navbar-nav">
			<li><a routerLink="customers">Customers</a></li>
			<li><a routerLink="products">Products</a></li>
		</ul>
	</nav>
	<router-outlet></router-outlet>