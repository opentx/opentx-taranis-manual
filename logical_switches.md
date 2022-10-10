# Logical Switches
Logical switches are essentially "virtual" switches which can change state depending on some input condition(s). These logical switches can be used in place of physical switches wherever applicable, and enable implementation of more complex programming functions. There are two main types of functions, comparison and (mathematical) logic, and a few with more specialized uses.

## Parameters
Each logical switch has several settings which define its behavior:

* `Function` selects the condition it evaluates using parameters `V1` and `V2` as inputs.
* The `AND Switch` - if defined - is AND-ed with the logical switch function, essentially acting as an "enable/disable" switch for the logical switch.
* A nonzero `Duration` sets how long the logical switch remains on, even if the condition is still true.
* Setting `Delay` means the logical switch will wait that long after the condition is true before turning on.

## Functions
### Comparisons
Check if value `V1` is less than (`<`), greater than (`>`), equal to (`=`), or approximately equal to (`~`) `V2`. Note that `X ≤ Y` is the inverse of `X > Y` - in other words, instead of checking if X is *less than or equal to* Y, check if it's *not greater than* Y.

| Function | V1 | V2 | Note |
| --- | --- | --- | --- |
| `a` vs `x` | Variable | Constant | Compares `V1` variable to fixed value `V2`. |
| `a` vs `b` | Variable | Variable | Compares variables `V1` and `V2`. |
| `\|a\|` vs `x` or `b` | Variable | Either | Compares the absolute value of `V1` - "is `V1` more/less than `V2` away from 0?" |
| `d ≥ x` | Delta (variable) | Constant | "Did `V1` *increase* by `V2` or more?" |
| `\|d\| ≥ x` | Delta (variable) | Constant | "Did `V1` *change* by `V2` or more?" |

### Logic operations
Compare the states of two switches. In brief: `AND` means "both", `OR` means "at least one", and `XOR` means "only one". The table below shows the possible input states and the resulting output states for each function.
| V1 | V2 | AND | OR | XOR |
| --- | --- | --- | --- | --- |
| OFF | OFF | OFF | OFF | OFF |
| **ON** | OFF | OFF | **ON** | **ON** |
| OFF | **ON** | OFF | **ON** | **ON** |
| **ON** | **ON** | **ON** | **ON** | OFF |

### Other
#### Edge
Detect a "pulse" of switch `V1`. `V2` contains two values which describe the pulse length "window" that will trigger the function - in other words, if switch `V1` is on longer than the first `V2` time, but shorter than the second (if defined), the logical switch turns on for the `Duration` set (if 0, the switch turns on and immediately off).
#### Timer
Turn the logical switch on for `V1` seconds, then off for `V2` seconds, then repeat. If set, the `AND` switch will start and stop the timer.
#### Sticky
Turn **on** when `V1` *becomes* true, and turn **off** when `V2` *becomes* true. Note that if e.g. `V2` is already true when the sticky switch turns on, you will need to turn `V2` off, then *back on* before the "sticky" switch turns off. Also, remember that the `AND` switch *does not* stop the conditions being checked - it only disables the output; switching the `AND` switch does not reset the conditions.
