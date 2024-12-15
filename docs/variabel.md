# Variabel

## Deklarasi variabel
- ### Deklarasi menggunakan `let`
    ```rust
    fn main(){
        let var_1 = "Hello Worlds";
        println!("{var_1}");
    }
    ```
    pada deklarasi variabel diatas, compiler secara cerdas akan mendeteksi jenis tipe data dari variabel `var_1` yaitu string.

- ### Deklarasi mutable variabel dengan `mut`
  Pada saat mendeklarasikan sebuah variabel, secara default variabel tersebut bersifat `immutable` atau bisa juga disebut `variabel konstanta`
  ```rust
  fn main(){
    let var1 = "Hello"; // variabel immutable
    let mut var2 = "Worlds"; // variabel mutable
    println!("{var1} {var2}"); // output Hello Worlds
    var2 = "Coders";
    println!("{var1} {var2}"); // output Hello Coders
  }
  ```
    

- ### Variabel *Type Inference* dan *Manifest Typing*
  1. *Type Inference*
    ```rust
    /*
        Typer Inference adalah
        dimana compiler secara cerdas
        mendeteksi type dari sebuah variabel
    */
    let var = 13;
    let var = "Hello";
    ```
  2. *Manifest Typing*
    ```rust
    /*
        Manifest Typing adalah
        kita menentukan type variabel
        secara manual
    */
    let var: i32 = 32; // Manifest Typing 
    ```
    notasi penulisan untuk *Manifest Typing* `name_var: tipedata`
- ### Deklarasi variabel tanpa *predefined value*
  Secara default saat mendeklarasikan sebuah variable kita biasanya sekaligus memberikan nilai pada sebuah variabel seperti kode berikut
  ```rust
  let var = 1;
  println!("{var}")
  ```
  nah ada cara agar nilai dari sebuah variabel di berikan belakangan juga di sebut *predefined value* seperti kode berikut:
  ```rust
  let var: i32;
  var = 32;
  println!("{var}")
  ```
  > ! saat memberi nilai pada variabel seperti diatas, jika variabel tersebut adalah immutable, maka pemberian nilai hanya boleh di lakukan sekali saja.
- ### Deklarasi banyak variabel sekaligus
  Kita juga bisa mendeklarasikan banyak variabel sekaligus, caranya seperti kode dibawah ini :
  ```rust
  // contoh 1
  let (var1, var2, var3) = (1, "Hello", "World");
  println!("{var1} {var2} {var3}");

  // contoh 2
  let (var1, var2, var3):(i32, &str, &str) = (1, "Hello", "Worlds");
  println!("{var1} {var2} {var3}");

  // contoh 3
  let (var1, var2, var3):(i32, &str, &str);
  var1 = 1;
  var2 = "Hello";
  var3 = "Worlds";
  println!("{var1} {var2} {var3}");

  //contoh 4
  let (var1, mut var2, var3):(i32, &str, &str) = (1, "Hello", "Worlds");
  var2 = "Haii";
  println!("{var1} {var2} {var3}");
  ```
  Pendefinisian banyak variabel dalam 1 statement dilakukan dengan menuliskan semua variabelnya dengan separator tanda `,` dan diapit tanda kurung `()`
- ### Deklarasi variabel dengan type varibel ditentukan value nya
  Berikut adalah alternatif penulisan untuk men-spesifikan type dari sebuah varibel setelah value
  ```rust
  // cara 1
  let var = 32i32;
  println!("{var}");

  //cara 2
  let var = 32_i32;
  println!("{var}");
  ```
  type variabel bisa langsung di tuliskan seletah value (`32i32`) atau menggunakan underscore (`32_i32`).
- ### Variabel *Shadowing*
  Ada konsep yang disebut *variabel shadowing* dimana sebenarnya variabel ini adalah variabel yang di definisikan ulang.
  ```rust
  let a = 32_i32;
  println!("{a}");
  let a = "Hello"; // di definisikan ulang menjadi sebuah string
  println!("{a}");
  ```
- ### Variabel `_`
  Ada kalanya kita menyimpan sebuah value pada sebuah variabel tapi varibel tersebut tidak pernah digunakan, misalkan kita hanya ingin menjalankan sebuah fungsi. Karna setiap variabel yang tidak digunakan akan menampilkan warning, maka untuk menghidarinya digunakan variabel `_`.
  ```rust
  fn main(){
    let _ = run_something();
  }
  ```