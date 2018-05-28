# Debug / Testing

## Intro
Today has been a long day!
I needed to refactor some old code that I made some months ago, because I had to reuse it in different places of the React application that we are developing.
I needed to use some methods, (and thanks to God they were completely pure and testable) but in one case I could not remember exactly what they were supposed to do!
That method was not even tested (my bad!).
This is how i got to know console.assert 

## console.assert

Imagine that you have these 2 function expression, but you can’t remember what they are supposed to do (of course this is just an example!)
```
const sum = (a,b) => a+b
const arrayGenerator = (n) => new Array(n)
```


You can use console.assert trying to help your memory!
(But please, pay attention: this is just a tool that can’t replace all those library that are made for testing:  jest,  karma, …)

		* console.assert with a true result
```
console.assert(sum(1,2) === 3) 
```
  this is ok, so it doesn't do anything

		* console.assert with a false result
```
console.assert(arrayGenerator(12) === 182) 
```
 this shows an error message, without breaking the app.