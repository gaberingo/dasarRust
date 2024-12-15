# Build dan Run Program Rust

## Command `cargo build`
Digunakan untuk mem-build kode program dengan output file binary
- Untuk pengguna windows :
```bash
cargo build
cd target/debug
nama_file.exe
```
- Untuk pengguna linux :
```bash
cargo build
cd target/debug
./nama_file
```

## Optimized build
Untuk distribution/production disarankan untuk generate *optimized* binary dengan menambahkan flag `--release` pada saat build `cargo build`

```bash
cargo build --release
```

## Command `rustc`
Untuk kompilasi program rust bisa juga menggunakan `rustc`.
Sebagai contoh kita akan kompile file `hello.rs`

```rust
// hello.rs
fn main(){
    println!("Hello Rust")
}
```

- Untuk pengguna linux :
```bash
rustc hello.rs
./hello
```
- Untuk pengguna windows :
```bash
rustc hello.rs
hello.exe
```
