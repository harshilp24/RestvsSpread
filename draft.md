
# JavaScript Rest vs Spread Operator – What’s the Difference?

You may have come across the terms Rest and Spread in your coding journey and wondered what they meant and how they differed. The JavaScript REST and Spread Operators are just two different ways to declaratively create arrays or array-like objects. When someone asks "What’s the difference?" They are asking which one is more appropriate for their particular situation.

In this article, we'll go over how they work, when to use them, and some common scenarios when they may be better for your code. We'll also take a look at how they work with promises in ES6. So, first, let's understand what a REST Parameter is.

## What is the Rest Parameter ( …rest)?

The rest operator is used to fill a JavaScript array with the remaining data from a user.

-   It creates a single resulting array from all elements in each iteration of the loop.
    
-   The rest operator is represented by the three dots ```(...yourValues)```
    
-   It allows you to handle a variety of inputs as arguments in a function easily. Using the rest parameter, you can supply an array with an endless number of parameters.
    

 **The rest operator is very handy when dealing with arrays and objects**. It allows you to perform complex operations in one line of code, rather than having to write numerous lines of code, just to iterate over the array. To better understand, let's have a look at how Rest Operators work.

  
  

## How does the Rest Parameter work?

Rest Parameter is used as a prefix to the function's last parameter in JavaScript functions. Let’s see an example to understand Rest Operator.

```js
//without rest
function  sum(a,b){
console.log(a+b);
}
sum(1,2,3,4,5,6,7);

//returns - > 3
```
So in JavaScript, a function can be called with any number of parameters, the above function returns 3 as sum of ```(a,b)``` i.e.```(1,2)```. This is because we specified two arguments, and only the first two arguments will be taken into consideration.

Now, let say you want sum of ```1 to 7```, so you will not write ```sum(a,b,c,d,e,f,g)```, this can cause errors and its time consuming. This is when the Rest Parameter comes into play.

With `rest parameters`, you can put as many arguments as you want into an array and do anything you want with them. As a result, lets rewrite the sum function:
  ```js
  //using rest param
function  sum(...values) {
let  outcome = 0;
for (let  arg  of  values) outcome += arg;
console.log(outcome);
return  outcome
}

sum(1) // returns - > 1
sum(1,2) // returns - > 3
sum(1, 2, 3, 4, 5, 6, 7) // returns - > 28
  ```
  _Try It Yourself on -  [Codesandbox](https://codesandbox.io/s/naughty-sanne-o4syq?file=/src/index.js)_
  ### In a Destructuring Assignment, How Does the Rest Operator Work?
  The rest operator is commonly used as a prefix to the last variable of a destructuring assignment. Lets see a example to better understand.
  ```js
variable const [name, lastName, ...otherval] = [
"Writer", "Developer", "Designer", "UI/UX", "Tech Lead"
];

console.log(otherval);

// It will return
['Designer', 'UI/UX', 'Tech Lead']
```
The rest operator (...) tells the system to fill an array with the rest of the user-supplied data. The array is then assigned to the ```otherval``` variable. As a result, **only```...otherval``` will be considered a rest variable.**

### What's the Difference Between Arguments and Rest Parameters?
- Arguments can be assigned to a variable or passed into a function.

- Rest parameters are only assigned an input value when called upon. When they return they leave their variable in their previous state (arguments must be assigned before they can work).
- **On a rest argument, for example, you may use the sort(), map(), forEach(), or pop() methods**. You can't, however, do the same with the arguments object.
- Arguments cannot be passed into functions like rest parameters.   Arguments are additional data, while rest parameters are used as input for other functions. Rest parameters will have inputs with specific names/contexts, but no outputs.

Instead of using the arguments object, it is better to use rest parameters, especially when writing ES6-compatible code.
Now that we understand how rest works, let's look at the spread operator to see how it differs.

## What is the Spread Operator (..spread)?
The JavaScript spread operator allows an array or an object to be spread or flattened into its elements; this is syntactically similar to the way arrays are implemented in languages like Python and R.

- Spread operator: loops through an array, pushing each item from the current array into a new one.
- Spread is mainly used with arrays, but it can also be applied to objects.
- It breaks it up into individual variables of the same name, or
-- merges a list of variables into a single statement, or 
-- converts an object to an array.

**Spread is mainly used for unpacking arrays into their members, but can also be useful when dealing with nested object structures where certain values are shared between them** (e.g., key-value pairs). It is not possible to apply the spread operator to regular JavaScript functions, because that would result in undefined behaviour.

## How does the Spread Operator work?
  
  ```js
 //without spread
function  lognames(name1,name2,name3){
console.log(name1,name2,name3);
}
var  names = ['John','Mark','James']
lognames(names[0],names[1],names[2])
//returns - > John Mark James
```

So in the above code, we are not using spread operator, so we have to call each name, which can be difficult task. To make task simple, we can simply accomplish this using the spread operator.

With Spread Operator, we can replace   ```lognames(names[0],names[1],names[2])``` with ``` ...names ```
```js
function  lognames(name1,name2,name3){
console.log(name1,name2,name3);
}
var  names = ['John','Mark','James']
//using spread 
lognames(...names)
//returns - > John Mark James
```

![Image courtesy stephaniecodes(https://twitter.com/stephaniecodes/status/1029453269242990594)](https://i.imgur.com/FeEU65i.png)

### Spread Use Cases
 Let's have a look at some of the ways spread may be used:
#### Adding array elements to an existing array
Unlike rest parameters, the spread operator can be used as the first input. If you want to add an element to the end of your array, you could do so as follows:
```js
const  info = ["My", "Name", "is"];
const  info2 = ["Hello,", ...info, "Harshil."];

console.log(info2);
//returns - > ['Hello,', 'My', 'Name', 'is', 'Harshil.']
```
As a result, the spread operator simply duplicated the contents of ```info``` into ```info2```,  leaving no connection to the original array. 

#### Converting a String into Individual Array Items Using Spread

To extend name's text value into individual items```(like - John into J,o,h,n)```, we will use the spread operator ```(...)``` within an array literal object ```([...])```:
```js
const  name = "Harshil Patel";
console.log([...name]);

//returns - > ['H', 'a', 'r', 's', 'h', 'i', 'l', ' ', 'P', 'a', 't', 'e', 'l']
```
#### Using Spread in a Function Call

We can use the spread operator if we had an array that we wished to send as a list of arguments to a function. Let's put our  ```sum``` method to use again.
```js
function  sum(a, b, c, d) {
return  a + b + c + d ;
}
const  args = [1, 2, 3, 4];
console.log(sum(...args));
//returns - > 10
```
Note : If the numbers array has more than four elements. The system will only utilise the first four items as ```sum()``` arguments in this scenario and disregard the rest.

#### Copying arrays
The spread operator can be used to duplicate an array in the following ways:
```js
const  arr1 = [1, 2, 3];
const  arr2 = [...arr1];

console.log(arr2);
```
#### Things to keep in mind while using Spread Operator. 
1). Identical characteristics are not cloned by the spread operator.
* Let's say you wanted to clone properties from object A to object B using the spread operator. Assume that object B has qualities that are identical to those of object A. In this instance, the versions in B will take precedence over those in A.
* In the below mentioned example,  ```name ``` and  ```about ``` have similar items, so spread will not clone similar values.
 ```js 
const  name = { firstName:  "Harshil", lastName:  "Patel" };
const  about = { ...name, firstName:  "Harshil", website:  "https://www.patelharshil.net" };
console.log(about);

//returns - > {firstName: 'Harshil', lastName: 'Patel', website: 'https://www.patelharshil.net'}
```


*Try It Yourself on - [Codesandbox ](https://codesandbox.io/s/hungry-leftpad-8idq5?file=/src/index.js)*


2). Spread operators can't expand the values of object literals.
* You can't use the spread operator to extend the values of a properties object since it's not an iterable object.

* On the other hand, the spread operator can be used to replicate properties from one object to another.

3). Be careful when you use spread on objects that include non-primitives!
* Assume you used the spread operator on a primitive values-only object (or array). The system will not establish a link between the original and simply replicated them.

## Wrapping it up

```... ``` might stand for both a spread operator and a rest parameter. How can you detect the difference between the two? Well, that depends on how you use it. It's simple to discern whether you are using the three dots as a rest parameter or a spread operator based on the context.

I hope that this article clarifies the spread operator and rest parameter. In addition, we saw examples and use cases of how to use each operator. Thanks for reading, Happy Coding!

Stay Safe !!
