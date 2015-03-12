# Intro Java

### Java untuk Programmer C

Created by [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

## Apakah benar-benar Java?

Ya untuk mata kuliah ini contoh implementasinya akan menggunakan Java.

Tapi jangan khawatir, code C pendampingnya selalu tersedia dan mahasiswa
bebas menggunakan bahasa pemrograman lain saat mengerjakan tugas

--

## Apakah benar-benar Java?

Yang pernah mengambil mata kuliah PBO sebelumnya atau yang pernah belajar
Java di luar kelas (dan merasakan kebingungan konsep OOP), jangan khawatir
kita akan melupakan semua istilah-istilah seperti inheritance, polimorfise,
abstract, interface, dan lain sebagainya.

Cukup class dan object untuk menjalankan code. Cukup itu.

---

## Perbedaan C dan Java

- C menggunakan file header, Java menggunakan Class
- C menggunakan printf(), Java menggunakan System.out.println()
- C menggunakan scanf(), oke untuk yang satu ini Java agak ribet
- C menggunakan array of char, Java menggunakan String

--

## Perbedaan C dan Java

- C ada variabel global dan lokal, Java ada variabel Class &amp; variabel fungsi
- C menggunakan struct, Java menggunakan Class
- C menggunakan include, Java menggunakan import
- C menggunakan fungsi `main()` sebagai starting point, Java menggunakan class
  yang memuat fungsi `public static void main(String [] args)`

---

## Yang Perlu Diingat

Baik menggunakan C maupun Java, kita akan memasuki dunia pemrograman yang lebih modular
tidak hanya semua digabungkan pada satu file saja, tapi dipisah ke dalam beberapa file.

Bedanya, C menggunakan kumpulan fungsi dalam suatu header file, sedangkan Java menggunakan
kumpulan fungsi dan variabel yang dirangkai dalam sebuah Class.

---

## Memulai Java

Sebuah program Java minimal harus memiliki sebuah class yang memuat fungsi `main()`:

Class Template <!-- .element: class="code_title" -->

```java
	class NamaClass{
		public static void main(String [] args){
			// Kode yang dieksekusi 
			// saat program dijalankan
		}
	}
```

Contoh Class <!-- .element: class="code_title" -->

```java
	class FirstApp{
		public static void main(String [] args){		
			System.out.print("Inilah Java.\n");
			System.out.print("Tidak terlalu berbeda dengan C bukan?");
		}
	}
```

\* catatan: nama class main harus sama persis dengan nama filenya <!-- .element: class="footnote" -->

---

### Pemrograman Modular (Class Modul)

Agar progam dapat digunakan berulang-ulang, lebih baik kita memisahkan antara 
program inti dan program pemanggil.

Modul.java <!-- .element: class="code_title" -->

```java
	class Modul{
		String nama;

		void setNama(String nilai){
			this.nama = nilai;
		}

		void printNama(){
			System.out.println(this.nama);
		}
	}
```

--

### Pemrograman Modular (Class Pemanggil)

MainApp.java <!-- .element: class="code_title" -->

```java
	class ModulApp{
		public static void main(String [] args){
			Modul modul = new Modul();

			modul.setNama("nama modul yang baru");
			modul.printModul();
		}
	}
```
1. Buat class yang diperlukan
2. Pada class utama, buatlah object dari kelas tersebut
   dan masukkan dalam variabel
3. Panggil fungsi-fungsi pada class modul melalui variabel
   yang telah dibuat.    

---

### Variabel dalam Java

- Sama seperti bahasa C, sebuah variabel dalam Java harus ditentukan tipe 
  datanya terlebih dahulu, kemudian baru dituliskan nama variabelnya.
- Semua perintah pemrograman dalam harus berada di dalam Class, termasuk variabel

Mahasiswa.java <!-- .element: class="code_title" -->

```java
	class Mahasiswa{
		String nim;
		String nama;
		String email, password;
		double ipk;

		// rest of the codes
	}
```

--

### Tipe Data

Java dan C memiliki tipe data yang hampir sama, dengan beberapa peningkatan.

- `int` untuk angka bulat
- `double` untuk angka pecahan (ada juga `float` tapi untuk pemula lebih 
  direkomendasikan menggunakan `double`)
- `String` (dengan S besar) untuk teks
- `char` untuk satu karakter
- `boolean` bernilai true atau false

--

Mahasiswa.java <!-- .element: class="code_title" -->

```java
// ... kode sebelumnya
	void penambahan(int nil1, int nil2){
		System.out.println(nil1 + " + " + nil2 + " = " (nil1+nil2));
	}

	void inputBiodata(String nim, String nama, String email){
		this.nim = nim;
		this.nama = nama;
		this.email = email;
	}

	void printBiodata(){
		System.out.println("NIM = "+this.nim
				+" | Nama = "+this.nama+" | Email = "+this.email);
	}
// ... kode setelahnya
```

* catatan: untuk menggabungkan string dengan variabel cukup dengan menggunakan 
	"+", tidak perlu menggunakan "%s" seperti dalam C. <!-- .element: class="footnote" -->

---

### Input dalam Java

- Pemanggilan fungsi input dalam java sedikit lebih ribet dari C, namun juga
	lebih jelas dan lebih mudah dihafal:

```java
// di bagian paling atas
import java.util.Scanner;

// kode dalam fungsi

Scanner input = new Scanner(System.in);
String namaLengkap = input.nextLine();
String namaDepan = input.next();
int harga = input.nextInt();
int nilai = input.nextDouble();

// kode dalam fungsi

```

---

### Kondisi &amp; Perulangan

- Sama seperti Bahasa C, dalam Java untuk kondisi masih menggunakan
  kata perintah `if (kondisi) { aksi }`.
- Operator pembanding yang digunakan pun masih sama `==`, `!=`, `<`, `>`, `<=`, `>=`.
- Operator logis tetap saja menggunakan `&&` untuk logika AND dan `||` untuk OR.
- Begitu juga untuk perulangan, kita tetap memiliki perintah 
  - `for(inisial, kondisi, increment){ }`,
  - `while(kondisi){ }`, 
  - dan `do{ } while(kondisi);`

--

Mahasiswa.java <!-- .element: class="code_title" -->

```java
// ... kode sebelumnya
	void nilaiHuruf(int nilAngka){
		if(nilAngka >= 85) 
			System.out.print("A");
		else if(nilAngka >= 70) 
			System.out.print("B");
		else if(nilAngka >= 60) 
			System.out.print("C");
		else if(nilAngka >= 50) 
			System.out.print("D");
		else
			System.out.print("E");
	}

	void berhitung(int sebanyak){
		for(int i = 0; i < sebanyak; i++){
			System.out.println("Berhitung ke: "+(i+1));
		}
	}
// ... kode sesudahnya
```

--

### Membandingkan String

- Khusus untuk String, jika dalam bahasa C kita harus menggunakan fungsi
  `strcmp()` yang didapatkan dari `String.h`, di dalam Java kita bisa menggunakan
  `varString.equals("String yang dibandingkan")`
- Bisa juga menggunakan `varString.equalsIgnoreCase("String yang dibandingkan")`
  untuk membandingkan String tanpa menghiraukan besar kecil hurufnya.

Mahasiswa.java <!-- .element: class="code_title" -->

```java

	void login(String inputEmail, String inputPassword){
		if(inputEmail.equalsIgnoreCase(this.email)
			&& inputPassword.equals(this.password) ){
			System.out.print("Login sesuai, silahkan masuk");
		} else {
			System.out.print("Login tidak sesuai, silahkan ulangi");
		}
	}

```

---

### Memecah Program dengan fungsi

- Mengapa perlu memisahkan program ke dalam fungsi &amp; class :
	- Meningkatkan waktu kompilasi
	- Membuat program semakin modular (hanya menggunakan fungsi yang diperlukan saja)
	- Program lebih mudah untuk dirawat
- Untuk memudahkan kuliah kita, mari disepakati class &amp; file yang akan kita gunakan:
	- File main application: Berisi class yang memuat fungsi `public static void main()`.
		Penamaan file dan class ini dengan pola seperti `StackApp`, `QueueApp`, `LinkedListApp`,
		dan lain sebagainya.
	- File pustaka aplikasi: Berisi class yang memuat fungsi-fungsi yang sedang kita pelajari.
		Model penamaannya terserah asal tidak menyalahi kaidah penamaan identifier.

--

### Konsep Dasar fungsi

Aturan mendefinisikan fungsi adalah sebagai berikut :

```java
return_type functionName( parameter list ) 
{ 
    body of the function 
} 
```

- **Tipe Kembalian (void atau tipe data)**: nilai yang akan dihasilkan oleh fungsi tersebut
- **Nama Fungsi**: digunakan sebagai identifier dan memiliki aturan penamaan yang sama 
	seperti variabel.
- **Parameter**: digunakan untuk memasukkan nilai dari luar fungsi ke dalam fungsi. 
	Memiliki aturan yang sama dengan deklarasi variabel dalam C.
- Di dalam Java, fungsi harus dimasukkan ke dalam sebuah Class

--

### Contoh Program Kalkulator (Library)

Kalkulator.java <!-- .element: class="code_title" -->

```java

class Kalkulator{
	int tambah(int nilai1, int nilai2){
	    return nilai1+nilai2;
	}

	int kurang(int nilai1, int nilai2){
	    return nilai1-nilai2;
	}

	double kali(int nilai1, int nilai2){
	    return nilai1*nilai2;
	}

	double bagi(int nilai1, int nilai2){
	    return nilai1/nilai2;
	}
}

```

--

### Pemanggilan Class dan Fungsi

- Jika sebuah fungsi dipanggil oleh fungsi lain pada class yang sama,
	maka kita cukup memanggil nama fungsi itu saja. Contoh:

Kalkulator.java <!-- .element: class="code_title" -->

```java
	// ... koding sebelumnya
	
	double kaliVersi2(int nilai1, int nilai2){
		double hasil;

		for(int i = 0; i < nilai2; i++){
			hasil = tambah(hasil, nilai1);
		}

		return hasil;
	}

	// ... koding setelahnya
```

- Jika sebuah fungsi dipanggil oleh fungsi lain pada class yang beda,
	maka kita harus:
	- membentuk object dari class library dengan perintah `new`
	- memasukkan object ke dalam sebuah variabel
	- memanggil fungsi dari variabel tersebut

--

### Contoh Program Kalkulator (Main Application)

```java

class KalkulatorApp{
	
	public static void main(String [] args){
		Kalkulator calc = new Kalkulator();

		System.out.println(calc.tambah(12, 19));
		System.out.println(calc.kurang(12, 20));
		System.out.println(calc.kali(10, 19));
		System.out.println(calc.bagi(15, 2));
	}

}

```

* dalam Java, jika library dan pemanggilnya masih dalam direktori yang sama, kita tidak perlu
	melakukan import (dalam C include) <!-- .element: class="footnote" -->

----

- `Kalkulator calc = new Kalkulator()` membentuk object dari class library dengan perintah `new`
	dan memasukkan ke dalam variabel `calc`
- `calc.tambah(12, 19)` memanggil fungsi dari variabel `calc`


--

### Parameter Fungsi

```java

	int kurang(int nilai1, int nilai2){
	    return nilai1-nilai2;
	}

	double kali(int nilai1, int nilai2){
	    return nilai1*nilai2;
	}

```

- Parameter adalah cara fungsi untuk menginputkan nilai dari luar fungsi untuk diproses
	di dalam fungsi.
- Deklarasi variabel memiliki cara yang sama persis dengan deklarasi variabel biasa.
- Setiap fungsi bisa memiliki 0 hingga tidak terbatas jumlah parameter.

--

### Sekup Variabel fungsi &amp; Variabel Class

- Sebuah variabel jika dideklarasikan di dalam sebuah fungsi (termasuk parameter) hanya
	dapat diakses di dalam fungsi tersebut.
- Sedangkan jika dideklarasikan di luar fungsi (tapi tetap di dalam sebuah class), maka
	variabel tersebut dapat diakses oleh fungsi apapun yang terdapat di dalam class tersebut.
- Hanya saja, untuk membedakan variabel fungsi dan variabel class, pengaksesan variabel 
	class menggunakan kata kunci `this.`.

```java
class Mahasiswa{
	String nim, nama, email;
	double ipk;

	void setIPK(int jmlSks, int totalNilai){
		this.ipk = totalNilai/jmlSks;
	}

	void getIPK(){
		return this.ipk;
	}
}
```

--

### Tipe Kembalian Fungsi

- Sama seperti C, semua fungsi pada Java memiliki tipe Kembalian
- Fungsi yang tidak memiliki tipe kembalian masih harus mengembalikan tipe `void`
- Untuk mengembalikan sebuah nilai, fungsi selalu diakhiri dengan perintah `return`

---

### Manipulasi Array

- Dalam Java berbeda dengan array dalam C hanya pada saat deklarasi saja.
	- dalam C kita deklarasi array `int nilai[10]`
	- dalam Java cara deklarasi array adalah `int [] nilai = new int[10]`
- Penulisan dan pengaksesannya masih dengan cara yang sama
- Cara yang digunakan Java memudahkan programmer untuk menginisialisasi array
	kembali di tengah program
- Deklarasi multidimensional array `int[][] matrix = new int[10][10]`

--

Kalkulator.java <!-- .element: class="code_title" -->

```java
// .. koding sebelumnya

int jmlHistori = 0;
double [] histori = new double[50] 

int tambah(int nilai1, int nilai2){
  int hasil = nilai1+nilai2; 
  histori[jmlHistori] = hasil; 
  
  return hasil;
}

void printHistori(){
	for(int i = 0; i < this.jmlHistori; i++){
		System.out.println(histori[i]);
	}
}

// .. koding setelahnya
```

---

### Lebih Mudah Java dibandingkan C

Beberapa aspek yang membuat Java lebih mudah dibandingkan C adalah:

- Java memiliki tipe data String dan kita bisa melakukan operasi berikut:
	- `String nama = "Namaku yang Baru"`
	- `nama.charAt(5)` untuk mengambil satu karakter dari String
- Java dapat mendeklarasikan array di tengah aplikasi tanpa menggunakn pointer
	- C: `int *a = malloc(N * sizeof(*a))`
	- Java: `int[] a = new int[N]`
- C mengakses elemen struct dengan cara yang berubah-ubah, sedangkan Java mengakses
	elemen class dengan cara yang sama persis.
- Contoh koding struktur data dalam Java lebih mudah dipahami daripada contoh program
	dalam C.

---

### Tugas Pertama

- Buatlah program untuk melakukan manipulasi matrix
- Terlebih dahulu buatlah library (class) MatrixManipulation yang berisikan:
	- 1 variabel class array 2 dimensi dengan nama `matrix`
	- fungsi `void penambahanMatrix()`
	- dan fungsi `void penguranganMatrix()`
- Kemudian jangan lupa untuk membuat file main applicationnya untuk menguji coba
	library yang telah dibuat

---

# THE END

### By Fahri Firdausillah / fahrifirdaus.web.id