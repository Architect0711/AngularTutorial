# Angular 5 Tutorial

I use this document as a reference for Angular development. All code examples are copy & paste-able

[Codevolution Angular 5 Tutorial - Youtube](https://www.youtube.com/watch?v=0eWrpsCLMJQ&list=PLC3y8-rFHvwhBRAgFinJR8KHIrCdTkZcZ)

[Codevolution Angular 5 Tutorial - Github](https://www.youtube.com/redirect?q=https%3A%2F%2Fgithub.com%2Fgopinav&redir_token=4qOBqon9qk1YpzwfftzVX-bbTz18MTUyMzA4NDk2OUAxNTIyOTk4NTY5&event=video_description&v=0eWrpsCLMJQ)

[Kudvenkat Angular CRUD Tutorial - Youtube](https://www.youtube.com/playlist?list=PL6n9fhu94yhXwcl3a6rIfAI7QmGYIkfK5)

## Get the Prerequisites

### Step 1: Get Node Package Manager (npm)

##### Download npm [here](https://www.npmjs.com/get-npm).

### Step 2: Get Angular

##### Installing Angular from npm is described [here](https://angular.io/guide/quickstart). This link also leads to the official documentation of Angular.

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

## CSS
### Class Binding
Single class:

    <h1 class="myHeadline">Headline</h1>

Multiple classes:

    <h1 class="myHeadline frontPage anotherClass">Headline</h1>

### Fluent Class Binding


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

### Conditional Fluent Class Binding

####Single class

There is an alternative syntax that binds one class based on a truthy or falsy value. If true, the CSS is applied.

*component.ts*

	public useCSS = true;

*component.html*

    <h1 [class.myHeadline]="useCSS">Headline</h1>

*component.css*

    .myHeadline {
    	color: blue;
    }

#### Multiple classes = ngClass Directive

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

		
### Style Binding
Inline binding to a single style parameter works as follows:

    <h2 [style.color]="'orange'">Text</h2>

### Conditional Style Binding
Conditional Style Binding looks like this: if *hasError* is true, then Text is red. Else it is green.

*component.ts*

    public hasError = false;
    
*component.html*

    <h2 [style.color]="hasError ? 'red' : 'green'">Text</h2>

### Fluent Style Binding
If two styles are not enough for the desired application, it is possible to bind an element to a string value that can be changed at runtime.

*component.ts*

    public highlightColor = "orange";
    
*component.html*

    <h2 [style.color]="highlightColor">Text</h2>


## Data Flow inside a Component: Class => View

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

*component.ts*

    public siteUrl = window.location.href

*component.html*

    {{siteUrl}}

### Property Binding - can also work with boolean values

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


## Data Flow inside a Component: View => Class

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

## Two Way Data Binding inside a Component: View <=> Class
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




## Form Validation

Angular disables the browser native validation on forms by default. Since the validation messages appear different in every browser, it is better to use custom validation. 

####Reactivate native validation#

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



## Data Flow between Components:	Child => Parent
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

## Data Flow between Components:	Parent => Child

In the parent component, declare a variable to hold the value sent by the child component. Mark that variable with the input decorator (which needs to be imported aswell).

 *parent.component.ts*

    import { ... , Input } from '@angular/core';

	...

    @Input() childData = "";
	
*child.component.html*

    <app-child (outputEventEmitter)="childData=$event"></app-child>

## Control the UI from code => Structural Directives (TBD)

###ngIf	*(If Statement)*



###ngFor *(Foreach Statement)*



###ngSwitch *(Switch Case Statement)*



## Angular Specific HTML Elements

###ng-content	*(Allow other elements inside this element)*

ngcontent + ngif


## Pipes

Pipes allow to transform the data before showing it in the view. The data is *only* transformed for the view. The values of the properties in the class do *not* change

### String Pipes

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
	
### Number Pipes

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

### Date & Time Pipes

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

## Services and Dependency Injection

The TypeScript codebehind files in Angular are supposed to control the view *only*.To implement application logic and share data across components, Angular provides Services which can be injected into the classes with the built-in Dependency Injection.

There are a few steps to take:

####Define the Service
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


####Register the Service with the Injector
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

####Declare the Service as a Dependency in the classes where it is needed
Now add the Dependency in the Components that need the Service using Constructor Injection. Be sure to declare the Variable with a leading underscore (like  _*customerService* ), as this is a naming convention for variables injected with Dependency Injection. The Service can now be used to get the Customer Array. Again, this is a basic example with hardcoded data, in reality the Service would probably make an HTTP call to get some data or read the data from a database.

*customers.component.ts*

	import { CustomerService } from '../services/customer.service';

	...

	private customers : Customer[] = [];

	constructor(private _customerService: CustomerService) { }

	ngOnInit() {
		this.customers = this._customerService.getCustomers();
	}


## HTTP Requests: Using Data fetched with HTTP requests

There are several ways to parse received Objects into [POCOs](https://en.wikipedia.org/wiki/Plain_old_CLR_object)

###Standard Method: Observables

Angulars standard method for processing HTTP Responses is turning them into Observables (or Arrays of Observables). An Observable is a sequence of items that arrive asynchronously over time (when the HTTP call returns and HTTP response).

#####Send HTTP Request
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

*customer.service.ts*

	import { HttpClient } from '@angular/common/http';

	constructor(private _http: HttpClient) {
		this.headers = new Headers();
		this.headers.append('Content-Type', 'application/json');
		this.headers.append('Accept', 'application/json');
	}



#####Get Observable from HTTP Response and cast it into an Array of Objects
To cast the HTTP Response into an Array of Customer Objects, the Type Customer and an ICustomer Interface need to be created first. For the sake of simplicity, the Type and Interface will be declared inside the Service file.

*customer.service.ts*

	@Injectable()
	export class CustomerService {

	...

		getCustomers(url : string): Observable<ICustomer[]>{
	    	return this._http.get<ICustomer[]>(url);
	  	}
	}

	export interface ICustomer {
	  id : number;
	  firstname : string;
	  lastname : string;
	  company : string;
	}
	
	export class Customer {
	  public id : number;
	  public firstname : string;
	  public lastname : string;
	  public company : string;
	}



#####Subscribe to the Observable from the Components that need the Data
The Component that requires the Data fetched from the HTTP Server can now subscribe to the "getCustomers()" Method. The Argument to the Subscribe Method is a Lambda Expression that tells the Subscribe Method to assign its data to the "customers" Array.


	export class CustomersComponent implements OnInit {
	
	private customers : Customer[] = [];
	
	....
	
		ngOnInit() {
			this._customerService.getCustomers()
				.subscribe(data => this.customers = data);
		}
	}

#####Assign the Array to a local Variable





###"Try Parse Method"

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

##Routing

To navigate between views, Angular provides a Router. To use it, several steps are necessary.

######Please note: to copy & paste these examples, your Angular app requires a *customers* component and a *products* component. Otherwise, the code snippets need to be changed according to your actual application.

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


### Routing from a Button Click

In the app.component.html, create a nav bar that holds some buttons which will call the routes. Configure the routes that shall be called using the `routerLink` directive provided the by the RouterModule. The `<router-outlet></router-outlet>` component specifies where the components that were specified in the `appRoutes` Array will be shown.

*app.component.html*


	<nav class="navbar navbar-default">
		<ul class="nav navbar-nav">
			<li><a routerLink="customers">Customers</a></li>
			<li><a routerLink="products">Products</a></li>
		</ul>
	</nav>
	<router-outlet></router-outlet>