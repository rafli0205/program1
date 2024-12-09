# Membuat Program dengan Object-Oriented Programming (OOP)

# Data Diri
Nama : Rafli Dhiya Fadhaly

Nim : 312410251

Kelas : TI 24 A2
### Struktur Program
**- Direktori Program:**
  - **.veny** - Vitual Environment Python
  - **Data** - Folder berisi modul untuk mengelola data mahasiswa
    - **init.py** - File inisialisasi modul **`data`**
    - **mahasiswa.py** - File berisi class **`mahasiswa`** dan class **`DataMahasiswa**. Class **`Mahasiswa`** digunakan untuk mengelola data mahasiswa, seperti mencari, menambahkan, menghapus, dan mengubah data mahasiswa.
  - **View** - Folder berisi modul untuk menampilkan antarmuka pengguna
    - **init.py** - File inisialisasi modul **`view`**
    - **input_form.py** - File berisi class untuk menampilkan form input data mahasiswa.
    - **mahasiswa.py** - File berisi class untuk menampilkan data mahasiswa dalam bentuk list dan detail.
  - **main.py** - File berisi program utama yang menampilkan menu utama program.

### Fungsi Setiap Modul:
1. **File**: data/mahasiswa.py
   **data/mahasiswa.py**
```python
class Mahasiswa:
    def __init__(self, nama, nim, jurusan):
        self.nama = nama
        self.nim = nim
        self.jurusan = jurusan

class DataMahasiswa:
    def __init__(self):
        self.mahasiswa = []

    def tambah_mahasiswa(self, mahasiswa):
        self.mahasiswa.append(mahasiswa)
        print("Mahasiswa berhasil ditambahkan.")

    def hapus_mahasiswa(self, nim):
        mahasiswa_sebelumnya = len(self.mahasiswa)
        self.mahasiswa = [m for m in self.mahasiswa if m.nim != nim]
        if len(self.mahasiswa) < mahasiswa_sebelumnya:
            print("Mahasiswa berhasil dihapus.")
        else:
            print("Data mahasiswa dengan NIM tersebut tidak ditemukan.")

    def cari_mahasiswa(self, nim):
        for m in self.mahasiswa:
            if m.nim == nim:
                return m
        return None

    def ubah_mahasiswa(self, nim, nama_baru, jurusan_baru):
        mahasiswa = self.cari_mahasiswa(nim)
        if mahasiswa:
            mahasiswa.nama = nama_baru
            mahasiswa.jurusan = jurusan_baru
            print("Data mahasiswa berhasil diubah.")
        else:
            print("Data mahasiswa dengan NIM tersebut tidak ditemukan.")
```
**Penjelasan**
- **Data**
  - **data/mahasiswa.py**
  a.**Class** `mahasiswa`
   - Mendefinisikan model data untuk class Mahasiswa dan class DataMahasiswa. Class DataMahasiswa digunakan untuk mengelola data mahasiswa, seperti mencari, menambahkan, menghapus, dan mengubah data mahasiswa.
  b.**Class** `dataMahasiswa`
   - Class ini digunakan untuk mengelola koleksi data mahasiswa.

2. **File**: view/input_form.py
   **view/input_form.py**
```python
class InputForm:
    def tampilkan_form(self):
        print("Form Input Data Mahasiswa:")
        # Logika untuk menampilkan form input data mahasiswa
        # Misalnya, bisa ditambahkan di main.py
```
**Penjelasan**
- **View**
  - **input_form.py**
    - Class ini bertanggung jawab untuk menampilkan form input data mahasiswa kepada pengguna.
    - Metode:
      - **tampilkan_form()**: Menampilkan antarmuka pengguna untuk memasukkan data mahasiswa baru. Metode ini dapat berisi logika untuk meminta input dari pengguna, tetapi tidak diimplementasikan secara spesifik dalam contoh.

3. **File:** view/mahasiswa.py
   **view/mahasiswa.py**
```python
class TampilkanMahasiswa:
    def tampilkan_list(self, data_mahasiswa):
        print("\nDaftar Mahasiswa:")
        for m in data_mahasiswa.mahasiswa:
            print(f'Nama: {m.nama}, NIM: {m.nim}, Jurusan: {m.jurusan}')

    def tampilkan_detail(self, mahasiswa):
        print("\nDetail Mahasiswa:")
        print(f'Nama: {mahasiswa.nama}')
        print(f'NIM: {mahasiswa.nim}')
        print(f'Jurusan: {mahasiswa.jurusan}')
```
**Penjelasan**
- **view**
  - **mahasiswa.py**
    - Class ini digunakan untuk menampilkan data mahasiswa kepada pengguna.
    - Metode :
      - **`tampilkan_list(data_mahasiswa)`**: Menampilkan daftar semua mahasiswa yang ada dalam objek **`DataMahasiswa`**. Metode ini akan mencetak nama, NIM, dan jurusan dari setiap mahasiswa.
      - **`tampilkan_detail(mahasiswa)`**: Menampilkan detail dari satu objek **`Mahasiswa`**, mencetak nama, NIM, dan jurusan mahasiswa tersebut.

4. **File**: main.py
   **main.py**
```python
def main():
    data_mahasiswa = DataMahasiswa()
    tampilkan_mahasiswa = TampilkanMahasiswa()
    
    while True:
        print("\nMenu:")
        print("1. Tambah Mahasiswa")
        print("2. Hapus Mahasiswa")
        print("3. Cari Mahasiswa")
        print("4. Ubah Mahasiswa")
        print("5. Tampilkan Semua Mahasiswa")
        print("6. Keluar")
        
        pilihan = input("Pilih menu (1-6): ")
        
        if pilihan == '1':
            nama = input("Masukkan nama: ")
            nim = input("Masukkan NIM: ")
            jurusan = input("Masukkan jurusan: ")
            mahasiswa = Mahasiswa(nama, nim, jurusan)
            data_mahasiswa.tambah_mahasiswa(mahasiswa)
        
        elif pilihan == '2':
            nim = input("Masukkan NIM mahasiswa yang ingin dihapus: ")
            data_mahasiswa.hapus_mahasiswa(nim)
        
        elif pilihan == '3':
            nim = input("Masukkan NIM mahasiswa yang dicari: ")
            mahasiswa = data_mahasiswa.cari_mahasiswa(nim)
            if mahasiswa:
                print("Mahasiswa ditemukan:")
                tampilkan_mahasiswa.tampilkan_detail(mahasiswa)
            else:
                print("Data mahasiswa dengan NIM tersebut tidak ditemukan.")
        
        elif pilihan == '4':
            nim = input("Masukkan NIM mahasiswa yang ingin diubah: ")
            nama_baru = input("Masukkan nama baru: ")
            jurusan_baru = input("Masukkan jurusan baru: ")
            data_mahasiswa.ubah_mahasiswa(nim, nama_baru, jurusan_baru)
        
        elif pilihan == '5':
            tampilkan_mahasiswa.tampilkan_list(data_mahasiswa)
        
        elif pilihan == '6':
            print("Keluar dari program.")
            break  # Mengakhiri loop while
        
        else:
            print("Pilihan tidak valid, silakan masukkan angka 1-6.")


if __name__ == "__main__":
    main()
```
**Penjelasan**
- **main.py**
  - **main()**
    - Ini adalah fungsi utama yang menjalankan program/
    - Logika:
      - Menyimpan objek **`DataMahasiswa`** untuk mengelola data mahasiswa.
      - Menampilkan menu utama kepada pengguna dengan pilihan untuk menambah, menghapus, mencari, mengubah, dan menampilkan data mahasiswa.
      - Menggunakan loop untuk terus meminta input dari pengguna hingga mereka memilih untuk keluar dari program.
      - Menggunakan metode dari class **`DataMahasiswa`** dan **`TampilkanMahasiswa`** untuk melakukan operasi sesuai dengan pilihan pengguna.

### Contoh modul/pengguna

**1. Menambahkan Data**
```python
Menu:
1. Tambah Mahasiswa
2. Hapus Mahasiswa
3. Cari Mahasiswa
4. Ubah Mahasiswa
5. Tampilkan Semua Mahasiswa
6. Keluar
Pilih menu (1-6): 1
Masukkan nama: Rafli
Masukkan NIM: 123
Masukkan jurusan: ti
Mahasiswa berhasil ditambahkan.
```

**2. Menghapus data**
```python
Menu:
1. Tambah Mahasiswa
2. Hapus Mahasiswa
3. Cari Mahasiswa
4. Ubah Mahasiswa
5. Tampilkan Semua Mahasiswa
6. Keluar
Pilih menu (1-6): 2
Masukkan NIM mahasiswa yang ingin dihapus: 123
Mahasiswa berhasil dihapus.
```

**3. Cari Mahasiswa**
```python
Menu:
1. Tambah Mahasiswa
2. Hapus Mahasiswa
3. Cari Mahasiswa
4. Ubah Mahasiswa
5. Tampilkan Semua Mahasiswa
6. Keluar
Pilih menu (1-6): 3
Masukkan NIM mahasiswa yang dicari: 123
Mahasiswa ditemukan:

Detail Mahasiswa:
Nama: Rafli
NIM: 123
Jurusan: ti
```

**4. Ubah Mahasiswa**
```python
Menu:
1. Tambah Mahasiswa
2. Hapus Mahasiswa
3. Cari Mahasiswa
4. Ubah Mahasiswa
5. Tampilkan Semua Mahasiswa
6. Keluar
Pilih menu (1-6): 4
Masukkan NIM mahasiswa yang ingin diubah: 123
Masukkan nama baru: udin
Masukkan jurusan baru: ti
Data mahasiswa berhasil diubah.
```

**5. tampilkan Mahasiswa**
```python
Menu:
1. Tambah Mahasiswa
2. Hapus Mahasiswa
3. Cari Mahasiswa
4. Ubah Mahasiswa
5. Tampilkan Semua Mahasiswa
6. Keluar
Pilih menu (1-6): 5

Daftar Mahasiswa:
Nama: udin, NIM: 123, Jurusan: ti
```
