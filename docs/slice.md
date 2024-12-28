# Slice
Slice adalah representasi dari *block of memory* berbentuk pointer dengan size yang dinamis. Kenapa disebut *block of memory* ? karena slice bekerja seperti sebuah pointer yang menyimpan kumpulan list alamat sejenis.

Notasi penulisan tipe slice adalah `&[T]` dimana `T` adalah tipe data. Slice bisa dibuat dari data array atau tipe kolektif lainnya dengan menggunakan kombinasi operator `&` dan range `..`

Contoh
```rust
let a: [i32; 4] = [22,33,12,44];
let slice_a: &[i32] = &a[0..3];
println!("{:?}", slice_a);
```

**`&a[0..3]`** -> `slice_a` meminjam nilai dari `a` yaitu dari item ke-0 sampai item ke-2.

Maka nilai dari `slice_a` adalah `[22, 33, 12]`.

### Slice *range syntax*
Berikut adalah beberapa contoh penggunaan *range* `..` untuk slicing.
```rust
let array_var = ["a", "ab", "cc", "abc"];

let slice_a = &array_var[..]; // Meminjam seluruh range

let slice_b = &array_var[2..]; // Meminjam dari index ke-2 sampai terakhir

let slice_c = &array_var[0..2]; // Meminjam dari index ke-0 sampai ke-1

let slice_d = &array_var[0..=2]; // Meminjam dari index ke-0 sampai ke-2

```

### Mutability pada Slice
Slice ada 2 jenis, yaitu *mutable* dan *immutable*. 

*Mutable* artinya nilai yang di pinjam dapat diubah nilainya dan pemilik asli dari nilai tersebut juga akan berpengaruh sehingga mengubah nilai item si pemilik juga.

*Immutable* artinya nilai yang di pinjam hanya bisa di baca dan tidak dapat di ubah.

notasi penulisan untuk *slice mutable* adalah `&mut`. Dengan operator ini maka borrowing menghasilkan data *mutable reference*, data yang nilainya diperbolehkan diubah meskipun data pinjaman.

```rust
let mut arr = [1,2,3,4,5];
let slice_a = &mut arr[0..3];

// Sebelum nilai di ganti
println!("nilai arr {arr}"); // output : [1,2,3,4,5]
println!("nilai slice_a {:?}", slice_a); // output : [1,2,3]

// Setelah di ubah
slice_a[0] = 10;
println!("nilai arr {arr}"); // output : [10,2,3,4,5]
println!("nilai slice_a {:?}", slice_a); // output : [10,2,3]
```

### Perulangan `for in` slice
Kita bisa memanfaatkan slice atau variable peminjam untuk melakukan perulangan
```rust
let var_a = [2,3,4,5,5];
let slice_a = &var_a[..3];

for var in slice_a {
    println!("{}", var);
}
```

contoh diatas kita membuat variabel `slice_a` lalu menggunakannya di perulangan, atau kita juga bisa secara langsung menggunakan slice pada perulangan seperti contoh ini

```rust
for var in &var_a[..3]{
    println!("{}", var);
}
```

### Perulangan `for in` slice mutable
Notasi penulisan slice mutable adalah `&mut name_var[start..end]`

Pada contoh berikut, kita akan mencoba untuk menambahkan 1 ke setiap bilangan yang di pinjam
```rust
let mut arr_a = [1,2,3,4,5];
for num in &mut arr_a[..]{
    *num += 1;
}
println!("{:?}", arr_a);
// output : [2,3,4,5,6]
```

> Ingat notasi untuk mutable slice adalah `&mut nama_variabel`
>
> Contoh benar --> `let slice_a = &mut var_a[..];`
>
> Contoh salah --> `let mut slice_a = var_a[..];`