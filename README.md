# A.R.C.A Relayer

[![Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://developer.android.com)
[![Privacy-First](https://img.shields.io/badge/Privacy-100%25%20Local-blue.svg)](#-kebijakan-privasi-privacy-policy)
[![License](https://img.shields.io/badge/License-MIT-brightgreen.svg)](LICENSE)

**A.R.C.A Relayer** (*Automated Research and Cognitive Assistant - Relayer*) adalah aplikasi Android mandiri yang dirancang untuk menangkap notifikasi pesan masuk (seperti WhatsApp) secara *real-time*, membacakan sapaan/isi pesan menggunakan modul *Text-To-Speech* (TTS) lokal, serta meneruskan (*relay*) data payload ke *endpoint* API kustom milik pengguna secara lokal maupun *online*.

---

## 🚀 Fitur Utama

- 🔔 **Notification Listener**: Membaca notifikasi masuk secara presisi menggunakan `NotificationListenerService`.
- 🗣️ **Local Text-To-Speech (TTS)**: Membacakan nama pengirim dan pesan secara otomatis di perangkat tanpa memerlukan koneksi internet.
- 🌐 **Custom API Relay**: Meneruskan data notifikasi ke server REST API / Webhook kustom melalui protokol HTTP/HTTPS (POST request).
- 🔒 **Privacy-First**: Seluruh pemrosesan teks dan audio berjalan 100% lokal. Tidak ada pelacakan pihak ketiga atau pengumpulan data ke server pengembang.
- ⚡ **Efisiensi Latar Belakang**: Berjalan sebagai *background service* yang ringan dengan konsumsi memori dan baterai minimal.

---

## ⚙️ Alur Kerja Sistem (System Workflow)

Sistem mengeksekusi setiap notifikasi masuk dengan urutan baris/proses sebagai berikut:

1. **Intercepting**: `NotificationListenerService` menangkap event notifikasi baru dari aplikasi yang ditentukan (contoh: WhatsApp).
2. **Parsing**: Sistem mengekstrak parameter `title` (pengirim) dan `text` (isi pesan) dari objek `StatusBarNotification`.
3. **Audio Execution**: Teks yang sudah diformat dikirim ke engine TTS lokal untuk dikonversi menjadi sinyal audio sapaan.
4. **Payload Building**: Sistem menyusun data JSON terstruktur berisi rincian notifikasi.
5. **Data Relaying**: Jika mode relay aktif, modul HTTP Client mengirimkan JSON payload ke URL API kustom yang telah dikonfigurasi.

---

## 🛠️ Prasyarat & Instalasi

### Prasyarat
- Android Studio Ladybug (2024.2.1) atau versi lebih baru
- JDK 17+
- Perangkat Android (Minimum SDK level 24 / Android 7.0 Nougat)

### Langkah Build & Run
1. **Kloning Repositori**:
   ```bash
   git clone [https://github.com/mal1shade/arca-relayer.git](https://github.com/mal1shade/arca-relayer.git)
   cd arca-relayer
