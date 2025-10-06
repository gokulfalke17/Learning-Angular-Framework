


/*

 ***Angular***
 ==============


1. What is Angular?

Angular is a web application framework built by Google.
It allows you to build Single Page Applications (SPAs) using TypeScript, components, services, etc.
It handles data binding, dependency injection, routing, and more, so you don’t reinvent common tasks.




2. What is Angular CLI?

Angular CLI is a command-line tool to help create and manage Angular projects.
You use commands like ng new, ng serve, ng generate component, ng build.
It sets up boilerplate, configuration, and build pipeline for you.




3. Advantages of Angular

Structured & opinionated framework — gives you clear ways to build apps.
Two-way data binding, dependency injection, modular architecture speed up development.
Strong community, tooling (CLI, testing), and maintainability for large apps.

4. Hooks in Angular

Lifecycle hooks are special methods that Angular calls at specific times in the life of a component or directive.
They let you run custom logic when a component is created, updated, or destroyed.

1. ngOnChanges(changes: SimpleChanges)

When it runs: Called before ngOnInit and whenever an @Input() property value changes.
Use case: React when parent sends new data to child.
Example:

ngOnChanges(changes: SimpleChanges) {
  console.log('Input property changed:', changes);
}


2. ngOnInit()

When it runs: Once after first ngOnChanges. Called only once in component’s life.
Use case: Initialize data, call APIs, set up values.
Example:

ngOnInit() {
  console.log('Component initialized');
}


3. ngDoCheck()

When it runs: Every change detection cycle. Runs often, more than ngOnChanges.
Use case: Detect and act on changes that Angular doesn’t catch with @Input().
Example:

ngDoCheck() {
  console.log('Change detection cycle running');
}

4. ngAfterContentInit()

When it runs: Called once after Angular inserts external content (<ng-content>) into component.
Use case: Run logic after projected content is ready.
Example:

ngAfterContentInit() {
  console.log('ng-content projected');
}


5. ngAfterContentChecked()

When it runs: After every change detection cycle on projected content.
Use case: Respond to updates in projected content.
Example:

ngAfterContentChecked() {
  console.log('Projected content checked');
}


6. ngAfterViewInit()

When it runs: Called once after component’s view (child components & template) is initialized.
Use case: Access @ViewChild() or DOM elements safely.
Example:

ngAfterViewInit() {
  console.log('Component view initialized');
}


7. ngAfterViewChecked()

When it runs: After every change detection cycle of the component’s view.
Use case: Respond when view updates (but avoid performance-heavy logic here).
Example:

ngAfterViewChecked() {
  console.log('Component view checked');
}


8. ngOnDestroy()

When it runs: Just before Angular destroys the component.
Use case: Clean up subscriptions, intervals, or event listeners to avoid memory leaks.
Example:

ngOnDestroy() {
  console.log('Component destroyed');
}

Full Lifecycle Flow Order :
When a component is created → destroyed, hooks fire in this order:
ngOnChanges (when @Input changes)
ngOnInit (once)
ngDoCheck (every change detection)
ngAfterContentInit (once)
ngAfterContentChecked (after every content check)
ngAfterViewInit (once)
ngAfterViewChecked (after every view check)
ngOnDestroy (before component removed)


Init hooks: ngOnInit, ngAfterContentInit, ngAfterViewInit
Check hooks: ngDoCheck, ngAfterContentChecked, ngAfterViewChecked
Destroy hook: ngOnDestroy



5. What is the latest version of Angular?

As of now, the latest stable Angular version is Angular 20 (released May 2025) 
Prior versions include v19, v18, etc. 
You can check using ng version or look at the Angular releases page.



6. New Features in Angular 17

Introduces control flow syntax in templates (@if, @for, @switch) to simplify template logic 
Adds deferrable views (@defer blocks) to defer loading of parts of template to reduce bundle size 
Improvements in SSR/hydration, better performance, and tighter integration of new features like signals 



7. Difference between ng serve & ng start

Actually, ng start is not a standard Angular CLI command (typo/mistake); the correct commands are ng serve and ng start may be alias in some setups.
ng serve compiles the app in memory and serves it locally (development server).
If ng start exists in some projects, it generally is alias or wrapper for ng serve (via npm scripts).




8. What is a Component in Angular & its types

A component is a building block of an Angular app, composed of HTML, TypeScript logic, and CSS.
It encapsulates view, behavior, and data for a part of UI (for example, a button, form, list).
Types: standalone component, routed component, dumb/presentational, container/smart components, etc.



9. What is Standalone Component

Standalone components don’t need to be declared inside an NgModule.
You use @Component({ standalone: true, ... }).
They simplify module structure and reduce boilerplate.




10. What is Module (NgModule)

A module groups related parts of the app: components, directives, pipes, services.
Each Angular application has at least one root module (AppModule).
Modules also define what parts are exposed (exports) and what they depend on (imports).




11. What is Directive

A directive is a class with special behavior that can change DOM, attributes, or structure.
Types: structural (e.g. *ngIf, *ngFor) change DOM layout, attribute (e.g. [ngClass]) change appearance or behavior.
You can also make custom directives to reuse behavior.




12. What is Pipe

A pipe is a transform function used in templates to format data.
Example pipes: date, uppercase, currency.
You can create custom pipes to transform values in template (e.g. myCustomPipe).




13. What is Routing

Routing is Angular’s way to navigate between different views (components) based on URL path.
You configure routes in RouterModule with path and component or loadChildren.
When URL changes, Angular loads the matched component into a <router-outlet>.




14. What is Guards

Guards are interfaces you implement to control route navigation.
Examples: CanActivate, CanDeactivate, CanLoad, CanActivateChild.
They allow or prevent routing based on logic (e.g. authentication, unsaved changes).



15. Lazy Loading in Angular

Lazy loading loads modules (or components) only when user navigates to route needing them, not at startup.
It reduces the initial bundle size and speeds up first load.
You use loadChildren in route config or import() dynamic loading.



16. What is Interpolation

Interpolation uses {{ … }} syntax in template to bind and display component’s variables.
Example: <h1>{{ title }}</h1>.
It is one-way binding from component to view.



17. What is Property Binding

Property binding binds a component property to an HTML element’s property.
Syntax: [src]="imgUrl", [disabled]="isDisabled".
It updates the view when component value changes.



18. What is Event Binding

Event binding reacts to user actions like clicks, input, etc.
Syntax: (click)="onClick()", (keyup)="onKey()".
It lets the view notify the component to run methods.



19. What is Two-Way Binding

Two-way binding allows sync between component and view in both directions.
Syntax: [(ngModel)]="name".
When user changes input, component value updates; when component changes, view updates.



20. What is Service

A service is a class that holds logic or data not tied to UI (e.g. API calls, data store).
You inject services into components or other services via dependency injection.
It promotes code reuse and separation of concerns.



21. What is HTTP Interceptor?

An interceptor is a class that intercepts HTTP requests/responses globally.
You can modify request (e.g. add auth header) or handle errors in one place.
You register interceptors in providers using HTTP_INTERCEPTORS.



22. How to pass headers in Angular services?

Use HttpHeaders and pass in HTTP options.
Example:
const headers = new HttpHeaders({ 'Authorization': 'token', 'Content-Type': 'application/json' });  
this.http.get(url, { headers: headers });

You can also chain .set() methods to modify headers.



23. What is Forms in Angular

Forms provide ways to capture user input and validate it.
Angular defines form models and validation rules through template-driven or reactive forms.
They help handling input, validation, error display, submission.



24. What is TDF (Template-Driven Form)

Template-driven form is a simpler form approach using directives in template (e.g. ngModel, ngForm).
You define form structure in HTML and Angular infers the rest.
Good for simple or small forms; less scalable for complex business logic.



25. Explain Reactive Forms

Reactive forms define the form model in component class using FormControl, FormGroup, FormArray.
You have full programmatic control, easier unit testing, and dynamic validation.
Better for large or complex forms.



26. Explain FormGroup, FormControl and FormArray

FormControl represents a single input field (value + validation).
FormGroup groups multiple FormControls into one object tree (e.g. an entire form).
FormArray is an array of FormControl or FormGroup to manage dynamic collections (e.g. list of addresses).



27. What is FormBuilder

FormBuilder is a convenience service to more easily create FormGroup and FormControl instances.
You call this.fb.group({...}) instead of manually instantiating controls.
It helps reduce boilerplate code.



28. What are Validators?

Validators are functions that check whether control’s value is valid or not (e.g. required, minLength, custom).
If valid, they return null; if not, they return an error object { errorName: true }.
You can use built-in or custom validators.



29. What is Typed Forms?

Typed forms ensure form values have correct TypeScript types.
They improve type safety and prevent mistakes (you know the shape of form.value).
Angular supports typed forms from version 14+.



30. How to take the disabled control value in reactive forms

By default, disabled controls are excluded from form.value.
To get disabled values too, use form.getRawValue().
getRawValue() returns values including disabled controls.



31. State Management in Angular

State management handles shared data and its flow in the app (e.g. user info, cart).
You can use services with BehaviorSubject, or libraries like NgRx, Akita, NGXS.
It helps to centralize state, make changes predictable, and avoid prop drilling.



32. How to pass data from one component to another?

Parent → Child: using @Input() property.
Child → Parent: using @Output() event emitter.
Sibling or distant components: via shared service or state management.



33. What is Signals in Angular

Signals are a new reactivity primitive (introduced around Angular 16/17) for fine-grained updates.
They hold a value and notify dependents when the value changes.
They simplify reactive updates without always needing Observables.



34. How to convert signal to observable?

You can wrap a signal into an Observable using utilities or toObservable() (or similar conversions).
This allows integrating signals with RxJS pipeline.
(Implementation may depend on Angular version and support.)



35. What is Deferable View

In Angular 17, deferrable views (via @defer block) allow parts of template to load later.
This reduces initial bundle size and speeds up first render. 
You wrap content inside @defer { … } and it loads when condition is met or later.



36. What is Control Flow Template

Angular 17 introduces a new control flow syntax (@if, @for, @switch) in templates. 
It replaces *ngIf, *ngFor, *ngSwitch with more declarative syntax.
It enhances readability, performance, and type safety in templates.



37. What is Server Side Rendering (SSR)

SSR means rendering the app’s HTML on the server first, then client takes over.
It improves SEO, faster first content paint, better performance for initial load.
Angular uses Angular Universal to support SSR.



38. What is Standalone Template

This likely refers to using standalone components and templates without modules.
In standalone setup, you define components directly with standalone: true, and templates don’t need NgModule.
This reduces boilerplate and improves modularity.



39. Why app.config in Angular

app.config is a pattern or configuration file to centralize configuration settings (URLs, API keys, feature flags).
You inject or import app.config to use configuration across modules or services.
It helps avoid scattering constants and magic values everywhere.



40. What is Material UI

Angular Material (Material UI) is a component library implementing Google’s Material Design for Angular.
Provides ready UI components like buttons, cards, dialogs, tables, form controls.
Using it speeds UI development and gives consistent look & feel.



41. How to use services & interceptors in standalone template

In standalone component, include providers in the component’s metadata:
@Component({ standalone: true, providers: [MyService, { provide: HTTP_INTERCEPTORS, useClass: MyInterceptor, multi: true }] })

Then you can inject the service or interceptor in that standalone component directly.



42. Explain RxJS in Angular

RxJS is a library for reactive programming using Observables, streams, and operators.
Angular uses RxJS heavily: for HTTP, events, forms, asynchronous operations.
RxJS gives you tools like map, filter, switchMap, catchError, etc.



43. What is Observable?

Observable is a stream of data that can emit multiple values over time.
You subscribe to it to receive data, and you can unsubscribe.
Used for HTTP calls, event streams, etc.



44. What is NgRx?

NgRx is a state management library based on Redux pattern for Angular.
It uses Store (state), Actions, Reducers, Effects to manage state flow.
NgRx helps in large apps to keep state predictable and maintainable.



45. How to use NgRx in standalone template

You import NgRx store modules into your standalone component via imports array.
You provide store, effects, etc., similar as in modules.
Then you can dispatch actions and select state inside your standalone components.



46. What is Provider in Angular

Provider tells Angular how to create (or get) a service or token.
It can be class provider, value provider, factory provider, etc.
You register providers in module, component, or using providedIn in @Injectable.



47. What is the use of --no-standalone keyword?

When generating new components (using CLI), --no-standalone forces the component to be declared in a module (not standalone).
So it will generate component inside NgModule declarations.
Useful if you prefer old module-based style instead of standalone.



48. How to deploy Angular application?

Build your app for production: ng build --prod (or ng build).
Upload the built dist/ folder to a web server, hosting service, or static hosting (e.g. Firebase hosting, Netlify, AWS S3).
Ensure server is configured to redirect all routes to index.html (for SPA routing).



49. How to upgrade Angular?

Use Angular CLI command: ng update @angular/cli @angular/core.
This updates dependencies, migrations, and config automatically.
Test your app after upgrade to catch breaking changes.



50. Difference between Subject & BehaviorSubject

Subject emits values only to subscribers that subscribe after emission (it does not replay past).
BehaviorSubject stores the latest value and emits immediately to new subscribers.
So BehaviorSubject always has an initial value and gives value on subscription.



*/





//===================================================================================================================
//===================================================================================================================



🟢 Basic Level (30+)
=====================

What is Angular?
Angular is a TypeScript-based frontend framework by Google. It is used to build single-page applications (SPAs). 
It provides data binding, components, services, and dependency injection.



Difference between AngularJS and Angular?
AngularJS (1.x) uses JavaScript, while Angular (2+) uses TypeScript. Angular is faster, modular, and component-based. 
AngularJS uses controllers and scope, Angular uses components.




What is TypeScript in Angular?
TypeScript is a superset of JavaScript with types. It helps catch errors early during development. 
Angular uses TypeScript to make code clean and maintainable.



What are Components in Angular?
Components are building blocks of Angular apps. Each component has HTML (view), TS (logic), and CSS (style). 
Example: Header, Navbar, Footer are components.



What are Modules in Angular?
Modules are containers that group components, services, and directives. The main module is AppModule. 
It organizes the application into logical parts.



What is a Template in Angular?
Template defines how the component’s view looks. It is written in HTML with Angular syntax like *ngFor and {{ }}. 
Templates are linked to components.



What is Data Binding in Angular?
Data binding connects component logic with the UI. Types are: Interpolation, Property binding, Event binding, 
and Two-way binding. Example: [(ngModel)].



What is Interpolation?
Interpolation displays component data in HTML using {{ }}. Example: {{username}}. It only works for one-way 
binding from TS to HTML.



What is Two-way Data Binding?
It means updating UI updates the component, and updating component updates UI. Done using [(ngModel)]. 
Example: input box linked with variable.



What are Directives in Angular?
Directives change DOM behavior or style. Types: Component, Structural (*ngIf, *ngFor), Attribute ([style], [class]).



*What is ngIf directive?
*ngIf conditionally displays elements. Example: <p *ngIf="isLoggedIn">Welcome</p>. If condition is false, element is not rendered.



*What is ngFor directive?
*ngFor is used to loop over arrays. Example: <li *ngFor="let item of items">{{item}}</li>. It generates dynamic lists.



What are Services in Angular?
Services hold reusable business logic. Example: Data fetching using HTTP. They are injected into components 
using Dependency Injection.



What is Dependency Injection (DI)?
DI is a design pattern where a class gets its dependencies from outside. Angular’s DI system injects services 
into components automatically.



What is Angular CLI?
Angular CLI is a command-line tool to create, build, and run Angular projects. Example: ng new, ng serve, ng generate.



What is Routing in Angular?
Routing allows navigation between views without page reload. It uses RouterModule. Example: /home, /about.



What is Single Page Application (SPA)?
SPA loads one HTML page and updates content dynamically. Angular supports SPA using routing. It improves user experience.



What are Pipes in Angular?
Pipes format data in templates. Example: date, currency, uppercase. Custom pipes can also be created.



What is Async Pipe?
Async pipe automatically subscribes to an Observable or Promise. It displays the latest value and unsubscribes automatically.



What is Lifecycle Hook in Angular?
Lifecycle hooks let you run code at specific times in a component’s life. Example: ngOnInit, ngOnDestroy.



What is ngOnInit()?
ngOnInit() runs after component is created and initialized. It is commonly used to fetch initial data.



What is ngOnDestroy()?
ngOnDestroy() runs just before component is destroyed. It is used to clean up resources like unsubscribing observables.



What is Event Binding?
Event binding connects events like click, keyup to component methods. Example: <button (click)="login()">Login</button>.



What is Property Binding?
Property binding sets values of HTML elements dynamically. Example: <img [src]="imageUrl">.



Difference between Constructor and ngOnInit?
Constructor is called when the component is created. ngOnInit runs after Angular initializes data-bound properties. 
ngOnInit is preferred for logic.



What is Angular Package.json used for?
package.json keeps all dependencies, dev tools, and scripts of the Angular project. Example: Angular core libraries, RxJS.



What is RxJS in Angular?
RxJS is a library for reactive programming with Observables. Angular uses it for async operations like HTTP requests.



What are Observables?
Observables represent data streams that can emit values over time. They are used with HTTP, events, etc.



What are Promises vs Observables?
Promise handles one async value, Observable handles multiple values over time. Observables are cancellable and more powerful.



What is Angular Universal?
Angular Universal is used for Server-Side Rendering (SSR). It improves SEO and performance of Angular apps.





🟡 Intermediate Angular Interview Questions (30+)
=================================================

What is Angular Change Detection?
Angular checks component data changes and updates the DOM. It runs automatically when events, HTTP, or timers happen. 
Developers can also trigger manually using ChangeDetectorRef.



What is ViewChild in Angular?
@ViewChild gets a reference to a child component, directive, or DOM element. It allows parent to control child component. 
Example: access input box value directly.



What is ViewChildren in Angular?
@ViewChildren gets multiple child elements or components. It returns a QueryList which can be iterated. 
Used when multiple similar children exist.



What is ContentChild in Angular?
@ContentChild gets projected content passed from parent using <ng-content>. It allows communication with transcluded content.



What is Lazy Loading in Angular?
Lazy loading loads modules only when required (on-demand). It reduces initial load time. Done via loadChildren in routes.



What is Preloading in Angular?
Preloading loads lazy modules in the background after app loads. Angular provides PreloadAllModules strategy. 
It balances speed and user experience.



What is ActivatedRoute in Angular?
ActivatedRoute gives route info like parameters and query params. Example: this.route.snapshot.paramMap.get('id'). 
It helps fetch dynamic data.



What is RouterOutlet in Angular?
<router-outlet> is a placeholder in template where routed component loads. Without it, navigation won’t show any content.



What is RouterLink in Angular?
routerLink is used to navigate between routes. Example: <a routerLink="/home">Home</a>. It avoids full page reload.



What is Guard in Angular?
Guards control route access. Example: AuthGuard allows navigation only if user is logged in. Guards implement interfaces 
like CanActivate.



What is CanActivate in Angular?
CanActivate guard decides if a route can be activated. Example: prevent accessing dashboard without login.



What is CanDeactivate in Angular?
CanDeactivate guard checks if user can leave a route. Example: warn before leaving a form with unsaved data.



What is Resolver in Angular?
Resolver pre-fetches data before route loads. Example: fetch user details before opening profile page. It prevents empty UI.



What is Difference between Subject and BehaviorSubject?
Subject emits values only after subscription. BehaviorSubject emits last stored value immediately to new subscribers. 
Useful for state management.



What is ReplaySubject in Angular?
ReplaySubject stores past values and replays them to new subscribers. Example: chat messages replayed to new user joining.



What is Async/Await in Angular?
async/await is used with Promises to write cleaner async code. It looks synchronous but works asynchronously. 
Example: fetch API call.



What is HttpClient in Angular?
HttpClient is a service to make HTTP calls. Example: this.http.get('/api/users'). It returns Observables for async handling.



How do you send HTTP Headers in Angular?
Use HttpHeaders with HttpClient. Example:
this.http.get(url, { headers: new HttpHeaders({ 'Auth': 'token' }) })



What is Interceptor in Angular?
Interceptor is middleware for HTTP calls. It can modify requests (add token) or handle responses (errors).



What is Error Handling in Angular HTTP?
Use catchError from RxJS with HttpClient. Example:
this.http.get(url).pipe(catchError(error => of([])))



What is FormControl in Angular?
FormControl tracks input value and validation state. Example:
name = new FormControl('');


What is FormGroup in Angular?
FormGroup groups multiple FormControls. Example: user form with name, email, password fields.



What is FormBuilder in Angular?
FormBuilder simplifies creating forms. Example:
this.form = this.fb.group({ name: [''], email: [''] });



Difference between Template-driven and Reactive Forms?
Template-driven forms use ngModel and are simple but less scalable. Reactive forms use FormGroup, 
FormControl, and are more powerful.



What is Validation in Angular Forms?
Validation checks if input is valid (like required, email, minLength). Angular supports built-in and custom validators.



How to create a Custom Validator in Angular?
Create a function that returns null if valid, or error object if invalid. Example: check password strength.



What is ngZone in Angular?
ngZone tells Angular when to run change detection. It helps optimize performance by running code outside Angular zone.



What is ChangeDetectorRef in Angular?
ChangeDetectorRef allows manual control of change detection. Used when Angular doesn’t auto-detect changes.



*What is TrackBy in Angular ngFor?
trackBy improves performance by tracking items with unique keys. Example:
<li *ngFor="let item of list; trackBy: trackById">{{item.name}}</li>



What is Dynamic Component Loading in Angular?
You can create and load components at runtime using ComponentFactoryResolver or ViewContainerRef. Useful for modals, popups.


What are Angular Animations?
Angular provides animation API using @angular/animations. Example: fade in/out using trigger, state, and transition.



What is Internationalization (i18n) in Angular?
i18n makes app support multiple languages. Angular uses i18n attribute and translation files for localization.



What is AOT Compilation in Angular?
Ahead-of-Time compilation converts templates to JavaScript before runtime. It makes app faster and smaller.



What is JIT Compilation in Angular?
Just-in-Time compilation compiles templates at runtime. Faster development but slower performance in production.



What is Angular Material?
Angular Material is a UI component library. It provides ready-made components like buttons, dialogs, tables with modern design.



What is State Management in Angular?
State management handles data flow across components. Tools like NgRx, BehaviorSubject, or services are used.



What is NgRx in Angular?
NgRx is a Redux-based state management library. It uses Store, Actions, Reducers, and Effects for predictable state.



What are Effects in NgRx?
Effects handle side effects like API calls in NgRx. They listen to actions and return new actions with results.



What are Selectors in NgRx?
Selectors fetch data from NgRx store efficiently. Example: get logged-in user details.



What is Angular Ivy?
Ivy is Angular’s new rendering engine. It makes apps smaller, faster, and improves debugging.



🔴 Advanced Angular Interview Questions (30+)
=============================================

What is Angular SSR (Server-Side Rendering)?
SSR means rendering Angular pages on the server before sending them to the browser. It improves SEO and first-page load time. 
Implemented using Angular Universal.



What is Angular PWA (Progressive Web App)?
PWA makes Angular apps installable like native apps. It uses service workers, offline support, and push notifications. 
Command: ng add @angular/pwa.



What are Angular Service Workers?
Service workers run in the background to cache resources. They enable offline mode and faster reloads. Angular provides 
built-in service worker support.



What is Micro-frontend Architecture in Angular?
Micro-frontend splits frontend into smaller independent apps. Each Angular app handles part of UI and integrates into one shell. 
It improves scalability.



What is Angular Ivy Renderer?
Ivy is Angular’s rendering engine from v9+. It makes apps smaller, faster, and improves debugging. It also allows dynamic 
component loading easily.



What is Zone.js in Angular?
Zone.js patches async APIs like setTimeout, HTTP, events. It notifies Angular when to trigger change detection. 
It is core for Angular reactivity.



How do you optimize performance in Angular apps?
Use OnPush change detection, trackBy in *ngFor, lazy loading, and caching. Also use async pipe to auto-unsubscribe. 
Minify and enable AOT for builds.



What is Angular Security XSS Protection?
Angular auto-escapes HTML to prevent XSS attacks. Use DomSanitizer if safe HTML is needed. Never use innerHTML directly.



What is CSRF and how Angular handles it?
CSRF is Cross-Site Request Forgery attack. Angular sends XSRF-TOKEN automatically with HTTP requests. Backend validates it.



What is Ahead-of-Time (AOT) vs Just-in-Time (JIT) Compilation?
AOT compiles templates at build time, JIT compiles at runtime. AOT gives better performance and smaller bundles. 
JIT is used in development.



What are Angular Schematics?
Schematics are code templates for generating Angular components, services, modules. Example: ng generate component home. 
They save development time.



What is Angular Builders?
Builders customize Angular CLI build and deploy process. Example: change webpack config, add custom scripts.



What are Angular Decorators?
Decorators are special functions that modify classes or methods. Examples: @Component, @Injectable, @NgModule. 
They provide metadata to Angular.



What is @Injectable in Angular?
@Injectable makes a service available for Dependency Injection. It tells Angular how to create and provide the service.



What is providedIn in @Injectable?
providedIn: 'root' makes service singleton across app. You can also use providedIn: 'any' or feature module. 
It helps with tree-shaking.



What is Tree Shaking in Angular?
Tree shaking removes unused code during build. Angular CLI and Ivy support it by default. It reduces final bundle size.



What is Differential Loading in Angular?
Differential loading creates two bundles: modern (ES2015) and legacy (ES5). Browser loads the optimized one. 
It improves performance.



What are Angular Polyfills?
Polyfills are scripts that provide modern features in old browsers. Example: Promise, fetch, async functions.
Angular includes them by default.



What is Angular Renderer2?
Renderer2 is used to manipulate DOM safely. Example: add/remove classes, styles, attributes. It works across 
platforms (browser, server).



What is Angular ElementRef?
ElementRef provides direct access to DOM element. Example: this.el.nativeElement. Should be used carefully due to XSS risk.



What is Angular Platform Browser?
@angular/platform-browser provides services like DomSanitizer and Title. It’s required for browser-based Angular apps.



What is Angular Platform Server?
@angular/platform-server is used for SSR (Angular Universal). It enables rendering Angular apps on the server.



What is Angular Dynamic Imports?
Dynamic imports allow lazy loading of modules/components. Example:
loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule)


What is Angular Webpack?
Webpack bundles Angular code into optimized files. Angular CLI internally uses Webpack for building. Developers rarely 
configure it directly.



What is Angular State Transfer API?
State Transfer API shares data between server-side and client-side rendering. It avoids duplicate API calls after SSR.



What is Angular Builder Optimizer?
It removes unnecessary Angular decorators during build. This makes app smaller and faster. Enabled by default in production build.



What is Angular Protractor?
Protractor is an end-to-end (E2E) testing framework for Angular. It simulates user actions and tests flows. 
(Note: deprecated in latest Angular).



What is Angular Karma?
Karma is a test runner for unit testing Angular code. It runs tests in browsers and shows results. Usually used with Jasmine.



What is Angular Jasmine?
Jasmine is a testing framework with describe and it functions. It is used for writing unit tests in Angular projects.



What is Angular TestBed?
TestBed is Angular’s testing environment. It creates testing modules and components for unit testing. 
Example: TestBed.configureTestingModule().



What is Angular Zones Issue and ngZone.run()?
Sometimes Angular misses updates outside zone (like setTimeout). ngZone.run() forces Angular to detect changes.


What are Angular Signals (Angular 16+)?
Signals are a new reactivity system. They replace heavy RxJS in some cases. They track values and auto-update UI.



What is Angular Hydration (Angular 17+)?
Hydration allows reusing server-rendered DOM instead of re-rendering. It speeds up SSR apps and improves SEO.



What is Standalone Component in Angular?
Standalone components don’t need NgModule. Example:
@Component({ standalone: true })
This simplifies module management.



What is Angular Microtask Queue vs Macrotask Queue?
Microtask queue includes promises/observables, macrotask queue includes setTimeout/events. Angular uses Zone.js to track both.



What is Angular Multi-provider?
Multi-providers allow multiple values for one injection token. Example: register multiple loggers under same token.



What is Angular InjectionToken?
InjectionToken creates custom tokens for DI. Example:
export const API_URL = new InjectionToken<string>('API_URL');


What is Angular Platform Detection (isPlatformBrowser)?
isPlatformBrowser() checks if code runs on browser or server. Useful in SSR for handling DOM safely.



What are Angular View Encapsulation types?
Emulated (default, adds scoped styles)
ShadowDom (uses real Shadow DOM)
None (global styles, no encapsulation)


What are Angular Best Practices for Production?
Use AOT, enable optimization, lazy load modules, secure with sanitization, cache API calls, and monitor performance with tools.



