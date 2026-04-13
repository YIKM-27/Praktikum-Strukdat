# ini adalah notul di kertas tapi saya pindahken ke sini di karenakan saya gabut waktu masih lama soalnya :D

## Pertanyaan :)

a. Stack selalu bekerja menggunakanprinsip LIFO (Last In First Out). Berikan minimal satu contoh logis penerapannya taprinsip LIFO pada fitur perangkat lunak/aplikasiyangsering Anda gunakan sehari-hari

b. Perhatikan urutan kode pada fungsi push. Mengapa program menggunakan variabel count sebagai indeks array terlebih dahulu (x->item[x->count] = data;), dan barusetelah itu menambahkan nilainya (++(x->count); )? Bagaimana jika ini dibalik?

c. Perhatikan luaran dari program di atas. Karena nilai MAXSTACK adalah 2, apa yang
terjadi ketika program mencoba memanggil push(6) dan push(7)?

d.Diinginkanpadabagianmainprogramdiatasmenjadisepertiberikut:
```cpp
int main() {
    membuatStack(&tumpukan);
    push(3, &tumpukan); push(5, &tumpukan);
    push(6, &tumpukan); push(7, &tumpukan);
    cetak();
    pop(&tumpukan); pop(&tumpukan);
    pop(&tumpukan); pop(&tumpukan);
    cetak();
    return 0;
}
```
Buatlah implementasi method pop yang memanipulasi variabel count dan mencetak nilai yang terhapus!
Jawabananda:
```cpp
voidpop(Stack*x){
}
```

d .Berdasarkan logika pada method pop Anda diatas apakah data yang di-pop benar benar dihapus secara permanen dari memori arrayx->item,atau hanyadiabaikan pembacaannya melalui penurunan variabelx->count?Jelaskanalasannya

## Jawaban
a. Contoh LIFO
Stack menggunakan prinsip LIFO (Last In First Out) yaitu data terakhir masuk akan keluar terlebih dahulu.
Contoh pada fitur Undo di Microsoft Word:
Jika kita mengetik A, B, C lalu menekan Undo, maka huruf C yang akan dihapus terlebih dahulu.

b. Alasan urutan pada push
Kode:
```cpp
x->item[x->count] = data;
++(x->count);
```
Penjelasan:
Variabel count menunjukkan jumlah data saat ini sekaligus indeks berikutnya yang kosong.
Data dimasukkan ke indeks count terlebih dahulu, kemudian count ditambah.

Jika dibalik:
```cpp
++(x->count);
x->item[x->count] = data;
```
maka data pertama akan masuk ke indeks 1, sehingga indeks 0 kosong dan menyebabkan kesalahan logika.

c. Kondisi saat MAXSTACK = 2

Stack hanya dapat menampung 2 data.
```
push(3) → berhasil
push(5) → berhasil
push(6) → gagal (Stack Penuh)
push(7) → gagal (Stack Penuh)
```
d. Implementasi fungsi pop
```cpp
void pop(Stack *x){
    if (isEmpty(x)) {
        cout << "Stack Kosong\n";
    } else {
        --(x->count);
        cout << "data yang dihapus: " << x->item[x->count] << endl;
    }
}
```

e. Apakah data benar-benar terhapus?
Data tidak benar-benar dihapus dari memori, tetapi hanya diabaikan.
Hal ini karena count dikurangi, sehingga data tersebut tidak lagi dianggap bagian dari stack, walaupun masih tersimpan di array. ```cpp aray{} ```
