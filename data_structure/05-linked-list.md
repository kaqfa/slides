# Linked List

### Konsep dan Implementasi Linked List

Created by [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Kenapa Linked List?

- Variabel yang dialokasikan memori pada saat kompilasi (sebelum berjalan)
  tidak dapat diubah ukurannya.
- Jika data lebih banyak dari ukuran data yang ditetapkan maka aplikasi tidak
  lagi dapat menampung data
- Sebaliknya jika data lebih sedikit dari ukuran alokasi, maka sisanya jadi
  mubadzir

--

### Here is Linked List

- LinkedList merupakan tipe data yang memungkinkan alokasi secara dinamis
- Memori dialokasikan saat ada data tambahan yang akan disimpan
- Sebuah LinkedList terdiri dari bagian data dan bagian link
- Bagian link yang akan menghubungkan satu elemen dengan elemen lain

--

### Representasi Linked List

[!img 'data_structure/images/linked_list.gif']

- Sebuah elemen Linked List sering digambarkan dengan kotak yang terdiri dari 2 bagian
- Bagian pertama untuk menyimpan data (bisa menyimpan banyak data)
- Bagian kedua menyimpan alamat memori dari elemen selanjutnya

--

### Representasi Linked List (2)

- Untuk mengetahui semua data dari sebuah Linked List, kita harus mengetahui Elemen
  awal dari Linked List tersebut.
- Sedangkan elemen-elemen selanjutnya dapat ditelusuri dari link yang ada pada setiap
  elemen
- Thus, jika link terputus di tengah jalan, maka elemen setelahnya tidak dapat diakses lagi
- Adapun elemen terakhir dari Linked List, ditandai dengan link yang berisi NULL

---

### Implementasi Dalam Java

- Ada 2 Class yang diperlukan untuk membuat sebuah struktur data Linked List
- Class Element / List (whatever you call it), untuk menyimpan informasi elemen
- Class LinkedList Untuk menyimpan informasi dan manipulasi elemen yang saling terkait

--

### Class Element

- Sesuai definisi, harus menyimpan 2 bagian yaitu bagian data dan bagian link
- Link merupakan variabel dengan tipe data dirinya sendiri

```java
class Element{
  int data;
  Element link;
}
```