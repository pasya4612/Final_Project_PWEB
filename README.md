JUDUL PROYEK

Rancang Bangun Aplikasi Manajemen Tugas dan Rangkuman Belajar “StudySync” Berbasis Web

<br>
TIM PENGEMBANG

Ary Pasya Fernanda (5025241053) — Frontend Development & Testing
Lucky Himawan Prasetya (5025241147) — Backend Development, Database Management & API Integration

🔗 Link Aplikasi: STUDYSYNC

📚 BAB 1: PENDAHULUAN
1.1 Latar Belakang

Tantangan utama yang dihadapi pelajar adalah mengelola tugas akademik yang jumlahnya banyak serta menjaga efisiensi dalam proses belajar. Banyak pelajar mengalami kesulitan dalam melacak tenggat waktu (due date) dan menentukan prioritas tugas, yang sering berujung pada tugas terlewat (overdue).

Selain itu, proses merangkum materi pembelajaran seringkali terpisah dari sistem manajemen tugas. Hal ini menyebabkan catatan belajar tersebar dan tidak terorganisir dengan baik. StudySync hadir sebagai solusi terpadu dengan menggabungkan manajemen tugas berbasis waktu dan alat pencatatan digital (New Notes) yang berfokus pada rangkuman akademik. Dengan StudySync, tugas diorganisir berdasarkan prioritas waktu dan rangkuman belajar disimpan secara terpusat dalam satu platform.

1.2 Tujuan Proyek

Tujuan dari pengembangan aplikasi StudySync adalah:

Sistem Tugas Intuitif
Mengimplementasikan sistem manajemen tugas (CRUD) dengan penandaan status otomatis (Today, Upcoming, Overdue) serta status fleksibel.

Modul Pencatatan (New Notes)
Mengembangkan modul New Notes untuk membuat, menyimpan, dan mengelola rangkuman akademik secara terpusat.

Visualisasi Progres
Menyediakan Dashboard untuk melacak statistik kinerja pengguna (Total Tugas dan Tugas Selesai).

Manajemen Grup Diskusi
Menyediakan modul Study Group sebagai wadah organisasi topik diskusi tanpa fitur private chat 1-on-1.

Autentikasi Fleksibel
Mengimplementasikan login standar serta Login melalui Google Account (SSO).

🛠️ BAB 2: IMPLEMENTASI TEKNIS
2.1 Frontend & Backend Development

StudySync dibangun menggunakan arsitektur 3-Tier Architecture dengan pendekatan native web development.

Tingkat Sistem	Teknologi	Implementasi Kunci
Presentasi (Frontend)	HTML, CSS, Bootstrap	Antarmuka responsif dan estetis menggunakan Bootstrap
Logika Bisnis (Backend)	PHP & JavaScript	Logika klasifikasi tugas, CRUD Tasks & Notes
Transfer Data	JSON	Komunikasi data antara client dan server
2.2 Database Implementation

Database digunakan untuk menyimpan seluruh data persisten sistem.

Teknologi: MySQL (dikelola menggunakan phpMyAdmin)

Data yang Disimpan:

Data Tugas

Data Notes (Rangkuman)

Data Study Group

Data Akun Pengguna

Logika PHP bertanggung jawab menjaga relasi dan integritas data dalam seluruh operasi Task Management dan New Notes.

2.3 Integrasi API

API: Google Account Single Sign-On (SSO)

Fungsi:
Memungkinkan pengguna login menggunakan akun Google tanpa registrasi manual, sehingga meningkatkan kemudahan akses dan pengalaman pengguna.

Implementasi:
Sinkronisasi autentikasi dilakukan di sisi backend.

2.4 Pengujian (Testing)

Pengujian dilakukan menggunakan metode Black Box Testing.

Fitur	Skenario Pengujian	Hasil yang Diharapkan	Status
Klasifikasi Otomatis	DL tugas lewat 1 hari	Masuk kategori Overdue	✅ Berhasil
New Notes (CRUD)	Create, Edit, Delete catatan	Data tersimpan dan terhapus normal	✅ Berhasil
Edit Status Tugas	Completed → Pending	Statistik Dashboard diperbarui	✅ Berhasil
Login Google SSO	Login via akun Google	Sesi login berhasil	✅ Berhasil
2.5 Diagram Sistem

Logika inti di backend (PHP) memproses data tugas berdasarkan waktu sistem untuk menentukan status (Today / Upcoming / Overdue).
Data Notes diproses melalui alur CRUD terpisah dan disimpan sebagai konten akademik terpusat. Seluruh data disimpan di database MySQL.

🚀 BAB 3: PANDUAN PENGGUNA (USER GUIDE)
3.1 Mengelola Tugas (Task Management)

Tambah Tugas
Klik "+ Add Task", sistem otomatis mengklasifikasikan tugas berdasarkan DL.

Status Fleksibel
Gunakan "Mark Complete" untuk menyelesaikan tugas dan "Edit" untuk mengubah kembali ke Pending.

Lacak Progres
Dashboard menampilkan statistik tugas secara real-time.

3.2 Membuat Rangkuman (New Notes)

Akses menu "New Notes"

Buat rangkuman atau catatan penting lalu simpan

Catatan dapat diedit atau dihapus kapan saja

3.3 Study Group

Masuk ke menu "Study Group" untuk membuat dan mengelola grup diskusi berdasarkan topik tertentu (tanpa fitur chat pribadi).

👨‍💻 BAB 4: PEMBAGIAN JOBDESK
Nama	NRP	Tanggung Jawab	Kontribusi Teknis
Lucky Himawan Prasetya	5025241147	Backend & Database	PHP Logic, CRUD Tasks & Notes, MySQL, Google SSO, JS Async
Ary Pasya Fernanda	5025241053	Frontend & Testing	UI (CSS & Bootstrap), Functional Testing
✅ BAB 5: PENUTUP
5.1 Kesimpulan

Aplikasi StudySync berhasil dikembangkan sebagai platform manajemen tugas dan rangkuman belajar berbasis web yang terintegrasi. Dengan dukungan teknologi PHP, MySQL, dan Bootstrap, StudySync mampu membantu pengguna mengelola tugas akademik secara efisien, menyimpan rangkuman belajar terpusat, serta memantau progres belajar melalui dashboard yang informatif.

<p align="center"> © 2025 StudySync </p>
