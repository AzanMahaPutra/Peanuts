# Penetration Testing Capstone Project: PT NutWear 🛡️

> **⚠️ DISCLAIMER PENTING:** 
> Seluruh aktivitas pengujian, pemindaian, dan eksploitasi keamanan yang didokumentasikan dalam repositori ini dilakukan secara eksklusif pada *environment lab* pribadi yang legal, aman, dan terisolasi (**OWASP Juice Shop** & **Metasploitable2**). **TIDAK ADA** sistem produksi atau aset milik pihak ketiga yang diuji atau dirugikan dalam proyek ini. Proyek ini disusun murni untuk tujuan edukasi, demonstrasi keahlian keamanan siber, dan portofolio profesional.

## 📖 Ringkasan Proyek
Repositori ini berisi dokumentasi lengkap dari simulasi pengujian penetrasi (*penetration testing*) ujung-ke-ujung (end-to-end) yang dilakukan terhadap infrastruktur fiktif "PT NutWear". Pengujian ini bertujuan untuk mengidentifikasi, mengeksploitasi, dan memberikan rekomendasi perbaikan (remediasi) terhadap kerentanan keamanan pada aplikasi web dan server infrastruktur.

* **Peran:** Junior Security Assessor
* **Metodologi:** Penetration Testing Execution Standard (PTES)
* **Status:** Selesai

## 🎯 Ruang Lingkup & Target
Pengujian dilakukan secara *Gray-box* terhadap dua target utama dalam jaringan lokal terisolasi:
1. **OWASP Juice Shop:** Aplikasi web modern yang rentan secara desain (Node.js/Express).
2. **Metasploitable2:** Mesin virtual Linux yang berisi berbagai layanan jaringan dengan miskonfigurasi dan perangkat lunak usang.

## 🛠️ Metodologi (PTES)
Proyek ini dijalankan mengikuti standar industri PTES yang mencakup fase-fase berikut:
1. **Intelligence Gathering:** Pemindaian port dan enumerasi layanan menggunakan Nmap.
2. **Vulnerability Analysis:** Analisis versi layanan dan pemetaan alur aplikasi web untuk menemukan celah potensial.
3. **Exploitation:** Pembuktian kerentanan (OWASP Top 10) menggunakan Burp Suite dan pengambilan alih server menggunakan Metasploit Framework.
4. **Post-Exploitation:** Dokumentasi eskalasi hak istimewa (*privilege escalation*) dan akses data sensitif.
5. **Reporting:** Penyusunan laporan teknis dan ringkasan eksekutif beserta rekomendasi perbaikan.

## 🚨 Sorotan Temuan (Key Findings)
Terdapat 4 (empat) kerentanan utama yang berhasil diidentifikasi dan dieksploitasi dalam proyek ini:
* **[Critical] SQL Injection (Bypass Authentication):** Memanipulasi *query* login untuk mendapatkan akses Administrator.
* **[Critical] FTP vsftpd 2.3.4 Backdoor:** Mengeksploitasi layanan FTP usang untuk mendapatkan akses *shell* root pada server Metasploitable2.
* **[High] Broken Access Control (IDOR):** Memanipulasi parameter API untuk mengakses keranjang belanja (*basket*) milik pengguna lain.
* **[Medium] Cross-Site Scripting (Reflected XSS):** Mengeksekusi *payload* JavaScript berbahaya melalui fitur pencarian produk.

*Detail eksploitasi, Proof of Concept (PoC), dan rekomendasi perbaikan dapat dilihat pada dokumen Laporan Lengkap.*

## 📂 Struktur Repositori
Untuk memudahkan reviu, bukti pengujian dan dokumen disusun dengan struktur berikut:

```text
📦 NutWear
 ┣ 📂 evidence/               # Bukti pengujian mentah
 ┃ ┣ 📂 01-recon/             # Hasil scan Nmap & enumerasi
 ┃ ┣ 📂 02-exploitation/      # Screenshot Burp Suite, payload, & shell
 ┃ ┗ 📂 03-post-exploit/      # Screenshot hak akses root (whoami/shadow)
 ┣ 📂 reports/                # Laporan final
 ┃ ┗ 📜 Laporan Penetration Testing.pdf
 ┗ 📜 README.md               # Ringkasan proyek (Halaman ini)
```

## 💻 Tools yang Digunakan
* **Kali Linux** (Sistem Operasi Penyerang)
* **Nmap** (Network Mapping & Port Scanning)
* **Burp Suite** (Web Proxy & API Interception)
* **Metasploit Framework** (Exploitation & Payload Delivery)
