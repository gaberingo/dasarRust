# Operator

### Operator Aritmatika
```rust
let (num1, num2) = (12, 2);

let penjumlahan = num1 + num2; // Penjumlahan
let pengurangan = num1 - num2; // Pengurangan
let perkalian = num1 * num2;   // Perkalian
let pembagian = num1 / num2;   // Pembagian
let modulus = num1 % num2;     // Sisa Bagi
```

### Operator Perbandingan
```rust
let (num1, num2) = (12, 4);

let adalah_sama = num1 == num2;
let adalah_tidak_sama = num1 != num2;
let lebih_besar = num1 > num2;
let lebih_kecil = num1 < num2;
let lebih_besar_sama_dengan = num1 >= num2;
let lebih_kecil_sama_dengan = num1 <= num2;
```

### Operator Negasi
```rust
let (val_left, val_right) = (12, -12);

// val_left di negasikan menjadi negatif lalu dilakukan perbandingan
let res_one = -val_left == val_right; 

// dilakukan perbandingan antara val_left dan val_right lalu hasilnya di negasikan sebaliknya dari hasil perbandingan
let res_two = !(val_left == val_right);
```

### Operator Logika / `bool`
```rust
let (bool1, bool2) = (false, true);

// Operator AND &&
let res_and = bool1 && bool2;

// Operator OR ||
let res_or = bool1 || bool2;

// Operator NOT !
let not_bool1 = !bool1
```

### Operator Bitwise
Operator bitwise biasanya digunakan untuk operasi binary

|   simbol  |   Kegunaan    |
|-----------|---------------|
|   `&`     |   `AND`       |
|   `\|`     |   `OR`       |
|   `^`     |   `XOR`       |
|   `!`     |   `NOT`       |
|   `<<`     |   `left shift`       |
|   `>>`     |   `right shift`       |

Contoh seperti operasi bitwise `AND` berikut ini

```
01000111
11001111
---------- &
01000111
```