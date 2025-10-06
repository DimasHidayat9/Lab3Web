# Membuat Dropdown Menu dan Listbox Dengan Multiple Selection.

Pada praktikum kali ini, saya membuat sebuah form HTML yang berfungsi untuk menginput data mahasiswa dengan beberapa elemen seperti input teks, radio button, dropdown menu, dan listbox.
Selain itu, saya juga menambahkan CSS agar tampilan form menjadi lebih menarik, rapi, dan mudah digunakan oleh pengguna.


# Struktur dan Elemen Form

Bagian utama form terdapat di dalam tag `<body>`.
Saya membuat sebuah `<div>` dengan class form-container sebagai wadah utama form agar bisa diatur posisinya menggunakan CSS. Di dalamnya terdapat tag `<header>` yang menampilkan judul “Form Data Mahasiswa” di bagian atas form.
Form utama dibuat menggunakan tag `<form>` dengan atribut action="proses.php" dan method="post".
Artinya, saat tombol kirim ditekan, data akan dikirim menggunakan metode POST ke file proses.php.
Untuk mengelompokkan isi form, saya menggunakan tag `<fieldset>` dan `<legend>` dengan teks “Informasi Mahasiswa” agar terlihat seperti kotak dengan judul di bagian atasnya.


# Berikut Adalah Kode Lengkap Form Data Mahasiswa
```
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Form Dropdown & Listbox - Lab 3</title>

  <style>
  
    body {
      font-family: "Poppins", Arial, sans-serif;
      background: linear-gradient(135deg, #d4fc79, #96e6a1);
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .form-container {
      background: #ffffff;
      width: 420px;
      padding: 30px 35px;
      border-radius: 15px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
      animation: fadeIn 0.7s ease-in-out;
    }

    header {
      text-align: center;
      margin-bottom: 20px;
    }

    header h1 {
      color: #197a43;
      font-size: 26px;
      margin: 0;
      letter-spacing: 1px;
    }

    fieldset {
      border: 2px solid #197a43;
      border-radius: 10px;
      padding: 20px;
    }

    legend {
      color: #197a43;
      font-weight: bold;
      font-size: 18px;
      padding: 0 10px;
    }

    .form-group {
      margin-bottom: 18px;
    }

    label {
      display: block;
      font-weight: 600;
      color: #333;
      margin-bottom: 6px;
    }

    /* Input teks, select, dan textarea */
    input[type="text"],
    select,
    textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #197a43;
      border-radius: 6px;
      font-size: 14px;
      transition: 0.3s;
      background-color: #f9f9f9;
    }

    input[type="text"]:focus,
    select:focus,
    textarea:focus {
      outline: none;
      border-color: #125d32;
      box-shadow: 0 0 6px rgba(25, 122, 67, 0.4);
      background-color: #fff;
    }

    select[multiple] {
      height: 110px;
    }

    .gender-options {
      display: flex;
      gap: 15px;
      align-items: center;
    }

    .gender-options label {
      font-weight: normal;
      color: #333;
      margin-bottom: 0;
    }

    input[type="radio"] {
      accent-color: #197a43;
      width: 16px;
      height: 16px;
    }

    .btn-submit {
      display: block;
      width: 100%;
      background-color: #197a43;
      color: white;
      border: none;
      border-radius: 6px;
      padding: 10px;
      font-size: 15px;
      font-weight: bold;
      letter-spacing: 0.5px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .btn-submit:hover {
      background-color: #125d32;
      transform: translateY(-2px);
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(-15px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @media (max-width: 480px) {
      .form-container {
        width: 90%;
        padding: 20px;
      }
      header h1 {
        font-size: 22px;
      }
    }
  </style>
</head>

<body>
  <div class="form-container">
    <header>
      <h1>Form Data Mahasiswa</h1>
    </header>

    <form action="proses.php" method="post">
      <fieldset>
        <legend>Informasi Mahasiswa</legend>

        <div class="form-group">
          <label for="nama">Nama Lengkap</label>
          <input type="text" id="nama" name="nama" placeholder="Masukkan nama lengkap Anda">
        </div>

        <div class="form-group">
          <label>Jenis Kelamin</label>
          <div class="gender-options">
            <input type="radio" id="Laki-laki" name="kelamin" value="Laki-laki">
            <label for="Laki-laki">Laki-laki</label>

            <input type="radio" id="Perempua" name="kelamin" value="Perempua">
            <label for="Perempua">Perempuan</label>
          </div>
        </div>

        <div class="form-group">
          <label for="jurusan">Jurusan</label>
          <select id="jurusan" name="jurusan">
            <option value="">-- Pilih Jurusan --</option>
            <option value="TI">Teknik Informatika</option>
            <option value="SI">Sistem Informasi</option>
            <option value="TE">Teknik Elektro</option>
            <option value="MI">Manajemen Informatika</option>
          </select>
        </div>

        <div class="form-group">
          <label for="hobi">Hobi</label>
          <select id="hobi" name="hobi[]" multiple>
            <option value="membaca">Membaca</option>
            <option value="olahraga">Olahraga</option>
            <option value="menulis">Menulis</option>
            <option value="musik">Musik</option>
            <option value="gaming">Gaming</option>
            <option value="traveling">Traveling</option>
          </select>
        </div>

        <button type="submit" class="btn-submit">Kirim Data</button>
      </fieldset>
    </form>
  </div>
```

</body>
</html>


# Hasil Output
<img width="1920" height="1080" alt="Screenshot (115)" src="https://github.com/user-attachments/assets/4121cf43-551a-43b3-a07b-91f2fb7bccc4" />


# Penjelasan Kode dan Fungsinya

Pada bagian awal kode, saya menggunakan tag `<!DOCTYPE html>` untuk menentukan bahwa dokumen ini ditulis menggunakan HTML5. Tag `<html lang="id">` menandakan bahwa bahasa utama yang digunakan dalam halaman ini adalah Bahasa Indonesia.
Di dalam bagian `<head>`, terdapat elemen `<meta>` yang mengatur karakter UTF-8 agar mendukung teks Bahasa Indonesia, serta viewport agar tampilan halaman tetap responsif di berbagai perangkat. Kemudian, saya menuliskan judul halaman di tag `<title>` dan memasukkan kode CSS di dalam tag `<style>` agar tampilan halaman menjadi lebih menarik.


# Input Nama Lengkap

Bagian pertama dari form adalah input teks untuk mengisi nama lengkap.
Kode yang digunakan adalah:
```
<input type="text" id="nama" name="nama" placeholder="Masukkan nama lengkap Anda">
```
Tag `<input type="text">` digunakan untuk menerima input teks satu baris.
Atribut placeholder memberikan petunjuk singkat di dalam kotak teks agar pengguna tahu apa yang harus diisi.


# Jenis Kelamin (Radio Button)

Selanjutnya, saya menambahkan dua buah radio button untuk memilih jenis kelamin, yaitu “Pria” dan “Wanita”.
Radio button hanya bisa dipilih satu dari dua opsi, dan keduanya menggunakan atribut name="kelamin" agar saling terhubung.
Contoh kodenya:
```
<input type="radio" id="pria" name="kelamin" value="Pria">
<label for="pria">Pria</label>

<input type="radio" id="wanita" name="kelamin" value="Wanita">
<label for="wanita">Wanita</label>
```
Saya juga membuat class gender-options di CSS agar posisi radio button dan label-nya sejajar dan terlihat rapi secara horizontal.


# Dropdown Jurusan

Setelah itu, saya menambahkan elemen dropdown menu menggunakan tag `<select>` dan `<option>`.
Dropdown digunakan untuk memilih salah satu jurusan yang tersedia seperti Teknik Informatika, Sistem Informasi, Teknik Elektro, dan Manajemen Informatika.
```
<select id="jurusan" name="jurusan">
  <option value="">-- Pilih Jurusan --</option>
  <option value="TI">Teknik Informatika</option>
  <option value="SI">Sistem Informasi</option>
  <option value="TE">Teknik Elektro</option>
  <option value="MI">Manajemen Informatika</option>
</select>
```
Penggunaan dropdown ini membuat pilihan lebih ringkas dan efisien karena hanya menampilkan satu opsi pada awalnya.


# Listbox Hobi (Multiple Selection)

Untuk menampilkan daftar hobi, saya menggunakan elemen listbox dengan atribut multiple.
Dengan cara ini, pengguna bisa memilih lebih dari satu hobi dengan menekan tombol Ctrl (di Windows) atau Command (di Mac).
Berikut contohnya:
```
<select id="hobi" name="hobi[]" multiple>
  <option value="membaca">Membaca</option>
  <option value="olahraga">Olahraga</option>
  <option value="menulis">Menulis</option>
  <option value="musik">Musik</option>
  <option value="gaming">Gaming</option>
  <option value="traveling">Traveling</option>
</select>
```
Atribut name="hobi[]" menunjukkan bahwa data hobi yang dipilih akan dikirim dalam bentuk array.


# Tombol Kirim Data

Bagian terakhir form adalah tombol kirim, yang dibuat menggunakan tag `<button>` dengan class btn-submit.
Tombol ini berfungsi untuk mengirim semua data yang telah diisi oleh pengguna.
```
<button type="submit" class="btn-submit">Kirim Data</button>
```
CSS pada tombol ini membuat tampilannya berwarna hijau dengan efek hover yang sedikit membesarkan dan menambah bayangan agar terlihat interaktif.


# Penjelasan CSS

Agar form terlihat menarik dan tidak monoton, saya menambahkan CSS styling langsung di dalam tag `<style>`.

1. Bagian body diberi background gradasi hijau lembut (linear-gradient(135deg, #d4fc79, #96e6a1)) agar tampilan lebih hidup. Form juga dibuat berada di tengah halaman dengan properti display: flex; justify-content: center; align-items: center;.
2. Class .form-container digunakan sebagai wadah utama form. Bagian ini diberi warna putih, sudut melengkung (border-radius: 15px), dan efek bayangan (box-shadow) agar terlihat seperti kartu (card).
3. Bagian `<fieldset>` dan `<legend>` digunakan untuk memberi batas dan judul pada isi form, serta diberi warna hijau sesuai tema.
4. Elemen input dan dropdown memiliki border berwarna hijau, latar belakang abu-abu muda, serta efek sorotan hijau saat diklik (focus).
5. Radio button didesain menggunakan properti accent-color: #197a43; agar warnanya senada dengan tema hijau form.
6. Tombol kirim diberi warna hijau tua dengan efek hover yang sedikit mengubah warna dan menambah bayangan, membuat tombol terlihat responsif saat diarahkan kursor.
7. Terakhir, saya menambahkan animasi fade-in agar form muncul secara halus ketika halaman dibuka.


# Kesimpulan

Melalui praktikum ini, saya belajar cara membuat form HTML dengan berbagai elemen seperti input text, radio button, dropdown, dan listbox multiple.
Saya juga memahami cara mempercantik tampilan menggunakan CSS internal, seperti memberi warna, border, padding, serta efek animasi.
Dengan menerapkan kombinasi HTML dan CSS ini, form menjadi tidak hanya fungsional tetapi juga menarik secara visual dan nyaman digunakan oleh pengguna.
