# Reflect
A 1D fungeoid inspired by [Backhand](https://github.com/GrayJoKing/Backhand/).

Unlike Backhand, the default step of the instruction pointer is 2; so the IP will execute a character, skip a character, execute another character, skip another character, ... etc.

This can be seen from the following example:
```
1 _ 2 + #
```

Before the terminate `#` instruction, only `1`, `_`, `2`, `+` are executed. (Numbers need a separator instead of pusing individual digits.) After halting, if nothing is outputted, the entire stack is implicitly outputted, so this will output `[3]`.

Another thing is that although the IP will bounce back if it goes across the right bound, execution will be terminated if the IP goes over the left bound. For example, the above program can be golfed to the following:
```
1+_2
```

Execution order:
```
1    Initial IP position. 
  _  End number: Push 1.
     IP is about to step out of bounds, so we move forward & reverse direction.
     (since IP is facing the right.)
   2 Push 2.
 +   Add. (1 + 2)

     When IP goes over the left bound, execution is terminated, and [3] is printed.
```
If you want to implement the behavior of reflection, you have 3 builtins:

* `|`:
