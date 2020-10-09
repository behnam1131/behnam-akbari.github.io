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

```img
![alt text](/_data/img/textSearch.png)
```