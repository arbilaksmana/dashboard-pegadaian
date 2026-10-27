PAKET DASHBOARD + PROXY LOKAL GALERI 24

ISI PAKET
- dashboard_sinkronisasi_galeri24.html : dashboard simulasi yang sudah dilengkapi status sinkronisasi
- server.js : proxy lokal untuk mengambil halaman harga resmi Galeri 24
- package.json : dependensi Node.js

PENTING TENTANG SUMBER DATA
Proxy mengambil halaman publik https://galeri24.co.id/harga-emas dan membaca harga jual 1 gram dari tabel halaman tersebut. Ini bukan API resmi Galeri 24; ini proxy/scraper atas halaman resmi. Jika Galeri 24 mengubah struktur halaman atau memblokir akses otomatis, parsing dapat gagal. Dashboard akan menampilkan status gagal dan mempertahankan harga sebelumnya, bukan mengarang harga baru.

CARA MENJALANKAN (Windows / macOS)
1. Instal Node.js versi 18 atau lebih baru dari https://nodejs.org/
2. Ekstrak ZIP ke folder yang mudah ditemukan.
3. Buka Command Prompt / Terminal di folder hasil ekstrak.
4. Jalankan: npm install
5. Jalankan: npm start
6. Biarkan terminal tetap terbuka.
7. Buka http://127.0.0.1:8787/ di browser (server juga menyajikan file dashboard, jadi tidak perlu membuka file HTML langsung).
8. Dashboard memeriksa harga setiap 5 menit; tombol "Perbarui sekarang" memaksa pemeriksaan manual.

TES PROXY
Buka http://127.0.0.1:8787/health untuk mengecek apakah proxy berjalan.
Buka http://127.0.0.1:8787/api/gold-prices untuk melihat hasil data harga.
Buka http://127.0.0.1:8787/api/gold-prices?refresh=true untuk memaksa mengambil ulang sumber.

CATATAN
- Harga di halaman resmi dapat berubah sewaktu-waktu; interval 5 menit hanya interval pemeriksaan dashboard, bukan jaminan harga sumber berubah setiap 5 menit.
- Halaman resmi menyebut harga yang berlaku adalah harga pada sistem Galeri 24. Verifikasi ulang sebelum dipakai sebagai penawaran resmi.
- Harga Antam/UBS/Lotus hanya akan terisi bila merek dan tabelnya ditemukan pada halaman resmi; jika tidak, dashboard mempertahankan nilai terakhir untuk merek tersebut.
- Proxy menyimpan harga terakhir selama 5 menit; jika pengambilan ulang gagal, proxy tetap mengirim harga terakhir dengan penanda `stale: true` alih-alih mengarang harga baru.
- Perhitungan cicilan pada dashboard tetap simulasi dan bukan penawaran pembiayaan resmi.
