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
| **Autentikasi** | Registrasi & Login | Mendukung pendaftaran akun standar. Login tersedia melalui kredensial biasa atau **Google Account (SSO)**. |
| **Profil** | Pengaturan Akun | Pengguna dapat mengakses profil untuk mengubah **Nama**, **Email**, dan **Kata Sandi**. |
| **Task Management**| Tambah Tugas | Memasukkan **Konteks** (judul), **Deskripsi**, **Due Date (DL)**, dan **Kategori** tugas. |
| | Edit/Delete Tugas | Mengubah semua detail tugas yang ada. Khusus edit, status **Completed** dapat dikembalikan menjadi **Pending**. |
| | Mark Complete | Menandai tugas sebagai selesai. |
| **Klasifikasi DL** | Tiga Kategori | Tugas dibagi menjadi: <ul><li>**Today List** (DL hari ini).</li><li>**Upcoming This Week** (DL dalam 7 hari ke depan, bukan hari ini).</li><li>**Overdue** (DL telah terlewat).</li></ul> |
| **Dashboard** | Metrik Kinerja | Menampilkan statistik real-time: **Total Tugas** dan **Completed Tugas**. |
| **Study Group** | Group Management | Membuat, Mengedit, dan Menghapus grup diskusi. |
| **Sosial** | Add Friend | Fitur untuk menambahkan anggota Study Group sebagai teman pribadi. |
| | Friend List | Mengelola pertemanan dengan opsi **Accept**, **Reject**, dan **Remove** teman. |
| | Private Chat | Menyediakan fungsi *chatting* 1-on-1 dengan teman yang sudah di-*accept* (mirip WA/Line). |

### 2.2 Arsitektur Sistem

StudySync menggunakan arsitektur *Client-Server* dengan logika bisnis terpusat.

#### Diagram Konteks (DFD Level 0)
Diagram ini menunjukkan StudySync sebagai sistem utama yang berinteraksi dengan **Pengguna**.

> **Aliran Data Kunci:** Data Tugas yang dimasukkan pengguna menjadi input vital, sementara Daftar Tugas yang sudah terkategorisasi dan Status Metrik Dashboard menjadi output utama.

#### Logika Alir Data Tugas (DFD Level 1: Task Management)
Proses ini menunjukkan bagaimana tugas yang baru ditambahkan diproses oleh sistem:



1.  **Pengelolaan Tugas:** Menerima **Add/Edit/Delete Task** dan **Mark Complete** dari pengguna, memperbarui $D1$ (Data Tugas).
2.  **Kategorisasi Otomatis:** Sistem membaca $D1$ dan membandingkan `Due Date` dengan tanggal saat ini, menghasilkan klasifikasi status (*Today*, *Upcoming*, *Overdue*).
3.  **Update Dashboard:** Perubahan status tugas (*Add* atau *Complete*) memicu pembaruan hitungan Total dan Completed Tasks.

---

## 🚀 BAB 3: PANDUAN PENGGUNA (USER GUIDE)

### 1. Memulai Akun dan Profil

* **Akses Cepat:** Gunakan **"Login dengan Google Account"** saat pertama kali mengakses untuk melewati proses registrasi manual.
* **Pengaturan Akun:** Di menu **"Profile"**, Anda dapat mengganti **Nama**, **Email**, dan menjaga keamanan akun dengan mengganti **Kata Sandi**.

### 2. Mengelola Tugas

| Fungsionalitas | Cara Penggunaan |
| :--- | :--- |
| **Menambah Tugas** | Klik **"+ Add Task"**. Pastikan DL diisi. Tugas akan otomatis masuk ke kategori waktu. |
| **Mengubah Status** | Klik tombol **"Mark Complete"**. Di Dashboard, **Completed Tasks** akan bertambah. |
| **Revisi Tugas** | Gunakan **"Edit"**. Anda dapat mengubah *semua* detail atau mengubah tugas yang sudah *Completed* kembali menjadi *Pending*. |
| **Melacak DL** | Prioritaskan **Today List**. Tugas yang terlewat akan otomatis muncul di **Overdue**. |

### 3. Berkolaborasi

* **Membuat Grup:** Buka **"Study Group"** $\rightarrow$ **"+ Buat Grup Baru"**. Anda bisa mengatur detail grup dan mengundang anggota.
* **Membangun Jaringan:** Di Study Group, Anda dapat memilih anggota dan **"Add Friend"**.
* **Mengelola Pertemanan:** Di **"Friend List"**, Anda bisa **Accept** atau **Reject** permintaan masuk, atau **Remove** teman yang sudah ada.
* **Chat Pribadi:** Pilih nama teman di **"Friend List"** untuk memulai **Private Chat** 1-on-1.

---

## ✅ BAB 4: PENUTUP

### 4.1 Kesimpulan
Proyek **StudySync** berhasil dikembangkan sebagai *platform* yang secara efektif menggabungkan manajemen tugas dengan kebutuhan kolaborasi pelajar. Implementasi logika kategorisasi tugas otomatis (Today, Upcoming, Overdue) dan fitur komunikasi terintegrasi (Study Group, Private Chat) telah memenuhi semua tujuan proyek yang ditetapkan. StudySync memberikan nilai tambah yang signifikan sebagai alat pendukung produktivitas akademik.

---
<center>
Copyright © 2025 StudySync.
</center>
