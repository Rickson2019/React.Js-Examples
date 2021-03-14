# Use Effect

What useEffect 

## Eamples


### Example 1

https://stackoverflow.com/questions/56247433/how-to-use-setstate-callback-on-react-hooks

```js
useEffect(() => {
   console.log('Do something after counter has changed', counter);
}, [counter]);
```

### Example 2

Intened to console.log() the `child_input_type_opt` state
after calling setOpt:

```js
    const [child_input_type_opt, setOpt] = useState(null)
```

This doesn't work properly, even though using promise:

```js
    const getOptionFunction = (option) => {
        console.log('getOptionFunction');
        console.log('option')
        let p = new Promise(async (resolve, reject) => {
            await setOpt(option)
            resolve('setState is executed')
        })


        p.then((str) => {

            console.log(str)
            console.log(child_input_type_opt)
        })
    }
``` 

This works fine:

```js
    useEffect(() => {
        console.log(child_input_type_opt)
    }, [child_input_type_opt])
```
