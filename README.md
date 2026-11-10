## Holaaaaaaa
# Sistem Manajemen Kost Berbasis OOP (Python)

Perancangan sistem manajemen kost sederhana berbasis Python dengan pendekatan **Object-Oriented Programming (OOP)**. Proyek ini dikerjakan untuk mata kuliah Pemrograman Berorientasi Objek, Program Studi S1 Sistem Informasi, Fakultas Sains dan Teknologi, Universitas Jambi.

## Latar Belakang
Pengelolaan kost secara manual rawan salah catat, sulit memantau ketersediaan kamar, dan datanya cenderung tidak teratur. Sistem ini memodelkan entitas seperti pemilik kost, kamar, penghuni, dan penyewaan sebagai class dan object agar pengelolaan data lebih rapi dan penyewaan ganda dapat dicegah.

## Tujuan
- Mengidentifikasi kebutuhan fungsional dan nonfungsional sistem.
- Merancang struktur class beserta atribut dan method-nya.
- Merancang hubungan dan interaksi antarobjek.
- Menyiapkan desain sebagai dasar implementasi di Python.

## Fitur
Program dirancang berbasis konsol dengan menu utama berikut:
1. Tambah kamar
2. Lihat daftar kamar
3. Daftarkan penghuni
4. Sewa kamar
5. Akhiri sewa
6. Laporan penyewaan
0. Keluar

## Kebutuhan Sistem
### Kebutuhan Fungsional
| Kode | Kebutuhan        | Deskripsi                                                                          |
|------|------------------|------------------------------------------------------------------------------------|
| F01  | Data Kamar       | Menyimpan dan menampilkan informasi kamar (nomor, tipe, harga sewa, status).       |
| F02  | Data Penghuni    | Menyimpan informasi penghuni kost.                                                 |
| F03  | Penyewaan        | Penghuni dapat menyewa kamar yang tersedia.                                        |
| F04  | Pengakhiran sewa | Memproses penghuni yang keluar dan mengembalikan status kamar menjadi tersedia.    |
| F05  | Validasi         | Menolak penyewaan jika kamar tidak tersedia.                                       |

### Kebutuhan Nonfungsional
- Dikembangkan menggunakan Python.
- Menerapkan prinsip OOP.
- Data divalidasi untuk menghindari nilai yang tidak sesuai.
- Informasi dan pesan kesalahan mudah dipahami.
- Kode dibagi ke dalam modul agar mudah dipelihara.

## Desain Clas
Semua atribut dirancang **private** (enkapsulasi) dan diakses lewat method agar data tervalidasi.
| Class         | Tanggung Jawab                                         | Atribut                                          | Method                                                        |
|---------------|--------------------------------------------------------|--------------------------------------------------|---------------------------------------------------------------|
| `PemilikKost` | Pemilik/admin yang mengelola sistem kost               | `nama_pemilik`, `no_telpon`                      | `tambah_kamar()`, `tambah_penghuni()`, `lihat_laporan_penyewaan()` |
| `Kamar`       | Kamar kost yang dikelola                               | `nomor_kamar`, `tipe`, `harga_sewa`, `status`    | `tersedia()`, `tempati()`, `kosongkan()`                      |
| `Penghuni`    | Penghuni yang dapat menyewa kamar                      | `id_penghuni`, `nama`, `no_telpon`               | `sewa_kamar()`, `keluar_kamar()`, `daftar_penghuni()`         |
| `Penyewaan`   | Transaksi penyewaan kamar                              | `penghuni`, `kamar`, `tanggal_masuk`, `tanggal_keluar` | `proses_penyewaan()`, `proses_pengakhiran()`            |

## Alur Kerja Singkat
Program dijalankan dari `main.py`, menampilkan menu, menjalankan fitur yang dipilih, lalu kembali ke menu sampai pengguna memilih `0`.
- **Tambah kamar:** ditolak jika nomor kamar sudah ada atau harga sewa negatif. Kamar baru berstatus `tersedia`.
- **Daftarkan penghuni:** data divalidasi, lalu penghuni dibuat dengan ID unik.
- **Sewa kamar:** penghuni harus sudah terdaftar dan kamar harus tersedia. Jika berhasil, objek `Penyewaan` dibuat dan status kamar menjadi `terisi`. Kamar yang sudah terisi ditolak (F05).
- **Akhiri sewa:** hanya berlaku untuk kamar dengan penyewaan aktif. Tanggal keluar dicatat dan status kamar kembali `tersedia`.
- **Laporan penyewaan:** menampilkan riwayat (penghuni, kamar, tanggal masuk, tanggal keluar).

## Rencana Struktur File
```
.
├── main.py          # Titik masuk program: menu konsol dan pemanggilan method
├── kamar.py         # Class Kamar (atribut private, getter/setter dengan validasi)
├── penghuni.py      # Class Penghuni
├── penyewaan.py     # Class Penyewaan (menghubungkan Penghuni dan Kamar)
├── pemilik_kost.py  # Class PemilikKost (daftar kamar dan riwayat penyewaan)
└── validasi.py      # Fungsi validasi: nomor telepon, harga sewa positif, format tanggal
```

## Tim
**Kelompok 7** (Program Studi S1 Sistem Informasi, Universitas Jambi)
| Nama                          | NIM        |
|-------------------------------|------------|
| Ahmad Alfaro Edro Ramadhan    | F1E125063  |
| Meisyta Marsha Winola         | F1E125025  |
| Devy Melisa Putri             | F1E125075  |
| Muhammad Faisol Hakim         | F1E125027  |

**Dosen Pengampu:** Edi Saputra, S.T., M.Sc.; Pariyadi, S.Kom., M.Kom.; Hamzah Alghifari, M.Kom.; Muhammad Damas Fatih, S.Kom., M.Kom.
