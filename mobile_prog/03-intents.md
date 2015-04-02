# <div class="highlight-blue">Section 03</div>

### Intent &amp; BroadcastReceivers

by: [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Kenalan dengan Intent

- Intent merupakan komponen penghubung activity dalam Android.
- Intent dapat digunakan untuk memanggil activity lain
- dan juga menerima parameter yang dikirimkan oleh activity 
  lain (ngirimnya ya pake Intent juga)

--

### Contoh Intent Sederhana

Contoh Intent yang memanggil activity lain dengan mendefinisikan Class-nya

```java
Intent it = null;
it = new Intent(this, HelloKitty.class);
```

---

### Intent Field

- **Action**: String yang merepresentasikan aksi yang diinginkan
- **Data**: data yang diasosiasikan terhadap Intent
- **Category**: informasi tambahan untuk menentukan komponen yang dapat meng-handle intent
- **Type**: spesifikasi MIME type dari data intent
- **Component**: menentukan komponen yang menerima sebuah intent
- **Extras**: informasi tambahan yang berhubungan dengan intent yang dikirim dalam bentuk key-value pairs
- **Flag**: untuk menspesifikasikan bagaimana intent di-handle

--

### Action

- ```ACTION_DIAL``` : untuk memanggil nomer telepon
- ```ACTION_EDIT``` : menampilkan data yang akan diedit
- ```ACTION_SYNC``` : singkronisasi dengan server
- ```ACTION_MAIN``` : menjadikan activity yang pertama dipanggil

--

### Data

- Data nomer yang akan dipanggil melalui telepon
```
Intent newInt = new Intent ( Intent.ACTION_DIAL, Uri.parse("tel:+15555555555"));
```

- Lokasi yang akan ditampilkan melalui peta
```
Uri.parse(“geo:0,0?q=1600+Pennsylvania+Ave+Washington+DC”)
```

--

### Category

- ```category_browsable``` : dapat ditangani dengan membuka browser
- ```category_launcher``` : dapat menentukan activity yang dipanggil pertama

--

### Component

- untuk memanggil activity tertentu secara pasti
```
Intent newInt = Intent(Context packageContext, Class<?> cls);
```
- atau dengan menggunakan method
  - ```setComponent()```
  - ```setClass()```
  - ```setClassName()```
  
--

### Extra

Contoh:

```
Intent newInt = new Intent(Intent.ACTION_SEND);
newInt.putExtra(android.content.Intent.EXTRA_EMAIL, 
new String[]{
    “aporter@cs.umd.edu”, “ceo@microsoft.com”,
    “potus@whitehouse.gov”,“mozart@musician.org”
});
```

Cara yang lain: 

```
putExtra(String name, String value);
putExtra(String name, float[] value);
```

---

### Invocation

- ```startActivity()```
- ```startActivityForResult()```
- ```startService()```
- ```bindService()```
- ```sendBroadcast()```
- ```sendOrderedBroadcast()```
- ```sendStickyBroadcast()```

---

### Explicit &amp; Implicit

- Explicit intent adalah intent yang dengan jelas memanggil nama komponen
  yang diinginkan untuk meng-handle intent tersebut.
- sedangkan Implicit intent adalah yang tidak secara jelas menentukan
  nama komponen (activity) yang dipanggil, namun hanya memberikan spesifikasi saja,
  kemudian android yang akan menentukan activity mana yang cocok.
  
--

### Intent Resolution Process

Proses untuk menentukan komponen mana yang cocok untuk intent yang diberikan:

- Langkah 1: ```Intent``` memanggil proses yang diinginkan
- Langkah 2: ```IntentFilter``` menentukan operasi apa yang dapat ditangani
  oleh activity tertentu. Dapat dispesifikasikan melalui Android Manifest
  atau *programmatically*.
- Langkah 3: Android mencari di database aplikasi terinstall apa saja yang dapat
  menangani intent tersebut.
  
--

### IntentFilter

Konfigurasi manifest untuk memberitahukan pada Android bahwa aplikasi tersebut
memiliki activity yang dadpt digunakan untuk meng-handle sebuah operasi:

```
<!-- This activity handles "SEND" actions with text data -->
<intent-filter>
    <action android:name="android.intent.action.SEND"/>
    <category android:name="android.intent.category.DEFAULT"/>
    <data android:mimeType="text/plain"/>
</intent-filter>
<!-- This activity handles "SEND" and "SEND_MULTIPLE" with media data -->
<intent-filter>
    <action android:name="android.intent.action.SEND"/>
    <action android:name="android.intent.action.SEND_MULTIPLE"/>
    <category android:name="android.intent.category.DEFAULT"/>
    <data android:mimeType="application/vnd.google.panorama360+jpg"/>
    <data android:mimeType="image/*"/>
    <data android:mimeType="video/*"/>
</intent-filter>
```

---

### BroadcastReceiver



### 