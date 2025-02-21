Recursion comes from the word `recur` which means to **occur again or repeatedly**. The term `recursion` is derived from the Latin word `recurrere`, which means "**to run back**" or "**to return**." 

In the context of **computer science and mathematics**, `recursion` refers to **the process of a function calling itself directly or indirectly to solve a problem by breaking it down into smaller,** more manageable sub-problems.

#Queston: recursion in programming is always linear is it true

#Ans:

No, recursion in programming is not always linear. The nature of recursion depends on how the recursive calls are made. Here are different types of recursion:

1. **Linear Recursion**: A function makes at most one recursive call each time it is invoked.
    
    - Example: Computing the factorial of a number.
    

```python
def factorial(n):     
if n == 0:         
return 1     
else:        
return n * factorial(n - 1)

```
    
2. **Tail Recursion**: A specific form of linear recursion where the recursive call is the last operation in the function.
    
    - Example: Tail-recursive factorial.
    
    python
    
    Copy code
    
    ```python
def tail_factorial(n, accumulator=1):     
if n == 0:         
return accumulator     
else:         
return tail_factorial(n - 1, n * accumulator)

```
    
3. **Tree Recursion**: A function makes multiple recursive calls each time it is invoked.
    
    - Example: Computing the nth Fibonacci number.

    
    ```python
def fibonacci(n):    
 if n <= 1:         
 return n     
 else:         
 return fibonacci(n - 1) + fibonacci(n - 2)
```
    
    
4. **Mutual Recursion**: Two or more functions are recursive through each other.
    
    - Example: Even and odd functions.
    
    
    ```python
    def is_even(n):     
    if n == 0:         
    return True     
    else:         
    return is_odd(n - 1)  
    
    def is_odd(n):     
    if n == 0:         
    return False     
    else:         
    return is_even(n - 1)
```
    
5. **Nested Recursion**: A recursive function passes the result of a recursive call as the parameter of another recursive call.
    
    - Example: Ackermann function.
    
    python
    
    Copy code
    
    ```python
    def ackermann(m, n):     
    if m == 0:         
    return n + 1     
    
    elif m > 0 and n == 0:   
          
    return ackermann(m - 1, 1) 
        
    else:         
    return ackermann(m - 1, ackermann(m, n - 1))
    
```
    

Each type of recursion has different characteristics and use cases, and they are not all linear.