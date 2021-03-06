# Fibonacci With ES6

![daniel](https://lh3.googleusercontent.com/-oT20EAIP6zI/AAAAAAAAAAI/AAAAAAAAAAA/K1bYEZIyw2s/mo/photo.jpg?sz=46)

## Table of Contents

  1. [Class definition](#class-definition)
  1. [Usage] (#usage)

##Class definition

``` javascript

"use strict";

let instance = Symbol();
let instanceEnforcer = Symbol();

/**
 * Class Fibanacci Serie
 */
class Fibonacci{
   

    static get instance(){
        if (!this[instance]) {
            this[instance] = new Fibonacci(instanceEnforcer);
        }

        return this[instance];
    }

    constructor(enforcer){
        if (enforcer !== instanceEnforcer) throw ('Cannot construct singleton');
    }

    execute(number){
        if (number == 0 || number == 1) return number;

        return this.execute(number-2) + this.execute(number-1);
    }

    static print(value){
        let res = '';
        let fibo = Fibonacci.instance;

        for (let i = 0; i < value; i++){
            res += `Fibonacci(${i}) = ${fibo.execute(i)} \n`;
        }

        return res;
    }
}
  ```

##Usage

``` javascript
Fibonacci.print(10)
  ```
