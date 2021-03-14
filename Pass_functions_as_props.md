# Pass Functions as Props

In order to get state in a child component from a parent component
we usually want to pass in a function into that component to grab data we need.

In the function it's best to invoke a hook 'set' method to change the corresponding state,
in order to do form submission and so on so forth.

## Use Case

There is a SelectionMenu.js child component in a parent component, MultipleChoice.js 
we want to get the selected option in the child component and deal with that option and 
in the parent component.

### Step 1: create the function in parent component

Parent Component 

```js
    // a hook to get user selected option.
    const [opt, setOpt] = useState(null)

    // Will be passed into SelectionMenu，to grab the option
    // user has chosen in the child component.
    const getOptionFunction = (option) => {
        console.log('getOptionFunction');
        console.log('option')
        setOpt(option)
        console.log(option)
        console.log(opt)
    }
```

### Step 2: pass the function in to child component

Parent Component

```js
return (
     <SelectionMenu
        options={Object.keys(admin_input_types)}
        prompt_label={'Choose a type of input to create'}
        func={(opt) => getOptionFunction(opt)} />
        )
 ```
 
 ### Step 3: use the function in the child component
 
 #### Destructure the props  
 
 ```js
export default function SelectionMenu({options, prompt_label, func}) {
 ```
 
 ### Invoke the function
 
 ```js
   const handleMenuItemClick = (event, index) => {
    setSelectedIndex(index);

    func(options[index])
    
    setAnchorEl(null);
  };
 ```
 
 
