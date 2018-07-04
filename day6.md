# Object setters and getters


```

let person = {
    _name: 'Marci',
    _age: 27,
    set age(newage){
      if(typeof newage === 'number'){
        this._age = newage
      }
    },
    get age(){
      console.log(`${this._name} is ${this._age} old`)
      return this._age
    }

  };

  // Nothing happens
  person.age = 'trying to change the age with a string'
  person.age


  // Update the age value
  person.age = 31
  person.age


```