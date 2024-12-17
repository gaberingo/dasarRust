# Seleksi Kondisi `if`,`else if`,`else`

### Keyword `if`

```rust
if operasiLogika {
    // blok kode
}
```

```rust
let var_num = 5;
if var_num < 10 {
    println!("var_num lebih kecil dari 10");
}

let bool1 = var_num > 2;
if bool1 {
    println!("nilai var_num lebih besar dari 2");
}
```

### Keyword `if`,`else if`,`else`

```rust
let a = 10;
if a < 5 {
    println!("lebih kecil dari 5");
} else if a > 5 {
    println!("lebih besar dari 5");
} else {
    println!("a adalah 5");
}
```

### Nested `if`

```rust
let number_c = 10;
if number_c > 6 {
    println!("selamat, anda lulus");

    if number_c == 10 {
        println!("dengan nilai sempurna");
    } else if number_c > 7 {
        println!("dengan nilai baik");
    } else {
        println!("dengan nilai cukup");
    }
} else {
    println!("anda tidak lulus");

    if number_c < 4 {
        println!("belajar lagi ya");
    } else {
        println!("jangan malas belajar!");
    }
}
```

### Returning from `if`
Returning `if` adalah kondisi unik dimana case pada sebuah kondisi ditampung sebagai *return value* atau nilai balik. Semisal untuk memberi nilai pada variabel yang sudah di deklarasikan tapi belum diberi nilai.
```rust
let number_d = 3;
let result_d: bool;

if number_d == 2 {
    result_d = true
} else {
    result_d = false
}

println!("result_d adalah {result_d}");
```
> Pada kode di atas, deklarasi variabel result_d dan pengisian nilainya adalah ditulis dalam statement terpisah. Cara ini diperbolehkan pada variable immutable (tanpa perlu membuatnya mutable) selama operasi assignment hanya dilakukan sekali saja setelah deklarasi.

atau bisa juga disederhanakan menjadi bentuk `let if`
```rust
let a = 3;
let b = if a > 10 {
    true
} else {
    false
};
```
dari contoh diatas, jika `a` lebih besar dari 10 maka `b` akan bernilai `true` dan bernilai `false` jika lebih kecil dari 10.

O iya, beberapa orang lebih memilih memanfaatkan indentasi untuk mempermudah memahami statement let if. Contohnya seperti ini:
```rust
let num = 12;
let bool1 = 
    if num > 12 {
        true
    } else {
        false
    };
println!("bool1 adalah {bool1}");
```

### Kombinasi Keyword `let` dan `if`, Dengan Tipe Data Eksplisit

```rust
let num: i32 = 123;
let word: $str = 
    if num > 200 {
        "lebih besar dari 200"
    } else if num == 123 {
        "nilainya sama dengan 123"
    } else {
        "nilainya dibawah 200 dan bukan 123"
    };
println!("{word}");
```
contoh lain
```rust
let max = 100.0;
let string_f = "nilai minimum kelulusan";
let result_f: f64 = if string_f == "nilai maksimum kelulusan" {
    max
} else {
    max * 3.0 / 4.0
};
println!("angka adalah {result_f}");
```