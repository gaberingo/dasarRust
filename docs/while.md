# While loop

### Keyword `while`
```rust
while kondisi {

}
```

```rust
let mut i = 0;

while i < 100 {
    println!("{i}");
    i += 1;
}
```

### Nested `while`
```rust
let mut i = 0;
let max = 5;

while i < max {
    let mut j = 0;
    let max_inner = i;

    while j < max_inner {
        print!("* ");
        j += 1;
    }
    println!();
    i += 1;
}
```

### Menambahkan delay dalam perulangan 
```rust
use std::thread::sleep;
use std::time::Duration;

fn main(){
    let mut i = 0;
    let max = 5;

    while i < max {
        println!("nilai {i}");
        i += 1;

        sleep(Duration::from_secs(1));
    }
}
```
> Keyword `use` memiliki banyak kegunaan. Pada contoh ini `use` difungsikan untuk import module, yang di bahasa Rust dikenal dengan istilah import paths.
