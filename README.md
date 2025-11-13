# Tugas-PBO-Pertemuan-Ketigabelas
Membuat Halaman Login, Register dan Lupa Password yang  Tersimpan di Database Postgresql diNetbeans. 
# JAVA PERSISTENCE API (JPA) 
Java Persistence API (JPA) adalah spesifikasi resmi Java yang digunakan untuk 
memetakan data dari database relasional ke dalam bentuk objek Java (Object Relational 
Mapping/ORM). Dengan JPA, pengembang dapat mengelola, menyimpan, dan mengambil 
data dari database tanpa perlu menulis banyak kode SQL secara langsung. 
JPA bekerja dengan cara menghubungkan kelas Java yang disebut Entity dengan 
tabel di dalam database. Setiap objek dari kelas tersebut mewakili satu baris data di tabel. 
Proses pengelolaan data dilakukan melalui EntityManager, yang bertugas untuk 
menambah, memperbarui, mencari, dan menghapus data. 
Selain itu, JPA juga menggunakan JPQL (Java Persistence Query Language), 
yaitu bahasa query yang mirip dengan SQL tetapi bekerja menggunakan nama kelas dan 
atribut, bukan nama tabel dan kolom. Konfigurasi koneksi dan pengaturan entitas JPA 
biasanya disimpan dalam file persistence.xml yang mendefinisikan unit persistensi. 
JPA hanya merupakan spesifikasi, sehingga untuk menggunakannya dibutuhkan 
implementasi seperti Hibernate, EclipseLink, atau OpenJPA. Dengan JPA, pengembangan 
aplikasi menjadi lebih efisien karena data dapat diolah langsung melalui objek Java tanpa 
perlu berinteraksi langsung dengan perintah SQL, serta mendukung berbagai sistem 
database dengan sedikit perubahan kode. 
# HALAMAN LOGIN 
Halaman login merupakan halaman awal yang digunakan pengguna untuk mengakses sistem 
dengan memasukkan username dan password. Pada aplikasi ini, proses autentikasi dilakukan 
dengan menghubungkan halaman login ke database menggunakan JPA (Java Persistence API). JPA 
berfungsi sebagai penghubung antara program Java dan database, sehingga data pengguna dapat 
diakses atau diverifikasi secara langsung melalui entitas (entity class). 
Pada implementasinya di NetBeans, dibuat kelas entitas bernama Login yang berisi 
atribut seperti id, username, dan password. Kelas ini diberi anotasi @Entity agar dikenali 
sebagai representasi tabel pada database. JPA akan secara otomatis memetakan kelas 
tersebut ke tabel yang ada di database, misalnya tabel login. 
Saat pengguna menekan tombol Login, sistem akan menjalankan query menggunakan 
EntityManager untuk memeriksa apakah kombinasi username dan password yang 
dimasukkan 
sesuai 
dengan 
data 
yang 
tersimpan 
di 
database. 
Jika data valid, pengguna akan diarahkan ke halaman utama aplikasi. Namun, jika data 
tidak ditemukan atau salah, maka sistem akan menampilkan pesan kesalahan. 
Dengan pendekatan ini, proses login menjadi lebih aman dan efisien karena seluruh 
interaksi data dikelola oleh JPA tanpa perlu menulis query SQL secara manual. Selain itu, 
penggunaan JPA memudahkan pengembangan aplikasi karena mendukung konsep Object 
Relational Mapping (ORM), yang memungkinkan objek Java langsung terhubung dengan 
tabel database.
# Langkah - langkah 
1. Persiapan Database di PostgreSQL. Buka pgAdmin → klik kanan pada “Databases” → pilih Create > Database. Beri nama database (misalnya: db_login) → klik Save. Buat tabel login dengan kolom: id (Primary Key, serial), username (varchar), password (varchar)
2. Koneksi Database ke NetBeans. Buka NetBeans → tab Services → pilih Databases. Klik kanan pada Drivers → PostgreSQL → Connect Using... Isi: Database: db_login. Username dan Password pgAdmin. Klik Test Connection untuk memastikan koneksi berhasil. Salin JDBC URL untuk konfigurasi JPA nanti.
3. Membuat Entity Classes dari Database. Klik kanan pada package proyek → New → Entity Classes from Database. Pilih Data Source sesuai koneksi database PostgreSQL. Pindahkan tabel login ke sisi kanan (Selected Tables). Centang: Generate Named Query Annotation for Persistent Field. Use Column Names in Relationship. Klik Finish.→ NetBeans akan membuat kelas Login.java dengan anotasi @Entity.
4. Membuat File Persistence. Klik kanan proyek → New → Other → Persistence → Persistence Unit. Beri nama unit (misalnya LoginPU). Pilih provider: EclipseLink dan database: PostgreSQL. Simpan file persistence.xml di folder META-INF.
5. Menambahkan Library. Klik kanan Libraries → Add Library → PostgreSQL JDBC Driver. Tambahkan juga JasperReports jika diperlukan (untuk laporan).
6. Membuat Package dan Form GUI. Buat package baru, misalnya: pertemuan13. Tambahkan empat JFrame Form: LoginForm.java, RegisterForm.java, ForgotPassword.java, MainDashboard.java
7. Desain dan Pemrograman Form Login. Tambahkan komponen: TextField untuk username PasswordField untuk password. Button Login, Register, dan Lupa Password Tambahkan event handler pada button Login: Gunakan EntityManager untuk mengambil data dari tabel login. Cocokkan username dan password dengan input pengguna .Jika cocok → tampilkan MainDashboard. Jika salah → tampilkan pesan “Login gagal”
8. Membuat Fitur Register dan Reset Password. RegisterForm.java → memungkinkan pengguna membuat akun baru dengan menyimpan data ke tabel login. ForgotPassword.java → pengguna memasukkan username untuk diarahkan ke form reset. ResetPassword.java → mengganti password lama dengan yang baru di database.
9. Membuat Main Class. Tambahkan file Main.java. Atur tampilan Nimbus Look and Feel. Jalankan new LoginForm().setVisible(true);
10. Uji Coba Aplikasi. Jalankan proyek. Tes: Login dengan data benar → masuk dashboard.Login salah → muncul pesan gagal. Lupa password → bisa reset. Register → akun tersimpan di database.
