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
```javascript
