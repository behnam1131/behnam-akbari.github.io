---
title: RxJS
---

## نکات

```ts
const keyup$ = fromEvent(document, "keyup");

const keyCode$ = keyup$.pipe(
  map(event => event.code)
);
```

```ts
```
```ts
```
```ts
```

```ts
const keyCodeWithPluck$ = keyup$.pipe(
  pluck("code")
);
```
```ts
const space$ = keyCode$.pipe(
  filter(code => code === 'Space')
);
```
```ts
const totalReducer = (acc, curr) => {
  return acc + curr;
};

const interval$ = interval(1000);   // شمارنده با گام 1 ثانیه

const total$ = interval$.pipe(
  take(3),
  reduce(totalReducer, 0)
).subscribe({
  next: console.log,
  complete: () => console.log("complete")
});
```
```ts
const name$ = state$.pipe(
  distinctUntilKeyChanged('name'),
  // distinctUntilChanged((prev, curr) => {
  //   return prev.name === curr.name;
  // }),
  map(state => state.name)
);
```
```ts
const abortClick$ = fromEvent(btn, "click");

counter$.pipe(
    mapTo(-1),
    scan((acc, curr) => {
      return acc + curr;
    }, 5),
    tap(console.log),
    takeWhile(value => value >= 0),
    takeUntil(abortClick$)
  )
  .subscribe(value => {
    countdown.innerHTML = value.toString();
    if (!value) {
      message.innerHTML = "Done";
    }
  });
```
