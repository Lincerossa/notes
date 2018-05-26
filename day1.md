# Proxy
* The Proxy is a new feature of es6.
* It’s an object. His constructor receives two arguments:
	1. {} -> object that will be “processed” by the Proxy object
	2. handler:

	— It’s an object that has specific methods used by the Proxy. (es. get, set, …)
	— The **get** methods, for example, receives two arguments:
  
		a] target: proxied object.
		b] name: property that the proxy tries to access

```
	const proxy = new Proxy({},handler)
```


 **Common Object Property Lookup Behavior**
```
	const user = {
		name: 'marcello',
		age: 27
	}

	user.name // marcello
```

**Proxied Object Property Lookup Behavior**

```
	const user = {
		name: 'marcello',
		age: 27
	}

	const handler = {
		get: (target, name) => {
			if(name in target){
				return target[name]
			}
			return 'the key doesn't exist'
		}
	}

	const myFirstProxy = new Proxy(user, handler)

	myFirstProxy.name // marcello
 	myFirstProxy.age // 27
	myFirstProxy.test // the key doesn't exist
```


**EXAMPLE**

We could, for example, simulate a **fake private property** of the object

  1. We create an object
```
const object = {
	_private : 'private',
	public: 'public'
}
```

  2.  We create the method get of the Proxy object
```
const handleProxy = {
	get: (target, name) => {
		if(name.indexOf("_") !== -1) return null
		return target[name]
    }
}
```

  3. We create a function (a **thunk** in this case) that will be used when we need to proxy an object
```
	const getProxiedObject = (obj, method) => new Proxy(obj, method)
```

  4. We call that function 
```
  const proxiedObject = getProxiedObject(object, handleProxy)
```

  5.  Let’s try to access it!
```
	proxiedObject._private //null
	proxiedObject.public // public

	...then the magic!
	proxiedObject._blablabla //public	
```