# Array

### Pengalaman array
Array (atau *fixed size array*) adalah kumpulan data dengan tipe sejenis, disimpan dalam 1 variabel. Array memiliki kapasitas yang nilainya ditentukan saat deklarasi/alokasi. Jumlah data dalam array pasti tidak boleh lebih dari kapasitas yang sudah ditentukan di awal. Data dalam array biasa disebut dengan *element* atau item.

> **Aturan Array di Rust !!!**
> 1. Tipe element harus Sejenis
> 2. Jumlah element tidak boleh lebih dari yang ditentukan

Contoh Deklarasi array
```rust
let mut numbers = [24, 12, 32, 7];
println!("array {:?}", numbers);

let data0 = numbers[0];
println!("elemen array ke 0 {data0}");

let data1 = numbers[1];
println!("elemen array ke 1 {data1}");

numbers[1] = 16;
numbers[3] = 8;
println!("array {numbers:?}");
```

### Deklarasi Array secara *inference*
Secara *inference* artinya secara cerdas compiler akan menentukan tipe dan ukuran dari array tersebut
```rust
let mut array1 = [1,2,3,4]; 
// Secara cerdas compiler mendeteksi tipe integer dengan ukuran 4
// [i32; 4]

let boolean = [true, false];
// [bool; 2]

let floating = [2.33, 3.14, 2.00001];
// [f32; 3]
```

> Untuk megakses value dalam array kita bisa menggunakan index
> `nama_array[index]`
```rust
let a = ["senin", "selasa", "rabu"];
let b = a[2];
```
Untuk megubah nilai pada array, pastikan bahwa array tersebut adalah array `mutable`

`let mut array1 = [1,2,3,4]`
maka untuk mengubah nilainya kita bisa lakukan :
`array1[1] = 10`

> Untuk menampilkan berbagai tipe variabel ke bentuk string kita bisa menggunakan formatted print `{:?}` atau `{nama_variabel:?}`
```rust
let array1: [&str; 2] = ["senin", "selasa"];
println!("output : {array1:?}");
// output : ["senin", "selasa"]
```

### Macam macam deklarasi array
1. *Type Inference*
    Tipe dimana secara cerdas compile menentukan tipe dan size array
    ```rust
    let array = [1,2,3,4];
    ```
2. *manifest typing* dengan *predefined value*
    Tipe dimana kita menentukan tipe data dan size dari array
    ```rust
    let array: [i8; 3] = [1, 2, 3];
    ```
3. Dengan Notasi penulisan `[T; N]`
    Penggunaan notasi `[T; N]` akan memiliki 2 pendekatan berbeda tergantung dimana notasi diletakkan. Contoh
    ```rust
    let mut array: [i8; 5] = [1,2,3,4,5];
    // notasi pertama [i8; 5] di letakkan setelah nama variabel 
    // maka notasi tersebut akan digunakan sebagai definisi tipe dan size array

    let mut array2 = [3; 5];
    // notasi kedua [3; 5] di letakkan sebagai 'predefined'
    // artinya semua element array bernilai 3 dengan size array adalah 5
    ```

### Melihat size array menggunakan method `len`
```rust
let num: [&str; 4] = ["val"; 4];
let size_num = num.len();
println!("array num memiliki {size_num} element");
```

### Perulangan array menggunakan `for in`
```rust
let arr:[&str; 4] = ["senin", "selala", "rabu", "kamis"];

// contoh1
for hari in arr {
    println!("{hari}");
}

// contoh2
for i in 0..arr.len(){
    println!("{arr[i]}")
}
```

### Perulangan array dengan `while` dan `loop`
```rust
let arr = [1,2,3,4];
let mut i = 0;
while i < arr.len() {
    println!("{}",arr[i]);
    i += 1;
}

let mut j = 0;

'loop1: loop {
    if j == arr.len() {
        break 'loop1;
    }
    println!("{}",arr[j]);
    j += 1;
}
```
> Nb. Penulisan format print `"{nama_variabel[index]}"` akan menimbulkan error

### Perulangan menggunakan `for in` dan `tuple`
```rust
let arr = ["ayam", "gurame", "capung"];
while (index, name) in arr.iter().enumerate() {
    println!("Index {} adalah {}", index, name)
}
```
Pada contoh diatas kita melihat terdapat 2 kali perubahan tipe yang dilakukan yaitu pertama diubah ke tipe `Iterator` lalu ke `Enumerate`, return dari tipe `Enumerate` ini adalah tuple yang berisi index dan valuenya

### Append element ke array
Operasi menambahkan sebuah elemen ke array yang hasilnya melebihi kapasitas ... adalah tidak bisa. Karena array memiliki size fixed, tidak dinamis. Solusinya adalah menggunakan tipe data Vector. Nantinya array perlu dikonversi ke bentu Vector terlebih dahulu kemudian di-append, lebih jelasnya kita bahas pada chapter Vector.

### Nested array
Array juga bisa menyimpan array atau disebut nested array misalkan `[[1,2,3],[4,5,6]]` atau contoh lainnya seperti matrix.
```rust
let arr = [[1,2,3], [4,5,6]];
for (index, baris) in arr.iter().enumerate() {
    println!("baris {}", index);
    for val in baris {
        println!("{}", val);
    }
}
```