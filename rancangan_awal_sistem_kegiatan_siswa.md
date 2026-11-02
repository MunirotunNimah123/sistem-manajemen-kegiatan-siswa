# Dokumentasi Awal Sistem Informasi Manajemen Kegiatan Siswa

**Judul penelitian:**

Sistem Informasi Manajemen Kegiatan Siswa Berbasis Web dengan
Implementasi Chatbot Menggunakan Cosine Similarity di SMK Negeri 2
Konawe Selatan

Dokumen ini berisi gambaran awal alur aplikasi dan aktor yang terlibat.
Rancangan masih dapat disesuaikan berdasarkan arahan dosen pembimbing
dan hasil analisis kebutuhan di sekolah.

------------------------------------------------------------------------

## 1. Alur Aplikasi

### A. Alur Admin

1.  Admin masuk ke sistem menggunakan akun yang telah terdaftar.
2.  Sistem memeriksa username dan password.
3.  Jika data login benar, admin masuk ke halaman dashboard.
4.  Admin mengelola data kegiatan siswa, meliputi:
    -   Menambahkan kegiatan baru.
    -   Mengubah informasi kegiatan.
    -   Menghapus kegiatan yang sudah tidak diperlukan.
    -   Mengatur jadwal, waktu, lokasi, deskripsi, persyaratan, batas
        pendaftaran, dan status kegiatan.
5.  Admin mengatur pendaftaran untuk kegiatan yang membutuhkan
    pendaftaran, misalnya membuka atau menutup pendaftaran.
6.  Admin melihat daftar siswa yang telah mendaftar pada setiap
    kegiatan.
7.  Admin mengelola basis pengetahuan chatbot, yaitu memasukkan atau
    memperbarui pasangan pertanyaan dan jawaban seputar kegiatan siswa.
8.  Admin dapat melihat data kegiatan, data pendaftaran, dan data
    pengetahuan chatbot yang tersimpan.

### B. Alur Siswa

1.  Siswa membuka website.
2.  Siswa masuk ke sistem apabila fitur login siswa diterapkan.
3.  Siswa melihat daftar kegiatan yang tersedia.
4.  Siswa memilih salah satu kegiatan untuk melihat detail, seperti
    deskripsi, jadwal, lokasi, persyaratan, dan status pendaftaran.
5.  Jika pendaftaran dibuka dan kegiatan memerlukan pendaftaran, siswa
    mengisi formulir pendaftaran.
6.  Sistem menyimpan data pendaftaran dan menampilkan informasi bahwa
    pendaftaran berhasil dikirim.
7.  Siswa dapat melihat informasi kegiatan dan menggunakan chatbot untuk
    menanyakan hal-hal terkait kegiatan siswa.
8.  Siswa mengetik pertanyaan pada chatbot.
9.  Sistem memproses teks pertanyaan, melakukan preprocessing, membentuk
    representasi TF-IDF, lalu menghitung kemiripan menggunakan Cosine
    Similarity terhadap pertanyaan dalam basis pengetahuan.
10. Jika nilai kemiripan memenuhi ambang batas (threshold) yang
    ditentukan, sistem menampilkan jawaban yang terkait. Jika tidak,
    sistem menampilkan pesan bahwa informasi belum ditemukan atau
    menyarankan siswa menghubungi admin/pengelola kegiatan.

### C. Alur Pengelolaan dan Jawaban Chatbot

1.  Admin menambahkan atau memperbarui data pertanyaan dan jawaban pada
    basis pengetahuan chatbot.
2.  Siswa mengirimkan pertanyaan melalui fitur chatbot.
3.  Sistem membersihkan dan memproses teks pertanyaan.
4.  Sistem mengubah teks menjadi bobot kata menggunakan TF-IDF.
5.  Sistem menghitung nilai Cosine Similarity antara pertanyaan siswa
    dan pertanyaan yang tersimpan.
6.  Sistem memilih pertanyaan dengan nilai kemiripan tertinggi.
7.  Jika nilai tertinggi memenuhi threshold, jawaban yang terkait
    ditampilkan kepada siswa.
8.  Jika tidak memenuhi threshold, chatbot memberikan respons bahwa
    jawaban belum tersedia.

**Catatan penting:** Penambahan kegiatan tidak otomatis berarti basis
pengetahuan chatbot ikut bertambah. Pada rancangan awal ini, admin
mengelola data kegiatan dan basis pengetahuan chatbot. Agar chatbot
dapat menjawab pertanyaan tentang kegiatan yang baru ditambahkan,
informasi terkait perlu dimasukkan atau disediakan pada basis
pengetahuan chatbot. Mekanisme otomatis mengambil data kegiatan dari
database dapat menjadi pengembangan rancangan tersendiri dan perlu
disepakati dengan dosen pembimbing.

### D. Ringkasan Alur Aplikasi

``` text
                         SISTEM
                           |
             +-------------+-------------+
             |                           |
           ADMIN                        SISWA
             |                           |
      Login ke sistem              Membuka website
             |                           |
       Dashboard                 Melihat kegiatan
             |                           |
     +-------+--------+             Melihat detail
     |       |        |                   |
  Kelola  Kelola   Lihat daftar       Mendaftar jika
  kegiatan chatbot  pendaftar         pendaftaran dibuka
     |       |        |                   |
     +-------+--------+                   |
             |                       Mengajukan
       Data tersimpan                 pertanyaan
             |                           |
             |                    Preprocessing teks
             |                           |
             |                         TF-IDF
             |                           |
             |                   Cosine Similarity
             |                           |
             +--------------------> Jawaban chatbot
```

------------------------------------------------------------------------

## 2. Aktor dan Use Case yang Terlibat

Pada rancangan awal, terdapat dua aktor utama agar ruang lingkup sistem
tetap terarah.

### A. Admin (Guru/Pengelola Kegiatan)

Admin adalah pihak sekolah yang diberi wewenang untuk mengelola
informasi kegiatan siswa dan basis pengetahuan chatbot.

Use case Admin:

1.  Login.
2.  Melihat dashboard.
3.  Mengelola data kegiatan:
    -   Menambah kegiatan.
    -   Melihat daftar kegiatan.
    -   Mengubah kegiatan.
    -   Menghapus kegiatan.
4.  Mengatur status dan periode pendaftaran.
5.  Melihat daftar siswa yang mendaftar.
6.  Mengelola basis pengetahuan chatbot:
    -   Menambah pertanyaan dan jawaban.
    -   Mengubah pertanyaan dan jawaban.
    -   Menghapus pertanyaan dan jawaban.
7.  Logout.

### B. Siswa

Siswa adalah pengguna yang mengakses informasi kegiatan, melakukan
pendaftaran, dan bertanya melalui chatbot.

Use case Siswa:

1.  Membuka halaman website.
2.  Login (jika fitur autentikasi siswa diterapkan).
3.  Melihat daftar kegiatan.
4.  Melihat detail kegiatan.
5.  Melakukan pendaftaran kegiatan.
6.  Melihat informasi/status pendaftaran (jika fitur ini diterapkan).
7.  Mengajukan pertanyaan melalui chatbot.
8.  Melihat jawaban chatbot.
9.  Logout (jika menggunakan login).

### C. Ringkasan Aktor dan Use Case

  -----------------------------------------------------------------------
  Aktor                               Use case utama
  ----------------------------------- -----------------------------------
  Admin                               Login, mengelola kegiatan, mengatur
                                      pendaftaran, melihat peserta,
                                      mengelola basis pengetahuan
                                      chatbot, logout

  Siswa                               Melihat kegiatan, melihat detail,
                                      mendaftar kegiatan, bertanya kepada
                                      chatbot, melihat jawaban
  -----------------------------------------------------------------------

### D. Batasan Rancangan Awal

-   Admin menjadi pengelola utama data kegiatan dan basis pengetahuan
    chatbot.
-   Siswa menjadi pengguna informasi dan layanan pendaftaran.
-   Chatbot difokuskan untuk menjawab pertanyaan seputar kegiatan siswa
    di sekolah, bukan pertanyaan umum di luar konteks tersebut.
-   Cosine Similarity digunakan untuk menghitung kemiripan pertanyaan
    siswa dengan pertanyaan pada basis pengetahuan.
-   TF-IDF digunakan untuk membentuk bobot kata sebelum perhitungan
    Cosine Similarity.
-   Jawaban chatbot berasal dari basis pengetahuan yang telah disiapkan,
    bukan dibuat bebas seperti chatbot generatif.
-   Fitur login siswa, status pendaftaran, persetujuan peserta, kuota,
    dan notifikasi masih perlu dipastikan melalui analisis kebutuhan
    serta arahan dosen pembimbing.

------------------------------------------------------------------------