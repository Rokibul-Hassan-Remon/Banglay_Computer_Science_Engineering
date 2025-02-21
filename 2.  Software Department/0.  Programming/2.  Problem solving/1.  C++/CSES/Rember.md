
## key note for problem solving


### `Problem`
###  Before, performing any operation on  `int`  data type , must remember one thing `int` variable can't store more than `\` 10<sup>11</sup> `\` . So ,  after  operation if there any possibility to get the value  more than `int` data  type storage(10<sup>10</sup>)  .How to solve this problem.
### `Sol` 
store the value in the `long long int ` data types variable but before storing value in the `long long int` variable , must do type caste on *calculated value* unless  get the same `int` data type memory storage and overflow problem will be arise and that's why u may get the negative value . Then understand this type of problem arise in your code.

# what actually happen if u take one` long long int` variable . 
# Explain : 
###  Bcz, `int` data type has `32 bit` .That's why , If all variables are`int` data types then after performing ,value stores in `int` memory storage( `32 bit` memory storage.
### May arise a question , " Though, i store the value in `long long int` (64 bits ) ,so why it take 32 bit space when storing .

# `Example:

```cpp
	int a=1000000;
	long long int b = a*a;
```

## You may ask that ,why after declaring long long data types of variable `b` . 
## `Sol`

At first , multiplication start then it goes to store in variable . so , it really doesn't matter what long long of data type u declare , ``only matter on operands data types , which has maximum bit of storage.``



in this example , using `int(32 bit)` memory storage for `a` but after  `multiplication` value will be 10<sup>12</sup> .
value not store in `long long int`  `b`
Because  of , after operation value store in these  operand data type which  has maximum bit of  memory storage. So, `a*a ` here both of the operand are in `int` data types so after multiplication value store in `a` data type which is `32 bit` .

```cpp
  = a    *     a
 = max( (32 bit) * (32 bit))
 = 32 bit (value)
 
 
```
That's the reason why multiplication result not store in b though it has sufficient ` bit(64) of storage` in memory







