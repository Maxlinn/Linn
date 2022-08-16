# Linn Programming Language

For a long time i am seeking for a language that suits all occasions. After thousands of hours coding and working on difference languages, it is high time to combine their advantages all together to build a new overwhelming one.

## Philosophy

- Both interpretable and compilable, depends on toolchains selected.
- Type is important. (to Lua)
- Indents are bad. (to Python)
- Everything must be made as simple as possible. But not simpler. (to Go)
- Convention over configuration. (to Java).
- Unified is better than seperated. (to C++, which defines variables in prefix, defines functions in infix, and calls member function in postfix).
- Pain is inevitable, but suffering should be optional. (to Rust)
- Macros, pattern matching, gammar sugars, standard package management and more modern language features are welcomed. (agree with Rust)

## Demo

This code (not a runnable program) demostrates basic ideas of Linn. You can discover hints from other languages like rust, go, c++, java

```linn
import (
    "io" all,
    "ds" all,  # common data structures like dict, list, set
    "github.com/cool/package" as utils,  # import remote package or module
)

# by default, all functions and classes are exported, add _ in the front to hide
class Man extends(Human){
    _dick_length: float @dump:omit_empty;
    fn __init__() = default;
    fn __wank();  # don't export
}

s: char.[] = "114514";  # declare an array of chars
amount: int | float | complex;  # compound type
result: bool?;  # optional
type fp = fn(int, int) -> int;  # type definition
d = dict!`a : b, c : d;`

# simple functions
@throws(ZeroDivideException)
fn divide(a :float, b: float) -> float{
    return a / b;
}

# named return value, can be later called, like main().ret_code!
# can be used when return tuple
# attr is like python argparse.namespace
@throws(null)
fn divmod(a :int.& `first operator` @in, 
          b :int.& `second operator` @in) 
          -> (quotient: int, remainder: int){
    quotient :int = a / b;
    remainder :int = a % b;
    return (quotient, remainder);
}

# literal, implement class.__`__
timeout = time_span!`10s`

fn __main__(
    args: int `number of arguments`,
    argv: char.&.& `arrays of arguments`
) -> ret_code: int `code to OS` {

    for(p: char. &= s; p.*; p += 1){
        # by default pass by value
        # .& means get pointer
        # .$ means reference (lvalue)
        # .* means deference
        # .(type) means explicit type cast

        char ch = p.*;
        # char and strings are distinguished
        io.print(ch.(int), end="\r\n"); }

    sorted!(s, s + s.len!, fn![args, argv.$](int.$ a, int.$ b){
        return a < b;});

    if!(result, true=fn(){io.print("success")}, false=fn(){io.print("failed")});

    return 0;
}
```
