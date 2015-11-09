# Beginners guide to JavaScript Object Oriented Programming

---

## Prerequisites
Before beginning this lesson you should feel confident about JavaScript concepts such as variables, types, functions, and scope.

## JavaScript Objects

There are two types of objects within JavaScript: Literal and Constructor. Literal objects do not have behaviour associated with an object (i.e. An object just containing data). If you want to add behaviour to your objects then constructor objects are the way to go. Constructor objects give you the ability to add methods to the object during construction or to give your class a prototype. Always remember to use the KISS (Keep It Simple Stupid) method!

#### Literal Objects

Object created using the literal syntax are what we call singletons. This means when a change is made to the object, it affects that object across the entire script.

```
//Let's make a person object using the literal notation

var person = {
  firstName: "John",
  lastName: "Smith",
  age: 21
}

//If we were to write out our person object our code would look like this.

document.write("First Name = " + person.firstName + "</br>" + "Last Name = " + person.lastName + "</br>" + "Age = " + person.age);
```

Our output from our code would look like this.

First Name = John
Last Name = Smith
Age = 21

Now let us try adding a new person to see what we get.

```
var person = {
  firstName: "John",
  lastName: "Smith",
  age: 21
}

document.write("First Name = " + person.firstName + "</br>" + "Last Name = " + person.lastName + "</br>" + "Age = " + 21);

//Create a new variable and assign the person object

var newPerson = person;

//Change the property of the person object using the new variable

newPerson.firstName = "Johnny";
newPerson.lastName = "Appleseed";
newPerson.age = 170;

// Now if we retrieve the propterties from the original object, you will notice that the properties have changed to the newPerson values.

document.write("First Name = " + person.firstName + "</br>" + "Last Name = " + person.lastName + "</br>" + "Age = " + 21);
```

Notice, like stated before, that when changing the property values within Literal Objects once a change is made it has changed that vaule of that property across the entire script.

#### Contructor Objects

Objects defined with a function constructor lets you have multiple instances of that object. This means that when a change is made to one instance, it will not affect other instances.

```
//Let's write a constructor object with the same values as the previous person object.

var person = function(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
}
```

Notice that the syntax for the constructor object has changed. We use the keyword "this", which is refering to our function "person". We could write "person.firstName = firstName;"" instead but for our code to look cleaner and more effecient the keyword "this" is symantically correct. Also instead of the use of commas, we use semi-colons in order to separate our code.

```
var Person = function(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
}

//Create a variable to add a new person object.

var john = new Person("John", "Smith", 21);
var johnny = new Person("Johnny", "Appleseed", 170);
```

Now that we have our constructor object we can create a new function within our constructor object that will return our object properties.

```
//Go back into our "Person" object and create a new function that will return our properties

var Person = function(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
  this.getPerson = function(Person) {
    return "First Name = " + this.firstName + "</br>" + "Last Name = " + this.lastName + "</br>" + "Age = " + this.age + "</br>";
  };
};

var john = new Person("John", "Smith", 21);
var johnny = new Person("Johnny", "Appleseed", 170);

document.write(john.getPerson());
document.write(johnny.getPerson());
```

Our output should look like this:

```
First Name = John
Last Name = Smith
Age = 21
First Name = Johnny
Last Name = Appleseed
Age = 170
```

#### Prototypes

Every JavaScript object has a prototype, which in itself is also an object. All JavaScript objects inherit their properties and methods from their prototype.

If we were to remove our "getPerson" function within our object we could simply add our same method using the prototype chain.

```
var person = function(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
};

person.prototype.getPerson = function(person) {
  return "First Name = " + this.firstName + "</br>" + "Last Name = " + this.lastName + "</br>" + "Age = " this.age + "</br>";
};

document.write(john.getPerson());
document.write(johnny.getPerson());
```

## Conclusion

So when to use Literal objects over Constructor objects? The rule of thumb or KISS method would be if you need multiple instances of the object use constructor functions, where as if you need just one instance of the object then use Literal.
