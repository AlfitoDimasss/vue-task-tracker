# Vue Task Tracker

Vue Task Tracker adalah aplikasi pelacak tugas sederhana berbasis web yang dikembangkan menggunakan Vue.js.

## Fitur Utama

- Tambahkan dan hapus tugas.
- Tandai tugas sebagai tugas penting.

## Stack dan Package yang Digunakan

- **Vue.js**: Library JavaScript yang digunakan untuk membangun antarmuka pengguna.
- **Vue Router**: Untuk manajemen rute aplikasi web.
- **JSON Server**: Untuk pembuatan server REST API (_Back-end_) sederhana dari file .JSON, untuk keperluan CRUD.

## Instalasi

1. Pastikan Anda memiliki Node.js dan npm terinstal.
2. Clone repositori ini ke lokal Anda dengan menjalankan
   perintah: `git clone https://github.com/username/vue-task-tracker.git`
3. Masuk ke direktori proyek: `cd vue-task-tracker`
4. Instal dependensi dengan menjalankan perintah: `npm install`

## Penggunaan

1. Jalankan server _back-end_ dengan perintah: `npm run server`
2. Pada terminal lainnya, jalankan aplikasi dengan perintah: `npm run dev`
3. Buka browser dan navigasikan ke `http://localhost:3000`
4. Anda sekarang dapat menambahkan dan menghapus tugas. Anda juga dapat merubah status tugas sebagai tugas penting
   dengan cara menekan 2 kali pada tugas yang akan diubah. Perubahan akan tersimpan pada file `db.json`.
