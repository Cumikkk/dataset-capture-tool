# Dataset Capture Tool

Aplikasi desktop untuk mengambil foto dataset secara cepat menggunakan webcam atau IP Webcam (Android). Dirancang untuk keperluan pembuatan dataset klasifikasi gambar (misalnya untuk pelatihan model machine learning / deep learning).

---

## Fitur

- Koneksi ke IP Webcam (Android) atau webcam lokal (index kamera)
- Preview kamera real-time langsung di aplikasi
- Mode burst: tahan tombol untuk foto beruntun otomatis
- Rotasi frame (portrait / landscape) tanpa restart
- Penomoran file otomatis dengan format `kelas_NNNN.jpg`
- Progress bar dan counter foto yang terupdate langsung
- Indikator status koneksi kamera (terhubung / terputus)
- Validasi input sebelum sesi dimulai
- Dataset tersimpan rapi per folder kelas

---

## Persyaratan

- Python 3.8 atau lebih baru
- Library yang dibutuhkan:

  ```
  opencv-python
  Pillow
  ```

  Tkinter sudah termasuk dalam instalasi Python standar di Windows. Untuk Linux, install dengan:

  ```
  sudo apt install python3-tk
  ```

---

## Instalasi

1. Clone atau download repository ini.

2. Install dependensi:

   ```
   pip install opencv-python Pillow
   ```

3. Jalankan aplikasi:

   ```
   python main.py
   ```

---

## Cara Penggunaan

### 1. Isi Form Setup

| Field | Keterangan |
|---|---|
| Nama Kelas | Nama kategori dataset. Hanya boleh huruf, angka, `_`, dan `-`. Contoh: `apel_merah` |
| Target Foto | Jumlah foto yang ingin diambil. Harus berupa angka lebih dari 0. |
| IP Webcam / Kamera | Isi dengan alamat IP jika menggunakan IP Webcam (contoh: `192.168.1.9:8080`), atau isi `0` untuk webcam bawaan laptop/PC. |

### 2. Ambil Foto

Setelah kamera terhubung, gunakan kontrol berikut:

| Aksi | Tombol |
|---|---|
| Foto satu kali | Klik tombol / tekan `Space` lalu lepas |
| Burst mode | Tahan tombol / tahan `Space` lebih dari 0.3 detik |
| Rotasi frame | Klik tombol Rotate / tekan `R` |
| Selesai / Keluar | Klik tombol Selesai atau tutup jendela |

### 3. Hasil

Foto tersimpan di folder `dataset/<nama_kelas>/` dengan format penamaan:

```
dataset/
└── apel_merah/
    ├── apel_merah_0001.jpg
    ├── apel_merah_0002.jpg
    └── ...
```

Jika folder sudah berisi foto sebelumnya, penomoran akan dilanjutkan secara otomatis.

---

## Konfigurasi

Beberapa nilai dapat diubah langsung di bagian atas file `main.py`:

| Konstanta | Default | Keterangan |
|---|---|---|
| `PREVIEW_WIDTH` | `920` | Lebar area preview kamera (px) |
| `PREVIEW_HEIGHT` | `650` | Tinggi area preview kamera (px) |
| `BURST_HOLD_THRESHOLD` | `0.3` | Durasi tahan (detik) sebelum burst aktif |
| `BURST_INTERVAL_MS` | `150` | Jeda antar foto saat burst (milidetik) |
| `OUTPUT_BASE_DIR` | `dataset` | Folder root penyimpanan dataset |

---

## Catatan

- Saat kamera terputus, frame lama tidak akan tersimpan ke dataset. Foto hanya diambil dari frame yang valid.
- Jika IP Webcam dimasukkan tanpa protokol, aplikasi akan otomatis menambahkan `http://` dan suffix `/video`.
- File yang dihitung sebagai foto valid hanya yang sesuai format `kelas_NNNN.jpg`. File lain di folder yang sama diabaikan.
- Aplikasi tidak mendukung resize jendela agar layout preview tetap konsisten.

---

## Lisensi

Proyek ini menggunakan lisensi [MIT](LICENSE). Copyright (c) 2026 M. Fahrul Alfanani.
