# Angular CLI:

The basic syntax is:
```bash
ng <command> [options]
```
⸻

## Install Angular CLI
**Install:** 
```bash
npm install @angular/cli
```
Install globally
```bash
npm install -g @angular/cli
```

**Install with Specific Version:**
```bash
npm install -g @angular/cli@10.4.7
```

### Check installation:
```bash
ng version
```
or:
```bash
ng v
```
Check available commands:

ng help

⸻

2. Angular CLI Version Commands

ng version

Shows:

* Angular CLI version
* Angular version
* Node.js version
* npm version
* Operating system
* Package versions

Short form:

ng v

Check CLI help:

ng help

Help for a particular command:

ng generate --help

or:

ng g --help

⸻

## 3. Create a New Angular Application

Basic:
```bash
ng new my-app
```
Example:
```bash
ng new employee-management
```
Angular CLI asks configuration questions such as:

Would you like to add Angular routing?
Which stylesheet format would you like to use?

⸻

Create without interactive questions
```bash
ng new my-app --routing --style=scss
```
Example:
```bash
ng new employee-management --routing --style=scss
```
⸻

4. Important ng new Options

Routing
```bash
ng new my-app --routing
```
Creates the application with routing.

⸻

CSS
```bash
ng new my-app --style=css
```
SCSS
```bash
ng new my-app --style=scss
```
Sass
```bash
ng new my-app --style=sass
```
Less
```bash
ng new my-app --style=less
```
⸻

Skip Git
```bash
ng new my-app --skip-git
```
⸻

Skip installation
```bash
ng new my-app --skip-install
```
⸻

Strict mode
```bash
ng new my-app --strict
```
⸻

Standalone application

Modern Angular applications use standalone APIs by default.

ng new my-app --standalone

⸻

5. Create Application in Current Directory

ng new my-app

Normally Angular creates:

my-app/

You can then enter it:

cd my-app

⸻

## 6. Start Angular Development Server
```bash
ng serve
```
Short form:
```bash
ng s
```
Usually application runs at:

http://localhost:4200

⸻

Open browser automatically
```bash
ng serve --open
```
Short:
```bash
ng s -o
```
⸻

Specify port
```bash
ng serve --port 4300
```
Then:

http://localhost:4300

⸻

Specify host
```bash
ng serve --host 0.0.0.0
```
Useful when accessing the Angular application from another machine.

⸻

Production configuration
```bash
ng serve --configuration production
```
Short:
```bash
ng serve -c production
```
⸻

7. Build Angular Application

Basic:
```bash
ng build
```
Short:
```bash
ng b
```
Angular creates the build output in:

dist/

Example:

dist/
└── my-app/

⸻

Production Build

Modern Angular CLI uses the appropriate production-oriented build configuration when building for deployment.
```bash
ng build --configuration production
```
Short:
```bash
ng build -c production
```
⸻

## 8. Build Output

After:
```bash
ng build
```
you generally get something like:

dist/
└── my-app/
    ├── browser/
    │   ├── index.html
    │   ├── main....js
    │   ├── styles....css
    │   └── ...
    └── ...

The exact output structure can vary by Angular version/configuration.

The build output, not your source files, is what you normally deploy to a web server.

⸻

## 9. Generate Commands

The most important Angular CLI command after ng new is:

ng generate

Short form:
```bash
ng g
```
General syntax:
```bash
ng generate <type> <name>
```
Example:
```bash
ng generate component employee
```
Short:
```bash
ng g c employee
```
⸻

10. Generate Component
```bash
ng generate component employee
```
Short:
```bash
ng g c employee
```
Creates component files such as:

employee/
├── employee.component.ts
├── employee.component.html
├── employee.component.css
└── employee.component.spec.ts

Depending on Angular version/configuration, the exact generated files can differ.

⸻

Component inside folder

ng g c employees/employee-list

Creates:

employees/
└── employee-list/

⸻

Skip test file
```bash
ng g c employee --skip-tests
```
Short:
```bash
ng g c employee --skip-tests
```
⸻

11. Generate Service
```bash
ng generate service employee
```
Short:
```bash
ng g s employee
```
Creates:

employee.service.ts
employee.service.spec.ts

Skip test:

ng g s employee --skip-tests

⸻

12. Generate Directive

ng generate directive highlight

Short:
```bash
ng g d highlight
```
⸻

13. Generate Pipe
```bash
ng generate pipe employee-status
```
Short:
```bash
ng g p employee-status
```
⸻

14. Generate Class
```bash
ng generate class employee
```
Short:
```bash
ng g cl employee
```
⸻

15. Generate Interface

ng generate interface employee

Short:
```bash
ng g i employee
```
Example:
```bash
ng g i models/employee
```
Can create:

employee.ts

⸻

16. Generate Enum
```bash
ng generate enum employee-status
```
Short:
```bash
ng g e employee-status
```
⸻

17. Generate Guard
```bash
ng generate guard auth
```
Short:
```bash
ng g g auth
```
Angular CLI may ask which guard type you want.

Example:

CanActivate
CanActivateChild
CanDeactivate
CanMatch

⸻

18. Generate Resolver
```bash
ng generate resolver employee
```
Short:
```bash
ng g r employee
```
Resolvers can load data before route activation.

⸻

19. Generate Interceptor
```bash
ng generate interceptor auth
```
Short:
```bash
ng g interceptor auth
```
Used commonly for:

* JWT token
* Authorization headers
* HTTP error handling
* Request/response modification

Example:

auth.interceptor.ts

⸻

20. Generate Middleware

Depending on Angular version/context, available generators can differ. Check:
```bash
ng generate --help
```
Do not assume every generator from older Angular tutorials exists in your installed version.

⸻

21. Generate Application

ng generate application admin

Short:

ng g application admin

Useful particularly when working with a workspace containing multiple applications.

⸻

22. Generate Library
```bash
ng generate library shared-ui
````
Short:
```bash
ng g library shared-ui
```
Useful for reusable Angular code.

⸻

23. Generate Module

Older/module-based Angular applications commonly use:

ng generate module employee

Short:

ng g m employee

Example:

ng g m employee --routing

However, modern Angular strongly uses standalone components, so you should understand both standalone and NgModule-based applications.

⸻

24. Generate Routing Module

ng g m app-routing --flat --module=app

This is mainly relevant to NgModule-based projects.

For modern standalone Angular, routing is commonly configured through application configuration and route files rather than an AppRoutingModule.

⸻

25. Generate Configuration

ng generate config

The exact generators/options available depend on your Angular CLI version.

Always check:

ng generate --help

⸻

26. List Available Generate Types
```bash
ng generate --help
```
This is very important.

**You will see available schematic types such as:**
- component
- directive
- enum
- guard
- interface
- interceptor
- library
- module
- pipe
- resolver
- service

The available list depends on your Angular CLI version.

⸻

27. Angular CLI Aliases

Common aliases:

Full command |	Short
|---|---|
ng serve |	ng s
ng build |	ng b
ng generate	| ng g
ng test |	ng t
ng lint |	ng lint
ng version |	ng v
ng e2e |	ng e2e

⸻

28. Test Angular Application
```bash
ng test
```
Short:
```bash
ng t
```
Runs unit tests using the test setup configured in the project.

⸻

Run tests once

Depending on the Angular/test runner version, use the appropriate CLI/test-runner options. Check:

ng test --help

⸻

29. End-to-End Testing

Historically:

ng e2e

Modern Angular does not necessarily include an E2E framework by default.

You may use tools such as:

* Playwright
* Cypress

The exact command depends on what you install/configure.

⸻

30. Lint

ng lint

Important:

Modern Angular projects may not have a lint target by default.

If ESLint is configured:

ng lint

works.

⸻

31. Angular Update

Check outdated Angular packages:

ng update

Update Angular CLI/core:

ng update @angular/cli @angular/core

Example:

ng update @angular/cli@21 @angular/core@21

Always check the Angular version and official migration guidance before performing a major-version update.

⸻

32. Update Specific Package

Example:

ng update @angular/material

⸻

33. Add Angular Package

Angular CLI provides:

ng add <package>

Example:

ng add @angular/material

ng add is different from:

npm install

ng add can install a package and execute that package’s Angular setup schematic.

⸻

34. Install Package with npm

Normal npm:

npm install package-name

Example:

npm install axios

Development dependency:

npm install --save-dev package-name

Example:

npm install --save-dev eslint

⸻

35. Angular Material

Install:

ng add @angular/material

This can configure:

* Angular Material
* CDK
* animations
* theme-related setup

⸻

36. Remove Package

Use npm:

npm uninstall package-name

Example:

npm uninstall axios

⸻

37. Angular Workspace

Create workspace:

ng new my-workspace

Typical structure:

my-workspace/
├── angular.json
├── package.json
├── tsconfig.json
├── src/
│   ├── main.ts
│   ├── index.html
│   └── app/
└── ...

⸻

38. Important Angular Files

angular.json

Angular CLI workspace configuration.

Contains configuration for:

* projects
* build
* serve
* test
* assets
* styles
* scripts
* configurations

⸻

package.json

Contains:

dependencies
devDependencies
scripts

Example:

{
  "scripts": {
    "start": "ng serve",
    "build": "ng build"
  }
}

⸻

package-lock.json

Locks installed npm dependency versions.

⸻

tsconfig.json

TypeScript configuration.

⸻

src/main.ts

Application entry point.

⸻

src/index.html

Main HTML page.

Angular application is loaded from here.

⸻

39. Run Through npm

Instead of:
```bash
ng serve
```
you can commonly use:
```bash
npm start
```
if package.json contains:

"start": "ng serve"

Build:

npm run build

if configured accordingly.

⸻

40. Serve With Specific Configuration
```bash
ng serve -c development
```
or:
```bash
ng serve -c production
```
Configuration is normally defined in:

angular.json

⸻

41. Build With Configuration
```bash
ng build -c production
```
or:
```bash
ng build --configuration production
```
⸻

42. File Replacement / Environment Configuration

Angular projects can have configuration/environment setup depending on the Angular version and project structure.

Typical commands:
```bash
ng build -c production
```
The selected configuration can control things such as:

* optimization
* source maps
* file replacements
* budgets
* output settings

⸻

43. Build With Base Href

Useful when deploying Angular under a subdirectory:

ng build --base-href /myapp/

For example:

https://example.com/myapp/

⸻

44. Deploy Angular to a Subdirectory

Example:
```bash
ng build --configuration production --base-href /employee/
```
Then deploy the generated build files under:

/employee/

⸻

45. Watch Build
```bash
ng build --watch
```
Angular rebuilds when source files change.

Useful during development.

⸻

46. Build With Source Maps

Depending on configuration:
```bash
ng build --source-map
```
Source maps help debugging generated JavaScript back to TypeScript source.

For production, consider whether source maps should be publicly exposed.

⸻

47. Build With Optimization
```bash
ng build --optimization
```
Optimization can include production-oriented optimizations depending on Angular CLI version/configuration.

⸻

48. Disable Optimization
```bash
ng build --optimization=false
```
Useful mainly for development/debugging scenarios.

⸻

49. Angular Cache

Angular CLI has a build cache.

Show cache information:

ng cache

Clean cache:

ng cache clean

Disable cache:

ng cache disable

Enable cache:

ng cache enable

⸻

50. Angular Analytics

Angular CLI can collect anonymous usage analytics depending on configuration.

Check:
```bash
ng analytics
```
Disable:

ng analytics disable

Enable:

ng analytics enable

⸻

51. Angular Configuration

View CLI configuration:

ng config

Set a configuration value:

ng config <key> <value>

Example syntax depends on the configuration property.

Check:
```bash
ng config --help
```
⸻

52. Get Angular CLI Help

Most important command for learning CLI:

ng help

For a command:

ng serve --help
ng build --help
ng generate component --help
ng update --help

⸻

53. Generate Component With Inline HTML
```bash
ng g c employee --inline-template
```
Instead of:

employee.component.html

the template can be placed inside the TypeScript component.

⸻

54. Generate Component With Inline CSS
```bash
ng g c employee --inline-style
```
⸻

55. Generate Component Without Tests
```bash
ng g c employee --skip-tests
```
⸻

56. Generate Component With Specific Style
```bash
ng g c employee --style=scss
```
⸻

57. Generate Component As Standalone

Modern Angular:
```bash
ng g c employee --standalone
```
Standalone components don’t require declaring the component in an NgModule.

⸻

58. Generate Component Without Standalone

For a module-based application:
```bash
ng g c employee --standalone=false
```
Use this only when your project architecture is using NgModules.

⸻

59. Generate Component and Specify Module

For module-based projects:
```bash
ng g c employee --module=app
```
This tells Angular CLI which module should declare the generated component.

⸻

60. Generate Service With ProvidedIn

Typical Angular service:

ng g s services/employee

Generated service commonly contains:
```js
@Injectable({
  providedIn: 'root'
})
```
This makes the service available through Angular’s root injector.

⸻

61. Generate Guard
```bash
ng g guard auth
```
Common use:
```
Login
  ↓
Auth Guard
  ↓
Dashboard
```
⸻

62. Generate Interceptor

ng g interceptor auth

Common use:

Angular
   ↓
HTTP Request
   ↓
Interceptor
   ↓
Add JWT
   ↓
Backend API

⸻

63. Generate Pipe
```bash
ng g pipe currency-format
```
Example:

Input
 ↓
Pipe
 ↓
Formatted Output

⸻

64. Generate Directive

ng g directive highlight

A directive changes or controls DOM behavior.

⸻

65. Generate Interface

ng g interface models/employee

Example:
```js
export interface Employee {
  id: number;
  name: string;
  salary: number;
}
```
⸻

66. Generate Enum
```bash
ng g enum models/employee-status
```
Example:
```js
export enum EmployeeStatus {
  Active,
  Inactive
}
```
⸻

67. Generate Class
```bash
ng g class models/employee
```
⸻

68. Generate Resolver
```bash
ng g resolver employee
```
Typical flow:
```
Route
 ↓
Resolver
 ↓
API
 ↓
Data
 ↓
Component
```
⸻

69. Generate Application

For multi-project workspace:
```bash
ng g application admin
```
Then:
```bash
ng serve admin
```
Build:
```bash
ng build admin
```
⸻

70. Generate Library
```bash
ng g library shared
```
Build library:

ng build shared

⸻

71. Multi-Project Workspace

You can have:

workspace/
├── projects/
│   ├── admin/
│   ├── customer/
│   └── shared/
└── angular.json

Then specify project:

ng build admin
ng build customer

⸻

72. Angular CLI + npm Basic Workflow

A very common workflow is:

npm install -g @angular/cli
ng new employee-app
cd employee-app
ng serve

Create component:
```bash
ng g c employees
```
Create service:
```bash
ng g s services/employee
```
Create interface:
```bash
ng g i models/employee
```
Create guard:
```bash
ng g g auth
```
Create interceptor:
```bash
ng g interceptor auth
```
Build:
```bash
ng build -c production
```
Deploy the generated build output.

⸻

73. Most Important Angular CLI Commands

Memorize these first:

ng new my-app
ng serve
ng build
ng generate component employee
ng generate service employee
ng generate interface employee
ng generate guard auth
ng generate interceptor auth
ng generate pipe format
ng generate directive highlight
ng test
ng update
ng add <package>
ng version
ng help

⸻

74. Short Commands You Should Memorize

ng new
ng s
ng b
ng g
ng g c
ng g s
ng g i
ng g g
ng g p
ng g d
ng g e
ng g cl
ng g r
ng test
ng v
ng help
ng update
ng add

⸻

75. Complete Angular CLI Cheat Sheet

Purpose	Command
Install CLI	npm install -g @angular/cli
Version	ng version
Help	ng help
Create app	ng new my-app
Start server	ng serve
Start + browser	ng serve -o
Custom port	ng serve --port 4300
Build	ng build
Production build	ng build -c production
Watch build	ng build --watch
Generate	ng generate
Generate short	ng g
Component	ng g c employee
Service	ng g s employee
Directive	ng g d highlight
Pipe	ng g p format
Guard	ng g g auth
Interface	ng g i employee
Enum	ng g e status
Class	ng g cl employee
Resolver	ng g r employee
Interceptor	ng g interceptor auth
Module	ng g m employee
Application	ng g application admin
Library	ng g library shared
Unit tests	ng test
Update packages	ng update
Add package	ng add package-name
Cache info	ng cache
Clear cache	ng cache clean
Analytics	ng analytics
CLI config	ng config

⸻

76. The Angular CLI Mental Model

Remember Angular CLI in 5 groups:
```
                 ANGULAR CLI
                      │
       ┌──────────────┼───────────────┐
       │              │               │
    CREATE         DEVELOP         GENERATE
       │              │               │
    ng new        ng serve          ng g c
                                  ng g s
                                  ng g g
                                  ng g i
       │
       └──────────────┬────────────────┘
                      │
                   BUILD
                      │
                  ng build
                      │
                   TEST/UPDATE
                      │
                ng test / ng update
```
The 10 commands to learn first

npm install -g @angular/cli
ng version
ng new my-app
cd my-app
ng serve
ng g c employee
ng g s employee
ng g g auth
ng build -c production
ng help

Important: Angular CLI commands and generated file structures can change between Angular major versions. When in doubt, use ng <command> --help on your installed CLI rather than relying on an older tutorial.