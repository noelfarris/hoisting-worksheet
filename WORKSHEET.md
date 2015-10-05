# JavaScript Hoisting Worksheet

## Instructions
1. Review each code snippet below.
2. Fill in what will be output to the console.
3. Run the code to see if you were correct.
4. Describe why the code behaved as it did.
5. Re-write the code snippet to maintain the same output, but to avoid hoisting.

```js
var myvar = 'my value'; 
  
(function() { 
	console.log(myvar);
	var myvar = 'local value'; 
})();
```

> output:
>-undefined
>-
>-
> why?
>-var myvar is being hoisted without it's definition. 
>-
>-
>-
>-
>-
> rewrite without hoisting
>-var myvar = 'my value';
>-
>-(function() {
	var myvar
	console.log(myvar);
	myvar = 'local value';
})

```js
var flag = true; 
  
function test() {
	if(flag) {
		var flag = false;
		console.log('Switch flag from true to false');
	}
	else {
		flag = true;
		console.log('Switch flag from false to true');
	}
}
test();
```

> output:
>-Switch flag from false to true
>-
>-
> why?
>-inside the if statment var flag is set to false.
>-
>-
>-
>-
>-
> rewrite without hoisting
>-var flag = true;

function test() {
	if(flag) {
	console.log('Switch flag from true to false');
	}
	else {
		flag = true;
		console.log('Switch flag from false to true');
	}
}
test();
>-


```js
var message = 'Hello world'; 
  
function saySomething() {
	console.log(message);
	var message = 'Foo bar';
}
saySomething();
```

> output:
>-undefined
>-
>-
> why?
>-var message = 'foo bar' is hoisted without the definition.
>-
>-
>-
>-
>-
> rewrite without hoisting
>-function saySomething() {
	var message
	console.log(message);
	var message = 'Foo bar';
}
saySomething();
>-


```js
var message = 'Hello world'; 
  
function saySomething() {
	console.log(message);
	message = 'Foo bar';
}
saySomething();
```

> output:
>-Hello World
>-
>-
> why?
>-console.log is looking at message defined globally.
>-
>-
>-
>-
>-


```js
function test() {
	console.log(a);
	console.log(foo());

	var a = 1;
	function foo() {
		return 2;
	}
}
 
test();
```

> output:
>-undefined, 2
>-
>-
> why?
>-var a is hoisted and function foo runs regardless of position.
>-

> rewrite without hoisting
>-function test() {
	var a;
	console.log(a);
	console.log(foo());

	var a = 1;
	function foo() {
		return 2;
	}
}


```js
(function() {
	console.log(bar);
	foo();

	function foo() {
		console.log('aloha');
	}

	var bar = 1;
	baz = 2;
})();
```

> output:
>-undefined, aloha
>-
>-
> why?
>-var bar is hoisted without being defined and function foo runs regarless of position.
>-
>-
>-
>-
>-
> rewrite without hoisting
>-(function() {
	var bar
	console.log(bar);
	foo();

	function foo() {
		console.log('aloha');
	}

	var bar = 1;
	baz = 2;
})();
>-


```js
var run = false;

function fancy(arg1, arg2) {
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	function run() {
		console.log('Will I run?');
	}
}
fancy();
```

> output:
>-I can run
>-
>-
> why?
>-the if statement is looking to see if the function run is true.
>-
>-
>-
>-
>-
> rewrite without hoisting
>-var run = false;

function fancy(arg1, arg2) {
	function run() {
		console.log('Will I run?');
	}
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	
}
fancy();
>-


```js
var run = false;

function fancy(arg1, arg2) {
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	var run = function() {
		console.log('Will I run?');
	}
}
fancy();
```

> output:
>-I can't run
>-
>-
> why?
>-var run = function will be hoisted without a definition and will be false, therefore the else statement will run.
>-
>-
>-
>-
>-
> rewrite without hoisting
>-var run = false;

function fancy(arg1, arg2) {
	var run;
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	var run = function() {
		console.log('Will I run?');
	}
}
fancy();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-