---
layout: post
title:  "React Hooks equivalents on Component Lifecycle."
image: /assets/images/react-logo.png
---
In React 16.8, the Hooks were introduced to reduce the complexity of the components lifecycle. This enables us to create components without visual logic (like React Router, that forces us to render a <Router> element).

The `useEffect()` function runs every time that a component renders unless you specify the variables to watch. 

## constructor(props) 
The constructor creates the initial state of the component. You can set the `this.state` to create initial values.

To do the same in React Hooks, you need to use a `useState()` function that returns an array with two elements: a variable that represents the state and a function to update the state.

The argument passed to `useState()` represents the initial state of the component. 

```
const [ variable, setVariable ] = useState(false) 
```

## render()
Basically, the component returns the elements that you want to render.

```
export function MyComponent(props) {
	return (
		<Button />
	)
}
```
### It is easy to handle inputs!
This is the simple it can gets
```
export function MyInput (props) {
	const [name, setName] = useState('Davi')
	return (
		<input 
			type="text"
			value = {name}
			onChange = {e => setName(e.target.value) }
		/>
	)
}
```

## componentDidMount()
Passing an empty array as last argument makes it only runs when component mounts for the first time. This locks the fuction for no dependencies. 
```
useEffect(()=> {
//...code
},[]) 
```
## componentDidUpdate()
Passing the variable to the second argument makes it run when the variable is updated using `setState()`.

```
const [variable, setVariable] = useState(false) // false is the default state. 

useEffect( () => {
//...code
}, [variable] )
```
Whenever you use `setVariable(true)`, the `useEffect()` function will run again. 

## componentWillUnmount()

`useEffect()` can return a function that runs before every subsequent call of the same `useEffect` instance. 
```
useEffect( () => {
	return () => {
		//... code
	}
}, [])
```
## componentShouldUpdate() 

```
useEffect( () => {
	return () => {
		//... code
	}
},[variable])
```

