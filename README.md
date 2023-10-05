# OOP-Relation

Before we learn about relationship on OOP, we will discuss about static method and instance method

```js
'use strict'

class Car {
    constructor(model, price){
        this.model = model;
        this.price = price
    }

    // this is instance method
    applyDiscount(){
        let today = new Date()
        let date = today.getDate()
        if(date % 8 === 0){
            this.price *= 0.9
            console.log(`Discount Applied`);
        }else{
            console.log(`Failed Applied Discount`);
        }
    }

    // this is  static method
    static startEngine(){
        console.log(`Engine Started from static method`);
    }
}

const newCar = new Car('Toyota', 150_000_000)


//to call instance method you need to make instance object first then call the method from the object
newCar.applyDiscount()

//to call static method you can direct call the method by call the class first then put the method
Car.startEngine()
```

## OOP - Relationship

## Composition

sebuah hubungan antar Class yang mana sebuah Class merupakan bagian dari Class lain, dan saling tergantung satu sama lain. Jika main Class tidak di instance, maka sub-class tidak akan terinstance karena sub class menjadi part dari main class.

## Aggregation

Hubungan antara dua Kelas dimana kelas bagian atau sub-class bisa eksis tanpa harus bergantung pada Kelas utama. jadi jika main Class tidak di instance sub-class masih dapat di instance secara terpisah.

for the example :
```js
'use strict'

//Main class is Car
class Car {
    constructor(model, price, engineName, enginePower){
        this.model = model;
        this.price = price
        // this property using relationship composition that's mean if Car destroy, the engine class here destroy too
        this.engine = new Engine(engineName, enginePower)
    }

    // this is instance method
    applyDiscount(){
        let today = new Date()
        let date = today.getDate()
        if(date % 8 === 0){
            this.price *= 0.9
            console.log(`Discount Applied`);
        }else{
            console.log(`Failed Applied Discount`);
        }
    }

    // this is  static method
    static startEngine(){
        console.log(`Engine Started from static method`);
    }
}

//this Sub-Class to Composition cause engine the part of Car
class Engine{
    constructor(name, power){
        this.name = name;
        this.power = power;
    }
    
    startEngine(){
        return `start Engine!`;
    }
}


//this Sub-class to Aggregation cause Driver not a part of Car but still have relationship with the Car
class Driver{
    constructor(name, gender){
        this.name = name;
        this.gender = gender
    }
    
    eat(){
        return `nyam nyam`
    }
}


const newCar = new Car('Toyota', 150_000_000, 'Horse Power', Infinity) // Horse Power and Infinity argument to fill constructor Car to fill constructor sub-class Engine
console.log(newCar.engine.startEngine());

//sub-class added after the instance the main class.. This is one of the features Aggregation
const newDriver = new Driver('Herry', 'male')
newCar.Driver = newDriver
console.log(newCar.Driver.eat());
```


