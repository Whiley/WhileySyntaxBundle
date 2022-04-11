# WhileySyntaxBundle

This provides syntax highlighting for programs written in the
[Whiley](http://whiley.org).  An example Whiley program is the
following:

```whiley
type nat is (int x) where x >= 0

function indexOf(int[] items, int item) -> (int r)
// If valid index returned, element matches item
ensures r >= 0 ==> items[r] == item
// If invalid index return, no element matches item
ensures r <  0 ==> all { i in 0..|items| | items[i] != item }
// Return value is between -1 and size of items
ensures r >= -1 && r < |items|:
    //
    nat i = 0
    while i < |items|
        where all { k in 0 .. i | items[k] != item }:
        //    
        if items[i] == item:
            return i
        i = i + 1
    //
    return -1
```