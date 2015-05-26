## <div class="highlight-blue">Section 05</div>

### Penyimpanan Data Lokal dengan SQLite

by: [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Database Lokal

- Database lokal memiliki sifat yang cukup berbeda jika dibandingkan 
  dengan database server seperti MySQL
- Pada database server, manajemen database terpisah dari aplikasi
- PHP dan MySQL memiliki servis yang berbeda
- Namun pada database lokal, manajemen database terletak di dalam aplikasi

--

### Database Lokal (2)

- Ada banyak jenis database lokal antara lain, dan yang paling banyak 
  digunakan adalah SQLite
- Karena bersifat lokal, kita tidak perlu menginstall software lain
- Namun database di-simpan pada sebuah file di penyimpanan lokal

---

### Langkah Database Lokal pada Android

- Membuat class model
- Membuat class Handler
  - Extend class SQLiteOpenHelper
  - Override method onCreate &amp; onUpgrade
  - Membuat method CRUD	
- Membuat class pemanggilnya

---

### File / Class Model

- Untuk membuat class Model, kita cukup membuat Class yang memiliki atribut
  sesuai dengan kolom yang dikehendaki
- Kemudian untuk memudahkan pengaksesan properti tabel buat juga atribut static
  TABLE dan masing-masing nama kolom yang dikehendaki
- Buat juga constructor untuk memudahkan membuat object baru

---

### Class Handler

- Class ini melakukan extends terhadap SQLiteOpenHelper
- Gunakan constructor untuk mendefinisikan nama database dan versi dari DB kita 
  (ingat SQLite tidak perlu koneksi, jadi kita tidak memerlukan username &amp; password)
  ```super(context, DATABASE_NAME, null, DATABASE_VERSION);```
- method onCreate akan dipanggil saat database dibuat, oleh karena itu, kta juga
  harus mengeksekusi perinta query SQL (DDL) untuk membuat tabel yang kita perlukan di sini
- sedangkan method onUpgrade akan dipanggil saat kita mengganti versi dari DB kita,
  untuk lebih mudahnya eksekusi peritah drop dan panggil method onCreate()

--

### CRUD Operations

- Untuk melakukan operasi baca tulis di SQLite, kita harus memanggil method
  ```getWritableDatabase()``` dan ```getReadableDatabase()``` yang disimpan
  pada variabel bertipe data ```SQLiteDatabase```
- Data yang akan dituliskan dalam database juga harus disimpan pada variabel
  bertipe data ```ContentValues```
- Sedangkan data yang didapat dari hasil query (DML) database disimpan pada
  varibel bertipe data ```Cursor```

--

### CRUD Operations (Insert)

```
public void addContact(Contact contact) {
    SQLiteDatabase db = this.getWritableDatabase();
 
    ContentValues values = new ContentValues();
    values.put(KEY_NAME, contact.getName()); // Contact Name
    values.put(KEY_PH_NO, contact.getPhoneNumber()); // Contact Phone Number
 
    // Inserting Row
    db.insert(TABLE_CONTACTS, null, values);
    db.close(); // Closing database connection
}
```

--

### CRUD Operations (Select)

```
public List<Contact> getAllContacts() {
    List<Contact> contactList = new ArrayList<Contact>();
    // Select All Query
    String selectQuery = "SELECT  * FROM " + TABLE_CONTACTS;
 
    SQLiteDatabase db = this.getWritableDatabase();
    Cursor cursor = db.rawQuery(selectQuery, null);
 
    // looping through all rows and adding to list
    if (cursor.moveToFirst()) {
        do {
            Contact contact = new Contact();
            contact.setID(Integer.parseInt(cursor.getString(0)));
            contact.setName(cursor.getString(1));
            contact.setPhoneNumber(cursor.getString(2));
            // Adding contact to list
            contactList.add(contact);
        } while (cursor.moveToNext());
    }
 
    // return contact list
    return contactList;
}
```

--

### CRUD Operations (Update)

```
public int updateContact(Contact contact) {
    SQLiteDatabase db = this.getWritableDatabase();
 
    ContentValues values = new ContentValues();
    values.put(KEY_NAME, contact.getName());
    values.put(KEY_PH_NO, contact.getPhoneNumber());
 
    // updating row
    return db.update(TABLE_CONTACTS, values, KEY_ID + " = ?",
            new String[] { String.valueOf(contact.getID()) });
}
```

--

### CRUD Operations (Delete)

```
public void deleteContact(Contact contact) {
    SQLiteDatabase db = this.getWritableDatabase();
    db.delete(TABLE_CONTACTS, KEY_ID + " = ?",
            new String[] { String.valueOf(contact.getID()) });
    db.close();
}
```

---

## Menggabungkan
### SQLite dengan REST Service 