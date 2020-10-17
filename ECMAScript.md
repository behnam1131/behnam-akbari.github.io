---
title: ECMAScript
---


# ECMAScript


## MAP()
```js
   var course = new Map();
   course.set('react' , {description : 'ui'});
   course.set('jest' , {description : 'testing'});

   console.log(course.get('react'));
   console.log(course.keys());
   console.log(course.values());
```

## Set()
```js
   var books = new Set();
   books.add('book 1');
   books.add('book 2')
        .add('book 3');

   console.log(books);
   console.log(books.size);
   console.log(books.has('book 2'));
   books.delete('book 2');
   console.log(books.has('book 2'));


   var data =[4,2,3,6,5,2,4,1,5,3,2];
   var set = new Set(data);  
   console.log(set); // 4,2,3,6,5,1 
  
```

## Iterators
```js
   var title = 'ES6';

   var iterateId = title[Symbol.iterator]();

   console.log(iterateId.next().value);  // E
   console.log(iterateId.next().value);  // S
   console.log(iterateId.next().value);  // 6
   console.log(iterateId.next().value);  // undefined

```

## Promise
``` js
const spacePeople = () => {
			return new Promise((resolves, rejects) => {
				const api = 'http://api.open-notify.org/astros.json';
				const request = new XMLHttpRequest();
				request.open('GET', api);
				request.onload = () => {
					if(request.status === 200) {
						resolves(JSON.parse(request.response));
					} else {
						rejects(Error(request.statusText));
					}
				};
				request.onerror = err => rejects(err);
				request.send();
			});
		};

		spacePeople().then(
			spaceData => console.log(spaceData),
			err => console.error(
				new Error('Cannot load space people')
			)
		);


```