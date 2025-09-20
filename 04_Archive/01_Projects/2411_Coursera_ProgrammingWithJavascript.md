
* Use variables, use `const`, then `let`, the `var` but rarely if ever
* Js objects
	* `var someObject = {}`
	* properties can be accessed and assigned using dot or square notation
		* `someObject.property` or `someObject['property']`
	* use `this` to refer to the object itseld similar to `self` in python classes
	* unlike python dicts, js objects are **not** iterable 
* Js classes 
	* `class someClass { contructur() {}}`
	* when defining class methods, no need to use the function keyword
	* to create an isntance use the `new` keyborws `const car1 = new Car('Ford')`
	* to create a subclass that inherets the base clas `class subClass extends baseClass {}`
* For loops: 
	* `for (i = 0 , i < 10, i++) {}` equivalent to pythons `for i in range(0,10,1):`'
* Built in constructors
	* new Date(); new Error(); new Map(); new Promise(); new Set()