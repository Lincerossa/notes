# Promise

## the Constructor
* The constructor of the Promise object takes a function 
* This function receives two arguments: resolve, and reject

```
	const myPromise = new Promise((resolve, reject) => {
   ...
	})
```


## the Value

* The promise value represents its status which can be “rejected”, “fulfilled”, or “pending”.

* The promise value changes when the resolve or reject functions are called

```
	const myPromise = new Promise((resolve, reject) => {
		// value -> pending
		...
		resolve() // value -> fulfilled
		...
		reject() // value -> rejected
	})
		
```

## the Prototype methods (then or catch)

* resolve is called -> value is fulfilled -> then() of the prototype is called
* reject is called -> value is rejected -> catch() of the prototype is called

```
myPromise
	.then(x => x) 
	.catch(err => err)
```


* The **then** method of the promise prototype **receives a function** (so it’s an  **higher order function**)
* That function receives what is passed to the resolve methods (that is the first argument of the function passed to the promise constructor, when the promise has been instantiated)









