# Konstanta

### Keyword `const`
Berbeda dengan variabel yang dideklarasikan menggunakan `let`, konstanta menggunakan `const`. Contoh:
```rust
const VAR: i32 = 123;
const LABEL: &str = "Label";
println!("{} {}", LABEL, PI);
```
aturan penulisan nama varibel konstanta adalah **screaming snake case**. Contohnya `VAR`, `CLASS_NAME`.
> Jangan menggunakan `mut` pada variabel konstanta karna akan menimbulkan error

### Keyword `static`
Ada cara lain untuk membuat variabel konstanta yaitu `static`. Contoh:
```rust
static NUMBER: i32 = 123;
fn main(){
    println!("{}", NUMBER);
}
```
> Apa bedanya menggunakan `const` dengan `static` ?
> Di Rust, konstanta yang dibuat via `const` tidak memiliki alamat memori yang pasti, dan setiap kali dipergunakan maka terjadi proses copy value. Sedangkan konstanta yang dibuat via keyword `static` mempunyai alamat memori yg fix/pasti.