# Panduan Pasang & Pakai — Kasir Servis Pro v9

## Isi paket
| File | Fungsi | Taruh di mana |
|---|---|---|
| `index.html`, `sw.js`, `lacak.html`, `manifest.webmanifest`, ikon `.png` | Aplikasi (yang dibuka di HP) | **GitHub Pages** (repo publik tidak apa-apa) |
| `Code.gs` | Server + database Google Sheets | **Apps Script saja. JANGAN diunggah ke GitHub** (berisi sandi awal Owner) |
| `TATA-TERTIB-TIM*.md` | Contoh tata tertib untuk dibagikan ke tim | Bebas (cetak / kirim) |

## A. Pasang dari nol (±20 menit)
1. **Google Sheet baru** → menu *Ekstensi › Apps Script* → hapus isi, tempel seluruh `Code.gs`.
2. Ubah baris `ADMIN_PASSWORD_AWAL` (sandi Owner pertama) → simpan.
3. Jalankan fungsi **`rapikanSemua`** (izinkan akses saat diminta) → sheet & warna terbentuk.
4. Jalankan fungsi **`izinkanAkses`** sekali (memberi izin Google Drive untuk foto & cadangan harian otomatis).
5. *Terapkan › Deployment baru › Aplikasi web*: jalankan sebagai **Saya**, akses **Siapa saja**. Salin URL `/exec`.
6. Unggah `index.html`, `sw.js`, `lacak.html`, `manifest.webmanifest`, semua `.png` ke repo GitHub Pages → buka alamatnya di HP → *Tambahkan ke layar utama*.
7. Di layar login: **Atur URL server** → tempel URL `/exec` → masuk sebagai Owner (username `admin`, sandi dari langkah 2) → segera ganti sandi.
8. Ikuti kartu **Panduan awal** di tab Input (versi netral): nama toko, alamat, WA, PIN Owner, tarif bagi hasil, hubungkan Sheets.
9. *Atur › Pengguna*: buat akun Admin depan & Teknisi (tiap orang akun sendiri).

**Update versi:** tempel `Code.gs` baru → *Terapkan › Kelola deployment › Edit › Versi baru* → jalankan `rapikanSemua`. Lalu unggah file aplikasi baru ke GitHub (nomor cache di `sw.js` sudah dinaikkan).

## B. Alur harian (terima unit baru)
**Pilihan 1 — Cek dulu (default, bila kerusakan belum pasti)**
1. Admin: Input Data → isi pelanggan, unit, keluhan, kunci layar, foto kondisi, tanda tangan → pilih **Teknisi pemeriksa** (mis. Teknisi 1) → *Simpan nota* (tanpa harga). Kirim bukti terima + tautan pantau ke WA pelanggan.
2. Unit diserahkan ke teknisi pemeriksa. Teknisi cek dan melapor ke admin (lisan/WA).
3. Admin: tab Nota → buka nota → **Hasil cek teknisi**: tulis temuan, tambah **tahap tindakan** dari yang paling ringan, tiap tahap diberi *Biaya ke pelanggan* + *Modal*. Contoh Oppo A5s restart: Tahap 1 “Instal ulang” Rp100.000 modal 0; Tahap 2 “Ganti IC eMMC” Rp350.000 modal 150.000. Bila perlu *Alihkan ke teknisi lain* (mis. Expert).
4. **Kirim hasil cek (WhatsApp)** — pesan hanya memuat tindakan dan biaya (modal tidak terlihat pelanggan).
5. Pelanggan setuju/nego → centang tahap yang disetujui (ubah biaya bila nego) → **Pakai tahap yang disetujui sebagai biaya nota**. Status otomatis *Dikerjakan*.
6. Tahap 1 gagal? Centang tahap 2 (persetujuan baru) → tekan tombol pakai lagi → biaya nota menjadi gabungan tahap yang dicentang.
7. Tidak bisa diperbaiki/batal setelah cek: isi **Biaya cek saja** → *Jadikan biaya nota*.
8. Selesai → pelanggan ambil → status *Diambil* (baru saat ini omzet & bagi hasil dihitung).

**Pilihan 2 — Harga sudah pasti** (ganti LCD/baterai standar): pilih *Harga sudah pasti*, isi **Tindakan**, **Biaya ke pelanggan** (harga nego akhir, sudah termasuk modal) dan **Modal**. Laba bersih = Biaya − Modal.

## C. Aturan peran
- **Owner**: semua menu, laporan, gaji, backup, pengguna.
- **Admin depan**: input nota, hasil cek, absen, stok (tanpa harga beli), tidak melihat laba/gaji/PIN.
- **Teknisi**: hanya nota miliknya (tanpa data pelanggan), pendapatan sendiri, absen, kasbon, SOP.

## D. Yang perlu dicek sendiri setelah pasang
Printer Bluetooth, kamera/foto, tautan pantau (`lacak.html`), cadangan Drive harian, dan jam server (zona WIB) hanya bisa dipastikan di perangkat dan Google Anda sendiri. Coba 1 nota uji dari awal sampai *Diambil*, lalu hapus.

> Sandi pengguna tersimpan apa adanya di sheet **Pengguna**. Jangan bagikan akses edit Sheet ke siapa pun selain Owner.

## E. Pengingat tim (tab Nota)
- **📣 Pengingat tim** (Owner & Admin depan): centang isi (unit belum dicek, menunggu persetujuan/dikerjakan, selesai belum diambil, stok menipis, belum absen), tambah catatan, tekan **Kirim ke WhatsApp** → pilih grup tim. Isi pesan dihitung otomatis dari data saat ini.
- **Pengumuman untuk tim** (Owner): tulis pengumuman untuk Semua / Teknisi / Admin depan. Muncul sebagai banner di aplikasi anggota tim sampai ia menekan “Sudah saya baca” (status baca tersimpan di HP masing-masing; Owner tidak melihat siapa yang sudah baca). Anggota menerimanya setelah aplikasi sinkron.
- Tidak ada notifikasi dorong ke HP: pengingat dibaca saat aplikasi dibuka atau lewat pesan WhatsApp yang Anda kirim.

## F. Kondisi awal unit & laporan untuk pelanggan
- Saat terima unit isi **Catatan kondisi awal** (mis. retak sudut kiri atas) dan ambil foto (maks. 4, disimpan di Google Drive toko).
- Catatan kondisi ikut tercetak di nota.
- Di tab Nota › buka nota › kotak **Kondisi awal unit**: tombol **Bagikan laporan kondisi awal** membuat satu gambar (data unit, catatan, foto, tanda tangan) yang bisa dikirim ke WhatsApp pelanggan sebagai bukti kondisi saat diterima. Foto tidak dicetak di nota thermal.

## G. Form penerimaan unit lengkap
Isian di Input Data (semua opsional, cukup ketuk): kunci layar (tombol Tidak ada / Sandi-PIN / Pola), jenis perangkat, warna, kelengkapan yang diserahkan, kondisi fisik, kondisi unit saat diterima, fungsi bermasalah, akun terkunci (iCloud/Google/FRP), riwayat servis, prioritas, estimasi selesai, catatan kondisi awal, foto, tanda tangan. Bisa diubah/dilengkapi lagi di tab Nota › kotak “Kelengkapan & kondisi unit”. Yang tercetak di nota dan laporan kondisi awal: jenis/warna, kelengkapan, kondisi fisik, kondisi saat diterima, fungsi bermasalah, estimasi. Akun terkunci, riwayat servis dan prioritas hanya untuk internal.

## H. Kunci perangkat (login lebih aman)
- Tiap perangkat membuat **Kode Perangkat** acak (tampil di layar login, mis. `AB12-CD34`). Teknisi dan Admin depan **hanya bisa masuk dari perangkat yang disetujui Owner**.
- Alur: staf mencoba masuk (sandi benar) → perangkat tercatat “Menunggu” → Owner buka **Atur › Perangkat** → pilih ikatan (satu akun tertentu, **Semua teknisi**, atau **Semua admin depan**) → **Setujui**. Staf masuk lagi.
- Perangkat kasir hanya bisa dipakai akun kasir; perangkat teknisi hanya akun teknisi; perangkat yang terikat satu akun tidak bisa dipakai akun lain.
- Sesi terikat ke perangkat: token yang disalin ke HP/PC lain tidak berlaku. Owner bisa **Blokir** atau **Hapus** perangkat kapan saja — staf di perangkat itu langsung dikeluarkan.
- Hanya Owner yang bisa mengatur. Kunci staf bisa dimatikan sementara (kotak centang di panel). **Kunci Owner** (opsional, default mati) mengikat akun Owner ke perangkat tertentu. Terkunci? Jalankan `bukaKunciPerangkatOwner` (atau `bukaSemuaKunciPerangkat`) di editor Apps Script.
- Daftar perangkat juga ada di sheet **Perangkat**; setiap persetujuan/penolakan tercatat di Aktivitas.
- Batas: ID perangkat disimpan di browser/aplikasi (bukan nomor seri hardware). Hapus data browser = perangkat dianggap baru dan perlu disetujui lagi. Setelah memasang versi ini, semua staf harus masuk ulang dan disetujui sekali.

## I. Hak akses per peran & sistem pendapatan teknisi
| Peran | Menu | Batas |
|---|---|---|
| **Owner** | Input, Nota, Stok, **Absen**, Gaji, Biaya, Laporan, Atur (Toko & tarif, Pengguna, **Perangkat**, Printer, Sheets, Data, Aktivitas, SOP, Tata tertib) | Akses penuh ke semua menu |
| **Admin depan** | Input Data (+ 📋 Katalog harga), Nota (buat, **edit selama belum Selesai/Diambil**, cetak, WhatsApp, status), **Kasbon (hanya input kasbon baru)**, Stok (lihat), Absen, SOP, Printer/Tampilan; kartu **Tugas hari ini** di Input Data | Tidak melihat gaji, saldo/riwayat/total kasbon, biaya toko, laporan, laba, modal stok, tarif bagi hasil; tidak mengelola pengguna/perangkat. Mengubah/membatalkan nota selesai wajib PIN Owner; hapus permanen hanya Owner. Server hanya menerima data Nota darinya, ditambah baris kasbon baru (tidak bisa mengubah atau menghapus kasbon, dan tidak bisa mencatat potong gaji). Kasbon yang ia input muncul di Kasbon tim milik Owner dengan keterangan siapa yang mencatat |
| **Teknisi** | Ringkasan, Pekerjaan (nota dan penghasilannya sendiri), Absen, Kasbon (miliknya), SOP, Tertib | Hanya nota dan penghasilan miliknya sendiri; tanpa data kontak pelanggan, foto, atau gaji orang lain |
- **Sistem pendapatan teknisi** (Owner, Atur › Toko & tarif, per teknisi, termasuk Teknisi 2): **Bagi hasil saja**, **Gaji pokok + bagi hasil**, atau **Gaji pokok saja**. Pindah mode tidak menghapus persentase lama (dipulihkan bila kembali ke bagi hasil). Perubahan berlaku untuk nota baru; nota lama memakai % saat dibuat. Gaji pokok masuk perhitungan Gaji, Laporan, dan dashboard teknisi yang bersangkutan.

## J. Katalog harga jasa (Level 1, 2, 3)
- **Owner** mengatur di **Atur › Katalog harga**: nama kerusakan/layanan, kategori, dan harga untuk **Level 1 (ringan)**, **Level 2 (sedang)**, **Level 3 (berat)**. Arti tiap level bisa diubah. Isian tersimpan otomatis dan ikut tersinkron.
- Harga bawaan (14 contoh untuk Software, HP, dan Laptop) hanya **perkiraan**. Sesuaikan dengan tarif toko Anda. Tombol **Kembalikan ke contoh bawaan** ada di bawah daftar.
- **Kasir (Owner dan Admin depan)** memakainya lewat tombol **📋 Katalog harga**: di layar Input (mode Langsung) dan di nota (edit). Di kotak **Hasil cek teknisi** tombolnya bernama **📋 Dari katalog**; di sana ada pilihan **Tambahkan semua level sebagai tahap** yang membuat Tahap 1 sampai 3 berurutan dari yang paling ringan.
- Ketuk harga pada level untuk memasukkannya ke nota (nama otomatis diberi akhiran Lv1/Lv2/Lv3). Harga masih bisa diubah di nota.
- Tombol **Bagikan daftar harga (WhatsApp)** mengirim seluruh daftar harga sebagai pesan.
- Harga di katalog adalah **harga jasa**. Sparepart dicatat terpisah.
- Admin depan hanya menerima katalog bila Code.gs di Google Sheet sudah versi v10.30 atau lebih baru (tempel Code.gs terbaru, lalu Deploy versi baru).

## K. Lisensi toko dengan jatah perangkat (v10.31)
- Saat menerbitkan kode (ADOB: Atur › Lisensi), isi **Jatah perangkat**. **1** = lisensi per perangkat seperti biasa (terikat HWID). **2 atau lebih** = **lisensi toko**: kode yang sama dipakai di perangkat Owner dan staf.
- Staf menempel kode toko di layar aktivasi, lalu masuk dengan akunnya. Perangkat staf tetap harus disetujui Owner di **Atur › Perangkat**.
- Jatah dihitung dari semua perangkat berstatus Disetujui (termasuk perangkat Owner). Bila penuh, persetujuan ditolak sampai ada perangkat yang dihapus/diblokir atau lisensi diperbesar.
- Owner mengirim jatah ke server otomatis saat membuka Atur › Perangkat setelah login. Server di Google Sheet/Cara 3 yang menegakkan batas ini; untuk Code.gs perlu versi v10.31 (tempel Code.gs terbaru lalu Deploy versi baru).
- Batas: lisensi tetap diperiksa di perangkat dan bisa diakali oleh yang paham teknis. Kode toko sebaiknya hanya dibagikan ke staf.
