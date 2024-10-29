Consume the value by replacing it with the default value and returning the previous value

```rust
use consumable::*;

let mut x : i32 = 42;
assert_eq!(x.consume(), 42);
assert_eq!(x, i32::default());
```

```rust
pub trait Consumable
{
    fn consume(&mut self) -> Self;
}

impl<T : Default> Consumable for T 
{
    fn consume(&mut self) -> Self { std::mem::take(self) }
}
```