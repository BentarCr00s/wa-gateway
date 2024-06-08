# Selamat datang di Gateway Whatsapp Multi Sesi Tanpa Kepala NodeJS

Pemasangan mudah Gateway Whatsapp multi sesi tanpa kepala dengan NodeJS

- Mendukung multi perangkat
- Mendukung multi sesi / multi nomor telepon
- Pesan anti keterlambatan
- Pesan Massal

#### Berdasarkan [wa-multi-session](https://github.com/mimamch/wa-multi-session)

## Variabel Lingkungan

Untuk menjalankan proyek ini, Anda perlu menambahkan variabel lingkungan berikut ke file .env Anda

```bash
// .env

PORT=5001 // port yang digunakan di mesin Anda
KEY=mysupersecretkey # Untuk Mengamankan Beberapa Data
```

## Instalasi dan Menjalankan

Clone proyek

```bash
  git clone https://github.com/BentarCr00s/wa-gateway
```

Buka direktori proyek

```bash
  cd wa_gateway
```

Pasang dependensi

```bash
  npm install
```

Mulai server

```bash
  npm run start
```

Buka di Browser & Mulai Sesi Baru

```bash
  http://localhost:5000/start-session?session=mysession&scan=true
```

## Referensi API

#### Tambahkan sesi baru

```bash
  GET /start-session?session=NAMA_SESI_BARU&scan=true
```

| Parameter | Tipe      | Deskripsi                               |
| :-------- | :-------- | :-------------------------------------- |
| `session` | `string`  | **Wajib**. Buat Nama Sesi Anda         |
| `scan`    | `boolean` | Tampilkan QR di Browser                 |

#### Kirim Pesan Teks

```bash
  POST /send-message
```

| Body      | Tipe     | Deskripsi                                                               |
| :-------- | :------- | :----------------------------------------------------------------------- |
| `session` | `string` | **Wajib**. Nama Sesi yang Telah Anda Buat                               |
| `to`      | `string` | **Wajib**. Nomor Telepon Penerima dengan Kode Negara (contoh: 62812345678) |
| `text`    | `string` | **Wajib**. Pesan Teks                                                  |

#### Kirim Pesan Massal

```bash
  POST /send-bulk-message
```

| Body      | Tipe     | Deskripsi                                         |
| :-------- | :------- | :-------------------------------------------------- |
| `session` | `string` | **Wajib**. Nama Sesi yang Telah Anda Buat         |
| `data`    | `array`  | **Wajib**. Array Data Pesan Objek                |
| `delay`   | `number` | Jeda Per-pesan dalam Milidetik, Default ke 5000ms |

#### Hapus sesi

```bash
  GET /delete-session?session=NAMA_SESI
```

| Parameter | Tipe     | Deskripsi                               |
| :-------- | :------- | :-------------------------------------- |
| `session` | `string` | **Wajib**. Buat Nama Sesi Anda          |

#### Dapatkan Semua ID Sesi

```bash
  GET /sessions?key=mysupersecretkey
```

| Parameter | Tipe     | Deskripsi                      |
| :-------- | :------- | :------------------------------- |
| `key`     | `string` | **Wajib**. Kunci pada file ".env" |
