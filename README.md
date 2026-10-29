# Catatan Pengeluaran - Proyek APK (Capacitor)

Isi folder `www/` adalah aplikasinya (index.html). Capacitor membungkusnya menjadi APK Android.

## Cara A - Build di komputer (Android Studio)
Butuh: Node.js 18+, Android Studio (sudah termasuk JDK 17).

    npm install
    npx cap add android
    npx cap sync android
    npx cap open android

Di Android Studio: Build > Build Bundle(s) / APK(s) > Build APK(s).
Hasil: android/app/build/outputs/apk/debug/app-debug.apk

Atau lewat terminal:

    cd android
    ./gradlew assembleDebug      (Windows: gradlew.bat assembleDebug)

## Cara B - Build gratis tanpa Android Studio (GitHub Actions)
1. Buat repositori baru di github.com, unggah seluruh isi folder ini (termasuk .github).
2. Buka tab Actions > "Build APK" > Run workflow (atau otomatis saat push ke branch main).
3. Setelah selesai (sekitar 3-5 menit), unduh "catatan-pengeluaran-apk" dari bagian Artifacts, ekstrak, lalu pasang app-debug.apk di HP.

## Memasang di HP
Kirim app-debug.apk ke HP, buka, izinkan "Instal dari sumber tidak dikenal", lalu pasang.

## Mengubah nama / ID aplikasi
Edit capacitor.config.json (appId dan appName) SEBELUM menjalankan `npx cap add android`.
appId harus unik, misalnya com.namaanda.catatanpengeluaran.

## Mengubah isi aplikasi
Edit www/index.html, lalu jalankan `npx cap sync android` dan build ulang.

## Catatan
- Data tersimpan di penyimpanan aplikasi pada HP (localStorage), tidak ada server.
- Tombol "Unduh CSV" tidak berfungsi di WebView Android. Jika perlu, tambahkan plugin @capacitor/filesystem dan @capacitor/share.
- APK debug cukup untuk dipakai pribadi. Untuk Google Play, buat APK/AAB release yang ditandatangani lewat Android Studio.
