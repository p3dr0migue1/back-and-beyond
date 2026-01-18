+++
date = '2024-11-05T18:30:03Z'
draft = false
tags = ['JavaScript']
title = 'Destructure in Javascript'
+++

Destructure with default value in JavaScript
```js
const { id, active = true } = {
	id: 10,
	name: "John"
};

console.log(id, active);
>>> 10 true
```

Destructure from array in JavaScript
```js
const [lat, lng] = [52.369661, 4.897243];

console.log(lat, lng);
>>> 52.369661 4.897243
```

Destructure from object in JavaScript
```js
const { lat, lng } = {
	lat: 52.369661,
	lng: 4.897243,
	elevation: -2
};

console.log(lat, lng);
>>> 52.369661 4.897243
```
