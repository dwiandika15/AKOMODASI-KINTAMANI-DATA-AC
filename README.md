# AKOMODASI-KINTAMANI-DATA-AC
# Nama: I Kadek Dwi Andika
# NIM: 2501010085

# 1. Pendahuluan
Praktikum ini bertujuan memperoleh data akomodasi di Kecamatan Kintamani dari OpenStreetMap (OSM), menyimpan
data mentah, mengubahnya menjadi tabel CSV, serta memeriksa kualitas dan kelengkapan data. Data OSM merupakan
data yang dihimpun oleh kontributor sehingga kelengkapan dan ketepatan atribut dapat berbeda-beda.

# 2. Metode Akuisisi Data 
Pengambilan data dilakukan menggunakan Overpass API dengan area administratif Kintamani dan filter tag tourism untuk kategori hotel, guest_house, hostel, motel, apartment, dan chalet. Respons API disimpan dalam format JSON sebagai data mentah, kemudian diratakan menjadi tabel menggunakan Python dan pandas. Data hasil perataan disimpan dalam format CSV. Endpoint yang digunakan: https://overpass-api.de/api/interpreter. Pengambilan data dilakukan pada 11 November 2026. File mentah disimpan dengan nama osm_akomodasi_kintamani_20261111_092507.json.

# 3. Hasil Akuisisi Data
Hasil akuisisi memperoleh 32 objek akomodasi. Data mencakup beberapa jenis akomodasi dengan jumlah sebagaimana
ditampilkan pada tabel berikut.
| No. | Jenis Akomodasi | Jumlah |
|-----|-----------------|--------|
| 1   | Hotel           | 16     |
| 2   | Guest House     | 9      |
| 3   | Hostel          | 4      |
| 4   | Chalet          | 2      |
| 5   | Motel           | 1      |
|     | **Total**       | **32** |

<img width="1296" height="576" alt="image" src="https://github.com/user-attachments/assets/6bcbca1f-5ed7-4c41-98e4-88e419144be6" />
Kategori terbanyak adalah hotel sebanyak 16 data, diikuti guest house sebanyak 9 data. Kategori hostel berjumlah 4,
chalet 2, dan motel 1. Jenis-jenis tersebut merupakan kategori yang tercatat pada tag tourism di OpenStreetMap.

# 4. Pemeriksaan Kualitas Data
| No. | Pemeriksaan Hasil | Jumlah |
|-----|-------------------|--------|
| 1 | Jumlah seluruh data | 32 |
| 2 | Data duplikat berdasarkan osm_type dan osm_id | 0 |
| 3 | Data tanpa nama | 1 |
| 4 | Koordinat kosong | 0 |
| 5 | Kolom desa kosong | 32 |
| 6 | Kolom bintang kosong | 31 |
| 7 | Kolom jumlah_kamar kosong | 30 |
| 8 | Kolom website kosong | 30 |
Pemeriksaan koordinat menunjukkan latitude berada pada rentang -8.2837958 hingga -8.2189435 dan longitude pada
rentang 115.2545822 hingga 115.4129261. Tidak ditemukan koordinat kosong. Atribut desa, bintang, jumlah kamar, dan
website yang kosong menunjukkan bahwa informasi tersebut belum tersedia pada tag OSM untuk sebagian besar objek;
kekosongan ini tidak otomatis berarti datanya salah.

# 5. Perbandingan dengan Data BPS
Berdasarkan publikasi Kecamatan Kintamani Dalam Angka 2023 yang diperiksa dalam praktikum, tercatat 19 hotel dan 39
penginapan, sehingga totalnya 58 akomodasi. Sementara itu, akuisisi OpenStreetMap pada 2026 memperoleh 32 objek.
| No. | Sumber Data | Tahun | Jumlah |
|-----|-------------|-------|--------|
| 1 | OpenStreetMap | 2026 | 32 |
| 2 | BPS Kecamatan Kintamani | 2023 | 58 |
Perbandingan sederhana jumlah data adalah 32 / 58 × 100% = 55,17%. Angka ini hanya rasio jumlah OSM terhadap
jumlah pada publikasi BPS, bukan persentase kelengkapan atau cakupan yang pasti. Tahun pengumpulan berbeda dan
pengelompokan jenis akomodasi pada kedua sumber mungkin tidak sama.
# 6. Verifikasi Manual Sampel
Sebanyak 10 sampel dipilih secara acak dari tabel menggunakan pandas (sample dengan random_state=42).
Penelusuran awal menemukan bukti yang mendukung keberadaan beberapa nama melalui direktori pariwisata pemerintah
dan situs akomodasi. Namun, tidak seluruh sampel memiliki sumber independen yang cukup untuk mengonfirmasi semua
aspek sekaligus.
| No. | Sampel | Catatan Hasil Penelusuran |
|-----|--------|---------------------------|
| 1 | Caldera | Ditemukan pada direktori pariwisata Bali sebagai Caldera Hotel & Restaurant. |
| 2 | Segara Hotel | Ditemukan pada direktori pariwisata Bali sebagai Segara Hotel & Restaurant. |
| 3 | The Lava Bali and Hot Spring | Ditemukan pada direktori pariwisata Bali sebagai cottage. |
| 4 | Villa Jempana | Website akomodasi ditemukan; lokasi disebut di kawasan Danau Batur, Kintamani. |
| 5 | Bunbulan Hill Hostel | Ada sumber yang menyebut keberadaan hostel; titik OSM bernama 'Entrance to:' sehingga objek perlu ditinjau. |
| 6 | 5 sampel lainnya | Belum memperoleh bukti independen yang cukup dalam penelusuran awal. |
Catatan: hasil penelusuran awal ini perlu dilengkapi dengan sumber bukti yang diizinkan oleh instruksi praktikum. Google
Maps dan situs pemesanan yang dilarang tidak digunakan sebagai bukti verifikasi. Nama akomodasi yang ditemukan
belum otomatis membuktikan bahwa jenis dan koordinat titik OSM juga tepat.

# 7. Kendala, Etika, dan Keterbatasan
Kendala utama adalah sejumlah atribut tidak tersedia pada data OSM, terutama desa, bintang, jumlah kamar, dan
website. Terdapat satu objek tanpa nama dan satu objek sampel dengan nama 'Entrance to: Bunbulan Hill Hostel' yang
perlu diperiksa karena mungkin merepresentasikan pintu masuk, bukan objek akomodasi. Data OSM juga bergantung
pada kontribusi sukarela sehingga tidak selalu mencakup seluruh akomodasi yang ada.
Dalam praktikum ini, data mentah JSON disimpan tanpa perubahan, hasil olahan disimpan sebagai CSV, dan
dokumentasi provenance serta data dictionary dibuat. Akuisisi tidak ditujukan untuk mengumpulkan nomor telepon, alamat
email, atau akun media sosial. Atribusi yang dicantumkan adalah © OpenStreetMap contributors dan data mengikuti Open
Database License (ODbL).

# 8. Refleksi
Melalui praktikum ini, saya memahami bahwa proses akuisisi data bukan hanya mengambil informasi dari API, tetapi juga perlu
memperhatikan sumber, cara penyimpanan, kualitas, dan etika penggunaan data. Saya belajar menggunakan Overpass API
untuk mengambil data OpenStreetMap, menyimpan respons mentah dalam JSON, lalu mengubahnya menjadi tabel CSV
menggunakan Python. Dari pemeriksaan kualitas, saya mengetahui bahwa data dapat memiliki nilai kosong meskipun proses
akuisisi berhasil. Contohnya, kolom desa belum terisi pada seluruh data, sedangkan beberapa informasi seperti bintang dan
jumlah kamar juga banyak yang belum tersedia. Perbandingan dengan BPS membantu saya memahami bahwa jumlah dari dua
sumber tidak selalu dapat dibandingkan secara langsung karena perbedaan tahun dan kategori. Saya juga belajar bahwa
verifikasi sampel harus menggunakan sumber yang diperbolehkan dan tidak boleh menyatakan data valid jika buktinya belum
cukup. Ke depannya, saya perlu memperbaiki dokumentasi sumber verifikasi dan menjelaskan keterbatasan data secara
terbuka agar hasil akuisisi lebih dapat dipercaya.

# 9. Berkas Pendukung

| No. | Berkas | Keterangan |
|-----|--------|------------|
| 1 | `data/raw/osm_akomodasi_kintamani_20261111_092507.json` | Respons mentah Overpass API |
| 2 | `data/interim/akomodasi_kintamani.csv` | Data hasil perataan |
| 3 | `docs/provenance.json` | Informasi asal-usul data dan hash MD5 |
| 4 | `docs/data_dictionary.csv` | Keterangan kolom dataset |
| 5 | `docs/data_ethics_checklist.csv` | Checklist etika akuisisi |
| 6 | `docs/perbandingan_bps.csv` | Perbandingan jumlah OSM dan BPS |
Sumber: OpenStreetMap melalui Overpass API; Badan Pusat Statistik Kabupaten Bangli, Kecamatan Kintamani Dalam
Angka 2023; Direktori Pariwisata Provinsi Bali 2023; dan website resmi Villa Jempana. Atribusi data OSM: ©
OpenStreetMap contributors.
