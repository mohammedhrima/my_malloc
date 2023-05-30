## my_malloc and my_free

- Memory leaks and double free suck, I tried to built "my_malloc" to solve those problems
- my_malloc: function allocate a spaces in the heap (with malloc) and frees them when main exit
- my_free / my_free_all:\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;- protected from double free\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;- my_free frees specific address\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;- my_free_all free all allocated spaces by my_malloc\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;- for programs that keep running and allocating space continuously\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;- or in case your program could exit somewhere outside the main,\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;put my_free_all() before exit()

## Usage :

```c
#include "Leaks-and-double-free-cure/header.h"

void   *ptr0 = my_malloc(1000);
int    *ptr1 = my_malloc(2000);
char  **ptr2 = my_malloc(5000);
char ***ptr3 = my_malloc(300);
my_free(ptr0);
my_frr_all();
```

## Running Tests

```bash
git clone https://github.com/mohammedhrima/Leaks-and-double-free-cure.git .
```
```bash
gcc leaks_curr.c leaks_curr_utils.c your_file.c #don't forget to include Leaks-and-double-free-cure/header.h
```

## Important : (what you need to know)

- void * , void**, void *** ..., are an addresses (for an allocate space in memory)
- Those addresses have the same size
```
        !!! size of pointer depends on computer architecture !!!
        In 32-bit computer machine sizeof(pointer) is 4 bytes
        In 64-bit computer machine sizeof(pointer) is 8 bytes
```

\
![001](https://user-images.githubusercontent.com/71414472/212447316-2f09d29c-c43c-4607-964e-178c93f69fc6.png) \
\
![002](https://user-images.githubusercontent.com/71414472/212447477-0bac06ba-71a3-4894-9f8c-652302f84ce7.png) \
\
![003](https://user-images.githubusercontent.com/71414472/212447320-93845755-9044-4ed9-a00b-77b69d27da65.png) \
\
![004](https://user-images.githubusercontent.com/71414472/212447327-d8aed60f-f55c-4ebe-b54e-ec53aefdb312.png)

