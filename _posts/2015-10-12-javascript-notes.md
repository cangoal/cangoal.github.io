---
layout: post
title: "JavaScript Notes"
date: 2015-10-12
---


编写js的类，使其拥有public和private类型的属性和方法
```javascript
function Person(_name,_age,_sex,_salary){
	//public
	this.name = _name;
	this.age = _age;

	//privare
	var sex = _sex;
	var salary = _salary;

	//public method
	this.getName = function(){
		return this.name;
	}

	this.getAge = function(){
		return this.age;
	}

	//private methd
	function getSex(){
		return sex;
	}

	function getSalary(){
		return salary;
	}

	this.display = function(){
		document.write(this.getName() + "---" + this.getAge() + "---" + getSex() + "----" + getSalary());
	}

}

var smirk = new Person("zy","21","f","5000");
smirk.display();
```

### this
interview question @ BloomReach
```javascript 
        var a = 1;
        var b = 2;
        var c = 3;
        (function(){
        	var a = "foo";
        	var b = "bar";
        	o = {
        		a: "a",
        		b: "b",
        		c: "c",
        		display: function(){
        			console.log(a); // foo
        			console.log(window.b); // 2
        			console.log(c);  // 3
        		}
        	}
        	o.display();
        }());
```
- how about add "this." before a and c in console.log statement?


### Object Creation
- The Factory Pattern
```javascript
function createPerson(name, age, job){ 
	var o = new Object();
	o.name = name;
	o.age = age;
	o.job = job;
	o.sayName = function(){
	alert(this.name); };
	return o;
}
var person1 = createPerson(“Nicholas”, 29, “Software Engineer”); 
var person2 = createPerson(“Greg”, 27, “Doctor”);
```
- The Constructor Pattern
```javascript
function Person(name, age, job){ 
	this.name = name;
	this.age = age;
	this.job = job;
	this.sayName = function(){ 
		alert(this.name);
	}; 
}
var person1 = new Person(“Nicholas”, 29, “Software Engineer”); 
var person2 = new Person(“Greg”, 27, “Doctor”);
``` 
The major downside to constructors is that methods are created once for each instance. So, in the previous example, both person1 and person2 have a method called sayName(), but those methods are not the same instance of Function. 


- The Prototype Pattern
```javascript
function Person(){ }
    Person.prototype.name = “Nicholas”; 
    Person.prototype.age = 29; 
    Person.prototype.job = “Software Engineer”; 
    Person.prototype.sayName = function(){
	alert(this.name); 
};
var person1 = new Person(); 
person1.sayName(); //”Nicholas”
var person2 = new Person();
person2.sayName(); //”Nicholas” 
alert(person1.sayName == person2.sayName); //true
```
The major problem is both properties and functions are shared by all instances



- Combination Constructor/Prototype Pattern

The constructor pattern defines instance properties, whereas the prototype pattern defines methods and shared properties. With this approach, each instance ends up with its own copy of the instance properties, but they all share references to methods, conserving memory.
```javascript
function Person(name, age, job){ 
	this.name = name;
	this.age = age;
	this.job = job;
	this.friends = [“Shelby”, “Court”]; 
};
Person.prototype = { 
	constructor: Person, 
	sayName : function () {
		alert(this.name); 
	}
};

var person1 = new Person(“Nicholas”, 29, “Software Engineer”); 
var person2 = new Person(“Greg”, 27, “Doctor”);

person1.friends.push(“Van”);
alert(person1.friends); //”Shelby,Court,Van” 
alert(person2.friends); //”Shelby,Court” 
alert(person1.friends === person2.friends); //false 
alert(person1.sayName === person2.sayName); //true
```

- Dynamic Prototype Pattern
- Parasitic Constructor Pattern
- Durable Constructor Pattern

### Inheritance
- Prototype Chaining
```javascript
//problems with prototype chaining
function SuperType(){
	this.colors = [“red”, “blue”, “green”];
};
function SubType(){ }

//inherit from SuperType 
SubType.prototype = new SuperType();
var instance1 = new SubType(); 
instance1.colors.push(“black”); 
alert(instance1.colors); //”red,blue,green,black”
var instance2 = new SubType(); 
alert(instance2.colors); //”red,blue,green,black”
```
- Constructor Stealing (object masquerading or classical inheritance)
```javascript
function SuperType(){
	this.colors = [“red”, “blue”, “green”];
}
function SubType(){
	 //inherit from SuperType
	 SuperType.call(this);
}
var instance1 = new SubType(); 
instance1.colors.push(“black”);
alert(instance1.colors); //”red,blue,green,black”

var instance2 = new SubType(); 
alert(instance2.colors); //”red,blue,green”

// The downside to using constructor stealing exclusively is that it introduces the same problems 
// as the constructor pattern for custom types: methods must be defined inside the constructor, 
//so there’s no function reuse.
```
- Combination Inheritance(sometimes also called pseudoclassical inheritance)
```javascript
function SuperType(name){
	this.name = name;
	this.colors = ["red", "blue", "green"];
}
SuperType.prototype.sayName = function(){ 
	alert(this.name);
};
function SubType(name, age){
	//inherit properties 
	SuperType.call(this, name);
	this.age = age; 
}
//inherit methods
SubType.prototype = new SuperType();
SubType.prototype.sayAge = function(){ 
	alert(this.age);
};
var instance1 = new SubType(“Nicholas”, 29); 
instance1.colors.push("black"); 
alert(instance1.colors); //”red,blue,green,black” 
instance1.sayName(); //”Nicholas”; 
instance1.sayAge(); //29
var instance2 = new SubType("Greg", 27); 
alert(instance2.colors); //”red,blue,green” 
instance2.sayName(); //”Greg”; 
instance2.sayAge(); //27
```
- Prototypal Inheritance
- Parasitic Inheritance
- Parasitic Combination Inheritance
