---
title: angular
---


## RxJS

```js
  private subject = new Subject();
  observable = this.subject.asObservable();

  this.observable.subscribe(e => {  
    if (e == 1) console.log('1' + e);
  });

  this.subject.next(1);
```


![image/textSearch](image/textSearch.PNG){: .center-image }
![image/Rxjs](image/Rxjs.PNG){: .center-image }

```link
https://github.com/sandikbarr/rxjs-todo
```


## Router

```js
<nav style="text-align:center">
  <button routerLink="login" routerLinkActive="selected-route">Login</button>
  <button routerLink="forgot" routerLinkActive="selected-route">Forgot Password</button>
</nav>
<div>
  <router-outlet></router-outlet>
</div>
```

## Lazy Loading

```js
const appRoutes: Routes = [
  {path: '', component: InstructionsComponent},
  
  {path: 'admin', loadChildren: 'app/admin/admin.module#AdminModule'},
  {path: 'products', loadChildren: 'app/Products/products.module#ProductsModule'}
];
.
.
.
export class AppModule { }
////////////////////////

const adminRoute: Routes = [
  {path: '', component: AdminComponent, canActivate: [LoggedInGuard],
    children: [
      {path: '', component: UsersComponent},
      {path: 'user-list', component: UsersComponent},
      {path: 'add', component: AddUserComponent},
      {path: 'permissions', component: PermissionsComponent, canDeactivate: [PerSavedGuardGuard]},
    ]}
]
@NgModule({
  imports: [
    CommonModule,
    RouterModule.forChild(adminRoute)
  ],
  .
  .
  .
})
export class AdminModule { }
///////////////////////////
const productRoutes: Routes = [
  {path: '', component: ProductsComponent,
    children: [
      {path: '', component: InstructionsComponent},
      {path: 'details/:id', component: DetailsComponent}
    ]},
]
@NgModule({
  imports: [
    CommonModule,
    SharedModule,
    RouterModule.forChild(productRoutes)
  ],
  declarations: [ProductsComponent,
  DetailsComponent],
  providers: [ProductServices]
})
export class ProductsModule { }

```