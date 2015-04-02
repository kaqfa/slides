# <div class="highlight-blue">Section 02</div>

### User Interface in Android

by: [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Sub Pembahasa UI di Android

- [Komponen Dasar UI](#01)
- [ViewGroup](#02)
- [Manajemen Layout](#03)
- [AdapterView](#05)
- [List &amp; Grid Layout](#06)
- [Fragment untuk UI Adaptif](#04)

---

### Komponen Dasar Android UI

- ```TextView```: teks yang biasa digunakan untuk label
- ```Button```: tombol yang bisa ditekan
- ```TextField```: inputan teks dengan beberapa variasi
- ```CheckBox```: kotak kecil dengan pilihan
- ```RadioButton```: sama seperti checkbox hanya saja pada radio button hanya
    1 pilihan yang bisa digunakan sekali waktu
- ```Spinner```*: seperti pilihan dropdown dalam HTML

---

### Contoh Penulisan View dengan XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" >

    <TextView
        android:id="@+id/text_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="@string/hello_android"
        android:textSize="24sp" />

</LinearLayout>
```
coursera-android &raquo; Examples &raquo; 4. user interface &raquo; HelloAndroidWithMenus <!-- .element: class="code_title" -->

--

### Contoh Button UI

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <Button
        android:id="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_marginLeft="10dip"
        android:text="@string/press_me_string" >
    </Button>

</RelativeLayout>
```
coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIButton <!-- .element: class="code_title" -->

--

### Contoh TextView, Button, dan CheckBox

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" >

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/checkbox_string" 
        android:textSize="24sp"/>

    <CheckBox
        android:id="@+id/checkbox"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/im_not_checked_string" 
        android:textSize="24sp"/>

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/hide_checkbox_string" 
        android:textSize="24sp">
    </Button>

</LinearLayout>
```
coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UICheckBox <!-- .element: class="code_title" -->

---

### Atribut Komponen

Setiap komponen UI memiliki atribut yang bisa diset, di antaranya:

- ```layout_width```: menentukan lebar dari komponen
- ```layout_height```: menentukan tinggi dari komponen
- ```id```: memberikan id baru pada komponen. Id yang diberikan nantinya dapat diakses dari source java melalui
    ```R.id.id_yang_dibuat```.
- ```input_type```: atribut ```EditText``` untuk menetukan jenis textbox yang diinginkan (```"text"```, ```"textEmailAddress"```, ```"number"```, ```"phone"```, dll)
- ```padding```: menentukan jarak dari garis pinggir dengan teks internal
- ```margin```: menentukan jarak garis pinggir dengan komponen lain

---

### Menjalankan Aksi pada Event

Ada beberapa cara untuk menjalankan event pada Android:

- Mengimplementasikan interface event
- Membuat anonymous class untuk event tertentu
- Memanggil method listener dari komponen tertentu
- Mengeset fungsi pemanggil pada komponen XML dan membuat fungsi
  tersebut pada activity pemanggilnya
  
--

### Mengimplementasikan interface event

```java
public class ExampleActivity extends Activity implements OnClickListener {
    protected void onCreate(Bundle savedValues) {
        ...
        Button button = (Button)findViewById(R.id.corky);
        button.setOnClickListener(this);
    }

    // Implement the OnClickListener callback
    public void onClick(View v) {
      // do something when the button is clicked
    }
    ...
}
```

--

### Membuat Anonymous Class

```java
// Create an anonymous implementation of OnClickListener
private OnClickListener mCorkyListener = new OnClickListener() {
    public void onClick(View v) {
      // do something when the button is clicked
    }
};

protected void onCreate(Bundle savedValues) {
    ...
    // Capture our button from layout
    Button button = (Button)findViewById(R.id.corky);
    // Register the onClick listener with the implementation above
    button.setOnClickListener(mCorkyListener);
    ...
}
```

--

### Memanggil Method Listener dari Object View

```java
    // Get a reference to the CheckBox
    final CheckBox checkbox = (CheckBox) findViewById(R.id.checkbox);

    // Set an OnClickListener on the CheckBox
    checkbox.setOnClickListener(new OnClickListener() {
        @Override
        public void onClick(View v) {

            // Check whether CheckBox is currently checked
            // Set CheckBox text accordingly
            if (checkbox.isChecked()) {
                checkbox.setText("I'm checked");
            } else {
                checkbox.setText("I'm not checked");
            }
        }
    });
```

--

### Set Fungsi yang Menjalankan Aksi Event

```xml
<Button 
    android:id="@+id/aButton"
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:text="@string/btn_text" 
    android:onClick="btnClick" />
```
Kode layout XML <!-- .element: class="code_title" -->

```java
public void btnClick(View v){   
    TextView teks = (TextView) findViewById(R.id.secondText);
    teks.setText("Teks yang berubah");
}
```
Kode Activity pemanggil layout tersebut <!-- .element: class="code_title" -->

--

### Tipe Event Listener

- ```onClck()```
- ```onLongClick()```
- ```onFocusChange()```
- ```onKey()```
- ```onTouch()```
- ```onCreateContextMenu()```

---

### Mengumpulkan beberapa View dengan ViewGroup

ViewGroup merupakan invisible view yang berguna untuk menggabungkan beberapa
komponen view sekaligus.

Class ViewGroup juga menjadi base class untuk container komponen dan layout

---

### Beberapa Komponen ViewGroup

- ```RadioGroup```: kumpulan radio button yang hanya bisa dipilih salah satu saja
- ```TimePicker```: dialog untuk menampilkan inputan waktu
- ```DatePicker```: dialog untuk menampilkan inputan tanggal
- ```WebView```: komponen untuk menampilkan halaman HTML (serta CSS &amp; Javascript)
- ```MapView```: komponen untuk menampilkan peta
- ```Gallery```: kumpulan beberapa gambar yang tersusun secara tabular
- ```Spinner```: kumpulan text yang dapat dipilih secara dropdown

--

### Cara-Cara Penggunaan ViewGroup

Setiap ViewGroup memiliki cara deklarasi dan penggunaan yang berbeda dan memerlukan
lebih banyak tahap dibandingkan komponen UI biasa:

- Radio Group: deklarasikan ```RadioGroup``` dan ```RadioButton``` semua pada file layout
  - Contoh : coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIRadioGroup
- Time Picker: tidak ada komponen yang dideklarasikan di file layout, namun dipanggil
  secara dinamis melalui kode Java dengan dibungkus pada sebuah kotak dialog
  - Contoh : coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UITimePicker
- DatePicker: sama seperti Time Picker
  - Contoh : coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIDatePicker
  
--

### Cara-Cara Penggunaan ViewGroup (2)

- Web View: deklarasikan ```WebView``` pada file layout, kemudian spesifikasikan halaman
  web yang ingin dipanggil pada kode Java
  - Contoh: coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIWebView
- Map View: hampir seperti Web View, namun memerlukan langkah yang lebih panjang (akan dibahas
  pada bagian Location Based Service setelah MID semester)
  - Contoh: coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIGoogleMaps
  - Langkah: https://developers.google.com/maps/documentation/android/start
- Gallery &amp; Spinner akan dibahas pada pada bagian selanjutnya di Adapter

---

### Mengatur Tata Letak dengan Layout

Layout merupakan sub Class dari ViewGroup yang mendefinisikan struktur tampilan dari
komponen View yang dimiliki.

- Layout Sederhana:
  - ```FrameLayout```: untuk Menampilkan hanya satu atau dua elemen aja
  - ```LinearLayout```: untuk menampilkan elemen secara berjajar horizontal atau vertical
  - ```RelativeLayout```: untuk menampilkan elemen yang posisinya diatur relatif terhadap
    komponen lain
  - ```TableLayout```: untuk menampilkan elemen yang diatur seperti tabel
- Layout Dinamis:
  - ```ListLayout```: menampilkan kelompok elemen secara dinamis secara berjajar
  - ```GridLayout```: menampilkan kelompok elemen secara dinamis dengan kotak-kotak
  
--

### Contoh RelativeLayout

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <!-- Note the use of android:hint to put explanatory text in the EditText  -->
    <EditText
        android:id="@+id/entry"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/type_here_string"
        android:textSize="24sp" />

    <Button
        android:id="@+id/ok_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        android:layout_below="@id/entry"
        android:layout_marginLeft="10dip"
        android:text="@string/ok_string"
        android:textSize="24sp" />

    <Button
        android:id="@+id/cancel_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignTop="@id/ok_button"
        android:layout_toLeftOf="@id/ok_button"
        android:text="@string/cancel_string"
        android:textSize="24sp" />

</RelativeLayout>
```

coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIRelativeLayout <!-- .element: class="code_title" -->

--

### Contoh TebleLayout

```xml
<?xml version="1.0" encoding="utf-8"?>
<TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:stretchColumns="1" >

    <!-- First row -->
    <TableRow>

        <!-- start in column 1 -->
        <TextView
            android:layout_column="1"
            android:padding="3dip"
            android:text="@string/open_string"
            android:textSize="24sp" />

        <TextView
            android:gravity="right"
            android:padding="3dip"
            android:text="@string/ctrl_o_string"
            android:textSize="24sp" />
    </TableRow>

    <TableRow>

        <TextView
            android:layout_column="1"
            android:padding="3dip"
            android:text="@string/save_string"
            android:textSize="24sp" />

        <TextView
            android:gravity="right"
            android:padding="3dip"
            android:text="@string/ctrl_s_string"
            android:textSize="24sp" />
    </TableRow>

    <TableRow>

        <TextView
            android:layout_column="1"
            android:padding="3dip"
            android:text="@string/save_as_string"
            android:textSize="24sp" />

        <TextView
            android:gravity="right"
            android:padding="3dip"
            android:text="@string/ctrl_shift_s_string"
            android:textSize="24sp" />
    </TableRow>

    <!-- Create a divider -->
    <View
        android:layout_height="2dip"
        android:background="#FF909090" />

    <TableRow>

        <TextView
            android:padding="3dip"
            android:text="@string/x_string"
            android:textSize="24sp" />

        <TextView
            android:padding="3dip"
            android:text="@string/import_string"
            android:textSize="24sp" />
    </TableRow>

    <TableRow>

        <TextView
            android:padding="3dip"
            android:text="@string/x_string"
            android:textSize="24sp" />

        <TextView
            android:padding="3dip"
            android:text="@string/export_string"
            android:textSize="24sp" />

        <TextView
            android:gravity="right"
            android:padding="3dip"
            android:text="@string/ctrl_e_string"
            android:textSize="24sp" />
    </TableRow>

    <View
        android:layout_height="2dip"
        android:background="#FF909090" />

    <TableRow>

        <TextView
            android:layout_column="1"
            android:padding="3dip"
            android:text="@string/quit_string"
            android:textSize="24sp" />
    </TableRow>

</TableLayout>
```

coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UITableLayout <!-- .element: class="code_title" -->

---

### ArrayAdapter dan BaseAdapter

- Beberapa komponen GroupView memerlukan proses untuk men-transform
  data sekuensial (array, list, kursor, dll) ke dalam kumpulan view.
- Dua jenis adapter yang sering digunakan adalah:
  - ```ArrayAdapter```: *Concrete Class* dan digunakan untuk mengadapatasi
    data sekuensial String.
  - ```BaseAdapter```: *Abstract Class* harus di-extend ke dalam bentuk
    yang lebih bervariasi.

---

### Spinner dengan ArrayAdapter

Untuk menampilkan beberapa data dengan menggunakan spinner, langkahnya
adalah sebagai berikut:

1. Buat array kumpulan String
2. Buat layout individu untuk tiap list-nya
   (bisa digantikan dengan layout spinner standar android)
3. Instantiasikan ArrayAdapter dengan tipe generic String
   yang mengambil nilai dari Array yang sudah dibuat, dan
   konfigurasi layout yang ditetapkan
4. pilih elemen spinner dan set adapter yang sudah dibuat

<hr />
*NB: contoh menggunakan coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UISpinner*

--

### Langkah 1 &amp; 2

string.xml <!-- .element: class="code_title" -->

```xml
<string-array name="colors">
    <item>red</item>
    <item>orange</item>
    <item>yellow</item>
    <item>green</item>
    <item>blue</item>
    <item>indigo</item>
    <item>violet</item>
</string-array>
```

SpinnerActivity.java <!-- .element: class="code_title" -->

```java
// another alternative
// String [] arrColor = {"red", "orange", "yellow", "green", "blue", "indigo", "violet"};
// Create an Adapter that holds a list of colors
ArrayAdapter<CharSequence> adapter = ArrayAdapter.createFromResource(
        this, R.array.colors, R.layout.dropdown_item /*arrColor*/);
```

--

### Langkah 3, 4, &amp; Listener

```java
Spinner spinner = (Spinner) findViewById(R.id.spinner);
spinner.setAdapter(adapter);

spinner.setOnItemSelectedListener(new OnItemSelectedListener() {...} );
```

---

### ListLayout dengan ArrayAdapter

- Dengan langkah yang hampir sama seperti Spinner yaitu deklarasi array,
  instantiasi adapter, dan set adapter
- Hanya saja untuk mempersingkat koding, Android sudah menyediakan 
  ListActivity yang merupakan extends dari Activity namun sudah mengimplementasikan
  ListLayout di dalamnya.
- Contoh penggunaannya di: coursera-android &raquo; Examples &raquo; 4. user interface &raquo; UIListView

---

### GridView dengan BaseAdapter

- Jika ingin menampilkan list komponen yang bukan sekedar string,
  diperlukan class Adapter yang lebih powerful, yaitu ```BaseAdapter```.
- Langkah penggunaannya adalah:
  - Buat class yang extends BaseAdapter
  - Class tersebut harus override ```getCount()```, ```getItem()```, ```getItemId()```,
    dan ```getView()```.
  - Deklarasikan list /  array data
  - Buat instantiasi class adapter yang telah dibuat dengan menggunakan data array
  - Pilih elemen gridview dan set dengan adapter yang telah dibuat
  
--

### Langkah 1: Class Adapter

```java
public class ImageAdapter extends BaseAdapter {
	private static final int PADDING = 8;
	private static final int WIDTH = 250;
	private static final int HEIGHT = 250;
	private Context mContext;
	private List<Integer> mThumbIds;

	// Store the list of image IDs
	public ImageAdapter(Context c, List<Integer> ids) {
		mContext = c;
		this.mThumbIds = ids;
	}

	...
}
```

--

### Langkah 2: Deklarasi Data Sekuensial

```java
private ArrayList<Integer> mThumbIdsFlowers = new ArrayList<Integer>(
        Arrays.asList(R.drawable.image1, R.drawable.image2,
                R.drawable.image3, R.drawable.image4, R.drawable.image5,
                R.drawable.image6, R.drawable.image7, R.drawable.image8,
                R.drawable.image9, R.drawable.image10, R.drawable.image11,
                R.drawable.image12));
```

--

### Langkah Selanjutnya ...

```java
GridView gridview = (GridView) findViewById(R.id.gridview);

// Create a new ImageAdapter and set it as the Adapter for this GridView
gridview.setAdapter(new ImageAdapter(this, mThumbIdsFlowers));

// Set an setOnItemClickListener on the GridView
gridview.setOnItemClickListener(new OnItemClickListener() {
        new OnItemClickListener() { ... } );
```

---

