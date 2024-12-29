# Tuple
Tuple merupakan variabel berisi berbagai banyak data dengan berbagai tipe data

Tuple dibuat dengan notasi diapit oleh `(` dan `)`. contohnya
```rust
let tuple_1 = (1, "halo", [1.2,3.4], true);
println!("{:?}", tuple_1);
```
Variabel `tuple_1` diatas berisi elemen dengan variasi tipe data yang berbeda seperti `i32`, `&str`, `array` dan `bool`.

Untuk mengambil atau menampilkan nilai dari elemen, gunakan notasi `.N` yang mana `N` adalah index elemen. Contoh
```rust
println!("{:?}", tuple_1.0);
println!("{:?}", tuple_1.1);
println!("{:?}", tuple_1.2[0]);
println!("{:?}", tuple_1.3);
```
### Mutable tuple
Cara untuk membuat mutable tuple dengan menambahkan `mut` pada saat deklarasi. Contoh
```rust
let mut mut_tuple: (&str, i32, [&str; 2], bool) = ("satu", 2, ["tiga", "empat"], true);
mut_tuple.3 = false;
mut_tuple.0 = "dua";

```

### Notasi deklarasi tuple

1. Type Inference
   
   adalah tipe dimana compiler secara otomatis menentukan tipe dari setiap elemen di tuple
   ```rust
   let tuple_a = ("senin", 2, [2,34], true);
   ```
2. Type Manifest typing

    adalah tipe dimana kita menentukan tipe dari elemen didalam tuple, biasanya diikuti predefined value untuk memberi nilai awal jika sifatnya mutable
    ```rust
    let mut tuple_b: (&str, i32, [i32; 2], bool) = ("default", 0, [0; 2], false);
    ```

### Packing tuple
Packing tuple adalah cara pembuatan tuple dimana elemen nya diambil dari variable lain
```rust
let name = "name";
let age = 23;

let tuple_info = (name, age);
```

### Unpacking tuple
Adalah kebalikan dari packing tuple, dimana kita membuat variabel dari tuple
```rust
let (name, age) = tuple_info;
```

### Tuple kosong `()`
Kita bisa mendefinisikan tuple tanpa isi
```rust
let mut tuple_kosong = ()
```