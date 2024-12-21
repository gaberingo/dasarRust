# Perulangan `for` - `in`

### Keyword `for` `in`
Untuk penulisan *range* pada `for` loop rust adalah `n..m`
> `0..5` berarti range `0` sampai `5-1`
> `0..=5` berarti range `0` sampai `5` 
```rust
for i in 0..5 {
    println!({i});
    // output : 0 1 2 3 4
}
```

### Label Perulangan
Kalau sebelumnya kita menggunakan `label` pada `loop`, untuk perulangan `for` juga bisa menggunakan `label`
```rust
'label_for: for i in 0..=10 {
    if i > 5 && i % 2 == 0 {
        println!("Perulangan di hentikan");
        break 'label_for;
    }

    println!({i})
}
```

### Perulangan `for in` pada array
```rust
let array = ["senin","selasa","rabu","kamis","jumat"];
for hari in array {
    println!("{hari}");
}
```