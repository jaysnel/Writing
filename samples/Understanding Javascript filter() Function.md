# Understanding Javascript: filter() Out the Noise

Javascript filter() function is one of my favorite array functions and can be very useful in many cases. But it can be tricky to get the hang of at first and to get over the that bump in the road you need to understand 2 things about filter().

1. Filter returns a new array so you will need to set this to a new variable.

2. You must realize that filter() is creating a new array based off of something inside of a different array that is being interpreted as either true or false.

Lets take a look. We will use this small data set of a few numbers for example:
```
let arrList = [2, 3, 4, 2, 5];
```
Now, lets say we want a new array containing only numbers greater than 3. Using filter() we could have our end product do something like this:
```
let newArr = arrList.filter(item => {
    return item > 3;
})
//[4,5];
```
But, what happened?

We know that filter needs to be set to a new variable since it returns a new array so we have set newArr to be just that:
```
let newArr;
```
Now we need to add the array that we want to filter which is arrList. So you can visualize(or type out if you are following along):
```
let newArr = arrList.filter();
```
Once we have this set up, we need a variable to let the filter() function know which element of the original array we are currently on. We will use the word “item” for this. (You can use anything you would like for this but I recommend it to always be something that makes sense).

At this moment, our steps so far have got us to this point:
```
let newArr = arrList.filter(item);
```
This item represents each value from newArr variable. So the first time we go through this function, item will first be the number 2 because that is the first element of the set, once the function does what it needs to do with this current number 2 it will go to 3 since it is the second number in the list and so on and so on:
```
let arrList = [2, 3, 4, 2, 5];
```
But, we still need to check each of these to see if each number is greater than 3. We will use arrow functions for this for shorthand and will be the code from earlier:
```
let newArr = arrList.filter(item => {
    return item > 3;
})
```
Note: You can also write this without the curly braces but for familiarity we will keep them.

So, we have a variable that will contain our new array, we have the variable we will use for each item in the array and now we have added the function that we need to evaluate to true or false.

So lets walk through this final step.

The arrList.filter() runs and the “item” variable gets set to 2.

In the function you see “return item > 3” which is really “return 2 > 3”.

2 is not larger than 3 so it skips it.

Item now becomes 3 or “item > 3” or “3 > 3”.

3 is not larger than 3 so it skips it.

Item now becomes 4 or “item > 3” or “4 > 3”

4 is larger than 3! So 4 gets added to this new array at which point it looks like this in the background running:
```
newArr = [4];
```
It will continue through 2 and then 5 until the end product:
```
newArr = [4, 5];
```
I hope this has helped you understand filter() in javascript just a little better. If you have any questions please feel free to reach out.

Happy coding!

