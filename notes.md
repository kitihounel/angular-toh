# Notes

## Routing
To add routing capabilities to the app, first add a routing module.
```
ng generate module app-routing --flat --module=app
```
- `--flat` puts the file in src/app instead of its own folder.
- `--module=app` tells the CLI to register it in the imports array of the AppModule.

Replace the code inside the file by soething similar to this.
```js
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { YourComponent } from './path/to/your.component';

// Configure your routes here...
const routes: Routes = [
  { path: 'your-path', component: YourComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

Update your `AppComponent` template and add a `router-outlet` element.
```html
<h1>{{title}}</h1>
<router-outlet></router-outlet>
<other-component></other-component>
```

Add links to enable users to navigate.
```html
<h1>{{title}}</h1>
<nav>
  <a routerLink="/your-path">Some text</a>
</nav>
<router-outlet></router-outlet>
<app-messages></app-messages>
```

Finally add a default route if you want. When the app starts, the browser's address
bar points to the web site's root. That doesn't match any existing route so the router
doesn't navigate anywhere. The space below the `<router-outlet>` is blank.

To make the app navigate to the dashboard automatically, add the following route to
the AppRoutingModule.Routes array.
```js
{ path: '', redirectTo: '/home', pathMatch: 'full' }
```

This route redirects a URL that fully matches the empty path to the route whose path is `/home`.
