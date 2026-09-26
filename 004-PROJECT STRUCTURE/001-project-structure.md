# Angular Project Structure

Overview

An Angular project contains several configuration files, source files, folders, and build-related files.

A typical Angular project, especially an Angular 10 project, looks like this:
```
my-angular-app/
│
├── e2e/
│
├── node_modules/
│
├── src/
│   ├── app/
│   ├── assets/
│   ├── environments/
│   │   ├── environment.ts
│   │   └── environment.prod.ts
│   │
│   ├── favicon.ico
│   ├── index.html
│   ├── main.ts
│   ├── polyfills.ts
│   └── styles.css
│
├── .browserslistrc
├── .editorconfig
├── .gitignore
├── angular.json
├── package.json
├── package-lock.json
├── tsconfig.json
├── tsconfig.app.json
└── tsconfig.spec.json
```
Important: The exact structure changes between Angular versions. The structure above is especially relevant to Angular 10.

⸻

1. angular.json

What is angular.json?

angular.json is the Angular CLI workspace configuration file.

Angular CLI reads this file when executing commands such as:
```bash
ng serve
ng build
ng test
```
It tells Angular CLI:

* Which projects exist
* Where source files are located
* How to build the application
* How to serve the application
* Which assets to copy
* Which styles to include
* Which scripts to include
* Development configuration
* Production configuration
* Build optimization settings
* Output directory

⸻

Example
```json
{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "version": 1,
  "projects": {
    "my-app": {
      "projectType": "application",
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/my-app",
            "index": "src/index.html",
            "main": "src/main.ts",
            "polyfills": "src/polyfills.ts",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.css"
            ]
          }
        }
      }
    }
  }
}
```
⸻

2. Important angular.json Properties

projects

Contains Angular projects in the workspace.
```bash
"projects": {
  "my-app": {
  }
}
```
A workspace can contain multiple applications/libraries.

⸻

projectType

"projectType": "application"

Can identify an application project.

A library can have:

"projectType": "library"

⸻

root

Defines the project root.

Example:

"root": ""

⸻

sourceRoot

Defines where application source code is located.

"sourceRoot": "src"

Therefore:

src/

is the source directory.

⸻

outputPath

Defines where the compiled application is generated.

"outputPath": "dist/my-app"

After:

ng build

the build files are generated there.

⸻

index

Specifies the HTML entry file:

"index": "src/index.html"

⸻

main

Specifies the application entry TypeScript file:

"main": "src/main.ts"

Flow:

main.ts
   ↓
Angular Application
   ↓
Components
   ↓
Browser

⸻

polyfills

Angular 10 commonly has:

"polyfills": "src/polyfills.ts"

It contains browser compatibility-related code.

⸻

assets

Example:

"assets": [
  "src/favicon.ico",
  "src/assets"
]

Angular copies these files into the build output.

⸻

styles

Example:
```json
"styles": [
  "src/styles.css"
]
```
These styles are included globally in the application.

⸻

scripts

External JavaScript files can be specified here.

Example:
```json
"scripts": [
  "src/assets/custom.js"
]
```
⸻

3. angular.json Configurations

Angular commonly has different configurations.

For example:
```json
"configurations": {
  "production": {
    "optimization": true,
    "sourceMap": false
  }
}
```
Then:

ng build --configuration production

or commonly:

ng build --prod

in Angular 10-era CLI.

⸻

4. angular.json — Development vs Production

Conceptually:
```
                  angular.json
                       │
              ┌────────┴────────┐
              │                 │
        development         production
              │                 │
        ng serve            ng build
                              --prod
```
Production configuration can enable:

* Optimization
* Minification
* AOT compilation
* Build optimizations
* File replacements
* Bundle budgets

⸻

5. package.json

What is package.json?

package.json is the npm project configuration file.

It contains:

* Project name
* Version
* npm scripts
* Dependencies
* Development dependencies

Example:
```json
{
  "name": "my-angular-app",
  "version": "0.0.0",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "test": "ng test"
  },
  "dependencies": {
    "@angular/core": "~10.2.0",
    "@angular/common": "~10.2.0"
  },
  "devDependencies": {
    "@angular/cli": "~10.2.0",
    "typescript": "~3.9.7"
  }
}
```
⸻

6. dependencies

These are packages required by the application.

Example:

"dependencies": {
  "@angular/core": "~10.2.0",
  "@angular/common": "~10.2.0",
  "rxjs": "~6.6.0"
}

Examples:

@angular/core
@angular/common
@angular/router
rxjs
zone.js

⸻

7. devDependencies

These are packages primarily needed for development/build/test.

Example:
```json
"devDependencies": {
  "@angular/cli": "~10.2.0",
  "@angular/compiler-cli": "~10.2.0",
  "typescript": "~3.9.7"
}
```
⸻

8. scripts

package.json can contain npm commands.

Example:
```json
"scripts": {
  "start": "ng serve",
  "build": "ng build",
  "test": "ng test"
}
```
Therefore:

npm start

runs:

ng serve

And:

npm run build

runs:

ng build

⸻

9. package-lock.json

Although not in your requested list, this file is important.

package-lock.json records the exact dependency tree installed by npm.

For example:

package.json
     ↓
Requested dependency versions
     ↓
package-lock.json
     ↓
Exact resolved dependency versions

This helps different developers/servers install consistent dependencies.

⸻

10. tsconfig.json

What is tsconfig.json?

tsconfig.json is the main TypeScript configuration file.

Angular uses TypeScript to write application code.

Example:
```json
{
  "compileOnSave": false,
  "compilerOptions": {
    "baseUrl": "./",
    "outDir": "./dist/out-tsc",
    "sourceMap": true,
    "declaration": false,
    "module": "es2020",
    "moduleResolution": "node",
    "experimentalDecorators": true,
    "target": "es2015",
    "typeRoots": [
      "node_modules/@types"
    ],
    "lib": [
      "es2018",
      "dom"
    ]
  }
}
```
⸻

11. Important tsconfig.json Options

target

Defines the JavaScript version TypeScript should compile to.

Example:

"target": "es2015"

Conceptually:

TypeScript
    ↓
Compiler
    ↓
JavaScript ES2015

⸻

module

Defines the JavaScript module system.

Example:

"module": "es2020"

⸻

moduleResolution

Defines how TypeScript finds imported modules.

Example:

"moduleResolution": "node"

⸻

sourceMap

"sourceMap": true

Creates source maps.

Source maps help debugging generated JavaScript using the original TypeScript source.

⸻

experimentalDecorators

"experimentalDecorators": true

Angular heavily uses decorators.

Example:
```js
@Component({
  selector: 'app-root'
})
export class AppComponent {
}
```
⸻

lib

Specifies libraries available to TypeScript.

Example:

"lib": [
  "es2018",
  "dom"
]

dom provides browser APIs/types.

⸻

12. tsconfig.app.json

What is tsconfig.app.json?

tsconfig.app.json is the TypeScript configuration specifically used for the Angular application code.

It usually extends the main tsconfig.json.

Example:
```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/app",
    "types": []
  },
  "files": [
    "src/main.ts",
    "src/polyfills.ts"
  ],
  "include": [
    "src/**/*.d.ts"
  ]
}
```
⸻

13. Why tsconfig.app.json Exists

Think of the configuration hierarchy:
```
tsconfig.json
       │
       ├── tsconfig.app.json
       │       │
       │       └── Application TypeScript
       │
       └── tsconfig.spec.json
               │
               └── Test TypeScript
```
The base configuration contains common TypeScript settings.

The application configuration contains application-specific settings.

⸻

14. files in tsconfig.app.json

Example:
```json
"files": [
  "src/main.ts",
  "src/polyfills.ts"
]
```
These are entry files that TypeScript needs to include.

⸻

15. include

Example:

"include": [
  "src/**/*.d.ts"
]

This tells TypeScript which additional files to include.

⸻

16. tsconfig.spec.json

What is tsconfig.spec.json?

tsconfig.spec.json contains TypeScript configuration for unit test files.

Example:
```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "types": [
      "jasmine"
    ]
  },
  "files": [
    "src/test.ts",
    "src/polyfills.ts"
  ],
  "include": [
    "src/**/*.spec.ts",
    "src/**/*.d.ts"
  ]
}
```
⸻

17. .spec.ts Files

Angular unit tests commonly use:

.spec.ts

Example:

employee.component.ts
employee.component.spec.ts

The first is application code.

The second contains tests.

⸻

18. tsconfig.app.json vs tsconfig.spec.json

File	Purpose
tsconfig.json	Base TypeScript configuration
tsconfig.app.json	Application TypeScript configuration
tsconfig.spec.json	Test TypeScript configuration

Simple diagram:

                  tsconfig.json
                       │
             ┌─────────┴─────────┐
             │                   │
    tsconfig.app.json     tsconfig.spec.json
             │                   │
        Application             Tests
             │                   │
       *.component.ts        *.spec.ts

⸻

19. main.ts

What is main.ts?

main.ts is the entry point of an Angular application.

Angular starts the application from this file.

In Angular 10, a typical main.ts looks like:

import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';
import { environment } from './environments/environment';
if (environment.production) {
  enableProdMode();
}
platformBrowserDynamic()
  .bootstrapModule(AppModule)
  .catch(err => console.error(err));

⸻

20. main.ts Flow

index.html
    ↓
main.ts
    ↓
AppModule
    ↓
Root Component
    ↓
AppComponent
    ↓
Application

⸻

21. platformBrowserDynamic()

platformBrowserDynamic()

Bootstraps Angular in the browser.

⸻

22. bootstrapModule()

Angular 10 commonly uses:

platformBrowserDynamic()
  .bootstrapModule(AppModule)

This tells Angular:

Start the application using AppModule.

⸻

23. AppModule

Typically:

src/app/app.module.ts

Example:
```js
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [
    AppComponent
  ]
})
export class AppModule {}
```
Angular 10 uses NgModules heavily.

Modern Angular also supports standalone applications, but Angular 10 projects are normally module-based.

⸻

24. index.html

What is index.html?

index.html is the main HTML page loaded by the browser.

Typical Angular 10:
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>MyApp</title>
  <base href="/">
  <meta name="viewport"
        content="width=device-width, initial-scale=1">
  <link rel="icon"
        type="image/x-icon"
        href="favicon.ico">
</head>
<body>
  <app-root></app-root>
</body>
</html>
```
⸻

25. <app-root>

This is extremely important.

<app-root></app-root>

Angular replaces/renders this element with the root component.

The selector may be defined in:
```js
@Component({
  selector: 'app-root'
})
```
So:

index.html
     ↓
<app-root>
     ↓
AppComponent

⸻

26. <base href="/">

<base href="/">

Angular routing uses the base URL.

For normal root deployment:

https://example.com/

use:

<base href="/">

For a subdirectory deployment, the base href may need to be changed.

Example:

<base href="/employee/">

or supplied during build:

ng build --base-href /employee/

⸻

27. styles.css

What is styles.css?

styles.css is the global stylesheet.

Example:
```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
button {
  cursor: pointer;
}
```
It can contain styles that should apply globally.

⸻

28. Global vs Component CSS

Suppose:
```
src/
├── styles.css
└── app/
    └── employee/
        ├── employee.component.ts
        ├── employee.component.html
        └── employee.component.css
```
styles.css

Global styles:

body {
  margin: 0;
}

employee.component.css

Styles specific to the component:

.employee-card {
  padding: 20px;
}

Conceptually:

styles.css
     ↓
Global styles
component.css
     ↓
Component styles

⸻

29. How styles.css Gets Loaded

angular.json commonly contains:
```
"styles": [
  "src/styles.css"
]
```
Angular CLI then includes it during the build.

Flow:

angular.json
     ↓
src/styles.css
     ↓
Angular Build
     ↓
Generated CSS
     ↓
Browser

⸻

30. polyfills.ts

What is a Polyfill?

A polyfill is code that provides missing browser functionality or compatibility behavior.

Angular 10 commonly has:

src/polyfills.ts

It may contain imports such as:

import 'zone.js/dist/zone';

depending on the Angular 10 project configuration.

⸻

31. Why Polyfills Were Important

Different browsers may support different JavaScript features.

Conceptually:

Application
     ↓
Uses modern JavaScript feature
     ↓
Old browser doesn't support it
     ↓
Polyfill provides compatibility

⸻

32. Angular and zone.js

Angular 10 commonly uses zone.js.

Example:

import 'zone.js/dist/zone';

zone.js helps Angular detect asynchronous operations and trigger change detection.

Conceptually:

HTTP request
     ↓
Promise / async operation
     ↓
Zone.js tracks activity
     ↓
Angular detects change
     ↓
UI updates

⸻

33. polyfills.ts and angular.json

Angular CLI knows where the polyfills file is because of:

"polyfills": "src/polyfills.ts"

The exact configuration can vary by Angular version.

⸻

34. assets

What is the assets folder?

The assets folder stores static files used by the Angular application.

Typical structure:

src/
└── assets/
    ├── images/
    ├── icons/
    ├── json/
    └── fonts/

Examples:

src/assets/logo.png
src/assets/images/user.jpg
src/assets/data/config.json

⸻

35. Using Assets in HTML

Suppose:

src/assets/logo.png

Then:

<img src="assets/logo.png" alt="Logo">

You normally don’t write:

<img src="src/assets/logo.png">

because src is the source directory, not the URL exposed by the built application.

⸻

36. Assets and angular.json

Example:
```json
"assets": [
  "src/favicon.ico",
  "src/assets"
]
```
Angular CLI copies these into the build output.

Conceptually:

src/assets/
      ↓
Angular CLI
      ↓
dist/.../assets/

⸻

37. JSON Files in Assets

Example:

src/assets/config/app-config.json

It can be requested from the application as:

assets/config/app-config.json

Example:

this.http.get('assets/config/app-config.json');

⸻

38. environments

What is the environments folder?

In Angular 10 projects, the environments folder is commonly:

src/environments/

Typical files:
```
environments/
├── environment.ts
└── environment.prod.ts
```
These files store configuration values that differ between environments.

For example:

Development
Production
Testing

⸻

39. environment.ts

Example:
```js
export const environment = {
  production: false,
  apiUrl: 'http://localhost:5000/api'
};
```
Development application can use:

http://localhost:5000/api

⸻

40. environment.prod.ts

Example:
```js
export const environment = {
  production: true,
  apiUrl: 'https://api.example.com/api'
};
```
Production uses:

https://api.example.com/api

⸻

41. Using Environment in TypeScript

Import:
```js
import { environment } from '../environments/environment';
```
Then:
```js
console.log(environment.apiUrl);
```
Or:
```js
this.http.get(
  environment.apiUrl + '/employees'
);
```
⸻

42. Environment File Replacement

This is an important Angular CLI concept.

In Angular 10, production configuration can contain:
```json
"fileReplacements": [
  {
    "replace": "src/environments/environment.ts",
    "with": "src/environments/environment.prod.ts"
  }
]
```
Then:

ng build --prod

can replace:

environment.ts

with:

environment.prod.ts

⸻

43. Environment Flow

Development:

Code
 ↓
environment.ts
 ↓
apiUrl = localhost

Production:

Code
 ↓
ng build --prod
 ↓
File Replacement
 ↓
environment.prod.ts
 ↓
apiUrl = production API

⸻

44. Important Environment Warning

Angular environment files are not secret storage.

For example, don’t put:

export const environment = {
  apiPassword: 'secret123'
};

Angular application code runs in the browser.

Anything bundled into the frontend can potentially be inspected by the user.

Do not put:

* Database passwords
* Private keys
* Server secrets
* API secrets that must remain confidential

in Angular environment files.

⸻

45. Complete Project Structure

For Angular 10, you may see:

my-angular-app/
│
├── e2e/
│
├── node_modules/
│
├── src/
│   │
│   ├── app/
│   │   ├── app.component.ts
│   │   ├── app.component.html
│   │   ├── app.component.css
│   │   ├── app.component.spec.ts
│   │   └── app.module.ts
│   │
│   ├── assets/
│   │   ├── images/
│   │   ├── icons/
│   │   └── json/
│   │
│   ├── environments/
│   │   ├── environment.ts
│   │   └── environment.prod.ts
│   │
│   ├── favicon.ico
│   ├── index.html
│   ├── main.ts
│   ├── polyfills.ts
│   └── styles.css
│
├── angular.json
├── package.json
├── package-lock.json
├── tsconfig.json
├── tsconfig.app.json
└── tsconfig.spec.json

⸻

46. Complete File Responsibility

File/Folder	Responsibility
angular.json	Angular CLI/build configuration
package.json	npm packages and scripts
package-lock.json	Exact npm dependency tree
tsconfig.json	Base TypeScript configuration
tsconfig.app.json	Application TypeScript configuration
tsconfig.spec.json	Test TypeScript configuration
main.ts	Angular application entry point
index.html	Main browser HTML page
styles.css	Global CSS
polyfills.ts	Browser compatibility/runtime polyfills
assets/	Static files
environments/	Environment-specific configuration
app/	Angular application code

⸻

47. Complete Application Startup Flow

When you run:

ng serve

the conceptual flow is:

                    ng serve
                       │
                       ▼
                 angular.json
                       │
                       ▼
                Angular CLI Build
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
          index.html          main.ts
                                 │
                                 ▼
                             AppModule
                                 │
                                 ▼
                           AppComponent
                                 │
                                 ▼
                            Angular App
                                 │
                                 ▼
                              Browser

⸻

48. Complete Build Flow

When you run:

ng build --prod

Angular CLI reads:

angular.json
     │
     ├── main.ts
     ├── polyfills.ts
     ├── index.html
     ├── styles.css
     ├── assets/
     └── environments/
              │
              ▼
       File replacement
              │
              ▼
       TypeScript compilation
              │
              ▼
       Angular compilation
              │
              ▼
       Optimization
              │
              ▼
             dist/

⸻

49. angular.json vs package.json

This is a very important difference.

angular.json

Controls Angular CLI behavior.

Build
Serve
Test
Assets
Styles
Scripts
Configurations

package.json

Controls npm/project dependencies.

Dependencies
DevDependencies
Scripts
Project metadata

Simple:

angular.json
     ↓
Angular CLI configuration
package.json
     ↓
npm/project package configuration

⸻

50. tsconfig.json vs angular.json

tsconfig.json

Controls:

TypeScript

For example:

target
module
strictness
source maps
module resolution

angular.json

Controls:

Angular CLI

For example:

build
serve
assets
styles
scripts
production configuration

⸻

51. main.ts vs index.html

index.html

Browser entry HTML:

<body>
  <app-root></app-root>
</body>

main.ts

Angular application entry:

platformBrowserDynamic()
  .bootstrapModule(AppModule);

Flow:

Browser
  ↓
index.html
  ↓
<app-root>
  ↓
main.ts
  ↓
AppModule
  ↓
AppComponent

⸻

52. assets vs styles.css

assets

Static files:

Images
JSON
Icons
Fonts

styles.css

Global CSS:

body {
  margin: 0;
}

⸻

53. tsconfig.app.json vs tsconfig.spec.json

Application

tsconfig.app.json
       ↓
Application source
       ↓
*.ts

Tests

tsconfig.spec.json
       ↓
Test source
       ↓
*.spec.ts

⸻

54. Important Angular 10 Commands Related to Structure

Create application:

ng new my-app

Generate component:

ng g c employee

Generate service:

ng g s employee

Generate module:

ng g m employee

Generate interface:

ng g i employee

Build:

ng build

Production build:

ng build --prod

Serve:

ng serve

Test:

ng test

⸻

55. Interview Questions

Q1. What is angular.json?

angular.json is the Angular CLI workspace configuration file. It controls project configuration such as build, serve, assets, styles, scripts, and environment-specific configurations.

⸻

Q2. What is package.json?

package.json contains npm project metadata, scripts, dependencies, and development dependencies.

⸻

Q3. What is tsconfig.json?

It contains the base TypeScript compiler configuration for the project.

⸻

Q4. What is tsconfig.app.json?

It contains TypeScript configuration specifically for compiling the Angular application.

⸻

Q5. What is tsconfig.spec.json?

It contains TypeScript configuration for unit-test files.

⸻

Q6. What is main.ts?

main.ts is the entry point from which the Angular application is bootstrapped.

⸻

Q7. What is index.html?

It is the main HTML page loaded by the browser and contains the root Angular element such as:

<app-root></app-root>

⸻

Q8. What is polyfills.ts?

It provides browser compatibility/runtime support for features that may not be available natively in target browsers.

⸻

Q9. What is the assets folder?

It contains static files such as images, icons, fonts, and JSON files that Angular CLI copies to the build output.

⸻

Q10. What is the environments folder?

It contains environment-specific configuration files such as:

environment.ts
environment.prod.ts

⸻

Q11. Where is the API URL usually configured?

In Angular 10 projects, commonly:

src/environments/environment.ts
src/environments/environment.prod.ts

⸻

Q12. Are environment variables secret?

No.

Angular frontend code runs in the browser, so values included in the frontend bundle should be considered publicly accessible.

⸻

56. One-Line Memory Trick

angular.json
→ Angular CLI configuration
package.json
→ npm packages + scripts
tsconfig.json
→ TypeScript base configuration
tsconfig.app.json
→ Application TypeScript configuration
tsconfig.spec.json
→ Test TypeScript configuration
main.ts
→ Angular application entry point
index.html
→ Browser HTML entry page
styles.css
→ Global CSS
polyfills.ts
→ Browser compatibility
assets/
→ Static files
environments/
→ Environment-specific configuration

57. Final Architecture

                         ANGULAR PROJECT
                               │
          ┌────────────────────┼─────────────────────┐
          │                    │                     │
       CONFIG                SOURCE                NPM
          │                    │                     │
          │                    │                 package.json
          │                    │                 package-lock.json
          │                    │
   ┌──────┼──────┐       ┌─────┼───────────┐
   │      │      │       │     │           │
angular  tsconfig  ...   app  assets   environments
.json      │             │
           │             │
      ┌────┴─────┐       │
      │          │       │
 tsconfig.app  tsconfig  Components
                .spec    Services
                         Modules
                         Guards
                         Pipes
                         etc.
                               │
                               ▼
                           main.ts
                               │
                               ▼
                           AppModule
                               │
                               ▼
                         AppComponent
                               │
                               ▼
                           index.html
                               │
                               ▼
                            Browser

This gives you the Angular 10 project-structure foundation: first understand angular.json/package.json/tsconfig* as configuration, then main.ts/index.html as startup files, and finally assets, styles.css, polyfills.ts, and environments as supporting application resources.