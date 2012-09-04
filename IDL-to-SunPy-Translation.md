This page provides some quick notes on translating from IDL to Sunpy.

## Function Mappings
* **SSW/IDL** to **Python/SunPy**
* _anytim_ goes to sunpy.util.parse_time
* histogram reverse indices ?
* referencing and dereferencing a pointer ?
* file_search ?
* value_locate ?
* _total_ goes to array.sum()
* mtotal ?
* integration
* int_tabulated ?
* f_div ?
* uniq/get_uniq ?

You can find a larger list [here](https://www.cfa.harvard.edu/~jbattat/computer/python/science/idl-numpy.html).

## The IDL where command
The where command is a very useful function in IDL which returns an array of indices which meet a particular requirement. For example,
<code>
a = indgen(100)
index = where(a LT 30)
b = a[index]
</code>
The b array now contains only those elements in a less than 30. The equivalent in Python/Sunpy is
<code>
import numpy as np
a = np.arange(0,100)
b = a[a < 30]
</code>
This is possible because the relationship, a < 30, returns a list of indices which are labeled as True or False. This list can then be used to index any other array.

