---
layout: post
title: "The missing parfor, or pythonic multiprocessing"
author: Mostafa
tags: Matlab Python process multiprocess parallel
---

When I am analysing big amounts of data, often there is a _for_ loop that does some preprocessing and maybe saves some intermediate results, and as far as this post is concerned, it takes a __looooong__ time to complete.
For instance, in my PhD, I preprocessed the data generated everyday for each animal.
It took almost half an hour per animal, and at times, we had ~30 active animals.
Cases such as this present an easy and ideal situation for multiprocessing.
In the previous example, animals are independent and they don't need to share any resources, so in principle, the preprocessing could be simply run in parallel on different CPU cores.
In Matlab, I used to just replace the _for_ keyword with _parfor_ (and sometimes a few other tweaks) and it just worked.
In Python however, it is a bit more delicate.

Following I will show how to deal with the simple case described above, that is to run iterations of a suitable for-loop in parallel.
Consider the following for-loop:
```
for i in range (bigN):
    factorial()
```
where 'factorial' returns the `math.factorial(1e6)` or _1000000!_.
The function 'factorial' just represents any time-consuming CPU-dependent computation that does not care about the exact iteration of the loop.
I used `time.perf_counter()` to measure how long my laptop takes to run the loop.
For `bigN=15`, it took ~170 seconds.
Importantly, python used only one process to calculate the entire code sequentially, so at any time, system resources looked like the image below.

![Image showing only one CPU core engaged](/images/posts/sequential_factorial_(dt=169.888s).png)

Obviously, this is rather wasteful, because modern computers have several processing cores.
Now, let's use the pythonic way of _parfor_.
```
from multiprocessing import Pool

def parallel_main():

    with Pool() as pool:
        out=pool.map( factorial, range(bigN) )
    
    return out
```
From the `Pool` class, I used the `map` method to feed elements of the `range(bigN)` to the same `factorial` function as before.
Check out the [documentation](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool) for other methods available in the `Pool` class which might fit your use-case better.
One nice option is the number of processes being used which could be specified when calling the `Pool()` class.
```
...
with Pool( processes=os.cpu_count() ) as pool:
...
```
The `processes` argument determines the number of processes and defaults to `os.cpu_count()` which is the maximum number of CPU cores available.
Now, running this code, with all the `os.cpu_count()` processes looked like this:

![Image showing every CPU core engaged](/images/posts/parallel_factorial_(dt=55.862s).png)

Every single available CPU core is fully engaged.
It took ~56 seconds (compared to 170s) to calculate the factorial of one million fifteen times!

Note that increasing the number of processes in the pool will not lower the execution time proportionally.
Choose wisely!
Starting processes itself takes time.
So, initialising too many processes to run a rather simple task will __increase__ the execution time and defeat the purpose.

Here, I just covered a simple and useful case.
This was not supposed to be a comprehensive tutorial in any way, there are many resources available online for multiprocessing and threading.