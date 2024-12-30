# Vector
Vector adalah tipe variable yang mirip dengan array, dimana element dalam vector wajib memiliki tipe data yang sama. Perbedaannya dengan array adalah vector memiliki jumlah elemen yang bersifat dinamis sehingga bisa di tambah maupun di kurangi. 

Vector memiliki 3 atribut penting untuk diketahui:
- pointer ke data asli
- lebar atau size
- kapasitas (representasi dari seberapa banyak memori di-booking untuk data vector tersebut)

Vector bisa bertambah jumlah isinya selama size di bawah kapasitas yang sudah dialokasikan. Jika suatu ketika vector isinya bertambah lebih banyak dari jumlah alokasi maksimal kapasitas, maka vector akan dialokasikan ulang dengan kapasitas yang lebih besar.

### Tipe data `Vec<T>`
`Vec<T>` adalah tipe yang merepresentasikan vector, yang mana `T` adalah tipe data dari element. Contoh :
```rust
let mut vector_1: Vec<i32> = vec![1,2,3,4];
``` 

### Deklarasi vektor, size, dan capacity

Salah satu cara untuk membuat data vector adalah menggunakan macro `vec` dengan penambahan prefix `!` menjadi `vec!`. Contoh :
```rust
let mut vector_1 = vec![1,2,3,4,5];

println!("{:?}", vector);
println!("size : {}, capacity : {}", vector.len(), vector.capacity());
```
### Method `pop`
Method `pop` pada vector berfungsi untuk menghapus elemen terakhir pada vector.
```rust
vector_1.pop();

println!("{:?}", vector);
println!("size : {}, capacity : {}", vector.len(), vector.capacity());
```

### Method `remove` -> menghapus element ke `i`
Method `remove` digunakan untuk menghapus element pada vector pada index tertentu.
```rust
vector_1.remove(2);
// element dengan index 2 akan di hapus dari vector

println!("{:?}", vector);
println!("size : {}, capacity : {}", vector.len(), vector.capacity());
```

### Method `push`
Method `push` digunakan untuk menambahkan element ke dalam vector.
```rust
vector_1.push(1);
vector_1.push(19);
println!("{:?}", vector);
println!("size : {}, capacity : {}", vector.len(), vector.capacity());
```
### Relokasi  vector
Perubahan kapasitas atau realokasi vector terjadi ketika sebuah vector isinya bertambah lebih banyak dari jumlah alokasi maksimal kapasitas.

Lalu apa efeknya? secara high level bisa dibilang tidak ada, namun kalau dibahas lebih rinci, efeknya adalah di sisi alokasi space untuk menampung elemen. Proses realokasi menghasilkan vector yang baru dengan kapasitas lebih besar.

### Mengubah value sebuah element menggunakan notasi `[i]`
Kita dapat menghubah nilai element didalam vector menggunakan notasi `[i]` sama seperti array.

```rust
vector_1[0] = 20;
// element index ke-0 akan diubah menjadi 20

println!("{:?}", vector_1[0]);
```

### Method `is_empty` -> Mengecek apakah vector kosong
Method ini digunakan untuk mengecek apakah sebuah vector memiliki element atau tidak.
```rust
if vector_1.is_empty() {
    println!("Vector ini Kosong");
} else {
    println!("Vector ini memiliki element sebanyak {}", vector_1.len());
}
```

### Method `clear`
Method clear digunakan untuk mengosongkan vector.
```rust
vector_1.clear();
```

### Method `append`
Method append digunakan untuk concatenation atau penggabungan vector. **Ingat** vector yang di gabungkan adalah vector dengan tipe data element yang sama. Pada method ini, teradat proses penggabungan dan pengosongan. Misalkan `vec2` akan di append ke `vec1` maka semua element pada `vec2` akan di pindahkan ke `vec1` lalu `vec2` akan di kosongkan. 
```rust
let mut vec1: Vec<i32> = vec![1,2,3,4,5];
let mut vec2: Vec<i32> = vec![6,7,8,9,0];

vec1.append(&mut vec2);

println!("data: {:?}", vec1);
println!("length: {}, capacity: {}", vec1.len(),  vec1.capacity());

// vec2 akan menjadi vector kosong
println!("data: {:?}", vec2);
println!("length: {}, capacity: {}", vec2.len(),  vec2.capacity());
```

### Method `sort`
Method `sort` digunakan untuk mengurutkan elemen vector.
```rust
println!("data: {:?}", result_one);
result_one.sort();
println!("data: {:?}", result_one);
```

### Macam deklarasi vektor
Cara deklarasi vector selanjutnya adalah pembuatan vector dengan isi kosong. Deklarasi vector ini mewajibkan tipe data vector dituliskan secara eksplisit, dikarenakan tipe data tidak bisa diidentifikasi dari isinya (karena isinya kosong). Contoh:
```rust
let mut vector_7: Vec<&str> = vec![];
let mut vector_8: Vec<&str> = Vec::new();
```
Deklarasi vector kosong bisa dilakukan dengan macro `vec` yang ditulis tanpa isi, atau bisa menggunakan `Vec::new()`.


### Iterasi data vector
Keyword `for in` bisa digunakan untuk iterasi vector. Cara penerapannya seperti pada array atau slice.
```rust
let vec_eight = vec![1, 2, 3];
for e in vec_eight {
    print!("{e} ");
}

// 1 2 3
```

### Ownership tipe data vector
Salah satu atribut vector yang penting untuk diketahui adalah, pemilik data sebenarnya (atau owner). Agar lebih jelas, silakan coba terlebih dahulu kode berikut.
```rust
let vec_ten = vec![1, 2, 3];
for e in vec_ten {
    print!("{e} ");
}
for i in 0..vec_ten.len() {
    print!("{} ", vec_ten[i]);
}
```
Terlihat sekilas tidak ada kode yang bermasalah dari program di atas, tapi error pada bagian `vec_ten.len()`, aneh.

Di Rust, ownership atau kepemilikan data adalah hal yang sangat penting. Saking pentingnya, beberapa orang menyebut Rust sebagai bahasa yang value oriented.

Dalam kasus kode program vector di atas, ketika keyword `for in` digunakan untuk mengiterasi vector `vec_ten`, membuat pemilik data vektor berpindah ke variabel `e`. Hal ini efeknya adalah ketika kita berusaha mengakses variabel yang sama setelah perulangan selesai, maka yang muncul adalah error, karena value-nya sudah berpindah.

Solusi untuk antisipasi error ini adalah dengan cara meminjam value yang sebenarnya dari owner, untuk kemudian digunakan dalam perulangan. Caranya dengan menggunakan teknik borrowing menggunakan operator `reference` yaitu `&`. Data sebenarnya milik owner dipinjam untuk dipergunakan di perulangan.

Silakan ubah kode yang sebelumnya ...
```rust
for e in vec_ten {
    print!("{e} ");
}
```
... menjadi seperti ini, kemudian run, maka error akan hilang.
```rust
for e in &vec_ten {
    print!("{e} ");
}
```
Salah satu alternatif cara lainnya untuk antisipasi value berpindah tempat adalah dengan menggunakan method `iter` untuk mengkonversi vector menjadi iterator. Jadi yang di-iterasi bukan vector-nya, melainkan objek iterator yang dibuat dari vector tersebut.
```rust
for e in vec_ten.iter() {
    print!("{e} ");
}
```

### Vector slice
```rust
let vec_population = vec![2, 1, 3];
let vec_sample = &vec_population[0..1];
println!("{:?}", vec_sample); // [2]
```

### Tipe data VecDeque<T>
Tipe data `VecDeque<T>` adalah sama seperti `Vec<T>` plus mendukung operasi menambah dan mengurangi elemen dari dua sisi secara efisien.

Pada tipe data `Vec<T>`, ada method pop yang fungsinya menghapus data elemen terakhir dan method push untuk menambah elemen baru dari kanan. Tipe data VecDeque memiliki bebebrapa method tambahan, yaitu:

- method `pop_front` untuk hapus data elemen pertama atau paling kiri (indeks ke-0)
- method `push_front` untuk menambah data dari kiri (indeks ke-0)
- method `pop_back` untuk hapus data elemen pertama atau paling kanan (indeks terakhir)
- method `push_back` untuk menambah data dari kanan (indeks terakhir)

```rust
use std::collections::VecDeque;

let mut vec_10 = VecDeque::from(vec!["a", "b", "c"]);

vec_10.pop_front();
vec_10.push_front("z");
println!("data: {:?}", vec_10);

vec_10.pop_back();
vec_10.push_back("h");
println!("data: {:?}", vec_10);
```

Tipe data `VecDeque<T>` tidak otomatis di-import. Kita perlu mengimport path di mana tipe data tersebut berada menggunakan keyword `use`.
```rust
use std::collections::VecDeque;
```

Cara membuat vector `VecDeque<T>` bisa menggunakan `VecDeque::from` dengan parameter diisi data vectornya, seperti pada kode program yang sudah ditulis.