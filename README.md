# Pocket Visionary: Android (Android Studio)

Aplikasi kamera yang memakai Gemini Vision untuk mendeskripsikan gambar, mengenali objek, membaca teks (OCR), dan menerjemahkan.

## Persyaratan
- Android Studio versi terbaru (Koala atau lebih baru), JDK 17 (sudah termasuk di Android Studio)
- Internet saat sync pertama (mengunduh Gradle 8.7 dan library)
- HP Android (USB debugging aktif) atau emulator

## Cara menjalankan
1. Android Studio → **File → Open** → pilih folder ini (yang berisi `settings.gradle.kts`).
2. Tunggu **Gradle Sync** selesai. Jika diminta, klik **Install** untuk Android SDK 34.
3. Colok HP lalu klik **Run ▶**. Untuk file APK: **Build → Build APK(s)**.
4. Di aplikasi, ketuk ikon ⚙ dan tempel **Gemini API key** dari https://aistudio.google.com/apikey
   (tanpa key, 3 contoh gambar tetap jalan dalam mode demo).

## Jika Gradle bermasalah
- Baca pesan error paling atas di tab **Build**.
- Settings → Build Tools → Gradle → **Gradle JDK = 17**.
- Pastikan internet aktif, lalu **File → Invalidate Caches / Restart** dan Sync ulang.
- Jangan ubah versi plugin: AGP 8.5.2, Kotlin 1.9.24, Gradle 8.7 (sudah saling cocok).

## Struktur
```
app/src/main/
├── AndroidManifest.xml                    izin INTERNET dan CAMERA
├── java/com/pocketvisionary/MainActivity.kt   WebView, izin kamera, pemilih file
└── assets/index.html                      UI aplikasi (bisa diedit di sini)
```

## Keamanan
API key disimpan di perangkat (localStorage) dan **tidak ada di kode**. Jangan commit key ke repo. Untuk produksi, gunakan Firebase AI Logic + App Check, bukan key di klien.
