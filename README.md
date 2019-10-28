# Precarga personalizada

## Paso 1

Se agregó el atributo data a algunos Routes en el app-routing-modules con el atributo preload en true:

`data: { preload: true }` 

para los módulos que queremos que se precargar. El resto serán cargados hasta que sean invocados.

## Paso 2

Se crea un servicio que implemente la interfaz PreloadingStrategy de '@angular/router'. Se sobreescribe el método de la interfaz del siguiente modo para que pueda leer el atributo preload.

`preload(route: Route, fn: () => Observable<any>): Observable<any> {
    if (route.data && route.data["preload"]) {
      return fn();
    } else {
      return of();
    }
 }`
