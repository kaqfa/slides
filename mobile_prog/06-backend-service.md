# <div class="highlight-blue">Section 01</div>

### Backend API Creation

by: [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Intro Menggunakan Django

- Django merupkan framework pengembangan aplikasi web
- Django menggunakan bahasa pemrograman Python
- Django memiliki fitur admin generator
- Dengan menambahkan plugin Django-Rest-Framework, kita 
  dapat membuat API service secara mudah
  
--

### Setting Django

--

### Membuat Model dan DB Migration

-- 

### Membuat Admin Otomatis

--

### Membuat Serializer

--

### Membuat Viewset

--

### Register Router

---

### RESTful Service dengan Lumen

- Lumen merupakan micro framework yang dibuat oleh Taylor Ottwel
  (pembuat Framework Laravel)
- Tujuan dari micro framework secara umum adalah memudahkan development
  aplikasi web sederhana dengan router dan middleware yang mudah diatur
- Dalam REST pengaturan Router memudahkan untuk mendesain URL
- Sedangkan middleware memudahkan untuk mengatur otentikasi dan permisi

---

### Memulai Lumen

- Pertama install aplikasi Composer untuk mendownload library dan 
  dependency secara otomatis
- Selajutnya ketikkan perintah berikut pada command prompt:
  ```composer global require "laravel/lumen-installer=~1.0"```
- Kemudian untuk membuat project lumen baru ketikkan kode berikut
  ```lumen new appname```

--

### Konfigurasi Lumen

- Untuk memudahkan pengembangan aplikasi ada baiknya kita mengaktifkan
  fitur Eloquent ORM-nya laravel dengan mengetikkan kode berikut pada
  **app.php**
  ```
  Dotenv::load(__DIR__.'/../');
 
  $app->withFacades(); 
  $app->withEloquent();
  ```

--

### Konfigurasi Lumen (2)

- Selanjutnya kita perlu membuat konfigurasi environment (termasuk koneksi database)
  dengan membuat file ```.env``` dan mengisinya dengan kode berikut:
  ```
  APP_ENV=local
  APP_DEBUG=true
  APP_KEY=SomeRandomKey!!!
   
  APP_LOCALE=en
  APP_FALLBACK_LOCALE=en
   
  DB_CONNECTION=mysql
  DB_HOST=localhost:3306
  DB_DATABASE=tutorial1
  DB_USERNAME=tutorial1
  DB_PASSWORD=tutorial1
   
  CACHE_DRIVER=memcached
  SESSION_DRIVER=memcached
  QUEUE_DRIVER=database
  ```

--

### Generate Tabel

- Laravel / Lumen memberikan cara untuk generate struktur tabel secara mudah
- Arahkan direktori aktif command prompt pada root folder dari aplikasi Lumen kita
- Ketikkan kode berikut untuk membuat template generating table
  ```
  artisan make:migration create_articles_table --create=articles
  ```
- Jika berhasil seharusnya kita memiliki file dengan nama 
  **xxxxxx_create_article_table.php** pada direktori database
  migrasi kita

--

### Generate Tabel (2)

- Edit fungsi ```up()``` pada file tersebut sehingga menjadi seperti berikut:
  ```
  public function up()
	{
		Schema::create('articles', function(Blueprint $table)
		{
			$table->increments('id');
			$table->string('title');
			$table->string('content');
			$table->timestamps();
		});
	}
  ```
- Kemudian untuk menjalankan aksi generator-nya jalankan perintah berikut pada 
  command prompt ```php artisan migrate```

--

### Membuat Model



--

### Membuat Controller

--

### Mengarahkan Router

--

### Uji coba Lumen

---

## Kesimpulan