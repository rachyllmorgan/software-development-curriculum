#Objects#

Objects are a cornerstone of the JavaScript language. Many built in data types such as errors, regular expressions, and functions are represented as objects in JavaScript. In order to be a successful JavaScript developer, you must have a firm grasp on how objects work. This article will teach you the basics of creating and manipulating objects in JavaScript.

Objects are composite data types which are built from primitives and other objects. An object’s building blocks are commonly referred to as its fields or properties. Properties are used to describe some aspect of an object. For example, a property can describe the length of a list, the color of a dog, or a person’s date of birth.

##Creating Objects##

Creating objects in JavaScript is easy. The language provides syntax known as object literal notation for quickly creating objects. Object literals are denoted by curly braces. The following example creates an empty object with no properties.

```
var object = {};
```

Inside of the curly braces, properties and their values are specified as a list of key/value pairs. Keys can be strings or identifiers, while values can be any valid expression. The list of key/value pairs is comma delimited, with each key and value separated by a colon. The following example creates an object with three properties using literal notation. The first property, `foo`, holds the number one. The second property, `bar`, is specified using a string, and also stores a string value. The third property, `baz`, stores an empty object.

```
var object = {
  foo: 1,
  "bar": "some string",
  baz: {
  }
};
```

Note the use of whitespace in the previous example. Each property has been written on a separate line and indented. The entire object could have been written on a single line, but the code is more readable in this format. This is especially true for objects with many properties or nested objects.

##Accessing Properties##

JavaScript provides two notations for accessing object properties. The first, and most common, is known as dot notation. Under dot notation, a property is accessed by giving the host object’s name, followed by a period (or dot), followed by the property name. The following example shows how dot notation is used to read from and write to a property. If `object.foo` initially held the value one, then its value would become two after executing this statement. Note that if `object.foo` did not already have a value, then it would be `undefined`.

```
object.foo = object.foo + 1;
```

The alternate syntax for accessing object properties is known as bracket notation. In bracket notation, the object name is followed by a set of square brackets. Inside the square brackets, the property name is specified as a string. The previous example of dot notation has been rewritten below to use bracket notation. While the code may look different, it is functionally equivalent to the previous example.

```
object["foo"] = object["foo"] + 1;
```

Bracket notation is more expressive than dot notation because it allows a variable to specify all or part of the property name. This is possible because the JavaScript interpreter automatically converts the expression within the square brackets to a string, and then retrieves the corresponding property. The following example shows how property names can be created on the fly using bracket notation. In the example, the property name `foo` is created by concatenating the contents of variable `f`, with the string `"oo"`.

```
var f = "f";

object[f + "oo"] = "bar";
```

Bracket notation also allows property names to contain characters that are forbidden in dot notation. For example, the following statement is completely legal in bracket notation. However, if you tried to create the same property name in dot notation, you would encounter a syntax error.

```
object["!@#$%^&*()."] = true;
```

###Accessing Nested Properties###

Properties of nested objects can be accessed by chaining dot and/or bracket references together. For example, the following object contains a nested object named `baz`, which contains another object named `foo`, which has a property named `bar` that holds the value five.

```
var object = {
  baz: {
    foo: {
      bar: 5
    }
  }
};
```

The following expressions access the nested property, `bar`. The first expression uses dot notation, while the second expression uses square bracket notation. The third expression combines both notations to achieve the same result.

```
object.baz.foo.bar;
object["baz"]["foo"]["bar"];
object["baz"].foo["bar"];
```
Expressions like the ones shown in the previous example can cause performance to suffer if used improperly. Evaluating each dot or bracket expression takes time. If the same property is used multiple times, then it makes more sense to access the property once, and then store the value in a local variable for all future uses. The following example uses `bar` many times within a loop. However, instead of wasting time computing the same value over and over, `bar` is stored in a local variable.

```
var bar = object.baz.foo.bar;
var count = 0;

for (var i = 0; i < 100000; i++) {
  count += bar;
  // better than count += object.baz.foo.bar;
}
```

##Functions as Methods##

When a function is used as an object property, it is called a method. Like properties, methods can also be specified in object literal notation. The following example shows how this is accomplished.

```
var object = {
  sum: function(foo, bar) {
    return foo + bar;
  }
};
```

Methods can also be invoked using dot and bracket notation. The following example invokes the `sum()` method from the previous example using both notations.

```
object.sum(1, 2);
object["sum"](1, 2);
```

##Adding Properties and Methods##

Object literal notation is useful for creating new objects, but it cannot add properties or methods to existing objects. Fortunately, adding new data to an object is as simple as creating an assignment statement. The following example creates an empty object. Two properties, `foo` and `bar`, and a method, `baz`, are then added using assignment statements. Note, that this example uses dot notation, but bracket notation would work equally as well.

```
var object = {};

object.foo = 1;
object.bar = null;
object.baz = function() {
  return "hello from baz()";
};
```

Source: http://www.sitepoint.com/back-to-basics-javascript-object-syntax/
