# Arab Learning App

**Arab Learning App** adalah platform *Learning Management System* (LMS) berbasis web yang dirancang khusus untuk kebutuhan perkuliahan dan pembelajaran Bahasa Arab. Aplikasi ini menghubungkan dosen dan mahasiswa dalam ruang kelas digital terstruktur yang mendukung penyajian naskah Arab (RTL), rekaman audio pelafalan (*istima'*), modul PDF, serta evaluasi pilihan ganda otomatis dan esai.

---

## Fitur Utama

### 1. Manajemen Kelas & Kelompok
* **Multi-Kelas Berbasis Kode:** Dosen dapat membuat berbagai kelas paralel; mahasiswa bergabung cukup menggunakan kode undangan unik tanpa input manual.
* **Pembagian Kelompok Diskusi:** Memecah anggota kelas ke dalam kelompok-kelompok kecil untuk latihan percakapan (*muhadatsah*), terjemahan, atau tugas kolaboratif.

### 2. Penyajian Materi Terstruktur (Multi-Format)
* **Naskah Teks Arab (RTL):** Mendukung tampilan kanan-ke-kiri (*Right-to-Left*) yang presisi untuk *mufradat*, *hiwar*, dan kaidah nahwu/sharf lengkap dengan harakat.
* **Modul & Lembar Kerja PDF:** Unggah dan distribusi diktat, bacaan (*qira'ah*), atau rangkuman materi yang dapat dibaca langsung maupun diunduh.
* **Audio Pelafalan (MP3):** Pemutar audio terintegrasi untuk latihan *istima'* dan contoh pelafalan *makhraj* langsung di dalam halaman materi.
* **Tautan Referensi Eksternal:** Menyematkan rujukan video, kamus daring, atau artikel pendukung secara terarah per pertemuan.
* **Urutan Silabus Terkunci:** Dosen dapat mengatur alur materi per pertemuan/topik sehingga mahasiswa belajar secara bertahap.

### 3. Evaluasi & Rekapitulasi Nilai
* **Koreksi Ganda (Objektif & Esai):** Soal pilihan ganda dikoreksi otomatis oleh sistem, sedangkan jawaban uraian/esai dinilai manual oleh dosen.
* **Buku Nilai & Ekspor CSV:** Rekapitulasi skor seluruh mahasiswa per pertemuan dan per tugas yang siap diunduh ke format `.csv` untuk administrasi akademik.
* **Keamanan Akses & Kunci Jawaban:** Visibilitas materi dibatasi berdasarkan keanggotaan kelas, dengan validasi jawaban di sisi server agar kunci jawaban tidak terekspos ke *browser*.

---

## Struktur Proyek (Saat Ini)

```text
arab-learning-app/
├── Arab Learning App — Landing Page.html   # Halaman muka (Landing Page) statis responsif
├── README.md                               # Dokumentasi umum repositori
└── PROJECT_SPEC.md                         # Spesifikasi teknis, arsitektur, dan ketentuan proyek
```

---

## Cara Menjalankan Landing Page Secara Lokal

Halaman *landing page* dibangun menggunakan HTML5 dan CSS3 murni tanpa ketergantungan *build tools* eksternal.

1. Kloning atau unduh repositori ini ke komputer lokal.
2. Buka file `Arab Learning App — Landing Page.html` langsung menggunakan peramban modern (Chrome, Firefox, Safari, atau Edge).
3. *(Opsional)* Gunakan ekstensi **Live Server** di VS Code atau jalankan server lokal sederhana:
   ```bash
   npx serve .
   ```

---

## Peta Jalan Pengembangan (Roadmap)

* [x] Perancangan antarmuka & *copywriting* Landing Page
* [ ] Implementasi autentikasi peran (Dosen & Mahasiswa)
* [ ] Sistem pembuatan kelas dan generator kode undangan
* [ ] Editor materi dengan dukungan penuh tipografi Arab (`Amiri` / `Noto Naskh Arabic`) dan *audio player*
* [ ] Modul kuis pilihan ganda (auto-grading) & esai (manual grading)
* [ ] Dasbor rekap nilai dan fitur ekspor CSV

---

## Lisensi

© 2026 **Arab Learning App**. Seluruh hak cipta dilindungi.