# Precarga Quicklink

## Paso 1

Se instala `npm i ngx-quicklink --save`

## Paso 2

Luego se importa el `QuicklinkModule` al `AppModule` y se usa el `QuicklinkStrategy` como `preloadingStrategy` en la configuración del `app-routing.module`.

```ts
import { QuicklinkModule, QuicklinkStrategy } from 'ngx-quicklink';

@NgModule({
  declarations: [...],
  imports: [
    // ...
    QuicklinkModule,
    RouterModule.forRoot(routes, { preloadingStrategy: QuicklinkStrategy }),
  ],
  bootstrap: [...]
})
export class AppModule {}
```

Lo que hace esta técnica es precargar solamente los módulos de los routerLink que estén en el viewport o, dicho de otro modo, en la zona visible del scroll de la página.