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