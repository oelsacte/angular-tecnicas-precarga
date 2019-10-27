# AngularTecnicasPrecarga

## Paso 1

Se agregó el atributo data a algunos Routes en el app-routing-modules con el atributo preload en true:

`data: { preload: true }` 

para los módulos que queremos que se precargar. El resto serán cargados hasta que sean invocados.

## Paso 2

Se crea un servicio que implemente la interfaz PreloadingStrategy de '@angular/router'. Se sobreescribe el método de la interfaz del siguiente modo para que pueda leer el atributo preload.

`preload(route: Route, fn: () => Observable<any>): Observable<any> {
    if (route.data && route.data[\"preload\"]) {
      return fn();
    } else {
      return of();
    }
 }`

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
