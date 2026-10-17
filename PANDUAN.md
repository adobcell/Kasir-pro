# Kasir Servis Pro — Panduan Pemasangan

Isi paket: `index.html` (aplikasi), `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `Code.gs` (skrip Google Sheets).

## 1. Pasang penghubung Google Sheets (±5 menit)
1. Masuk ke Gmail yang ingin dipakai, buka https://sheets.google.com lalu buat Spreadsheet kosong (nama bebas, mis. "Data Kasir Servis").
2. Menu **Ekstensi › Apps Script**. Hapus isi default, tempel seluruh isi `Code.gs`.
3. Ubah baris `var TOKEN = '...'` menjadi kode rahasia buatan Anda (mis. 16 karakter acak). Simpan (ikon disket).
4. Klik **Deploy › Deployment baru › Jenis: Aplikasi web**.
   - Jalankan sebagai: **Saya**
   - Yang memiliki akses: **Siapa saja**
5. Klik Deploy, setujui izin akses Google (jika muncul "belum diverifikasi": Lanjutan › Buka proyek). Salin **URL aplikasi web** (berakhiran `/exec`).
6. Di aplikasi: **Atur › Google Sheets**, tempel URL dan kode rahasia yang sama, lalu tekan **Hubungkan & uji**.

Sheet "Nota", "Pengeluaran", dan "Pengaturan" dibuat otomatis. Kolom terakhir `DataJSON` jangan diubah/dihapus karena dipakai untuk memulihkan data. Setelah mengubah kode skrip, buat deployment versi baru.

Catatan keamanan: siapa pun yang tahu URL dan kode rahasia dapat membaca/menulis data, jadi jangan dibagikan.

## 2. Taruh aplikasi di internet (HTTPS) agar bisa dipasang
Bluetooth dan "Pasang aplikasi" hanya bekerja lewat HTTPS. Pilih salah satu (gratis):
- **Netlify Drop**: buka https://app.netlify.com/drop, seret folder berisi semua berkas paket.
- **GitHub Pages**: unggah semua berkas ke repositori, aktifkan Pages.
- **Cloudflare Pages**: unggah sebagai proyek statis.

## 3. Pasang di HP
Buka alamat tadi di **Chrome Android** › menu ⋮ › **Pasang aplikasi**. Ikonnya muncul di layar utama dan bisa dipakai offline.

Ingin berkas APK? Buka https://www.pwabuilder.com, masukkan alamat aplikasi Anda, pilih Android, lalu unduh paketnya.

## 4. Hubungkan printer thermal
1. Nyalakan printer, aktifkan Bluetooth dan Lokasi di HP (jangan dipasangkan lewat pengaturan HP).
2. **Atur › Printer**: pilih lebar kertas (58/80 mm), tekan **Hubungkan printer**, pilih printer, lalu **Tes cetak**.
3. Aktifkan **Cetak otomatis** bila nota ingin tercetak saat disimpan.

Jika tes cetak gagal:
- Browser hanya dapat memakai printer **Bluetooth LE (BLE)**. Printer Bluetooth Classic/SPP tidak muncul. Solusi: tombol **Bagikan gambar nota** lalu pilih aplikasi printer (mis. RawBT).
- Cetak terpotong/berantakan: ubah **Kecepatan kirim** ke "Aman", atau mode cetak ke "Teks".
- Lebar tidak pas: sesuaikan 58/80 mm.

## 5. Tema & tampilan
**Atur › Tampilan**: 6 tema (Hijau Bengkel, Malam Hijau, Samudra, Senja, Mawar, Kontras Tinggi) + otomatis ikut HP, serta ukuran tulisan kecil/sedang/besar. Font ikut berganti sesuai tema.

## 6. Cadangan
Data tersimpan di HP dan disinkronkan ke Sheet. Tambahan: **Atur › Data** untuk unduh cadangan .json / CSV. Sinkron memakai aturan "data terbaru menang", dan perubahan saat offline dikirim otomatis setelah online.

## 7. Tutup buku bulanan & kinerja teknisi
- **Laporan › Tutup buku**: setelah bulan rampung, tekan "Tutup buku bulan ini". Nota, status, pengeluaran, dan gaji pokok bulan itu terkunci dan rekapnya tersimpan. Bulan berikutnya otomatis mulai dari nol. Bisa dibuka kembali bila ada koreksi.
- **Laporan › Kinerja teknisi**: jumlah unit tiap teknisi (selesai, proses, batal), pendapatan jasa, laba sparepart, dan komisinya, lengkap dengan daftar unit per teknisi.
- **Laporan › Rekap semua bulan**: ringkasan nota, omzet, laba bersih, dan status Ditutup/Terbuka tiap bulan.

## 8. Alur nota (versi terbaru)
- **Kasir**: isi pelanggan, unit, keluhan, teknisi, dan rincian. Harga otomatis tampil sebagai rupiah (150.000). Nota baru berstatus **Cek**.
- **Nota**: ubah status (Cek, Proses, Selesai, atau Batal), pilih metode pembayaran, atur masa garansi, dan **Edit nota** bila ada koreksi data.

## 9. Fitur tambahan (versi 4)
- **Kasir › Hari ini**: jumlah nota, nilai nota, unit dalam proses, unit menunggu diambil, dan rincian Tunai/Transfer/QRIS untuk dicocokkan saat tutup toko.
- **Kondisi unit & kelengkapan**: catatan kondisi fisik dan aksesori (dengan tombol cepat) tercetak di nota sebagai bukti kondisi awal.
- **Nota › Cari**: cari berdasarkan nama, nomor nota, nomor HP, perangkat, atau IMEI.
- **Nota › Belum diambil**: daftar unit Selesai yang belum diambil beserta lama menunggu. Tersedia pesan "Pengingat pengambilan unit".
- **Sandi/pola pelanggan** dihapus otomatis saat status Selesai (dan bisa dihapus manual).
- **Laporan › Modal awal & balik modal**: isi modal, lihat sisa modal dan perkiraan balik modal.
- **Atur › Keamanan**: kunci aplikasi dengan PIN 4–6 angka dan kunci otomatis.
- Perbaikan: tombol "Pakai angka awal" tidak lagi menghapus daftar bulan yang sudah ditutup buku.
