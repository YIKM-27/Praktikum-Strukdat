a.

Antrian linear dengan array biasa bisa mengalami penuh palsu karena walaupun ada data yang sudah keluar di depan, indeks tetap tidak kembali, jadi dianggap penuh.

Circular queue mengatasi ini dengan membuat indeks berputar ke awal lagi menggunakan modulus (%), sehingga tempat kosong di depan bisa dipakai kembali.

b.

Jika MAX_Q = 5 dan q->rear = 4, maka:

q->rear = (4 + 1) % 5 = 0

Jadi nilai q->rear yang baru adalah 0.

c.

Output program setelah dijalankan:

Proses Enqueue:
10 berhasil dimasukkan ke antrian.
20 berhasil dimasukkan ke antrian.
30 berhasil dimasukkan ke antrian.
40 berhasil dimasukkan ke antrian.
50 berhasil dimasukkan ke antrian.

Uji coba antrian penuh:
Maaf antrian penuh

Pesan saat enqueue(60) adalah “Maaf antrian penuh”.

d.
void dequeue(Queue *q) {
    if (isEmpty(q)) {
        cout << "Antrian kosong" << endl;
    } else {
        int value = q->data[q->front];
        cout << value << " dihapus dari antrian." << endl;
        q->front = (q->front + 1) % MAX_Q;
        q->count--;
    }
}
e.

Setelah antrian penuh (5 data), lalu dilakukan dequeue 2 kali, maka ada 2 ruang kosong.

Saat enqueue(70), nilai 70 berhasil masuk karena circular queue memungkinkan penggunaan kembali slot yang sudah kosong dengan sistem melingkar.