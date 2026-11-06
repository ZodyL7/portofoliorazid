# Portfolio Raihan Zidan — Versi HTML & CSS Murni

Website ini dibuat **tanpa JavaScript, tanpa npm, tanpa build tool** — cuma HTML dan CSS biasa.
Tinggal buka `index.html` di browser, selesai.

Struktur halaman fokus ke 3 bagian saja, urutannya:
1. **Perkenalan** (foto + perkenalan singkat)
2. **Dokumentasi PJBL** (3 kartu proyek dengan detail)
3. **Portofolio Video Editing** (6 video TikTok yang diputar langsung di halaman)

## 📁 Struktur File

```
portfolio-html-css/
├─ index.html              ← semua isi/teks website ada di sini
├─ style.css                 ← semua tampilan/warna/layout ada di sini
├─ images/
│  ├─ foto-profil.jpg         ← foto profil kamu (sudah diisi)
│  ├─ project-lab.jpeg          ← dokumentasi maintenance lab komputer (sudah diisi)
│  ├─ project-jellyfin.png       ← screenshot dashboard Jellyfin (sudah diisi)
│  └─ project-maket.jpeg          ← foto maket input-output (sudah diisi)
└─ cv/
   └─ CV-Raihan-Zidan.pdf      ← file CV yang bisa diunduh (masih placeholder, ganti sendiri)
```

Semua foto dokumentasi PJBL dan foto profil **sudah diisi dengan foto asli kamu** — tinggal
ganti kalau suatu saat mau diperbarui, dengan cara yang sama seperti di bawah ini.

## 🖼️ Cara Ganti Foto Profil (PALING MUDAH)

**Tidak perlu edit kode sama sekali.** Caranya:

1. Siapkan foto kamu, format apapun boleh (jpg, png, dll).
2. Beri nama file itu **persis**: `foto-profil.jpg` (kalau foto kamu `.png`, tetap kasih nama
   `foto-profil.jpg` — isinya tetap akan terbaca, browser tidak mempermasalahkan ini).
3. Timpa (overwrite/replace) file lama di folder `images/` dengan file barumu.
4. Refresh browser. Selesai — tidak ada baris kode yang perlu diubah.

> ⚠️ Penyebab paling umum foto tidak muncul: nama file beda dari yang tertulis di kode
> (termasuk huruf besar/kecil — `Foto-Profil.jpg` ≠ `foto-profil.jpg`), atau file belum
> benar-benar tersimpan di folder `images/`. Kalau masih bermasalah, buka halaman di browser,
> tekan **F12** → tab **Console**, cari pesan error berwarna merah (biasanya **404**) yang
> menyebutkan nama file — itu petunjuk paling akurat soal apa yang salah.

## 🎬 Cara Ganti Video (Embed TikTok)

Video di section "Portofolio Video Editing" ditempel langsung dari TikTok pakai `<iframe>` —
videonya benar-benar bisa diputar di halaman, tanpa JavaScript.

1. Buka video TikTok kamu, lalu lihat alamat URL-nya di address bar. Formatnya kira-kira:
   ```
   https://www.tiktok.com/@username/video/7123456789012345678
   ```
2. Copy **angka panjang di bagian paling akhir** URL itu — itu adalah ID video-nya.
3. Buka `index.html`, cari tulisan `GANTI_ID_VIDEO_1` (pakai Ctrl+F), lalu ganti dengan angka
   ID video kamu. Ulangi untuk `GANTI_ID_VIDEO_2` sampai `GANTI_ID_VIDEO_6`.
4. Sambil di situ, ganti juga judul (`video-card__title`) dan penjelasan
   (`video-card__desc`) di tiap kartu dengan video dan cerita editing kamu yang sebenarnya.

> Catatan: video TikTok yang akunnya di-private tidak akan bisa muncul lewat embed. Pastikan
> video yang kamu pakai statusnya publik.

## ✏️ Cara Edit Lainnya

1. Buka folder ini di **VS Code**.
2. Edit teks lain langsung di `index.html` (judul proyek, deskripsi, dll).
3. Mau ubah warna/tampilan? Edit `style.css`, terutama bagian paling atas (`:root { ... }`)
   yang berisi variabel warna — ubah satu variabel, berubah di semua tempat yang memakainya.
4. Install extension **Live Server** di VS Code supaya setiap kamu simpan file, browser
   otomatis refresh — klik kanan `index.html` → **Open with Live Server**.

## 🧩 Beberapa Trik CSS yang Dipakai (tanpa JavaScript)

- **Menu mobile (hamburger)**: pakai trik `<input type="checkbox">` tersembunyi + `<label>`
  sebagai tombol. CSS membaca status `:checked` untuk menampilkan/menyembunyikan menu.
- **Detail proyek (modal)**: pakai trik CSS `:target`. Tombol "Lihat Detail" mengarah ke
  `#id-elemen`, lalu CSS menampilkan elemen itu saat sedang jadi target URL. Tombol tutup
  mengarah balik ke `#dokumentasi-pjbl`.
- **Video TikTok**: pakai `<iframe>` langsung ke `https://www.tiktok.com/embed/v2/ID_VIDEO` —
  ini format resmi dari TikTok untuk menampilkan video tanpa perlu script tambahan.
- **Smooth scroll**: cukup satu baris CSS `scroll-behavior: smooth;` di `html`.

Karena ini trik CSS murni (bukan JavaScript), menu mobile tidak otomatis tertutup saat kamu
klik salah satu link menu — tinggal tap ikon hamburger/X lagi untuk menutup. Ini trade-off
yang wajar untuk website tanpa JavaScript.

## 🌐 Cara Publikasi ke GitHub Pages (supaya bisa diakses orang lain)

1. **Buat akun GitHub** (jika belum punya) di [github.com](https://github.com).
2. **Buat repository baru**, misalnya beri nama `portfolio-raihan-zidan`.
3. Upload semua file di folder ini ke repository tersebut. Dua cara:
   - **Lewat browser**: di halaman repository, klik **Add file → Upload files**, lalu drag
     semua isi folder `portfolio-html-css` (bukan foldernya, tapi isinya) ke situ, lalu
     klik **Commit changes**.
   - **Lewat Git/terminal** (kalau sudah familiar):
     ```bash
     cd portfolio-html-css
     git init
     git add .
     git commit -m "Portfolio pertama"
     git branch -M main
     git remote add origin https://github.com/username-kamu/portfolio-raihan-zidan.git
     git push -u origin main
     ```
4. Di halaman repository, buka **Settings → Pages**.
5. Pada bagian **Build and deployment → Source**, pilih **Deploy from a branch**.
6. Pada **Branch**, pilih `main` dan folder `/ (root)`, lalu klik **Save**.
7. Tunggu 1–2 menit, lalu website kamu akan aktif di:
   ```
   https://username-kamu.github.io/portfolio-raihan-zidan/
   ```
   (GitHub akan menampilkan link ini otomatis di halaman Settings → Pages setelah berhasil.)

Setiap kali kamu mengubah file dan meng-upload ulang (atau `git push`), GitHub Pages akan
otomatis memperbarui website dalam beberapa menit.
