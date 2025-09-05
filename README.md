# Bookshelf API

API sederhana untuk mengelola koleksi buku menggunakan Node.js dan Hapi Framework. Proyek ini dibuat untuk submission kelas Backend Pemula Dicoding.

## Fitur

- ✨ Tambah buku baru
- 📚 Lihat semua buku dengan filter
- 🔍 Lihat detail buku berdasarkan ID  
- ✏️ Edit informasi buku
- 🗑️ Hapus buku

## Teknologi

- **Node.js** - Runtime JavaScript
- **Hapi.js** - Framework web untuk Node.js
- **nanoid** - Generator ID unik
- **ESLint** - Linter untuk kode JavaScript

## Instalasi

1. Clone repository
```bash
git clone https://github.com/farkhanmaul/bookshelf-api.git
cd bookshelf-api
```

2. Install dependencies
```bash
npm install
```

3. Jalankan server
```bash
npm start
```

Server akan berjalan di `http://localhost:5000`

## API Endpoints

### 1. Tambah Buku
```
POST /books
```

**Request Body:**
```json
{
  "name": "string (required)",
  "year": "number",
  "author": "string", 
  "summary": "string",
  "publisher": "string",
  "pageCount": "number",
  "readPage": "number",
  "reading": "boolean"
}
```

**Response Success (201):**
```json
{
  "status": "success",
  "message": "Buku berhasil ditambahkan",
  "data": {
    "bookId": "string"
  }
}
```

### 2. Lihat Semua Buku
```
GET /books
```

**Query Parameters (opsional):**
- `name` - Filter berdasarkan nama buku
- `reading` - Filter buku yang sedang dibaca (0/1)
- `finished` - Filter buku yang sudah selesai dibaca (0/1)

**Response (200):**
```json
{
  "status": "success",
  "data": {
    "books": [
      {
        "id": "string",
        "name": "string", 
        "publisher": "string"
      }
    ]
  }
}
```

### 3. Lihat Detail Buku
```
GET /books/{id}
```

**Response Success (200):**
```json
{
  "status": "success",
  "data": {
    "book": {
      "id": "string",
      "name": "string",
      "year": "number",
      "author": "string",
      "summary": "string", 
      "publisher": "string",
      "pageCount": "number",
      "readPage": "number",
      "finished": "boolean",
      "reading": "boolean",
      "insertedAt": "string",
      "updatedAt": "string"
    }
  }
}
```

### 4. Edit Buku
```
PUT /books/{id}
```

**Request Body:** (sama dengan POST /books)

**Response Success (200):**
```json
{
  "status": "success", 
  "message": "Buku berhasil diperbarui"
}
```

### 5. Hapus Buku
```
DELETE /books/{id}
```

**Response Success (200):**
```json
{
  "status": "success",
  "message": "Buku berhasil dihapus"
}
```

## Validasi

- **name** wajib diisi
- **readPage** tidak boleh lebih besar dari **pageCount**
- **finished** otomatis `true` jika **readPage** sama dengan **pageCount**

## Error Responses

**400 Bad Request:**
```json
{
  "status": "fail",
  "message": "Pesan error"
}
```

**404 Not Found:**
```json
{
  "status": "fail", 
  "message": "Buku tidak ditemukan"
}
```

## Development

Jalankan linter:
```bash
npm run lint
```

## Struktur Proyek

```
bookshelf-api/
├── src/
│   ├── books.js      # Data store (array) untuk buku
│   ├── handler.js    # Handler untuk setiap endpoint
│   ├── routes.js     # Konfigurasi routing
│   └── server.js     # Setup server Hapi
├── package.json
└── README.md
```

## Author

Dibuat oleh [farkhanmaul](https://github.com/farkhanmaul) untuk submission Backend Pemula Dicoding.
