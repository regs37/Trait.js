
![Trait.js](https://github.com/regs37/Trait.js/blob/master/src/img/trait.js-logo.png?raw=true)

![liscense](https://img.shields.io/npm/l/trait.js) ![downloads](https://img.shields.io/npm/dw/trait.js) ![version](https://img.shields.io/npm/v/trait.js) ![build](https://img.shields.io/github/workflow/status/regs37/trait.js/Node.js%20CI)

**Trait.js** is a helper which allows javascript to have the same behavior with the Php Trait feature. Allows you to inherit or reuse methods to any classes or objects. There's been other libraries/repositories out there that is also respresents the javascript equivalent of **Php - Traits**. Among them, this solution is a lightweight package and serves only one purpose, **allow any classes to inherit methods from a trait**.

### Installation
##### NPM

```javascript
npm install trait.js
```


### Sample Usage:

Let's create a simple trait that displays the user's fullname.

#### UserTrait.js
```javascript
    import trait from 'trait.js'

    export default trait({
        getFullname: function(){
    	    return `${this.first_name} ${this.last_name}`;
        }
    })
```
#### User.js

For example we have a user model here that wants to use the **UserTrait.js**
```javascript
    import UserTrait from './UserTrait.js';

    export default class User {
        constructor({first_name, last_name}){
    	    this.first_name = first_name;
    	    this.last_name = last_name;
        }
    }

    UserTrait.inheritTo(User);
    // or
    UserTrait.in(User); // a shorthand for inheritTo
```
Let's try to use that method:
```javascript
    import User from './User.js';

    let user = new User({
        first_name: "Foo",
        last_name: "Bar",
    });

    // We can now use the trait method getFullname()
    console.log(user.getFullname()); // Foo Bar
```
### Why use Trait?

In Php, [Traits](https://www.php.net/manual/en/language.oop5.traits.php) are a mechanism for code reuse in single inheritance languages such as PHP. A Trait is intended to reduce some limitations of single inheritance by enabling a developer to reuse sets of methods freely in several independent classes living in different class hierarchies. The semantics of the combination of Traits and classes is defined in a way which reduces complexity, and avoids the typical problems associated with multiple inheritance and Mixins.

A Trait is similar to a class, but only intended to group functionality in a fine-grained and consistent way. It is not possible to instantiate a Trait on its own. It is an addition to traditional inheritance and enables horizontal composition of behavior; that is, the application of class members without requiring inheritance.

> https://www.php.net/manual/en/language.oop5.traits.php

### License
GNU General Public License © 2020 Regs Isabelo
