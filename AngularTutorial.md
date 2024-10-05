# Angular Tutorial

Angular is javascript popular framework which use full to create single page application,

### Setting up the local environment and workspace

###### for angular first you need to install node js you can instal it by using following link

https://nodejs.org/en/download

###### Install the Angular CLI using following command

`'npm install -g @angular/cli'`

now Angular dependency install in your computer

###### create project

you can create project using following command
`ng new my-app`

## Lifecycle hooks

###### ngOnChanges()

Respond when Angular sets or resets data-bound input properties. The method receives a SimpleChanges object of current and previous property values.it did not call if you did not specify input on child componant .

###### ngOnInit()

Initialize the directive or component after Angular first displays the data-bound properties and sets the directive or component's input properties. See details in Initializing a component or directive in this document.

###### ngDoCheck()

Detect and act upon changes that Angular can't or won't detect on its own.

###### ngAfterContentInit()

Respond after Angular projects external content into the component's view, or into the view that a directive is in.

###### ngAfterContentChecked()

Respond after Angular checks the content projected into the directive or component.

###### ngAfterViewInit()

Respond after Angular initializes the component's views and child views, or the view that contains the directive.

###### ngAfterViewChecked()

Respond after Angular checks the component's views and child views, or the view that contains the directive.

###### ngOnDestroy()

Cleanup just before Angular destroys the directive or component. Unsubscribe Observables and detach event handlers to avoid memory leaks

### View encapsulation

View encapsulation is a technique to manage a scope of style base on selection of ViewEncapsulation.

##### three type of View encapsulation

#### ViewEncapsulation.None

The styles of components are added to the <head> of the document, making them available throughout the application, so are completely global and affect any matching elements within the document.

```
@Component({
selector: 'app-no-encapsulation',
template: `
  <h2>None</h2>
  <div class="none-message">No encapsulation</div>
`,
styles: ['h2, .none-message { color: red; }'],
encapsulation: ViewEncapsulation.None,
})
export class NoEncapsulationComponent { }
```

Angular adds the styles for this component as global styles to the <head> of the document.

As already mentioned, Angular also adds the styles to all shadow DOM hosts, making the styles available throughout the whole application.

### ViewEncapsulation.Emulated

The styles of components are added to the <head> of the document, making them available throughout the application, but their selectors only affect elements within their respective components' templates.

```
@Component({
  selector: 'app-emulated-encapsulation',
  template: `
    <h2>Emulated</h2>
    <div class="emulated-message">Emulated encapsulation</div>
    <app-no-encapsulation></app-no-encapsulation>
  `,
  styles: ['h2, .emulated-message { color: green; }'],
  encapsulation: ViewEncapsulation.Emulated,
})
export class EmulatedEncapsulationComponent { }
```

Comparable to ViewEncapsulation.None, Angular adds the styles for this component to the <head> of the document, but with "scoped" styles.

Only the elements directly within this component's template are going to match its styles. Since the "scoped" styles from the EmulatedEncapsulationComponent are specific, they override the global styles from the NoEncapsulationComponent.

In this example, the EmulatedEncapsulationComponent contains a NoEncapsulationComponent, but NoEncapsulationComponent is still styled as expected since the EmulatedEncapsulationComponent 's "scoped" styles do not match elements in its template.

#### ViewEncapsulation.ShadowDom

The styles of components are only added to the shadow DOM host, ensuring that they only affect elements within their respective components' views.

```
@Component({
selector: 'app-shadow-dom-encapsulation',
template: `
  <h2>ShadowDom</h2>
  <div class="shadow-message">Shadow DOM encapsulation</div>
  <app-emulated-encapsulation></app-emulated-encapsulation>
  <app-no-encapsulation></app-no-encapsulation>
`,
styles: ['h2, .shadow-message { color: blue; }'],
encapsulation: ViewEncapsulation.ShadowDom,
})
export class ShadowDomEncapsulationComponent { }
```

In this example, the ShadowDomEncapsulationComponent contains both a NoEncapsulationComponent and EmulatedEncapsulationComponent.

The styles added by the ShadowDomEncapsulationComponent component are available throughout the shadow DOM of this component, and so to both the NoEncapsulationComponent and EmulatedEncapsulationComponent.

The EmulatedEncapsulationComponent has specific "scoped" styles, so the styling of this component's template is unaffected.

Since styles from ShadowDomEncapsulationComponent are added to the shadow host after the global styles, the h2 style overrides the style from the NoEncapsulationComponent. The result is that the h2 element in the NoEncapsulationComponent is colored blue rather than red, which may not be what the component's author intended.

### Component interaction

This cookbook contains recipes for common component communication scenarios in which two or more components share information.

###### Pass data from parent to child with input binding

To pass data between parent componant to child we need to use @input decorator in child componant and pass input value from parent
where we call child componant

for example

parent componant html

```
<app-child [myinput]="data" > </app-child>

```

child componant ts

```
@input('myinput') myinput :any

```

###### Sending data to a parent component

We can shared data between parent to child using @output decorator and eventEmiter

child componant ts

```
@Output() newItemEvent = new EventEmitter<string>();

  addNewItem(value: string) {
    this.newItemEvent.emit(value);
  }

```

parent componant html

```
<app-child (addNewItem)="addItem($event)" > <app-child/>

```

parent componant ts

```
addItem(event:any){
  console.log(event);
}
```

### Content projection

Content projection is a pattern in which you insert, or project, the content you want to use inside another component. For example, you could have a Card component that accepts content provided by another component.

#### Single-slot content projection

With this type of content projection, a component accepts content from a single source.

define following tag in child componant

```
 <ng-content></ng-content>

```

parent componant call chld using following code

```
<app-zippy-basic>
  <p>Is content projection cool?</p>
</app-zippy-basic>
```

#### Multi-slot content projection

In this scenario, a component accepts content from multiple sources.

To create a component that uses multi-slot content projection:

Create a component.

In the template for your component, add an <ng-content> element where you want the projected content to appear.

Add a select attribute to the <ng-content> elements. Angular supports selectors for any combination of tag name, attribute, CSS class, and the :not pseudo-class.

For example, the following component uses two <ng-content> elements.

```
  Default:
    <ng-content></ng-content>

    Question:
    <ng-content select="[question]"></ng-content>
```

```
<app-zippy-multislot>
  <p question>
    Is content projection cool?
  </p>
  <p>Let's learn about content projection!</p>
</app-zippy-multislot>
```

If your component includes an <ng-content> element without a select attribute, that instance receives all projected components that do not match any of the other <ng-content> elements.

In the preceding example, only the second <ng-content> element defines a select attribute. As a result, the first <ng-content> element receives any other content projected into the component.

#### Conditional content projection

Components that use conditional content projection render content only when specific conditions are met.

If your component needs to conditionally render content, or render content multiple times, you should configure that component to accept an <ng-template> element that contains the content you want to conditionally render.

Using an <ng-content> element in these cases is not recommended, because when the consumer of a component supplies the content, that content is always initialized, even if the component does not define an <ng-content> element or if that <ng-content> element is inside of an ngIf statement.

### interpolation

interpolation is technique to display ts variable value or expression inside html using `{{}}` this brackets

### Property binding

Property binding in Angular helps you set values for properties of HTML elements or directives. Use property binding to do things such as toggle button functionality, set paths programmatically, and share values between components.

##### Binding to a property

To bind to an element's property, enclose it in square brackets, [], which identifies the property as a target property. A target property is the DOM property to which you want to assign a value. For example, the target property in the following code is the image element's src property.

```

<img alt="item" [src]="itemImageUrl">

```

Another example is disabling a button when the component says that it isUnchanged:

```
<!-- Bind button disabled state to `isUnchanged` property -->
<button type="button" [disabled]="isUnchanged">Disabled Button</button>
```

#### Attribute bindings

Attribute binding in Angular helps you set values for attributes directly. With attribute binding, you can improve accessibility, style your application dynamically, and manage multiple CSS classes or styles simultaneously.
Attribute binding syntax resembles property binding, but instead of an element property between brackets, you precede the name of the attribute with the prefix attr, followed by a dot.

for exmaple Binding ARIA attributes

#### Binding to an attribute

It is recommended that you set an element property with a property binding whenever possible. However, sometimes you don't have an element property to bind. In those situations, use attribute binding.

###### Binding ARIA attributes

```
<button type="button" [attr.aria-label]="actionName">{{actionName}} with Aria</button>

```

###### Binding to colspan

```
<!--  expression calculates colspan=2 -->
<tr><td [attr.colspan]="1 + 1">One-Two</td></tr>
```

## Class and style binding

Use class and style bindings to add and remove CSS class names from an element's class attribute and to set styles dynamically.

###### Binding to a single CSS class

To create a single class binding, type the following:

`[class.sale]="onSale"`

###### Binding to multiple CSS classes

```
[class]="classExpression"
```

classExpression can be form of following way

```
classExpression:any = "my-class-1 my-class-2 my-class-3"
classExpression:any = {foo: true, bar: false}
classExpression:any = ['foo', 'bar']

```

#### Event binding

Event binding lets you listen for and respond to user actions such as keystrokes, mouse movements, clicks, and touches.

#### Binding to events

To bind to an event you use the Angular event binding syntax. This syntax consists of a target event name within parentheses to the left of an equal sign, and a quoted template statement to the right. In the following example, the target event name is click and the template statement is onSave().

Event binding syntax

```
<button (click)="onSave()">Save</button>
```

#### Two-way binding

Two-way binding gives components in your application a way to share data. Use two-way binding to listen for events and update values simultaneously between parent and child components.

Two-way binding combines property binding with event binding:

Property binding sets a specific element property.
Event binding listens for an element change event.

#### Adding two-way data binding

Angular's two-way binding syntax is a combination of square brackets and parentheses, [()]. The [()] syntax combines the brackets of property binding, [], with the parentheses of event binding, (), as follows.

src/app/app.component.html

```
<app-sizer [(size)]="fontSizePx"></app-sizer>
```

##### @HostBinding and @HostListener in Angular

The HostBinding & HostListener are decorators in Angular. HostListener listens to host event#### Built-in directivesswhile HostBinding allows us to bind to a property of the host element.The host is an element on which we attach our component or directive. This feature allows us to take some action whenever the user performs some action on the host element.

#### Host Element

The host element is the element on which we attach our directive or component. Remember components are directives with a view (template).

For Example

Consider the following ttToggle directive. We built this directive in our tutorial custom directive in Angular. We attach it to a button element. Here the button element is the host element.

```
<button ttToggle>Click To Toggle</button>
```

In the following example for the apphighlight directive, p element is the host element

```
<div>
  <p apphighlight>
    <div>This text will be highlighted</div>
  </p>
</div>
```

#### Transforming Data Using Pipes

Use pipes to transform strings, currency amounts, dates, and other data for display. Pipes are simple functions to use in template expressions to accept an input value and return a transformed value. Pipes are useful because you can use them throughout your application, while only declaring each pipe once. For example, you would use a pipe to show a date as April 15, 1988 rather than the raw string format.

Angular provides built-in pipes for typical data transformations, including transformations for internationalization (i18n), which use locale information to format data. The following are commonly used built-in pipes for data formatting:

DatePipe: Formats a date value according to locale rules.
UpperCasePipe: Transforms text to all upper case.
LowerCasePipe: Transforms text to all lower case.
CurrencyPipe: Transforms a number to a currency string, formatted according to locale rules.
DecimalPipe: Transforms a number into a string with a decimal point, formatted according to locale rules.
PercentPipe: Transforms a number to a percentage string, formatted according to locale rules.

##### types of pipes
two types of pipes pure and impure

###### pure pipe

pure pipes are pipes which call when it detect changes in value
by default when we create custom pipes are pure pipe like follow.

```
@Pipe({
  name: 'testpipe',
  pure:true
})
```
###### impure pipe

impure pipes call everytime when it detech any change.
for example in object trasform case we need to use impure pipe
by default when we create custom pipes are pure pipe like follow.

```
@Pipe({
  name: 'testpipe',
  pure:false
})
```


##### creating custom pipes


by using following command ou can generate pipe file

```
ng g p pipename

```

Example

```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'testpipe'
})
export class TestpipePipe implements PipeTransform {

  transform(value: number, ...args: unknown[]): number {
    return this.findFact(value);
  }
  findFact(value:number){
    let fact = 1;
    for(let i =2 ; i<=value ; i++){

      fact = fact*i;
    }
    return fact;
  }

}

```

Let us look at the code in details

We need to import the Pipe & PipeTransform libraries from Angular. These libraries are part of the Angular Core

```
import {Pipe, PipeTransform} from '@angular/core';
```

Our class must implement the PipeTransform interface.

```
@pipe({
    name: 'tempConverter'
})
export class TempConverterPipe implements PipeTransform {


}
```

The PipeTransform interface defines only one method transform. The interface definition is as follows.

```
interface PipeTransform {
 transform(value: any, ...args: any[]): any
}
```

The first argument value is the value, that pipe needs to transform. We can also include any number of arguments. The method must return the final transformed data.

The following is Our implementation of the transform method. The first is Value and the second is the Unit. The unit expects either C (Convert to Celsius) or F ( convert to Fahrenheit). It converts the value received to either to Celsius or to Fahrenheit based on the Unit.


### directives

#### Built-in directives

Directives are classes that add additional behavior to elements in your Angular applications. Use Angular's built-in directives to manage forms, lists, styles, and what users see.

The different types of Angular directives are as follows:

Components directives -> with a template. This type of directive is the most common directive type.
Attribute directives  -> directives that change the appearance or behavior of an element, component, or another directive.
Structural directives -> directives that change the DOM layout by adding and removing DOM elements.

#### uide covers built-in attribute directives and structural directives.

#### Built-in attribute directives

Attribute directives listen to and modify the behavior of other HTML elements, attributes, properties, and components.

Many NgModules such as the RouterModule and the FormsModule define their own attribute directives. The most common attribute directives are as follows:

NgClass —> adds and removes a set of CSS classes.
NgStyle —> adds and removes a set of HTML styles.
NgModel —> adds two-way data binding to an HTML form element.

##### Building an attribute directive

This section walks you through creating a highlight directive that sets the background color of the host element to yellow.

To create a directive, use the CLI command ng generate directive.

```
ng generate directive highlight
```

The @Directive() decorator's configuration property specifies the directive's CSS attribute selector, [appHighlight].

Import ElementRef from @angular/core. ElementRef grants direct access to the host DOM element through its nativeElement property.

Add ElementRef in the directive's constructor() to inject a reference to the host DOM element, the element to which you apply appHighlight.

Add logic to the HighlightDirective class that sets the background to yellow.

src/app/highlight.directive.ts

```
import { Directive, ElementRef } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
    constructor(private el: ElementRef) {
       this.el.nativeElement.style.backgroundColor = 'yellow';
    }
}
```

Applying an attribute directive
To use the HighlightDirective, add a <p> element to the HTML template with the directive as an attribute.

src/app/app.component.html

```
<p appHighlight>Highlight me!</p>

```

##### Handling user events

This section shows you how to detect when a user mouses into or out of the element and to respond by setting or clearing the highlight color.

Import HostListener from '@angular/core'.

src/app/highlight.directive.ts (imports)

```
import { Directive, ElementRef, HostListener } from '@angular/core';
```

The handlers delegate to a helper method, highlight(), that sets the color on the host DOM element, el.

The complete directive is as follows:

src/app/highlight.directive.ts

```
@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {

  constructor(private el: ElementRef) { }


  @HostListener('mouseenter') onMouseEnter() {
    this.highlight('yellow');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.highlight('');
  }

  private highlight(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }

}
```

#### Passing values into an attribute directive

This section walks you through setting the highlight color while applying the HighlightDirective.

In highlight.directive.ts, import Input from @angular/core.

src/app/highlight.directive.ts (imports)

```
import { Directive, ElementRef, HostListener, Input } from '@angular/core';
Add an appHighlight @Input() property.
```

src/app/highlight.directive.ts

```
@Input() appHighlight = '';
```

In app.component.ts, add a color property to the AppComponent.

src/app/app.component.ts (class)
``
export class AppComponent {
color = 'yellow';
}

``

To simultaneously apply the directive and the color, use property binding with the appHighlight directive selector, setting it equal to color.

src/app/app.component.html (color)

```
<p [appHighlight]="color">Highlight me!</p>
```

The [appHighlight] attribute binding performs two tasks:

applies the highlighting directive to the <p> element
sets the directive's highlight color with a property binding

##### Binding to a second property

This section guides you through configuring your application so the developer can set the default color.

Add a second Input() property to HighlightDirective called defaultColor.

src/app/highlight.directive.ts (defaultColor)

```
@Input() defaultColor = '';
```

To bind to the AppComponent.color and fall back to "violet" as the default color, add the following HTML. In this case, the defaultColor binding doesn't use square brackets, [], because it is static.

src/app/app.component.html (defaultColor)

```
<p [appHighlight]="color" defaultColor="violet">
  Highlight me too!
</p>
```

##### Deactivating Angular processing with NgNonBindable

To prevent expression evaluation in the browser, add ngNonBindable to the host element. ngNonBindable deactivates interpolation, directives, and binding in templates.

In the following example, the expression {{ 1 + 1 }} renders just as it does in your code editor, and does not display 2.

src/app/app.component.html

```
<p>Use ngNonBindable to stop evaluation.</p>
<p ngNonBindable>This should not evaluate: {{ 1 + 1 }}</p>
```

Applying ngNonBindable to an element stops binding for that element's child elements. However, ngNonBindable still lets directives work on the element where you apply ngNonBindable. In the following example, the appHighlight directive is still active but Angular does not evaluate the expression {{ 1 + 1 }}.

src/app/app.component.html

```
<h3>ngNonBindable with a directive</h3>
<div ngNonBindable [appHighlight]="'yellow'">This should not evaluate: {{ 1 +1 }}, but will highlight yellow.
</div>
```

If you apply ngNonBindable to a parent element, Angular disables interpolation and binding of any sort, such as property binding or event binding, for the element's children.

#### Built-in structural directives

Structural directives are responsible for HTML layout. They shape or reshape the DOM's structure, typically by adding, removing, and manipulating the host elements to which they are attached.

This section introduces the most common built-in structural directives:

*NgIf     —> conditionally creates or disposes of subviews from the template.
*NgFor    —> repeat a node for each item in a list.
*NgSwitch —> a set of directives that switch among alternative views.

## Dependency injection in Angular

When you develop a smaller part of your system, like a module or a class, you may need to use features from other classes. For example, you may need an HTTP service to make backend calls. Dependency Injection, or DI, is a design pattern and mechanism for creating and delivering some parts of an application to other parts of an application that require them. Angular supports this design pattern and you can use it in your applications to increase flexibility and modularity.

For example if you created any service by using @injectable decorator then if you want to use this service in multiple componant then you just need to inject that service in your componant and now you can use that service method and property in your componant

you can also change that service acess by modifying there providers array

Note :- if you want to create seperate reference of this service in your componant then you just need to import this service 
in componant's provider section so now that compoant has seperate reference for this service .


## What is AOT and JIT Compiler in Angular ?

Difficulty Level : Easy
Last Updated : 05 Nov, 2020
An angular application mainly consists of HTML templates, their components which include various TypeScript files. There are some unit testing and configuration file. Whenever we run over an application, the browser cannot understand the code directly hence we have to compile our code.

##### What is Ahead of Time (AOT) compiler ?

All technologies Ahead of Time is a process of compiling higher-level language or intermediate language into a native machine code, which is system dependent.

In simple words, when you serve/build your angular application, the Ahead of Time compiler converts your code during the build time before your browser downloads and runs that code. From Angular 9, by default compiling option is set to true for ahead of time compiler.

#### Why should you use the Ahead of Time compiler ?

When you are using Ahead of Time Compiler, compilation only happens once, while you build your project.
We don’t have to ship the HTML templates and the Angular compiler whenever we enter a new component.
It can minimize the size of your application.
The browser does not need to compile the code in run time, it can directly render the application immediately, without waiting to compile the app first so, it provides quicker component rendering.
The Ahead of time compiler detects template error earlier. It detects and reports template binding errors during the build steps before users can see them.
AOT provides better security. It compiles HTML components and templates into JavaScript files long before they are served into the client display. So, there are no templates to read and no risky client-side HTML or JavaScript evaluation. This will reduce the chances of injections attacks.

#### How Ahead of Time works ?

We use Typescript, HTML, style-sheets to develop our Angular project and ng build –prod or ng build to build our source code into bundles which include JS files, index.html, style-sheets, and assets files.

Now Angular uses the angular compiler (whichever you have selected) to build source code, and they do it in three phases, which are code analysis, code generation and template type checking. At the end of this process, bundle size will be much smaller than the JIT compiler’s bundle size.

After that AOT builds this into a war file to deploy directly by using Heroku or by JBoss or by any other hosting that supports Node. And then we map this host to the domain by using a CNAME.

Now the clients can access your web application via the domain. The browser will download all necessary files like HTML, style-sheets, and JavaScript which is needed for the default view. At last, your application will get bootstrap and get rendered.

#### How to compile your app in ahead of time compiler:

For compiling your app in Ahead of time, you don’t have to do much, because from angular 9 default compiling option is set to Ahead of time. Just add –AoT at the end ng serve –aot.

##### What is the Just in Time (JIT) compiler ?

Just in time compiler provides compilation during the execution of the program at a run time before execution. In simple words, code get compiles when it’s needed, not at the build time.

#### Why and When Should you use Just In Time Compiler ?

Just in time compiler compiles each file separately and it’s mostly compiled in the browser. You don’t have to build your project again after changing your code.
Most compiling is done on the browser side, so it will take less compiling time.
If you have a big project or a situation where some of your components don’t come in use most of the time then you should use the Just in time compiler.
Just in Time compiler is best when your application is in local development

#### How Just in Time compiler Works?

Initially, compiler was responsible for converting a high-level language into machine language, which would then be converted into executable code.

Just in time compiler, compiles code at runtime which means instead of interpreting byte code at build time, it will compile byte code when that component is called.

##### A few important points:

In case of Just in time, not all code is compiled at the initial time. Only necessary component which are going to be needed at the starting of your application will be compiled. Then if the functionality is need in your project and it’s not in compiled code, that function or component will be compiled.
This process will help to reduce the burden on the CPU and make your app render fast.
One more interesting thing is, you can see and link to your source code in inspect mode because Just in Time, compiles your code with JIT mode and a map file.

##### Comparison between Ahead of Time (AOT) and Just in Time (JIT) –

JIT AOT
JIT downloads the compiler and compiles code exactly before Displaying in the browser. AOT has already complied with the code while building your application, so it doesn’t have to compile at runtime.
Loading in JIT is slower than the AOT because it needs to compile your application at runtime. Loading in AOT is much quicker than the JIT because it already has compiled your code at build time.
JIT is more suitable for development mode. AOT is much suitable in the case of Production mode.
Bundle size is higher compare to AOT. Bundle size optimized in AOT, in results AOT bundle size is half the size of JIT bundles.
You can run your app in JIT with this command:

ng build OR ng serve
To run your app in AOT you have to provide –aot at the end like:

ng build --aot OR ng serve --aot  
You can catch template binding error at display time. You can catch the template error at building your application.

### Conclusion:

You can compile your angular application in two ways: JIT and AOT. Both are suitable for a different scenario like you can use JIT for development mode and AOT is better in production mode. Implementing features and debugging is easy in JIT mode since you have to map files while AOT does not have it. However, that AOT provides a big benefit to angular developers for production mode by reducing bundle size and making your app render faster.

#### Lazy loading basics

This section introduces the basic procedure for configuring a lazy-loaded route. For a step-by-step example, see the step-by-step setup section on this page.

To lazy load Angular modules, use loadChildren (instead of component) in your AppRoutingModule routes configuration as follows.

AppRoutingModule (excerpt)

```
const routes: Routes = [
  {
    path: 'items',
    loadChildren: () => import('./items/items.module').then(m => m.ItemsModule)
  }
];

```

#### Step-by-step setup

There are two main steps to setting up a lazy-loaded feature module:

Create the feature module with the CLI, using the --route flag.
Configure the routes.

#### Create a feature module with routing

Next, you’ll need a feature module with a component to route to. To make one, enter the following command in the terminal, where customers is the name of the feature module. The path for loading the customers feature modules is also customers because it is specified with the --route option:

```
ng generate module customers --route customers --module app.module
```

## some concept

### Observable

- a stream of events to which observers can subscribe.

### Observer

- an object with next, error and complete methods, which subscribes to an observable.

### Subscription function

- the function which executes each time an observer subscribes to an observable.

### Producer

- the source of data for an observable, the thing that calls an observers next, error, and complete methods.

### Cold observable -

an observable which creates its producer.

### Hot observable -

an observable which closes over its producer.

### Finite observable -

an observable which completes.

### Infinite observable -

an observable which never completes.

### Unicast observable -

an observable whose emitted values are not shared amongst subscribers.

### Multicast observable -

an observable whose emitted values are shared amongst subscribers.

## LVY

### What is IVY?

Ivy is the pipeline of rendering and compilation of the next-generation. It is very advanced and offers advanced features that were not available before. The speed provided by it is amazing. The loading is very fast even in the networks that are slow. It is very simple to use without any complications. The bundle size is also reduced with its help. It was first available in the Angular version 8 with Angular Ivy opt-in.

Ivy is a complete rewrite of Angular’s rendering engine. In fact, it is the fourth rewrite of the engine and the third since Angular 2. But unlike rewrites two and three, Ivy promises huge improvements to your application. With Ivy, you can compile components more independently of each other. This improves development times since recompiling an application will only involve compiling the components that changed.

### Concepts of IVY

Locality and tree shaking are two key aspects that Ivy always considers. They both are able to make Ivy capable of what it can do. The process of independent compilation of every component with its information. The partial changes are compiled in the process that makes the process faster by not changing all the project files.

#### Tree Shaking

Tree shaking is a term that means removing unused code during the bundling process. This can be done by using tools like Rollup and Uglify ,During the build process, tree shaking tools use static analysis and eliminate the unused and unreferenced code .

#### Locality

The locality is the process of compiling each component independently with its own local information that rebuilds faster by compiling partial changes and not the entire project files. This increases the speed of your build process.

## Decorator
Decorators are a fundamental concept in TypeScript. Decorators are methods or design patterns that are labeled with a prefixed @ symbol and preceded by a class, method, or property.

#### Types of decorators:

###### Class Decorator
Class Decorators are the highest-level decorators that determine the purpose of the classes. They indicate to Angular that a specific class is a component or module. And the decorator enables us to declare this effect without having to write any code within the class.

for example @component is class decorator

###### Method Decorator:
Method decorators, as the name implies, are used to add functionality to the methods defined within our class

Example: @HostListener, is a good example of method decorators.

###### Property Decorator
These are the second most popular types of decorators. They enable us to enhance some of the properties in our classes.

There are many property decorators available for example @Input(), @Output, @ReadOnly(), @Override() 

###### Parameter Decorator
The arguments of your class constructors are decorated using parameter decorators.
Example  @inject()


## What are HTTP interceptors ?
it is work like middleware in angular .
Using the HttpClient, interceptors allow us to intercept incoming and outgoing HTTP requests. They are capable of handling both HttpRequest and HttpResponse. We can edit or update the value of the request by intercepting the HTTP request, and we can perform some specified actions on a specific status code or message by intercepting the answer.


#### HostBinding

Host Binding binds a Host element property to a variable in the directive or component

### HostListener

Decorator that declares a DOM event to listen for, and provides a handler method to run when that event occurs.