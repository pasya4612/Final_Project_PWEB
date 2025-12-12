<h1 align="center">LAPORAN PROYEK PENGEMBANGAN WEB: STUDYSYNC</h1>

<p align="center">
  <img src="https://via.placeholder.com/300x150?text=STUDYSYNC+LOGO" width="300" alt="Logo StudySync">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Final+Project-brightgreen" alt="Status">
  <img src="https://img.shields.io/badge/Technology-Web+Application-blue" alt="Technology">
</p>

## JUDUL PROYEK:
**Rancang Bangun Aplikasi Manajemen Tugas dan Kolaborasi Belajar "StudySync" Berbasis Web**

<br>

## TIM PENGEMBANG:
**[Nama Pengembang 1]** [5025xxxxxx] [Backend & Logika Sistem]<br>
**[Nama Pengembang 2]** [5025xxxxxx] [Frontend & User Interface]

---

## 📚 BAB 1: PENDAHULUAN

### 1.1 Latar Belakang
Dunia pendidikan modern menuntut pelajar untuk mengelola banyak tugas dan tenggat waktu secara simultan. Kurangnya sistem terpusat untuk melacak kewajiban ini seringkali mengakibatkan tugas terlambat dikumpulkan (*overdue*) atau terlewat. Studi menunjukkan bahwa pelajar sering kesulitan memprioritaskan tugas tanpa adanya klasifikasi waktu yang jelas.

Selain masalah manajemen waktu, proses diskusi dan belajar kelompok seringkali tersebar di berbagai *platform* komunikasi eksternal, yang tidak terintegrasi dengan *to-do list* mereka. **StudySync** hadir sebagai solusi terpadu untuk mengatasi tantangan tersebut, menggabungkan fitur manajemen tugas yang cerdas, seperti penandaan status otomatis (**Today, Upcoming, Overdue**), dengan alat kolaborasi sosial, seperti **Study Group** dan **Private Chat**, yang terintegrasi langsung dalam konteks akademik pengguna. Dengan demikian, StudySync bertujuan meningkatkan efisiensi belajar dan memfasilitasi komunikasi yang terfokus.

### 1.2 Tujuan Proyek
Tujuan utama dari pengembangan aplikasi StudySync ini adalah:
1.  **Sistem Tugas Intuitif:** Merancang dan mengimplementasikan sistem manajemen tugas yang intuitif, mencakup fitur penambahan, pengeditan (termasuk mengubah status *Completed* ke *Pending*), penyelesaian (*Mark Complete*), dan penandaan status otomatis (**Today, Upcoming, Overdue**).
2.  **Modul Kolaborasi Penuh:** Mengembangkan modul kolaborasi yang memungkinkan pengguna membuat **Study Group** untuk diskusi, mengelola **Friend List** (Accept, Reject, Remove), dan melakukan **Private Chat** 1-on-1.
3.  **Visualisasi Progres:** Menyediakan *dashboard* visual untuk melacak statistik progres belajar pengguna, yaitu **Total Tugas** yang dimasukkan dan **Tugas Selesai** (*Completed*).
4.  **Autentikasi Fleksibel:** Mengimplementasikan sistem autentikasi yang aman, mencakup registrasi/login standar serta opsi login melalui **Google Account (SSO)** untuk kemudahan akses.

---

## 🛠️ BAB 2: ANALISIS DAN PERANCANGAN SISTEM

### 2.1 Fitur Utama (*Functional Requirements*)

| Modul | Fitur | Deskripsi Fungsionalitas Rinci |
| :--- | :--- | :--- |
| **Autentikasi** | Registrasi & Login | Login standar dan **Login via Google Account (SSO)**. |
| **Task Management**| Klasifikasi DL | Tugas dibagi otomatis ke: **Today List**, **Upcoming This Week**, dan **Overdue**. |
| | Edit/Delete Tugas | Mengubah semua detail, termasuk status **Completed** dapat dikembalikan menjadi **Pending**. |
| **Kolaborasi** | Study Group | Membuat, Mengedit, dan Menghapus grup diskusi. |
| **Sosial** | Friend & Chat | **Add Friend**, mengelola pertemanan (**Accept/Reject/Remove**), dan **Private Chat** 1-on-1. |
| **Dashboard** | Metrik Kinerja | Menampilkan statistik **Total Tugas** dan **Completed Tugas**. |

### 2.2 Arsitektur Sistem (Narasi)

StudySync dikembangkan menggunakan arsitektur **3-Tier (Tiga Tingkat)**, yang memisahkan tanggung jawab sistem menjadi tiga lapisan utama untuk efisiensi dan pemeliharaan:

#### A. Tingkat Presentasi (Presentation Tier / Frontend)
Lapisan ini bertanggung jawab atas interaksi pengguna.
* **Fungsi:** Menampilkan antarmuka web (Dashboard, Daftar Tugas, Chat UI), menerima input dari pengguna (klik tombol, pengisian formulir), dan mengirimkannya ke Tingkat Logika.
* **Teknologi:** HTML, CSS, JavaScript (Framework/Library Frontend jika digunakan).

#### B. Tingkat Logika Bisnis (Business Logic Tier / Backend)
Lapisan ini adalah inti pemrosesan StudySync.
* **Fungsi:** Mengelola autentikasi pengguna, menjalankan operasi CRUD Tugas, dan yang terpenting, menjalankan **Logika Klasifikasi Otomatis** dan **Manajemen Sosial**.
* **Spesifikasi Logika Kunci:**
    * **Klasifikasi Tugas:** Logika ini membandingkan `due_date` tugas dengan *timestamp* sistem untuk menentukan status (`DL < Hari Ini` = Overdue; `DL = Hari Ini` = Today; `DL <= 7 Hari` = Upcoming).
    * **Manajemen Status:** Mengelola transisi status tugas (*Pending* $\leftrightarrow$ *Completed*) dan memperbarui metrik Dashboard.
    * **Manajemen Sosial:** Mengelola relasi di tabel pertemanan, memproses status *Accept/Reject*, dan mengelola riwayat pesan Private Chat.
* **Teknologi:** PHP/Python/Node.js (sesuai implementasi backend).

#### C. Tingkat Data (Data Tier / Database)
Lapisan ini bertanggung jawab untuk penyimpanan data yang persisten.
* **Fungsi:** Menyimpan data pengguna, semua detail tugas, relasi Study Group, status pertemanan, dan riwayat Private Chat.
* **Teknologi:** MySQL/PostgreSQL (atau sejenisnya).

### 2.3 Aliran Data Utama (Task Management)

Aliran data dalam StudySync berpusat pada pemrosesan tugas yang dinamis:
1.  **Input Tugas:** Pengguna memasukkan data tugas baru (Konteks, Deskripsi, DL, Kategori) melalui Tingkat Presentasi.
2.  **Penyimpanan:** Data dikirim ke Tingkat Logika Bisnis, divalidasi, dan disimpan dalam Tingkat Data (Database).
3.  **Permintaan Tampilan:** Ketika Dashboard diminta, Tingkat Logika Bisnis mengambil semua tugas pengguna dari Database.
4.  **Pemrosesan Klasifikasi:** Logika Bisnis menjalankan *query* atau fungsi yang membandingkan `due_date` setiap tugas dengan tanggal saat ini, mengkategorikannya menjadi **Today**, **Upcoming**, atau **Overdue**.
5.  **Output:** Hasil kategorisasi dan metrik kinerja (Total/Completed) dikirim kembali melalui Tingkat Presentasi ke layar pengguna.

---

## 🚀 BAB 3: PANDUAN PENGGUNA (USER GUIDE)

### 1. Memulai Akun dan Profil

* **Akses Cepat:** Gunakan **"Login dengan Google Account"** saat pertama kali mengakses.
* **Pengaturan Akun:** Di menu **"Profile"**, Anda dapat mengganti **Nama**, **Email**, dan **Kata Sandi**.

### 2. Mengelola Tugas

| Fungsionalitas | Cara Penggunaan |
| :--- | :--- |
| **Menambah Tugas** | Klik **"+ Add Task"**. Pastikan DL diisi. Tugas akan otomatis masuk ke kategori waktu. |
| **Mengubah Status** | Klik tombol **"Mark Complete"**. Di Dashboard, **Completed Tasks** akan bertambah. |
| **Revisi Tugas** | Gunakan **"Edit"**. Anda dapat mengubah *semua* detail atau mengubah tugas yang sudah *Completed* kembali menjadi *Pending*. |
| **Melacak DL** | Prioritaskan **Today List**. Tugas yang terlewat akan otomatis muncul di **Overdue**. |

### 3. Berkolaborasi

* **Membuat Grup:** Buka **"Study Group"** $\rightarrow$ **"+ Buat Grup Baru"**.
* **Membangun Jaringan:** Di Study Group, Anda dapat memilih anggota dan **"Add Friend"**.
* **Mengelola Pertemanan:** Di **"Friend List"**, Anda bisa **Accept** atau **Reject** permintaan masuk, atau **Remove** teman.
* **Chat Pribadi:** Pilih nama teman di **"Friend List"** untuk memulai **Private Chat** 1-on-1.

---

## ✅ BAB 4: PENUTUP

### 4.1 Kesimpulan
Proyek **StudySync** berhasil dikembangkan sebagai *platform* yang secara efektif menggabungkan manajemen tugas dengan kebutuhan kolaborasi pelajar. Implementasi logika kategorisasi tugas otomatis (Today, Upcoming, Overdue) dan fitur komunikasi terintegrasi (Study Group, Private Chat) telah memenuhi semua tujuan proyek yang ditetapkan. StudySync memberikan nilai tambah yang signifikan sebagai alat pendukung produktivitas akademik.

---
<center>
Copyright © 2025 StudySync.
</center>
