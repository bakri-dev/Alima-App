# Spesifikasi & Ketentuan Proyek — Arab Learning App

**Versi Dokumen:** 1.0  
**Tanggal:** November 2026  
**Status:** Tahap Inisiasi & Landing Page  

---

## 1. Latar Belakang & Tujuan Proyek

Pembelajaran Bahasa Arab di tingkat perguruan tinggi maupun kursus intensif membutuhkan penanganan khusus yang sering kali kurang optimal pada LMS umum—terutama terkait keterbacaan teks Arab berharakat (*Right-to-Left*), integrasi audio pelafalan (*istima'*), serta alur evaluasi bertahap per pertemuan.

**Tujuan Utama:**
1. Menyediakan ruang kelas digital terstruktur bagi dosen untuk mengelola silabus Bahasa Arab per pertemuan.
2. Memudahkan mahasiswa mengakses materi lintas format (Teks Arab, PDF, Audio MP3, Tautan) dari perangkat *desktop* maupun *mobile* tanpa instalasi aplikasi tambahan.
3. Menyederhanakan proses evaluasi (Pilihan Ganda & Esai) hingga pelaporan nilai akhir dalam format standar akademik (CSV).

---

## 2. Peran Pengguna (*User Roles*) & Hak Akses

| Peran | Deskripsi | Hak Akses Utama |
| :--- | :--- | :--- |
| **Pengunjung (*Guest*)** | Pengguna yang belum masuk ke sistem. | Melihat halaman *Landing Page*, informasi fitur, dan formulir registrasi/masuk. |
| **Dosen (*Instructor*)** | Pengampu mata kuliah atau kelas Bahasa Arab. | Membuat/mengelola kelas, menerbitkan kode kelas, membagi kelompok, mengunggah materi, menyusun soal PG & esai, mengoreksi esai, dan mengekspor rekap nilai CSV. |
| **Mahasiswa (*Student*)** | Peserta didik yang terdaftar di kelas. | Bergabung ke kelas via kode unik, mengakses materi sesuai urutan silabus, mengerjakan soal PG & esai sebelum tenggat, dan melihat nilai pribadi. |

---

## 3. Spesifikasi Fungsional (*Functional Requirements*)

### 3.1. Autentikasi & Manajemen Kelas
* **FR-01:** Sistem menyediakan pendaftaran dan masuk terpisah untuk peran **Dosen** dan **Mahasiswa**.
* **FR-02:** Setiap kelas yang dibuat oleh Dosen menghasilkan **Kode Kelas Unik** (misal: 6–8 karakter alfanumerik) yang dapat dibagikan kepada mahasiswa.
* **FR-03:** Mahasiswa hanya dapat mengakses materi dan tugas dari kelas tempat ia terdaftar secara aktif.
* **FR-04:** Dosen dapat mengelompokkan mahasiswa di dalam satu kelas ke dalam sub-kelompok diskusi/tugas.

### 3.2. Manajemen Materi Ajar
* **FR-05 (Naskah Arab RTL):** Editor dan penampil teks wajib mendukung atribut `dir="rtl"` dan `lang="ar"` dengan *font* khusus Arab (`Amiri` atau `Noto Naskh Arabic`) agar harakat tidak terpotong atau bertumpuk.
* **FR-06 (Dokumen PDF):** Mendukung unggah file `.pdf` dengan ukuran maksimal yang ditentukan (misal: 20 MB per file) serta penampil pratinjau (*viewer*) dan opsi unduh.
* **FR-07 (Audio MP3):** Mendukung unggah file audio `.mp3` dengan pemutar audio bawaan (*play/pause*, *seek*, pengaturan kecepatan putar) langsung di halaman materi.
* **FR-08 (Tautan Eksternal):** Mendukung penyematan URL eksternal beserta deskripsi singkat.
* **FR-09 (Urutan Terkunci):** Dosen dapat mengaktifkan opsi prasyarat sehingga mahasiswa wajib menyelesaikan pertemuan $N$ sebelum membuka pertemuan $N+1$.

### 3.3. Asesmen, Penilaian & Rekapitulasi
* **FR-10:** Paket tugas/kuis mendukung kombinasi soal **Pilihan Ganda (PG)** dan **Esai** beserta pengaturan tenggat waktu (*deadline*).
* **FR-11:** Skor soal Pilihan Ganda dihitung secara otomatis segera setelah mahasiswa mengirimkan jawaban.
* **FR-12:** Jawaban Esai masuk ke antrean penilaian Dosen untuk diberikan skor dan umpan balik manual.
* **FR-13:** Rekapitulasi nilai per kelas dapat diekspor ke dalam berkas `.csv` (UTF-8 dengan BOM agar karakter Arab terbaca baik di Microsoft Excel).

---

## 4. Spesifikasi Non-Fungsional & Ketentuan Teknis

### 4.1. Standar Antarmuka & Desain (UI/UX)
* **Palet Warna Resmi:**
  * *Primary Navy:* `#1E3A5F` (Identitas akademik, header blok, penekanan utama)
  * *Primary Green:* `#2D7A4F` / *Hover:* `#1F5938` (Aksi utama, indikator aktif)
  * *Soft Surface:* `#F0F4F8` & `#E8F5EE` (Latar sekunder & *badge*)
  * *Text Primary:* `#1A2B3C` / *Muted:* `#5A7184`
* **Tipografi:**
  * *Heading & Angka Statistik:* `Playfair Display`
  * *Antarmuka & Teks Latin:* `Inter`
  * *Naskah Bahasa Arab:* `Amiri` (wajib *line-height* $\ge 1.6$ pada paragraf Arab berharakat)
* **Responsivitas:** Tata letak harus beradaptasi mulus pada layar *mobile* ($\le 768\text{px}$), tablet, dan *desktop* ($\ge 1200\text{px}$), serta menghormati preferensi `prefers-reduced-motion`.

### 4.2. Keamanan & Integritas Data (*Security Rules*)
* **SEC-01 (Proteksi Kunci Jawaban):** Kunci jawaban soal Pilihan Ganda **tidak boleh** dikirimkan ke *client/browser* saat sesi pengerjaan berlangsung. Evaluasi skor wajib dilakukan sepenuhnya di sisi *server* (*backend*).
* **SEC-02 (Kontrol Akses Berbasis Peran):** Setiap *endpoint* API dan berkas media (PDF/MP3) harus memvalidasi sesi pengguna dan keanggotaan kelas (*authorization check*).
* **SEC-03 (Validasi Unggahan):** File yang diunggah wajib divalidasi tipe MIME dan ukurannya untuk mencegah unggahan skrip berbahaya.

### 4.3. Performa & Aksesibilitas
* **PERF-01:** Halaman *Landing Page* dan antarmuka inti harus ringan dengan waktu muat awal (*First Contentful Paint*) di bawah 1,5 detik pada koneksi standar.
* **A11Y-01:** Seluruh ikon dekoratif wajib menggunakan `aria-hidden="true"`, elemen interaktif memiliki fokus keyboard yang jelas, dan kontras warna memenuhi standar WCAG AA.

---

## 5. Kriteria Penerimaan (*Acceptance Criteria*)

Sebuah rilis dinyatakan memenuhi ketentuan proyek apabila:
1. Seluruh alur utama (Buat Kelas $\rightarrow$ Gabung Kode $\rightarrow$ Akses Materi Arab/PDF/Audio $\rightarrow$ Kerjakan Soal $\rightarrow$ Ekspor CSV) berjalan tanpa galat.
2. Teks Arab berharakat tampil jelas tanpa tumpang tindih di peramban Chrome, Safari, dan Firefox versi terbaru.
3. Pengujian inspeksi jaringan (*Network Tab*) memastikan tidak ada kebocoran kunci jawaban soal pada respons API sisi mahasiswa.