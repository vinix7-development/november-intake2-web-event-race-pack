# Web Event Race Pack

Judul: Rancang Bangun Portal Web Direktori, Pendaftaran, dan Manajemen Race Pack
Event Lari & Marathon Lokal

## Aktor
- Pengunjung: melihat direktori event tanpa login
- Pelari (peserta): mendaftar, membayar, mengunduh e-ticket, mengambil race pack
- Penyelenggara (EO): membuat event, mengelola kategori, kuota, peserta, dan race pack
- Petugas pengambilan race pack: memindai QR dan mencatat serah terima
- Admin platform: memverifikasi penyelenggara dan event, mengelola master data

## 1. Direktori event
- Daftar event dengan filter kota, tanggal, kategori jarak (5K/10K/HM/FM), dan status pendaftaran
- Detail event: rute (peta), jadwal, harga per kategori, kuota tersisa, isi race pack, FAQ
- Kalender event dan pencarian
- Label status: segera dibuka, early bird, dibuka, kuota penuh, ditutup, selesai

## 2. Pendaftaran peserta
- Akun pelari dengan profil yang tersimpan (data diri, kontak darurat, golongan darah opsional)
- Formulir pendaftaran per kategori: ukuran jersey, kontak darurat, persetujuan waiver
- Pendaftaran kolektif/komunitas (satu pembayar, banyak peserta)
- Harga bertingkat (early bird, normal) dan kode promo
- Kuota per kategori yang aman dari overbooking (transaksi + lock)
- Pembayaran lewat payment gateway (Midtrans/Xendit sandbox), batas waktu bayar, auto-expire
- E-ticket/bukti pendaftaran dengan QR code unik; nomor BIB dibagikan otomatis per kategori
- Email notifikasi: pendaftaran, pembayaran berhasil, pengingat pengambilan race pack

## 3. Manajemen race pack (inti sistem)
- Penyelenggara mengatur isi race pack per kategori (BIB, jersey, medali, goodie bag)
- Rekap stok jersey per ukuran berdasarkan data pendaftaran
- Jadwal dan lokasi pengambilan (RPC - Race Pack Collection), bisa dibagi per slot
- Pemindaian QR oleh petugas dari HP (web kamera), verifikasi identitas, tanda serah terima
- Pengambilan diwakilkan: surat kuasa/foto KTP + QR milik peserta
- Status per peserta: belum diambil, sudah diambil (waktu, petugas, penerima)
- Dashboard real-time: jumlah sudah/belum diambil, per kategori dan per ukuran jersey
- Mencegah pengambilan ganda (satu QR hanya bisa dipakai sekali)

## 4. Panel penyelenggara (EO)
- CRUD event, kategori, harga, kuota, dan promo
- Daftar peserta, pencarian, ekspor CSV/Excel
- Laporan keuangan pendaftaran per kategori
- Broadcast pengumuman ke peserta
- Unggah hasil lomba (CSV) agar peserta bisa melihat waktu finisnya (opsional)

## 5. Panel admin platform
- Verifikasi akun penyelenggara dan persetujuan event sebelum tampil di direktori
- Master data kota, kategori jarak, ukuran jersey
- Statistik platform: jumlah event, peserta, transaksi

## Nilai tambah teknis
- QR code bertanda tangan (HMAC) agar tidak bisa dipalsukan
- Mode pemindaian tahan sinyal lemah di lokasi RPC
- Audit log setiap serah terima race pack

## Di luar lingkup MVP
- Timing chip/RFID, live tracking, aplikasi mobile native

## Prototipe (canvas desain, 7 halaman)
https://claude.ai/artifact/VHTQ3LELtHVhsahRn3cDrP

Halaman: Direktori event, Detail event, Pendaftaran & pembayaran, Tiket saya (e-ticket + QR),
Petugas scan race pack (mobile), Dashboard penyelenggara (race pack), Admin platform.
Data di prototipe bersifat fiktif.
