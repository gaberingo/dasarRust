# Loop, Break, Continue, Label
Ada keyword yang memiliki fungsi sama seperti `while` yaitu `loop`.

### Keyword `loop`
```rust
fn main(){
    let mut i = 0;

    loop {
        println!("nilai i: {}", i);
        i += 1;
    }
}
```

### Keyword `break`
`loop` menghasilkan perulangan tanpa henti, untuk menghentikannya kita perlu menggunakan `break`.
```rust
let mux i = 0;
let max = 5;

loop {
    println!("nilai i: {}", i);
    if i == max {
        break;
    }
    i += 1;
}

println!("Perulangan selesai");
```

### Nested `loop`
```rust
let mut i = 0;
let max = 5;

loop {
    let mut j = 0;
    let inner_max = 5;

    loop {
        println!("nilai j: {}", j);
        if j == inner_max {
            break;
        }

        j += 1;
    }

    if i == max {
        break;
    }

    i += 1;
}

println!("Perulangan Selesai");
```

### Keyword `continue`
`continue` digunakan untuk melanjutkan perulangan secara paksa dan melewatkan perintah dibawahnya. Misalkan kita akan membuat perulangan dimana jika nilai `i` adalah bernilai genap maka akan kita skip.
```rust
let mut i = 0;
let max = 5;
loop {
    if i == max {
        break;
    }
    if i % 2 == 0 {
        i += 1;
        continue;
    }
    println!("Nilai i akan bernilai ganjil, yaitu: {}", i);
    i += 1;
}
```

### Label perulangan
Perulangan menggunakan `loop` bisa ditandai dengan label. Tujuan dari pelabelan ini adalah agar kita bisa melakukan eksekusi `break` atau `continue` ke perulangan diluar di luar blok kode perulangan statement itu berada.
```rust
// loop biasa
loop {
    // statement
    break;
}

// loop dengan label
'nama_label: loop {
    // statement
    break 'nama_label;
}
```
Pemberian label pada `loop` diawali dengan tanda petik `'` didepan nama label.

Berikut adalah contoh dimana kita kan melakukan `break` pada sebuah perulangan dengan label dari nested `loop`

```rust
let mut i = 0;

// Main loop with label label1
'label1: loop {
    i += 1;
    let mut j = 9;
    loop {    
        println!("nilai j : {}", j);
        if j % i == 0 {
            break 'label1;
        }
        j -= 1;
    }
    println!();
}
```

### Returning from `loop`
*Returning from* `loop` adalah sebuah teknik pada rust untuk me-return nilai menggunakan `loop` dan `break`. Nah jadi di rust itu kita bisa return nilai menggunakan `loop`, semisal ada sebuah nilai yang dimana untuk mendapatkan nilai final kita harus melakukan fungsi yang berulang, lalu bagaimana me-return nilai akhirnya? untuk me-return nilai akhirnya kita menggunakan `break`. Contoh:
```rust
let nilai_akhir: i32;
let mut i = 1;

nilai_akhir = loop {
    if i < 20 && i % 5 == 0 {
        break i * 2;
    }
    i += 1;
}

println!("Nilai akhir adalah : {}", nilai_akhir);
```