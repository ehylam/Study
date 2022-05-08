? = needs further studying.

### step(edge, test);
Returns `0.0` when test is less than edge, otherwise it will return `1.0`.

### mod(any x, any y);
Returns the value of `x` modulo (remainder) `y` which is done by `x - y * floor(x / y)`.

### ? floor(any x); 
Returns the nearest integer less than or equal to `x`.

### ? frac(any x);
Returns the fractional part of x which is done by `x - floor(x)`.


### smoothstep(edge0, edge1, test)
Anything below  `edge0` will be a `0`, anything above `edge1`  will be a `1`, anything in-between will be interpolated values (consistent incremental values?).
![[Pasted image 20220508144034.png]]
- Screenshot from "An Object Is A" Youtube channel.