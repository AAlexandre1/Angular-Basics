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
Only works for something that returns a string in the end, or that can be converted into a string. You can also hard code a string {{ 'server }} Can also be used to call a method that returns a string
{{ setServerStatus() }}


# Property Binding
Square brackets are used for binding a property in HTML to code in JavaScript. 