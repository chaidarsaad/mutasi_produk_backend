# 📦 Aplikasi Manajemen Mutasi Produk (Laravel REST API) + Filament Admin Panel + Scramble for API Documentation

Sistem REST API berbasis Laravel untuk manajemen produk, lokasi gudang, dan mutasi stok antar lokasi. Autentikasi menggunakan Laravel Sanctum, dan semua layanan dijalankan via Docker. Selain itu, tersedia **Filament Admin Panel** untuk kebutuhan dashboard berbasis web (GUI).

---

## 🔄 Alur Aplikasi

1. **Autentikasi**

    - Register & Login via API (menghasilkan token Bearer)
    - Token digunakan untuk akses endpoint setelah login

2. **Produk**

    - Tambah/edit produk: nama, harga beli/jual, barcode, deskripsi, satuan, gambar (opsional)
    - Produk dapat memiliki lebih dari satu kategori
    - Produk juga memiliki stok per lokasi (via pivot `produk_lokasi`)

3. **Lokasi**

    - Menyimpan info lokasi gudang: nama, alamat, dan keterangan

4. **Mutasi**

    - Jenis: `masuk`, `keluar`
    - Status: `pending`, `approved`, `cancelled`
    - Approval akan menambah/mengurangi stok produk sesuai jenis
    - Menyimpan user pencatat (`user_id`) dan pembuat (`created_by`)

5. **Kategori Produk**

    - Produk dapat memiliki banyak kategori (many-to-many)

6. **Filament Admin Panel**
    - GUI berbasis web untuk mengelola data produk, lokasi, kategori, mutasi dan role
    - Otentikasi login menggunakan user Laravel biasa

---

## ⚙️ Cara Instalasi & Menjalankan (Docker)

### 1. Clone Repository

```bash
git clone https://github.com/chaidarsaad/mutasi_produk_backend.git
cd nama-project
cp .env.example .env
docker-compose up -d --build
docker exec -it <nama_container_app> bash
composer install
php artisan key:generate
php artisan migrate --seed
```

🔐 API Endpoint
Akses melalui Postman atau aplikasi klien:
http://localhost:8000/api

🔐 Docs API
Akses melalui Postman atau aplikasi klien:
http://localhost:8000/docs/api

🌐 Filament Admin Panel
Akses dashboard admin Filament di:
http://localhost:8000/admin

Dokumentasi postman:
https://blue-equinox-229547.postman.co/workspace/My-Workspace~6c1a8dc9-09cd-46f7-8d5a-ca34aee3952e/collection/20561574-06e400eb-893c-4c62-b26b-70288765edf6?action=share&creator=20561574&active-environment=20561574-27f275d7-015d-4990-a306-7c990ef2ecb4

Link uji coba:
https://www.mutasi-produk.genzproject.my.id
