# Proxy (another tip)

## Intro
Sometimes it takes a while to prevent your application for breaking when it comes to accessing many objects and theirs properties!

## Problem

* example of the situation:

```
	const people = contry && 
		country.region &&
		country.region.city &&
		getPeople(country.region.city)

```

* but I would like just to write this (without breaking):

```
	const people = getPeople(country.region.city)
```


## Solution

```

const countries = {
	italy: {
		lombardia: {
			milan: 12,
			gravedona: 1,	
		},
		lazio: {
			rome: 3
		}
	},
	france:{
		IDontKnow: {
			paris: 4
		}
	}
}


const handler = {
	get: (target,name) => {
		return target[name] === undefined
			? new Proxy(target, handler)
			: target[name]
    }
}
const safeAccess = obj => new Proxy(obj, handler)

const proxiedCountries = safeAccess(countries)

```

* let’s try to access it

```

proxiedCountries.italy.lombardia.milan // 12


proxiedCountries.italy.friuli // Proxy {italy: {…}, france: {…}}

proxiedCountries.a.b.c.italy.lombardia.milan // 12
```