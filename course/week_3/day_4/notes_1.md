# Week 3 - Day 4

## Arrays:

Arrays are the most basic data structure that JavaScript offers users. 

Arrays can store any type of data including `numbers` `strings` `booleans` etc.   

### Syntax:

```javascript
var array_name = [element1, element2 ...]
```

**Example:**  

```javascript
var numbers = [0, 2, 3, 56, 90]
```

### Empty Arrays:

Lets say you have some data you want to store in an array at a later time. You can declare an empty array before you generate your data as follows. 

**Example:**  

```javascript
var emptyArray = []
```

### Can you store multiple types of data in the same array ?

The simple answer is ***YES!***. JavaScript allows you to store all types of data within the same array. 

**Example:**

```javascript
var multiple = [12, "Masai", true]
```

The above array `multiple` has 3 different types of data in it. Namely `number` `string` and `boolean`.


### Array Length

Getting the array length is simple. Just use the `arrayname.length` property.

**Example:**

```javascript
var numbers = [0, 1, 2, 3, 4]
console.log(numbers.length)
```

**Output:**

```javascript
5
```


### Accessing array elements:

Just like strings we can use the `array[index]` syntax to access any element of an array. 

***Example:**

```javascript
var fruits = ["apple", "pear", "mango", "banana"]
console.log(fruits[0])
console.log(fruits[fruits.length-1])
```

**Output:**

```javascript
apple
banana
```

### Looping Through Arrays

Again just like strings we can loop through arrays and access each element by its `index`.

**Example:**

```javascript 
var cities = ["bangalore", "mumbai", "chennai", "new york", "hong kong"]

for(var i = 0; i < cities.length;i++){
	console.log(cities[i])
}
```

**Output:**

```
bangalore
mumbai
chennai
new york
hong kong
```

### Adding to the End of an array:

You can add an element to the end of an array by using the `arrayname.push(element)` function. 

**Example:**

```javascript 
var cities = ["bangalore", "mumbai", "chennai", "new york", "hong kong"]
cities.push("delhi")
```

***Output:**

```javascript
["bangalore", "mumbai", "chennai", "new york", "hong kong", "delhi"]
```

### Removing from the end of an array

You can remove an element from the end of an array by using the `arrayname.pop()` function. 

**Example:**

```javascript 
var cities = ["bangalore", "mumbai", "chennai", "new york", "hong kong"]
cities.pop()
```

***Output:**

```javascript
["bangalore", "mumbai", "chennai", "new york"]
```

The `pop()` function also returns the removed value. 

There are many more useful array functions available in JavaScript, you can read about them in this link [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
