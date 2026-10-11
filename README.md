# BPJS Ketenagakerjaan JHT Professional Calculator & Audit Simulator

Sebuah aplikasi web *single-file* berbasis HTML, Tailwind CSS, dan JavaScript murni yang dirancang untuk mensimulasikan, memproyeksikan, dan mengaudit saldo Jaminan Hari Tua (JHT) BPJS Ketenagakerjaan. Aplikasi ini ditujukan bagi profesional HR, Akuntan, dan Penilai Aktuaria untuk melakukan rekonsiliasi dan estimasi cadangan kompensasi purnakarya.

## 🌟 Fitur Utama

* **Real-time Actuarial Engine:** Perhitungan bunga majemuk bulanan secara instan berdasarkan parameter input.
* **Regulasi Terkini:** Menggunakan basis aturan proporsi iuran standar (3,7% Pemberi Kerja, 2,0% Pekerja) sesuai regulasi yang berlaku.
* **Eskalasi Upah (Wage Growth):** Mendukung perhitungan proyeksi kenaikan gaji tahunan.
* **Visualisasi Komprehensif:** Dilengkapi grafik area interaktif (menggunakan Chart.js) yang memisahkan proporsi "Pokok Iuran" dan "Hasil Pengembangan (Bunga)".
* **Tabel Audit Fleksibel:** Menampilkan jadwal akumulasi dalam mode **Ringkasan Tahunan** maupun **Rincian Bulanan**.
* **Ekspor Data (CSV):** Unduh hasil simulasi dalam format `.csv` untuk keperluan rekonsiliasi lebih lanjut di Microsoft Excel atau sistem ERP.
* **Konvensi Setoran:** Opsi penyesuaian bobot prorata hari mengendap (Awal, Tengah, atau Akhir bulan).

## ⚖️ Dasar Hukum & Regulasi

Aplikasi ini menggunakan kerangka matematis yang merujuk pada:
* **PP No. 46 Tahun 2015** tentang Penyelenggaraan Program Jaminan Hari Tua.
* **PP No. 60 Tahun 2015** tentang Perubahan atas PP No 46 Tahun 2015.

*Disclaimer: Aplikasi ini bersifat simulasi awal (initial checking). Hasil aktual dari BPJS Ketenagakerjaan dapat memiliki deviasi minor karena tanggal cut-off kliring bank, fluktuasi floating yield, dan kebijakan pembulatan.*

## 🧮 Model Matematis

Mesin simulasi menggunakan formula dasar akumulasi bulanan sebagai berikut:

**1. Formula Saldo Bulanan**
$$S_t = S_{t-1} + H_t + I_t$$

* $S_t$: Saldo pada akhir bulan ke-$t$
* $S_{t-1}$: Saldo pada akhir bulan sebelumnya
* $H_t$: Hasil pengembangan (bunga) bulan berjalan
* $I_t$: Total iuran baru bulan berjalan (5,7% dari upah)

**2. Formula Hasil Pengembangan (Prorata)**
$$H_t = \left( S_{t-1} \times r_m \right) + \left( I_t \times r_m \times \frac{d}{D} \right)$$

* $r_m$: Suku bunga bulanan efektif ($r_{\text{tahunan}} / 12$)
* $d/D$: Konvensi waktu setoran (Faktor prorata hari mengendap)

## 🚀 Cara Penggunaan

Aplikasi ini bersifat mandiri (standalone/single-file) dan tidak membutuhkan server atau instalasi *backend*.

1. Unduh atau salin kode file `jht_calculator_audit.html`.
2. Buka file tersebut menggunakan web browser modern (Google Chrome, Mozilla Firefox, Safari, atau Microsoft Edge).
3. Pastikan perangkat Anda terhubung ke internet saat pertama kali membuka, karena aplikasi perlu memuat *library* eksternal (Tailwind CSS, Chart.js, Lucide Icons, dan Google Fonts) melalui CDN.
4. Masukkan parameter gaji, masa kerja, dan asumsi bunga pada panel sebelah kiri. Grafik dan tabel akan diperbarui secara otomatis (*real-time*).

## 🛠️ Tech Stack

* **Markup/Styling:** HTML5, [Tailwind CSS](https://tailwindcss.com/) (via CDN)
* **Interactivity/Logic:** Vanilla JavaScript (ES6)
* **Data Visualization:** [Chart.js](https://www.chartjs.org/)
* **Icons & Typography:** [Lucide Icons](https://lucide.dev/), Google Fonts (Plus Jakarta Sans, JetBrains Mono)

## 📄 Lisensi

Proyek ini bersifat *open-source* dan bebas digunakan, dimodifikasi, serta didistribusikan untuk keperluan audit internal maupun edukasi.