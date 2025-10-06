Angular Q | A 
==============

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


