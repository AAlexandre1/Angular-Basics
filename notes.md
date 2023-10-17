Angular Basics

Angular is a JS framework that changes the DOM (HTML) at runtime

app-root is a component created by the CLI

main.ts is the first script to be executed

platformBrowserDynamic().bootstrapModule(AppModule);
This line starts the Angular application by passing an app module to the method
AppModule refers to app.module.ts
Under @ngModule bootstrap lists all the components which 
Angular should know at the time it analyzes the index.html file

The main.ts file starts Angular and passes app.module as an argument. The module tells Angular to start the app component. Angular then reads the app componenet, and therefore knows the selector app-root. Now Angular is able to handle app-root in the index.html file and inserts the app component.


The app-root component holds the entire application. All other components are nested inside it. 

# Component
A component is just a TypeScript class. It allows Angular to create objects based on the blueprint.

Components can have their own code, styling, template, and logic. 
Components allow for a complex application to be split into reusable parts. Components can be used more than once allowing for easy replication of  logic and/or styling. It is easy to update, or exchange, individual components as compared to a single html file. 


# Creating a new component

The selectors for all components we create will be added to the app.component.html file, NOT the index.html file. The root component is where new components will be added. It's good practice to name the folder for a component the same as the nam of the component. 

When naming component files put the name of the component followed by component. For example a header component TypeScript file would be named: header.component.ts.
A search bar component html file would be named: search.component.html.

# Exporting a component

Exporting the component allows it to be used outside of the original component file. Export a component by entering export class followed by the component name and the description. For example a canvas component would be exported by typing: export class CanvasComponent. In order to denote to Angular that this is a component instead of a regular class, a decorator is used to enhance the class. Decorators can be used to enhance many elements other than classes. 

Use the component decorator. 
@Component()

This decorator is not known inherintly so it needs to be imported. It is imported from @angular/core
import { Component } from /'@angular/core';
The core package hold the core functionalities of Angular.

# Selector

Now that the @Component decorator is known to TypeScript, it will be able to parse this file and compile it to JavaScript. Now a JavaScript object needs to be passed on to the component decorator to configure it. Here we can enter some metadata that will tell Angular what to do with the class/cmoponent.

Now we can enter the selector which is essentially the HTML tag for this component. 
Make sure the selctor name you choose is UNIQUE so it doesn't overwrite any default HTML element. It is typical to prefix it with app- and then the name. 

The selector can now be used later to use this component in other component's HTML files. 

# Template

Use templateURL to reference an external HTML file. Create an HTML file for the component. Use the path for the HTML file for the template Url.


# AppModule

In app.module.ts

Angular uses modules to bundle components and pieces of the app into packages. The module(s) provide Angular information on the features and app has and uses. @NgModule is the decorator for the module. There are four properties on the object passed to @NgModule:
declarations,
imports,
providers, 
bootstrap
Bootstrap tells Angular which component to bew aware of when the app starts. 

In order to use a component you need to add it to the AppModule. Creating a file does not tell Angular that a component exists. It needs to be registrered in @NgModule to be used. To do that the component needs to be added to declarations. That alone does not tell TypeScript where to find the component it also needs to be imported. Use the correct file path. 

# Implementing custom components

Now the selector app-server is added to the app.component.html file as an element. In selector can be used multiple time to add a component more than once. 


# Generate a new component

Alternatively a new component could be generated using the terminal.
ng g c new-component-name
This will create a new component.
To create a component in a specific folder use:
ng g c folder-name/new-component-name
Make sure when creating a component this way that the CLI imports the new server to the app module. It should be imported at the top and in @NgModule under declarations.

# Component template
Every component Requires a template. Either a link to a template file or a template in the TypeScript file.
Instead of using an external template file, an inline template can be used. This defines the HTML code in the TypeScript code. 
To use inline template go to the ts file for the component. In the decorator change templateUrl to template. Write the template code where the template link was. When using single quotes do not add space or wrap the code. Using back ticks instead of single quotes allows it to support line wrapping and spaces.

# Component styles
Components can be styled by using the CSS file for the component. Multiple style sheets can be linked under the styleURLs. Styles can be defined in the ts file by replacing styleURLs with style and adding the css code. 


# Component Selector
Selectors should be unique. by adding square brackets around the selector it will select and element instead of an attribute. For example selecting an element would look like this:
selector: 'app-server'
Selecting an attribute would look like this:
selector: '[app-server]'
In the HTML code/template an element selector would look like:
<app-server></app-server>
An attribute selector would look like:
<div class="app-server"></div>
While an attribute can be used you can not use ID as a selector nor psuedo-selectore such as hover


# Databinding
Communication between your TypeScript code and your template(HTML)

Output data from Typescript code to the HTML file. 
Can use string interpolation {{ data }}
Or Property Binding [propertyName] = "data"

React to user events using event binding (event) = "expression"

Two-Way-Binding [(ngModel)] = "data"


# String interpolation
Data binding
{{ serverID }}
Only works for something that returns a string in the end, or that can be converted into a string. You can also hard code a string {{ 'server' }} Can also be used to call a method that returns a string
{{ setServerStatus() }}
Can only be used within a normal template. Can not be used within another expression of that template.


# Property Binding
Square brackets are used for binding a property of an HTML element to code in JavaScript.
<button [disabled = "!allowNewServer"]></button>
Do not use curly braces. Can also be used to call a method. This is not an HTML attribute, it is a syntax recognized by Angular.


# Property Binding vs String Interpolation
String interpolation will output the value of a property as a string
<p> {{ allowNewServer }} </p>
Use string interpolation to output text to something in your template.

Property binding will bind a property of an element to a property in your javaScript
<p [innerText = "allowNewServer"]></p>
Use property bindng to change the property of an HTML element, directive, or component.

NEVER mix property binding and string interpolation. Property binidng uses a syntax recognized by Angular. Between the quotation marks TypeScript can be used. Using string interpolation will break it. String interpolation can only be used within a normal template. It can not be used within another expression of that template.


# Event Binding
(eventName) = "callMethod()" 
<button (click) = "onCreateServer()">Add Server </button>
Allows JavaScript to listen to events.
Create a property in the ts file. Create a method. Using on at the beginning of the method name, i.e. onCreateServer, helps make it clear that the user will call the method. You can set the property to something. Use event binding to call the method. Use parentheses around the event you want to trigger the method. Set it equal to the method you want to execute. You can put the code directly there, but it is not a good idea. 

$event is a reserved variable name that can be used with event binding. $event gives us the event data that is emitted with that event. The type of event is Event. (event: Event) In the method we can target a part of the event.
this.serverName = event.target.value;
If you are unsure what to target, log the event to see what you want to target.
Not every element type will have a value. An input element will have a value. In order to specify that the element is type input, it can be explicitly informed.
(<HTMLInputElement>.target).value
This informs TypeScript that the type of the HTML element is an HTML input element. 

# Two Way Databinding
Combines event bidning and property binding. Combine the syntaxes of square brackets for property binding and parentheses for event binding. 
Must use a special directive, ngModel.
To use ngModel the FormsModule from angular/forms needs to be added to the imports[] array under @NgModule in the AppModule ts file.
import { FormsModule } from '@angular/forms'; 
Reacts to events in both directions. 

# Directives
Directive are instructions in the DOM. Components are directives with a template. Component slectors instruct Angular to add the content of the component template and the logic in the TypeSCript code in the place where the selector is. 

# Custom Directives
You can make custom directives. 
using the directive decorator a directive can be defined. 
@Directive({
   selector:'[directiveSelectorName]
})
The directive is then exported.
export class directiveSelector Name {
   directive code here
}
Directive are typically added with an attribute selector. The selector of a directive can be configured just like the selector of a component. A CSS class, or element style, can also be a a directive.


# Built-in Directives
Built in directives start with ng.
Structural directives change the structure of the DOM by adding or removing elements.
Attribute directives only change the element they are added to, and they look like normal HTML attributes. 

# ngIf
ngIf is a structural directive. It determines whether an element is added or not. When set to false the element is not hidden, it is not there. When set to true the elemnt is then added to the DOM The condition for adding the element is placed between the quotation marks. ngIf requires that the condition returns a boolean. 
Must use an asterisk before ngIf. 
<p *ngIf = "condition">Hello<p>

# ngIf Adding an else condition
Using ngIf else adds and else condition to ngIf.
To create an alternative use ng-template and a local reference.
<ng-template #noServer>
<p>Alternative text here.</p>
</ng-template>
Then add the else after the ngIf condition.
<p *ngIf = "serverCreated; else noServer">Original text here.</p>
Now if the condition is met the element is shown, if it is not met the the alternative template is shown instead. Can also use ngIf with a reverse check. ngIf = "!condition"

# ngStyle
ngStyle is an attribute directive. Allows you to dynamically update the style of an element. 
<p [ngStyle] = "{bacgroundColor: color}">
The square brackets are not a part of the directive name, they idicate that we are binding to a property of the directive. The property we are binding to is also called ngStyle. The ngStyle property expects a Javascript object. Then we define the key-value pair. The style name is the key, and the value of the style is the value. When making a JavaScript property name, the key, use 'background-color' in quotes,
<p [ngStyle] = "{'bacground-color': color}">
or use backgroundColor with camel case.
<p [ngStyle] = "{bacgroundColor: color}">
The value of the property can be hard coded in. 
<p [ngStyle] = "{bacgroundColor: blue}">
The value of the property can be a method that will return the correct value. 
<p [ngStyle] = "{bacgroundColor: getColor()}">


# ngClass
ngClass is an attribute directive. It allows us to dynamically add or remove CSS classes.
<p [ngClass] = "{online: this.serverStatus === 'onine'}" >
Reuqires property binding
The key should be the CSS class name and the value is the condition that determines if the class should be added to the element or not. If the class name has a dash wrap it in single quotes.
<p [ngClass] = "{'status-online': this.serverStatus === 'onine'}" >


# ngFor
ngFor is a structural directive. Allows you to create a node for each item in an array.
<p *ngFor = "let item of items "></p>
Remember to use an asterisk because this a structural directive. The name of the item does not matter. Once it is created here it becomes a variable that can be used elsewhere in the template. The name of the array has to match the array name in the TypeScript code. 
<p *ngFor = "let crazyChocolateCakes of books "></p>

# Getting index when using ngFor
*ngFor = "count of items; let i = index"
by using index you can use more than just incrementing or decrement numbrs as a check for ngStyle and ngClass. Using index will allow you access to the index of the current iteration. Index starts at zero, the fifth item will have the index of 4. The index can be bound to any variable you want. 
*ngFor = "cake of bakeryItems; let baking = index"


