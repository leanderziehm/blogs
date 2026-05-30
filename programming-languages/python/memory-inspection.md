# Memory Inspection

## Profiling:

```
python -m cProfile foo.py
```



### Memory Observation

Garbage Collector:

```
import gc
gc.get_objects()
```

```
import tracemalloc

tracemalloc.start()

a = [str(i) for i in range(10000)]

snapshot = tracemalloc.take_snapshot()
top_stats = snapshot.statistics('lineno')

for stat in top_stats[:10]:
    print(stat)
```

### Deep object memory analysis

#### `pympler`

This is one of the best practical libraries.

Install:

```
pip install pympler
```

Use:

```
from pympler import asizeofasizeof.asizeof(obj)
```

It gives **deep size including referenced objects**.

Also useful:

```
from pympler import muppy, summaryall_objects = muppy.get_objects()sum1 = summary.summarize(all_objects)summary.print_(sum1)
```

This shows memory grouped by object type (very useful for class behavior).

***

#### `objgraph` (understanding object relationships)

This is the “Cheat Engine feeling” but for Python object graphs.

Install:

```
pip install objgraph
```

Examples:

```
import objgraphobjgraph.show_most_common_types()objgraph.show_backrefs([some_object], filename='graph.png')
```

This shows **who is holding references to what**.

***

### Memory allocation at interpreter level

Python doesn’t give raw memory addresses in a useful way, but you can inspect identity:

```
id(obj)
```

And sometimes:

```
import ctypesctypes.addressof(ctypes.py_object(obj))
```

⚠️ This is low-level and not very useful for learning memory behavior beyond curiosity.

***

### profiling tools

#### `memory_profiler`

Line-by-line memory usage.

```
pip install memory_profiler
```

Usage:

```
from memory_profiler import profile@profiledef my_func():    x = [i for i in range(100000)]    return x
```

Run:

```
python -m memory_profiler your_script.py
```

***

#### `guppy3` (Heapy)

Very powerful heap analysis:

```
pip install guppy3
```

```
from guppy import hpyh = hpy()print(h.heap())
```

This gives you a heap breakdown similar to memory inspectors in other languages.

***

### System-level profiling

If you want _real mastery_, you also step outside Python:

#### Linux tools:

* `valgrind` + `massif` (heap profiler)
* `/proc/<pid>/status`
* `pmap`
* `smem`

Example:

```
valgrind --tool=massif python script.py
```

Then visualize memory growth.
