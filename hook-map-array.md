# React JS hooks and map() with arrays

## Hooks

Let's say you want to add some new stuff into a state that is an array

Initially it looks like this:

```js
const [items, setItems] = useState([{ key: 0, id: 0, type: 'fruits', name:'apple' }, { key: 1, id: 1, type: 'meat', name : 'beef' }])
```

Then you want to push `vegetables` into the `items` array:

```js
let newItem = { key: 1, id: 1, type: 'vegetables',  name : 'celery'}
```

Will this work?

```js
setItems(prevState => items.concat(newItem));
```

How about this?

```js
setItems(prevState => items.push(newItem));
```

Neither of them works.

You should do the following to make it work:

```js
    setItems(prevState => [...prevState, newInput]);
```

## map()
