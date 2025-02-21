![[Pasted image 20240624140402.png]]

# Standard Input Stream(CIN):

- It’s an predefined object or an instance of an istream class.
- Istream is connected to the input devise i.e., keyboard to take input.
- Here stream extraction(>>) operator is used to extract sequence of bytes.

# Standard Output Stream(COUT):

- It’s an predefined object or an instance of an ostream class.
- ostream is connected to the output devise i.e., display screen.
- Here stream insertion(<<) operator is used to insert the data.


### cpp
```cpp

#include<bits/stdc++.h>

using namespace std;
int main()

{

  int a,b,c;
  cin>>a>>b>>c;

	cout<<a+b+c<<endl;
    return 0;

}

```

![[Pasted image 20240624141900.png]]


# FAST I/O

In competitive programming it is important to read input as fast as possible and operations has to be performed faster there performance matters.

**_We can make the fast one even faster. How…?_**

```markdown
```cpp
std:: ios::sync_with_stdio(sync:false);
std:: cin.tie(tiestr:NULL);
std:: cout.tie(tiestr:NULL);

```

> by adding these few lines into your code. explanation 👇

#  `std::ios::sync_with_stdio(false);`
**C++ iostream** standard streams with their corresponding standard **C streams** are Synchronized . By adding` std::ios::sync_with_stdio (false);` which is true **by default**.
 
It avoids synchronization. If you **disable the synchronization**, then **C++ streams** are allowed to have their **own independent buffers**.
Then , c++ program compiler don't need to wait for program pointer which starts before ,complete C programs `scanf( )` and` printf( )` these 2 function . now , it really no  need   to wait to accomplishment of `scanf( )` and` printf( )` . 

# C++ iostream standard streams with their corresponding standard C streams are Synchronized.**what does this means ?**
# C++ and C Streams

- **C++ Streams**: In C++, we use `std::cin` for input and `std::cout` for output.
- **C Streams**: In C (the older language), we use `stdin` for input and `stdout` for output.

# Synchronization

- **Synchronized Streams**: By default, C++ streams `cin`  and `cout` are "**synchronized**" with C streams (`stdin` and `stdout`). This means they work together to ensure that input and output operations happen in the correct order, even if you mix C and C++ code.

# Why Synchronization?

Imagine you have a program that uses both C++ and C functions for input and output. Without synchronization:

- If you write something with `printf` (a C function) and then read with `cin` (a C++ function), the order of operations might get messed up.
- Synchronization ensures that `cout` waits for `printf` to finish before it starts, and vice versa.

# Example

Here's a simple program showing synchronized streams:


```cpp
#include <iostream>
#include <cstdio> 

int main() 
{   
std::cout << "Hello from std::cout" << std::endl; 
printf("Hello from printf\n");     
return 0; 
}
```

``

Without synchronization, the output might look jumbled. With synchronization, it ensures "Hello from `cout` appears before "Hello from `printf`

## Disabling Synchronization

- ### Performance: 
				 **Synchronization** **slows** **down** the program because it adds overhead. Disabling it can make input/output operations faster, which is important in competitive programming.
    
- ### How to Disable: 
					You can disable synchronization with the line `ios::sync_with_stdio(false)`.
    

## Summary 
- **With Synchronization**: C++ streams and C streams work together to ensure the correct order of input and output.
- **Without Synchronization**: Disabling it makes `cin` and `cout` faster but can cause issues if you mix C and C++ I/O operations.

I hope this makes the concept clear!

# `  std::cin.tie(NULL);`

Simply it unties `cin` from `cout` which means output is `flushed`/displayed on the console only on `demand` or when the `buffer is full`.(`AVOIDS FLUSHING`)
## **what does this means:** "Simply it unties `cin` from `cout` which means output is flushed/displayed on the console only on demand or when the buffer is full.(AVOIDS FLUSHING)"
## Ans
The statement is describing a technique or mechanism where the output stream (`cout` in C++ terminology) is not automatically flushed to the console after each output operation. Here’s a breakdown of what each part means:

1. **Unties `cin` from `cout`**: In C++, the `cin` and `cout` streams are tied by default, which means that output to `cout` (standard output) can cause `cin` (standard input) to be flushed (cleared) automatically. Untying them means disabling this automatic flushing mechanism.
    
2. **Output is flushed/displayed on demand or when the buffer is full**: When `cout` is untied from `cin`, output written to `cout` is not immediately displayed on the console. Instead, it stays in a buffer (temporary storage). Output is only displayed (flushed) in two scenarios:
    
    - On demand: This typically happens when you explicitly request the buffer to be flushed, such as by using `flush()` or `endl`.
    - When the buffer is full: If the output buffer reaches its capacity, the contents of the buffer are automatically flushed to the console to free up space for new output.
3. **Avoids flushing**: By not automatically flushing the output after each write operation, this approach can improve performance in scenarios where frequent small outputs occur. Flushing involves an overhead cost, so delaying it until necessary (buffer is full or explicitly requested) can optimize performance.
    

In essence, "unties `cin` from `cout`" refers to disabling the automatic synchronization between input and output streams in C++, which affects how and when output is displayed on the console. This technique can be beneficial in situations where performance optimization is crucial and frequent flushing of output to the console is not necessary.

# Example:

first understand the buzzwords.

- Buffer -> simply buffer is a temporary placeholder, operations are performed faster.
- Flushing -> storing buffered data to permanent memory.

**Buffer flush or flushing the buffer ->buffer means storing temporarily+ flushing means saving permanently.**

**Ex:**
