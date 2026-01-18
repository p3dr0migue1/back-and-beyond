+++
date = '2024-11-04T16:16:49Z'
draft = false
tags = ['Python']
title = 'Function Execution Duration'
+++

Here is a little example on how to print the time it took for a function to execute/complete.

```python
import time


def how_long(x):
	t0 = time.time()
	for n in range(x):
		j = n*x
	print("Total time: {} sec".format(str(time.time() - t0))


if __name__ == "__main__":
	how_long(100000)
```
