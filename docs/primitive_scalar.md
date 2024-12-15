# Tipe Data -> Primitive Scalar

### Signed Integers
Signed Integers adalah nilai numerik/integer yang bisa bernilai negatif dan positif. Tipe data ini ditandai dengan `i`, contohnya `i8` dimana berarti nilai yang bisa ditampung adalah dari `-(2⁷)` sampai `2⁷-1`.
```rust
let var = 12;
let var2:i8 = 120;
let var3 = 12_i8;

prinln!("{var} {var2} {var3}")

let i8max = i8::MAX; //mengambil nilai max dari tipe i8
let i8min = i8::MIN; //mengambil nilai min dari tipe i8

prinln!("{i8max} {i8min}");
```

### Unsigned Integers
Unsigned Integer adalah nilai numerik/integer yang range nilainya dimulai dari `0` dan bukan negatif. Tipe ini ditandai dengan `u`, misal `u8` maka nilai yang bisa ditampung adalah `0` sampai `2⁸`.
```rust
let var = 12_u8;
let var2:u32 = 128;

prinln!("{var} {var2}");

let u8max = u8::MAX; //mengambil nilai max dari tipe u8
let u8min = u8::MIN; //mengambil nilai min dari tipe u8

prinln!("{u8max} {u8min}");
```

### Floating Point
Floating point atau angka desimal, ditandai dengan `f`. Ada 2 tipe floating point di rust, yaitu `f32` dan `f64`. 
```rust
let fp1 = 3.14_f32;
let fp2: f64 = 3.14;
println!("{} | {:.5}", fp1, fp2);

let f32max = f32::MAX; //mengambil nilai max dari tipe f32
let f32min = f32::MIN; //mengambil nilai min dari tipe f32

prinln!("{f32max} {f32min}");
```
untuk mengatur jumlah angka dibelakang koma kita bisa menggunakan `:.n`

### Bool
Nilai boolean pada Rust hanya ada 2 nilai saja, `true` dan `false`.
```rust
let b1 = true;
let b2 = false;

println!("{b1} {b2}")
```

### Char
Tipe char menampung nilai unicode, contohnya `'m'`,`'-'`,`'2'`. Penulisannya menggunakan notasi `''`, diapit tanda petik satu.
```rust
let c1 = 'n';
let c2 = '-';
let c3 = '2';

println!("{} | {} | {}", c1, c2, c3);
```

### Pointer scalar
Deklarasi tipe data pointer cukup mudah, yaitu dengan menuliskan deklarasinya seperti biasa tapi ditambahkan karakter `&`.
```rust
let ptr1: &i32 = &24;
println!("{}", ptr1);
```

### Tipe data primitive compound
Selain beberapa tipe data yang sudah dibahas di atas, ada juga jenis tipe data primitif jenis lainnya, yaitu primitive compound yang di antaranya adalah Array dan Tuple. Lebih detailnya mengenai tipe tersebut dibahas pada chapter terpisah.