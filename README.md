# Tugas 6 Praktikum Mobile Pertemuan 8
- Nama   : Nisa Izzatul Ummah
- NIM    : H1D023034
- Shift  : D

# Hasil Screenshot
<img width="300" height="600" alt="Screenshot_1762842767" src="https://github.com/user-attachments/assets/59cacf3a-ef17-4af2-a124-ac5ce5743837" /> <img width="300" height="600" alt="Screenshot_1762842868" src="https://github.com/user-attachments/assets/752506a5-57be-4843-be15-3c19943a21c0" />

# Penjelasn Source Code
## Alur Umum
Aplikasi ini memiliki dua halaman utama:
- FormData: Halaman untuk menginput data mahasiswa.
- TampilData: Halaman untuk menampilkan data yang telah diinput.

## 1. Input Data pada Form
Pada halaman FormData, pengguna mengisi:
- Nama Lengkap → disimpan pada _namaController.text
- NIM → disimpan pada _nimController.text
- Tahun Lahir → disimpan pada _selectedTahun
Semua input dikontrol menggunakan TextEditingController dan komponen DropdownButtonFormField untuk tahun lahir.

## 2. Mengirim Data ke Halaman Tampil
Ketika tombol “TAMPILKAN DATA” ditekan, proses validasi dijalankan.
Jika data valid, maka dilakukan navigasi ke halaman TampilData menggunakan Navigator.push() berikut:

<pre> ```dartNavigator.of(context).push(
  MaterialPageRoute(
    builder: (context) => TampilData(
      nama: _namaController.text,
      nim: _nimController.text,
      tahunLahir: _selectedTahun!,
    ),
  ),
);``` </pre>

Pada baris ini, data dikirim dari form menuju halaman tampilan melalui parameter konstruktor (nama, nim, tahunLahir).

## 3. Menerima dan Menampilkan Data
Halaman TampilData menerima data tersebut melalui konstruktor:

<pre> ```dartclass TampilData extends StatelessWidget {
  final String nama;
  final String nim;
  final int tahunLahir;

  const TampilData({
    required this.nama,
    required this.nim,
    required this.tahunLahir,
  });
}``` </pre>

Data kemudian digunakan untuk ditampilkan kembali ke pengguna dan menghitung umur menggunakan:

<pre> ```dartint get umur => DateTime.now().year - tahunLahir;``` </pre>

## 4. Kembali ke Halaman Form
Saat tombol “KEMBALI KE FORM” ditekan, halaman TampilData ditutup menggunakan:

<pre> ```dartNavigator.of(context).pop();``` </pre>

Sehingga pengguna kembali ke halaman input form tanpa kehilangan data sebelumnya.

## Kesimpulan
Proses passing data dilakukan menggunakan:
- Navigator.push() untuk berpindah halaman sekaligus mengirim data.
- Konstruktor class untuk menerima data di halaman tujuan.
