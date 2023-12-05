# FLog

`flog` is a tool that helps formatting nested and structured logs.

## Example

```python
import flog

def fact(n):
    if n == 1:
        flog.log("Reached base case")
        return 1
    flog.open(f"Computing fact({n})")
    flog.log(f"Recursive step: {n} * fact({n-1})")
    res = n * fact(n-1)
    flog.close(f"fact({n})={res}")
    return res

flog.param["open.style"] = flog.style.BOLD + flog.style.YELLOW
flog.param["log.style"] = flog.style.UNDERLINE
flog.param["close.style"] = flog.style.GREEN

fact(4)
```
Will produce the following output:
```
┌─Computing fact(4)
│ Recursive step: 4 * fact(3)
│ ┌─Computing fact(3)
│ │ Recursive step: 3 * fact(2)
│ │ ┌─Computing fact(2)
│ │ │ Recursive step: 2 * fact(1)
│ │ │ Reached base case
│ │ └─fact(2)=2
│ └─fact(3)=6
└─fact(4)=24
```
Try it on your terminal!

## Others

[`ftimer`](https://github.com/fsossai/ftimer) is a project that uses FLog. Go take a look!
