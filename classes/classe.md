# Classe

```javascript
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}


let myCar1 = new Car("Ford", 2014);
let myCar2 = new Car("Audi", 2019);

console.log("My car is " + myCar1.age() + " years old.";)
```

{% hint style="info" %}
En el nom de les classes s'utilitza la convenció **UpperCamelCasse**
{% endhint %}
