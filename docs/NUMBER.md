# Number
Generate a random number of any kind. Integer by default.

For decimal/floating-point numbers, use `float()`.
For numbers not in base-10, you can use `hex()`, `octal()` and `binary()`.

For numeric strings of a given length, use `string().numeric()`.

## between
Sets the lower and upper bound of the returned value. The bounds are inclusive.

### Parameters
| Name | Type   | Descrption                        |
| ---- | ------ | --------------------------------- |
| min  | number | Lower bound for generated number. |
| max  | number | Upper bound for generated number. |

**Throws:** When `min` is greater than `max`. When there are no suitable numbers between `min` and `max`.

```typescript
function between(min: number, max: number)
```

### Examples
```typescript
number().between(1, 5).exec(); // 1
number().between(1, 3).exec(); // 2
number().between(7, 10).exec(); // 10
number().float().between(0.0, 8.0).exec(); // 5.3
number().float().between(1n, 100n).exec(); // 5.3
number().binary().between(5, 10).exec(); // '111'
number().binary().between(-3, 0).exec(); // '-11'
number().hex().between(1, 15).exec(); // 'a'
```

## bigInt
Sets the returned value to be a [BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Data_structures#bigint_type).

**Default Range:** `0n - min + 999999999999999n`

```typescript
function bigInt()
```

### Examples
```typescript
number().bigInt().exec(); // 30_000_000_000n
```

## binary
Sets the returned value to be a string representation of a binary number.

**Default Range:** `0 - Number.MAX_SAFE_INTEGER`

### Examples
```typescript
number().binary().exec(); // '110101'
```

### See Also
- `string().binary()`: For generating a binary string with a given length.

## even
Sets the returned value to be an even number.

**Throws:** When there are no suitable numbers between `min` and `max`.

### Examples
```typescript
number().even().exec(); // 2
number().binary().even().exec(); // '100'
number().bigInt().even().exec(); // 70_000_000_000n
```

## float
Sets the returned value to be a floating-point number. To limit the number of decimal places, use `multipleOf` or `fractionDigits`.

**Default Range:** `0.0 - 1.0`

### Functions
#### digits
The maximum number of digits to appear after the decimal point, for example 2 will round to 2 decimal points. Cannot be used with `multipleOf`.

**Throws:** When both `digits` and `multipleOf` are passed. When `digits` is negative. When there are no suitable numbers between `min` and `max`.

```typescript
function digits(amount: number)
```

### Examples
```typescript
number().float().exec(); // 0.31415972
number().float().digits(2).exec(); // 0.12
number().float().multipleOf(0.01).exec(); // 0.91 – same as above
number().float().digits(5).exec(); // 0.2014
```

## hex
Sets the returned value to be a string representation of a lowercase hexadecimal number.

**Default Range:** `0 - Number.MAX_SAFE_INTEGER`

### Examples
```typescript
number().hex().exec(); // 'af17'
```

### See Also
- `string().hex()`: For generating a hexadecimal string with a given length.

## max
Sets the upper bound of the returned value. The bound is inclusive.

**Throws:** When `min` is greater than `max`. When there are no suitable numbers between `min` and `max`.

```typescript
function max(max: number)
```

### Examples
```typescript
number().max(5).exec(); // 4
```

## min
Sets the lower bound of the returned value. The bound is inclusive.

**Throws:** When `min` is greater than `max`. When there are no suitable numbers between `min` and `max`.

```typescript
function min(min: number)
```

### Examples
```typescript
number().min(5).exec(); // 8
```

## multipleOf
Sets the generated number to be a multiple of the given number.

**Throws:** When both `digits` and `multipleOf` are passed. When `multipleOf` is negative. When there are no suitable numbers between `min` and `max`.

```typescript
function multipleOf(num: number);
```

### Examples
```typescript
number().float().multipleOf(0.001).exec(); // 0.005
number().multipleOf(8).exec(); // 32
number().binary().multipleOf(3).exec(); // 1001
```

## negative
Sets the generated number to be negative.

**Throws:** When there are no suitable numbers between `min` and `max`.

### Examples
```typescript
number().negative().exec(); // -3
number().float().negative().exec(); // -0.3034
number().binary().negative().exec(); // -101101
```

## octal
Sets the returned value to be a string representation of an octal number.

**Default Range:** `0 - Number.MAX_SAFE_INTEGER`

### Examples
```typescript
number().octal().exec(); // '377'
```

### See Also
- `string().octal()`: For generating a octal string with a given length.

## odd
Sets the returned value to be an odd number.

**Throws:** When there are no suitable numbers between `min` and `max`.

### Examples
```typescript
number().odd().exec(); // 1
number().binary().odd().exec(); // '101'
number().bigInt().odd().exec(); // 70_000_000_001n
```

## positive
Sets the generated number to be positive.

**Throws:** When there are no suitable numbers between `min` and `max`.

### Examples
```typescript
number().positive().exec(); // 3
number().float().positive().exec(); // 0.3034
number().binary().positive().exec(); // 101101
