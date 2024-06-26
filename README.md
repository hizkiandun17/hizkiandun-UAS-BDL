# Manajemen Klinik Kesehatan

### Deskripsi Project
Proyek ini adalah sistem manajemen klinik kesehatan yang mencakup beberapa fitur utama, termasuk pengelolaaan pasien, dokter, janji temu, rekam medis, dan transaksi obat. Sistem ini dirancang untuk memberikan dukungan administratif dan operasional yang efisien bagi klinik kesehatan.

## Tujuan Proyek
Tujuan dari proyek manajemen klinik kesehatan ini adalah:

1. Meningkatkan Efisiensi Administratif:
   - Mempercepat dan mempermudah proses administrasi klinik dengan menyimpan data pasien, dokter, janji temu, dan rekam medis secara terpusat.

2. Meningkatkan Akurasi Data:
   - Mengurangi kesalahan manusia dalam pencatatan data medis dan administrasi melalui otomatisasi dan validasi data.

3. Mempermudah Akses Informasi:
   - Menyediakan akses cepat dan mudah ke informasi pasien, jadwal janji temu, dan riwayat medis, yang membantu tenaga medis dalam pengambilan keputusan.

4. Mengoptimalkan Pengelolaan Stok Obat:
   - Mengimplementasikan sistem otomatis untuk memantau dan mengelola stok obat, sehingga memastikan ketersediaan obat dan menghindari kekurangan stok.

5. Meningkatkan Kepuasan Pasien:
   - Meningkatkan pengalaman pasien dengan menyediakan sistem yang efisien untuk penjadwalan janji temu dan manajemen rekam medis, yang mengurangi waktu tunggu dan meningkatkan pelayanan.

6. Memfasilitasi Replikasi dan Backup Data:
   - Menerapkan strategi backup dan replikasi data untuk menjaga keamanan dan ketersediaan data, serta memastikan pemulihan data yang cepat dan efektif jika terjadi kegagalan sistem.

7. Menyediakan Laporan dan Analisis Data:
   - Menyediakan laporan agregat dan analisis data untuk membantu manajemen klinik dalam pengambilan keputusan strategis berdasarkan data yang akurat dan terkini.

Dengan mencapai tujuan-tujuan ini, proyek manajemen klinik kesehatan ini diharapkan dapat mendukung operasional klinik secara keseluruhan, meningkatkan efisiensi kerja, dan memberikan layanan yang lebih baik kepada pasien.


### Fitur Utama:
1. **Manajemen Pasien**: Menyimpan data pasien termasuk informasi pribadi dan kontak.
2. **Manajemen Dokter**: Menyimpan data dokter termasuk spesialisasi dan informasi kontak.
3. **Janji Temu**: Mengatur jadwal janji temu antara pasien dan dokter.
4. **Rekam Medis**: Menyimpan riwayat medis pasien.
5. **Transaksi Obat**: Mengelola transaksi obat dan mengupdate stok obat secara otomatis.

## Entity Relationship Diagram (ERD)
![Blank diagram](https://github.com/hizkiandun17/hizkiandun-UAS-BDL/assets/114422593/38ae09f5-8e99-41ef-9f20-df733b9cd2d1)

## Relasi
### Relasi One-to-Many (Satu ke Banyak)
1. Pasien ke JanjiTemu:
   *Penjelasan*: Setiap pasien dapat memiliki banyak janji temu.
   *ERD*: Pasien.id_pasien (PK) ke JanjiTemu.id_pasien (FK).

2. Dokter ke JanjiTemu:
   - *Penjelasan*: Setiap dokter dapat memiliki banyak janji temu.
   - *Relasi*: Satu dokter (one) -> Banyak janji temu (many).
   - *ERD*: Dokter.id_dokter (PK) ke JanjiTemu.id_dokter (FK).

3. Pasien ke RekamMedis:
   - *Penjelasan*: Setiap pasien dapat memiliki banyak rekam medis.
   - *Relasi*: Satu pasien (one) -> Banyak rekam medis (many).
   - *ERD*: Pasien.id_pasien (PK) ke RekamMedis.id_pasien (FK).

4. Dokter ke RekamMedis:
   - *Penjelasan*: Setiap dokter dapat memiliki banyak rekam medis yang dia buat.
   - *Relasi*: Satu dokter (one) -> Banyak rekam medis (many).
   - *ERD*: Dokter.id_dokter (PK) ke RekamMedis.id_dokter (FK).

5. Obat ke Transaksi:
   - *Penjelasan*: Setiap jenis obat dapat muncul di banyak transaksi.
   - *Relasi*: Satu obat (one) -> Banyak transaksi (many).
   - *ERD*: Obat.id_obat (PK) ke Transaksi.id_obat (FK).

### Relasi Many-to-One (Banyak ke Satu)
1. JanjiTemu ke Pasien:
   - *Penjelasan*: Banyak janji temu dapat dimiliki oleh satu pasien.
   - *Relasi*: Banyak janji temu (many) -> Satu pasien (one).
   - *ERD*: JanjiTemu.id_pasien (FK) ke Pasien.id_pasien (PK).

2. JanjiTemu ke Dokter:
   - *Penjelasan*: Banyak janji temu dapat dilakukan oleh satu dokter.
   - *Relasi*: Banyak janji temu (many) -> Satu dokter (one).
   - *ERD*: JanjiTemu.id_dokter (FK) ke Dokter.id_dokter (PK).

3. RekamMedis ke Pasien:
   - *Penjelasan*: Banyak rekam medis dapat dimiliki oleh satu pasien.
   - *Relasi*: Banyak rekam medis (many) -> Satu pasien (one).
   - *ERD*: RekamMedis.id_pasien (FK) ke Pasien.id_pasien (PK).

4. RekamMedis ke Dokter:
   - *Penjelasan*: Banyak rekam medis dapat dibuat oleh satu dokter.
   - *Relasi*: Banyak rekam medis (many) -> Satu dokter (one).
   - *ERD*: RekamMedis.id_dokter (FK) ke Dokter.id_dokter (PK).

5. Transaksi ke Obat:
   - *Penjelasan*: Banyak transaksi dapat melibatkan satu jenis obat.
   - *Relasi*: Banyak transaksi (many) -> Satu obat (one).
   - *ERD*: Transaksi.id_obat (FK) ke Obat.id_obat (PK).


## Skema Basis Data


### TABEL PASIEN
```sql
CREATE TABLE Pasien (
	id_pasien INT PRIMARY KEY,
	nama VARCHAR (100),
	alamat TEXT,
	tanggal_lahir DATE,
	jenis_kelamin CHAR(1),
	no_telepon VARCHAR(15)
);

```
### Penjelasan:
Tabel 'Pasien' menyimpan informasi tentang pasien, termasuk 'id_pasien' sebagai primary key, nama, alamat, tanggal lahir, jenis kelamin, dan nomor telepon.

### TABEL DOKTER
```sql

CREATE TABLE Dokter (
	id_dokter INT PRIMARY KEY,
	nama VARCHAR(100),
	spesialisasi VARCHAR(100),
	no_telepon VARCHAR(15)
);

```
### Penjelasan:
Tabel 'Dokter' menyimpan informasi tentang doketer, termasuk 'id_dokter' sebagai primary key, nama, spesialisasi, dan nomor telepon.

### TABEL JANJI TEMU
```sql
--TABLE JANJI TEMU
CREATE TABLE JanjiTemu (
	id_janjitemu INT PRIMARY KEY,
	id_pasien INT,
	id_dokter INT,
	tanggal DATE,
	waktu TIME,
	keluhan TEXT,
	FOREIGN KEY (id_pasien) REFERENCES Pasien(id_pasien),
	FOREIGN KEY (id_dokter) REFERENCES Dokter(id_dokter)
);

```
### Penjelasan:
Tabel 'JanjiTemu' menyimpan informasi tentang janji temu antara pasien dan dokter, termasuk 'id_janjitemu' sebagai primary key, 'id_pasien' dan 'id_dokter' sebagai foreign key yang merujuk ke tabel 'Pasien' dan 'Dokter', tanggal, waktu, dan keluhan.

### TABEL REKAM MEDIS
```sql

--TABLE REKAM MEDIS
CREATE TABLE RekamMedis (
	id_rekammedis INT PRIMARY KEY,
	id_pasien INT,
	id_dokter INT,
	tanggal DATE,
	diagnosis TEXT,
	terapi TEXT,
	FOREIGN KEY (id_pasien) REFERENCES Pasien(id_pasien),
	FOREIGN KEY (id_dokter) REFERENCES Dokter(id_dokter)
);

```
### Penjelasan:
Tabel 'RekamMedis' menyimpan riwayat medis pasien, termasuk 'id_rekammedis' sebagai primary key, 'id_pasien' dan 'id_dokter' sebagai foreign key yang merujuk ke tabel 'Pasien' dan 'Dokter', tanggal, diagnosis, dan terapi.

### TABEL OBAT
```sql
-- TABLE OBAT
CREATE TABLE Obat (
	id_obat INT PRIMARY KEY,
	nama_obat VARCHAR(100),
	stok INT
);
```
### Penjelasan: 
Tabel 'Obat' menyimpan informasi tentang obat, termasuk 'id_obat' sebagai primary key, nama obat, dan stok.

### TABEL TRANSAKSI
```sql
-- TABLE TRANSAKSI
CREATE TABLE Transaksi (
	id_transaksi INT PRIMARY KEY ,
	id_obat INT,
	jumlah INT,
	FOREIGN KEY (id_obat) REFERENCES Obat(id_obat)
);
```
### Penjelasan:
Tabel 'Transaksi' menyimpan informasi tentang transaksi obat, termasuk 'id_transaksi' sebagai primary key, 'id_obat' sebagai foreign key yang merujuk ke tabel 'obat', dan jumlah obat yang ditransaksikan

### RELASI
1. Tabel 'JanjiTemu' memiliki relasi dengan tabel 'Pasien' dan 'Dokter'.
2. Tabel 'RekamMedis' memiliki relasi dengan tabel 'Pasien' dan 'Dokter'.
3. Tabel 'Transaksi' memiliki relasi dengan tabel 'Obat'.

## PROSES TRIGGER & VIEW
1. Trigger untuk update stok obat ketika ada transaksi
```sql
DELIMITER $$

CREATE TRIGGER update_stok_obat
AFTER INSERT ON Transaksi
FOR EACH ROW
BEGIN 
    UPDATE Obat
    SET stok = stok - NEW.jumlah
    WHERE id_obat = NEW.id_obat;
 END;
 $$
 
 DELIMITER;
```
#### Penjelasan:
Trigger ini diaktifkan setiap kali ada insert baru pada tabel 'Transaksi'. Trigger ini secara otomatis mengurangi stok obat pada tabel 'Obat' berdasarkan jumlah obat yang ditransaksikan.

2. View untuk melihat jumlah janji tamu per dokter
``` sql
CREATE VIEW View_JanjiTemuPerDokter AS
SELECT Dokter.nama, COUNT(JanjiTemu.id_janjitemu) AS jumlah_janjitemu
FROM Dokter 
LEFT JOIN JanjiTemu ON Dokter.id_dokter = JanjiTemu.id_dokter
GROUP BY Dokter.nama;
```
#### Penjelasan:
View ini menggabungkan tabel 'Dokter' dengan tabel 'JanjiTemu' untuk menghitung jumlah janji temu yang dimiliki setiap dokter. Hasilnya menampilkan nama dokter dan jumlah temu mereka.

### OPERASI AGREGAT
Operasi agregat ini digunakan untuk menghitung jumlah pasien per bulan berdasarkan janji temu.

```sql
SELECT 
    EXTRACT(MONTH FROM tanggal) AS bulan, 
    COUNT(*) AS jumlah_pasien 
FROM 
    JanjiTemu 
GROUP BY 
    EXTRACT(MONTH FROM tanggal);
```
#### Penjelasan:
Query ini menghitung jumlah janji temu yang terjadi setiap bulan. Kolom 'tanggal' diekstrak bulannya dan kemudian dikelompokkan berdasarkan bulan tersebut, sehingga menghasilkan jumlah pasien per bulan.

### INDEKS
Indeks ini ditambahkan untuk meningkatkan performa pencarian pada tabel 'Pasien' dan 'Dokter'

```sql
CREATE INDEX idx_nama_pasien ON Pasien(nama);
CREATE INDEX idx_nama_dokter ON Dokter(nama);
```
#### Penjelasan:
Indeks ini dibuat pada kolom 'nama' di tabel 'Pasien' dan 'Dokter' untuk mempercepat operasi pencarian dan query yang menggunakan kolom tersebut.

### LEFT JOIN
Menampilkan daftar pasien beserta janji temu mereka dan nama dokter.

```sql
SELECT Pasien.nama AS nama_pasien, JanjiTemu.tanggal, Dokter.nama AS nama_dokter
FROM Pasien
LEFT JOIN JanjiTemu ON Pasien.id_pasien = JanjiTemu.id_pasien
LEFT JOIN Dokter ON JanjiTemu.id_dokter = Dokter.id_dokter;
```
#### Penjelasan:
Query ini menggunakan 'LEFT JOIN' untuk menggabungkan tabel 'Pasien', 'JanjiTemu', dan 'Dokter', untuk menampilkan semua pasien beserta janji tamu mereka, termasuk yang tidak memiliki janji temu.

### INNER JOIN
Menampilkan daftar pasien beserta janji temu mereka dan nama dokter.

```sql
SELECT Pasien.nama, Dokter.nama, JanjiTemu.tanggal
FROM JanjiTemu
INNER JOIN Pasien ON JanjiTemu.id_pasien = Pasien.id_pasien
INNER JOIN Dokter ON JanjiTemu.id_dokter = Dokter.id_dokter;
```
#### Penjelasan:
Query ini menggunakan 'INNER JOIN' untuk menampilkan daftar pasien yang memiliki janji temu dengan dokter, hanya menampilkan data yang memiliki relasi di kedua tabel.

### SUBQUERY
Menampilkan nama dan spesialisasi dokter yang memiliki janji temu pada tanggal tertentu.

```sql
SELECT nama, spesialisasi
FROM Dokter
WHERE id_dokter IN (SELECT id_dokter FROM JanjiTemu WHERE tanggal = '2024-0-26');
```
#### Penjelasan:
Query ini menggunakan subquery untuk menampilkan nama dan spesialisasi dokter yang memiliki janji temu pada tanggal tertentu ('2024-06-26').

### HAVING
Menampilkan jumlah janji per pasien yang memiliki lebih dari satu janji.
```sql
SELECT id_pasien, COUNT(*) AS jumlah_janji
FROM JanjiTemu
GROUP BY id_pasien
HAVING COUNT(*) > 1;
```
#### Penjelasan:
Query ini mengelompokkan janji temu berdasarkan 'id_pasien' dan menggunakan klausa 'HAVING' untuk menampilkan hanya pasien yang memiliki lebih dari satu janji temu.

### WILDCARD
Menampilkan semua data pasien yang namanya mengandung 'Siti'.
```sql
SELECT * FROM Pasien
WHERE nama LIKE '%Siti%';

```
#### Penjelasan:
Query ini menggunakan operator 'LIKE' dengan wildcard '%' untuk menampilkan semua data pasien yang namanya mengandung 'Siti'.

## Kesimpulan
Proyek manajemen klinik kesehatan ini dirancang untuk meningkatkan efisiensi dan akurasi dalam pengelolaan data pasien, dokter, janji temu, rekam medis, dan transaksi obat melalui sistem basis data yang terstruktur dengan baik. Melalui implementasi relasi one-to-many dan many-to-one, sistem ini memastikan setiap entitas terkait dengan benar, memudahkan akses dan integritas data. Penggunaan trigger untuk mengelola stok obat secara otomatis dan view untuk laporan jumlah janji temu per dokter lebih lanjut meningkatkan fungsionalitas sistem. Dengan strategi backup dan replikasi data, proyek ini juga menjamin keamanan dan ketersediaan data, memberikan dukungan komprehensif bagi operasional klinik kesehatan untuk memberikan pelayanan yang lebih baik dan efisien kepada pasien.






