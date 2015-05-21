# <div class="highlight-blue">Section 06</div>

### Backend API Creation

by: [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Langkah Umum Bekerja dengan Framework

- Create project
- Setting project
- Model dan migrasi database
- Membuat controller
- Membuat URL router

---

### Intro Menggunakan Django

- Django merupkan framework pengembangan aplikasi web
- Django menggunakan bahasa pemrograman Python
- Django memiliki fitur admin generator
- Dengan menambahkan plugin Django-Rest-Framework, kita 
  dapat membuat API service secara mudah
- Bonus, ada browsable API untuk memudahkan dokumentasi service
  
--

### Langkah Khusus Django

- Membuat project dan aplikasi
- Membuat model dan migrasi database
- Membuat admin (untuk tampilan GUI)
- Membuat serializer
- Membuat viewset (controller)
- Register router

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
  **bootstrap/app.php**
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
  DB_DATABASE=tutorial
  DB_USERNAME=root
  DB_PASSWORD=root
   
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

- Seperti pada Laravel 5, *by default* direktori Model tidak lagi ada pada
  instalasi Lumen
- Sebagai gantinya kita bisa menaruh model di manapun
- Buat file Article.php pada direktori App
- Kemudian ketikkan kode berikut pada file tersebut

```
<?php namespace App;
 use Illuminate\Database\Eloquent\Model;
 
 class Article extends Model{}
```

--

### Membuat Controller

- Controller adalah kumpulan fungsi yang akan dijalankan
  saat suatu URL dipanggil.
- Untuk membuat controler, buat satu file baru dengan nama
  ArticleController pada direktori app/http/controller dan
  ketikkan kode berikut
  
```
<?php namespace App\Http\Controllers;
 
use App\Article;
use App\Http\Controllers\Controller;
use Illuminate\Http\Request;
 
 
class ArticleController extends Controller{
 
    public function index(){
        $articles  = Article::all();
        return response()->json($articles);
    }
}
```

--

### Membuat Controller (2)

- Jangan lupa tambahkan juga fungsi lain untuk melengkapi
  CRUD dari model Article
  
```
public function getArticle($id){
    $article  = Article::find($id);
    return response()->json($article);
}

public function saveArticle(Request $request){
    $article = new Article();
		$article->title = $request->input('title');
		$article->content = $request->input('content');
		$article->save();		
    return response()->json($article);
}

public function deleteArticle($id){
    $article  = Article::find($id);
    $article->delete();
    return response()->json('success');
}

public function updateArticle(Request $request,$id){
    $article  = Article::find($id);
    $article->title = $request->input('title');
    $article->content = $request->input('content');
    $article->save();
    return response()->json($article);
}
```

--

### Mengarahkan Router

- Langkah terakhir adalah mendesain URL yang digunakan
  untuk mengakses aksi yang sudah kita buat
- Caranya dengan mengedit file Routes.php yang ada pada direktori
  app dengan menambahkan kode berikut
```
$app->get('api/article','App\Http\Controllers\ArticleController@index');
$app->get('api/article/{id}','App\Http\Controllers\ArticleController@getArticle');
$app->post('api/article','App\Http\Controllers\ArticleController@saveArticle');
$app->put('api/article/{id}','App\Http\Controllers\ArticleController@updateArticle');
$app->delete('api/article/{id}','App\Http\Controllers\ArticleController@deleteArticle');
```

--

### Uji coba Lumen

- Jalankan aplikasi lumen pertama kita dengan menjalankan perintah berikut
  pada command prompt:
  ```
  php artisan serv
  ```
- Lihat hasilnya pada browser atau API browser 

---

## Konsumsi Service
### Manipulasi Hasil Data via Service

---

### Alur Akses Data Service

- Buat class pengakses jaringan
- Tambahkan permisi penggunaan Internet pada manifest
- Buat class activity dengan tambahan inner class
  - Inner class dibuat private dan inherit AsyncTask
  - Override method doInBackground 
  - Class akses jaringan yang telah dibuat dapat digunakan pada method tersebut
  - Untuk mempercantik bisa juga override method onPreExcute dan onPostExecute
- Buat event untuk memanggil inner class tersebut

--

### Class Pengakses Jaringan

- Class ini menggunakan ```HTTPClient```, ```HTTPEntity```, dan ```HTTPRespose```
  - ```HTTPClient``` untuk konfigurasi akses url yang diinginkan
  - ```HTTPEntity``` untuk mengirimkan parameter tambahan
  - ```HTTPResponse``` untuk menerima data response yang diberikan server
- Untuk manipulasi data response sebaiknya jangan di class ini
- Contoh dapat dilihat pada class ServiceHandler.java

--

### Permisi Penggunaan Internet

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

--

### Inner Class AsyncTask

- Karena koneksi jaringan adalah pekerjaan yang memakan waktu, 
  kita perlu membungkusnya ke dalam tugas yang dikerjakan secara asingkron
- Artinya setelah tugas dimulai, aplikasi masih dapat mengerjakan hal lain
  sambil menunggu koneksi selesai
- Meski demikian, jika pekerjaan lain membutuhkan data yang didapatkan dari
  jaringan, lebih baik kita membuat penanda tunggu

--

### Inner Class AsyncTask (2)

- override ```onPreExecute``` untuk mengeset apa yang harus dikerjakan sebelum
  melakukan pemanggilan jaringan
- overring ```onPostExecute``` untuk mengeset apa yang harus dikerjakan setelah
  pemanggilan jaringan selesai
- dan wajib override ```doInBackground``` untuk mendeskripsikan apa saja yang
  dilakukan aplikasi setelah mendapatkan data dari jaringan
  
--

### Inner Class AsyncTask (3)

- Pada ```doInBackground``` kita memanggil class akses data service untuk mendapatkan
  data dari jaringan berupa text dalam format JSON
- Selanjutnya gunakan class ```JSONObject``` dan ```JSONArray``` untuk memanipulasi
  data dalam bentuk JSON tersebut
- Setelah semua data disimpan dalam bentuk Array, List, atau Map baru dapat dimanipulasi
  lebih lanjut dengan adapter