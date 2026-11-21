# Mebel POS Premium

Aplikasi Point of Sale (POS) untuk toko mebel — single file HTML + Google Sheets sync.

## Fitur

- Login 3 peran: **Pemilik** (full), **Kasir** (penjualan), **Gudang** (pembelian)
- Manajemen pengguna (khusus Pemilik)
- Kasir dengan keranjang, diskon, metode bayar, cetak nota
- Manajemen stok, pembelian, pengeluaran
- Dashboard & laporan
- Upload logo & profil toko
- Sinkronisasi opsional ke Google Sheets

## Struktur File

```
mebel-pos/
├── index.html          # Aplikasi utama (buka di browser)
├── appscript/
│   └── Code.gs         # Backend Google Apps Script
└── README.md
```

## Cara Pakai (Tanpa Google Sheets)

1. Buka `index.html` di browser
2. Login default:
   - Pemilik: `pemilik` / `pemilik123`
   - Kasir: `kasir` / `kasir123`
   - Gudang: `gudang` / `gudang123`
3. Data tersimpan di localStorage browser

## Setup Google Sheets Sync

### 1. Buat Spreadsheet

1. Buat Google Sheet baru
2. Extensions → Apps Script
3. Hapus kode default, tempel isi `appscript/Code.gs`
4. Jalankan fungsi `setupSheets()` sekali (beri izin)
5. Deploy → New deployment → Type: **Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Salin URL Web App

### 2. Hubungkan ke Aplikasi

1. Buka aplikasi → Login sebagai Pemilik
2. Masuk menu **Pengaturan**
3. Tempel URL Web App di kolom URL
4. Klik **Simpan Pengaturan**
5. Gunakan tombol **Ambil data** atau **Kirim semua data**

Setiap transaksi (penjualan, pembelian, dll) akan otomatis tersimpan ke Sheet jika URL sudah diisi.

## Default Users

| Username | Password   | Peran   |
|----------|------------|---------|
| pemilik  | pemilik123 | Pemilik |
| kasir    | kasir123   | Kasir   |
| gudang   | gudang123  | Gudang  |

Ubah/tambah user lewat menu Pengaturan (login sebagai Pemilik).

## Catatan

- Logo toko disimpan sebagai base64 di localStorage
- Untuk multi-device, gunakan sinkronisasi Google Sheets
- Apps Script harus di-deploy ulang setiap ada perubahan kode
