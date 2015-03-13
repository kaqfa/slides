## Aplikasi Penggajian
### Dengan Menggunakan Linked List

Sebuah perusahaan memiliki pegawai yang harus digaji tiap bulannya.
Sistem penggajian pada perusahaan tersebut didasarkan pada pangkat,
hari kerja, dan tunjangan keluarga. Lebih detail aturan penggajian pada
perusahaan tersebut adalah sebagai berikut:

- [1] Direktur = 500.000,- / hari
- [2] Manajer  = 300.000,- / hari
- [3] Pegawai Senior = 150.000,- / hari
- [4] Pegawai Junior = 75.000,- / hari

Sedangkan untuk tunjangan keluarga adalah didasarkan pada jumlah anak
yang dimiliki, dengan ketentuan sebagai berikut:

- 0 anak    = 0,- / bulan
- 1 anak    = 200.000,- / bulan
- 2 anak    = 350.000,- / bulan
- 3 anak    = 500.000,- / bulan
- >= 4 anak = 600.000,- / bulan

Sehingga, seorang manajer yang masuk penuh selama 22 hari dalam 1 bulan
serta memiliki 2 anak maka jumlah gajinya adalah:

Gaji Pokok         : 22 x 300.000 = 6.600.000,-
Tunjangan keluarga : 350.000,-
Jumlah             : 6.950.000,-


Tugas anda adalah membuat program untuk melakukan perhitungan gaji pegawai
dengan spesifikasi sebagai berikut:

1. Menu Utama : 
   - Input Data Pegawai
   - Input Data Anak Pegawai
   - Input Rekap Gaji
   - Laporan Gaji Per-Bulan

2. Data yang diinputkan pada data pegawai adalah :
   - Kode Pegawai
   - Nama Pegawai
   - Tahun Masuk
   - Jabatan
   - Status Marital

3. Data yang diinputkan pada data anak pegawai adalah :
   - Kode pegawai (orang tua)
   - Nama anak
   - Jenis kelamin
   - Tanggal lahir

4. Data yang diinputkan pada data input rekap gaji adalah :
   - Tahun dan bulan periode gaji
   - Kode Pegawai
   - Jumlah hari masuk

5. Laporan gaji per bulan akan meminta user untuk menginputkan tahun
   dan bulan periode gaji yang diinginkan. Kemudian program akan
   menampilkan gaji semua pegawai dengan urutan pegawai yang memiliki
   pangkat tertinggi akan ditampilkan terlebih dahulu


Untuk menyimpan semua data, silahkan menggunakan tipe data linked list
baik yang anda buat sendiri atau tipe data linked list yang tersedia pada
Java Collection.


Fitur tambahan yang bisa dibuat:

- Halaman login dengan username & password yang tersimpan di file
- Menyimpan data pegawai, anak, dan rekap gaji ke dalam file CSV, JSon, atau XML
- Tools untuk generating data secara otomatis secara random
- Tampilan GUI yang menarik
- Beberapa pilihan sorting data laporan gaji berdasarkan, pangkat, jumlah gaji, 
  jumlah anak, urut abjad nama, dan lain sebagainya