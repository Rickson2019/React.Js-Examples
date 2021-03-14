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

### You should do the following to make it work:

```js
    setItems(prevState => [...prevState, newInput]);
```

## map()

`map()` only works on instances of `Array`.

If you want to render data in the format of an array, this is the way 
to do it.

If you are dealing with nested array, you use nested map().

the first map() will deal with one dimensional array,
while the second map() is going to render the stuff in two dimensional arrays.

```js
{
    (input_groups instanceof Array) && input_groups.map((group) =>
        <div className={styles.input_group}>
            {group.map((item) =>
                item.type &&
                <Fragment>
                    <label>{item.type}</label>
                    <input key={item.id} name={item.id} id={`input-${item.id}`} />
                </Fragment>
            )}
        </div>
    )
}
```



