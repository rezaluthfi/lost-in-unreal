# Lost In Unreal - UAS Praktikum Pengembangan Game

Project ini adalah tugas akhir (UAS) mata kuliah Pengembangan Game. Game ini merupakan platformer 3D sederhana yang dibuat menggunakan **Unreal Engine 5** dengan fokus pada implementasi logika Blueprint, UI System, dan Game State Management.

## 🎮 Fitur Utama

### 1. Core Gameplay
*   **Objective:** Mengumpulkan seluruh koin yang tersebar di level untuk memenangkan permainan.
*   **Obstacle:** Rintangan yang mematikan. Jika pemain menabrak, karakter akan mati (Ragdoll physics) dan level akan restart otomatis.
*   **HUD:** Menampilkan Health Bar secara real-time.

### 2. Advanced UI System (Poin Utama)
*   **Win Condition (Animation):**
    *   Menggunakan **Timeline** dan **Lerp** untuk transisi efek *Background Blur* secara halus saat pemain menang.
    *   Otomatis mem-pause game dan menampilkan kursor mouse.
*   **Main Menu:**
    *   Menggunakan **3D Camera Actor** sebagai background menu (Live Background).
    *   Fitur tombol *Play* dan *Quit* dengan Alert Popup ("Are you sure?").
    *   Desain responsif (Anchors & Alignment).
*   **Pause Menu:**
    *   Dapat dipanggil kapan saja menggunakan tombol **'M'**.
    *   Menggunakan logika **FlipFlop** untuk Toggle Pause/Unpause.
    *   Memastikan keyboard tetap aktif saat pause (*Execute when Paused*) agar pemain bisa Resume kembali.

### 3. Technical Implementation
*   **Input Mode Management:** Penanganan transisi yang mulus antara `Game Only`, `UI Only`, dan `Game And UI` untuk mencegah bug kontrol karakter.
*   **GameMode Separation:** Menggunakan `GM_Menu` (tanpa Pawn) untuk Main Menu dan `ThirdPersonGameMode` untuk Level gameplay agar logic karakter tidak berjalan di menu.
*   **Mouse Cursor Handling:** Logika pembersih (*Cleaner*) di `BeginPlay` untuk memastikan kursor mouse hilang saat masuk gameplay dan muncul saat di menu.

## 🕹️ Kontrol (Controls)

| Tombol | Fungsi |
| :--- | :--- |
| **W, A, S, D** | Bergerak |
| **Space** | Lompat |
| **M** | Pause / Resume Menu |
| **Mouse** | Mengarahkan Kamera & Interaksi UI |

## 🛠️ Setup & Instalasi

1.  Clone repositori ini atau download sebagai ZIP.
2.  Pastikan Anda memiliki **Unreal Engine 5** (Versi yang sesuai) terinstal.
3.  Klik kanan pada file `.uproject` -> **Generate Visual Studio project files**.
4.  Buka file `.uproject`.
5.  Tunggu *Shaders Compilation* selesai.
6.  Buka folder `Content/Maps` dan jalankan `Map_MainMenu` untuk memulai dari awal.

## 📂 Struktur Blueprint Penting

*   `BP_ThirdPersonCharacter`: Logic utama pergerakan, sistem koin, kondisi menang (WinProcess), dan Pause logic.
*   `WBP_GameUI`: Widget untuk Pause Menu dan Win Screen (mengandung efek Blur).
*   `WBP_HUD`: Tampilan skor koin dan darah.
*   `BP_Coin`: Logic item pickup dan komunikasi ke karakter (Cast to Character).
*   `GM_Menu`: GameMode khusus untuk Main Menu agar karakter tidak spawn.
---
**Developed by Reza Luthfi Akbar**
