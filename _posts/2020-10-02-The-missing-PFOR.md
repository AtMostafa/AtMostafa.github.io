---
layout: post
title: "The missing _parfor_, or pythonic multiprocessing"
author: Mostafa
tags: Matlab Python process multiprocess parallel
---

When I am analysing big amounts of data, often there is a _for_ loop that does some preprocessing and maybe saves some intermediate results, and as far as this post is concerned, it takes a __looooong__ time to complete.
For instance, in my PhD, I used to preprocess the data generated everyday for each animal at the end of the day.
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
The function 'factorial' just represents any time-consuming CPU-dependent computation that is independent of the loop iteration.
I used `time.perf_counter()` to measure how long my laptop takes to run the loop.
For `bigN=15`, it took ~170 seconds.
Importantly, python used only one process to calculate the entire code sequentially, so at any time, system resources looked like the image below.

!(Image showing only one CPU core engaged)[/images/posts/sequential_factorial_(dt=169.888s).png]

