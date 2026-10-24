PANDUAN INTEGRASI WEBSITE PUBLIK MASJID AL-AMIN

Isi paket:
1. website_masjid_al_amin_terintegrasi.html — versi website dengan koneksi baca-publik ke Google Sheets.
2. Code.gs — backend Apps Script dengan endpoint publicContent (hanya baca slide/galeri berstatus Publik).

PENTING: jangan unggah website sebelum memasukkan URL Web App Anda. PIN admin tidak ditaruh di HTML publik.

A. Perbarui Apps Script
1. Buka proyek Apps Script yang sekarang dipakai dashboard.
2. Ganti isi Code.gs dengan file Code.gs dari paket ini.
3. Simpan.
4. Deploy > Manage deployments > Edit (ikon pensil) > Version: New version > Deploy.
   Gunakan deployment yang sama agar URL /exec tetap sama, jika editor mengizinkan memperbarui deployment tersebut.
5. Pastikan dashboard masih bisa melakukan tes koneksi.

B. Masukkan URL API ke website
1. Buka website_masjid_al_amin_terintegrasi.html dengan editor teks/kode (misalnya VS Code).
2. Cari teks: const PUBLIC_CONTENT_API_URL = '';
3. Masukkan URL Web App /exec di antara tanda kutip, contoh: const PUBLIC_CONTENT_API_URL = 'https://script.google.com/macros/s/ID_DEPLOYMENT/exec';
4. Simpan file. Jangan masukkan PIN admin ke file website.

C. Isi konten dari dashboard
1. Di dashboard, buka Slide Foto Header. Buat atau edit slide, isi URL foto publik, atur urutan, lalu set status menjadi Publik.
2. Buka Galeri Foto. Isi URL foto, judul, kategori, keterangan, lalu set status Publik.
3. Pastikan gambar dapat dibuka langsung tanpa login. URL berbagi Google Drive biasa mungkin tidak selalu cocok; gunakan URL gambar yang dapat diakses publik.
4. Buka website terintegrasi yang di-hosting. Slide dan galeri Publik akan dimuat dari Sheets. Konten Draft/Arsip tidak dikirim ke website.

D. Perilaku cadangan
- Jika URL API belum diisi atau belum ada slide berstatus Publik, slide header bawaan tetap dipakai.
- Jika galeri belum memiliki foto Publik, galeri ilustrasi bawaan tetap ditampilkan.
- Data publik hanya dibaca; semua tambah/edit/hapus tetap melalui dashboard admin.

E. Keamanan dan pengujian
- Endpoint publicContent tidak memerlukan PIN, tetapi hanya mengembalikan kolom konten slide/galeri berstatus Publik. Jangan menyimpan data rahasia di kolom-kolom tersebut.
- Perubahan Code.gs harus dideploy sebagai versi baru sebelum website memanggil action=publicContent.
- Setelah mengunggah website, tes satu slide dan satu foto galeri berstatus Publik; kemudian ubah menjadi Draft dan pastikan tidak lagi tampil setelah refresh.
