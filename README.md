

## Perubahan 1 - Box Element
<img width="1280" height="76" alt="02-box-element-detail" src="https://github.com/user-attachments/assets/9c160f95-479d-4a2d-9eb0-de8a24f441a3" />




### Penjelasan

Latihan pertama membuat konsep **box element** dan **float**. Tiga `div` diberi
`float: left` sehingga berjajar horizontal, lalu `div4` diberi `clear: left`
agar turun ke baris baru di bawah ketiga div tersebut.

```css
div {
  float: left;
  padding: 10px;
}

.div1 { background: red; }
.div2 { background: yellow; }
.div3 { background: green; }

.div4 {
  background-color: blue;
  clear: left;   /* memaksa div4 turun ke bawah elemen float */
  float: none;   /* div4 tidak ikut mengambang */
  color: #fff;
}
```

**Detail CSS:**

- `float: left` membuat `div1`, `div2`, dan `div3` berderet ke samping.
- `clear: left` pada `div4` menghentikan pengaruh float di sisi kiri, sehingga
  `div4` tampil satu baris penuh di bawahnya.
- `float: none` memastikan `div4` kembali menjadi elemen normal (tidak mengambang).
- `padding: 10px` menambah ruang di dalam kotak, sehingga total lebar kotak
  bertambah (contoh penerapan box model).


---

## Perubahan 2 - Layout Sederhana Halaman Home

### Penjelasan

Membuat kerangka layout web sederhana menggunakan **HTML5 semantic elements**:
`<header>`, `<nav>`, `<section>`, `<aside>`, dan `<footer>`.

Struktur utama:

```html
<div id="container">
  <header><h1>Layout Sederhana</h1></header>
  <nav>Home | Artikel | About | Kontak</nav>
  <section id="hero">...</section>
  <section id="wrapper">
    <section id="main">...konten + 3 box + 2 artikel...</section>
    <aside id="sidebar">...widget...</aside>
  </section>
  <footer>...</footer>
</div>
```

**Detail CSS yang ditambahkan:**

1. **Reset & font** - `* { margin: 0; padding: 0; }` menghapus jarak bawaan
   browser, lalu memakai font Google `Open Sans`.
2. **Container** - `width: 980px; margin: 0 auto;` membuat konten di tengah
   halaman dan `box-shadow` memberi efek bayangan.
3. **Navigasi** - `nav` diberi background biru `#1f5faa`; link `display:
   inline-block` agar padding atas-bawah bekerja; class `.active` dan `:hover`
   berwarna lebih terang.
4. **Hero** - panel abu-abu dengan padding besar dan tombol `.btn-large`.
5. **Main & sidebar** - `#main` (`float: left`, 640px) dan `#sidebar`
   (`float: left`, 260px) diletakkan berdampingan. Total 900px + padding
   masih muat di container 980px.
6. **Footer** - `clear: both` agar footer selalu berada di bawah elemen float.
7. **Box 3 kolom** - `.box` memakai `float: left; width: 33.333333%` dan
   `box-sizing: border-box` supaya padding tidak menambah lebar.
8. **Clearfix** - `.row:after` dan `.entry:after` memakai `content: '';
   display: table; clear: both;` untuk membersihkan float tanpa elemen tambahan.
9. **Artikel** - `.entry img` mengambang kiri, `.right-img` mengambang kanan.
10. **Tombol** - `.btn`, `.btn-default`, dan `.btn-large` sebagai variasi tombol.

### Gambar

Halaman Home secara penuh:

<img width="1280" height="1407" alt="03-home" src="https://github.com/user-attachments/assets/b4831413-8a16-4023-a398-8fcbadf8398a" />

Detail hero panel:

<img width="980" height="290" alt="04-home-hero" src="https://github.com/user-attachments/assets/3912c166-a3b0-4622-bb11-037a86ae8437" />


Detail 3 box konten (float 33.33%):

<img width="660" height="280" alt="05-home-box-content" src="https://github.com/user-attachments/assets/79a45b1e-4ef3-476a-a454-526a1067c806" />


Detail artikel dengan gambar mengambang:

<img width="640" height="195" alt="06-home-artikel" src="https://github.com/user-attachments/assets/a4142d02-6876-4989-8514-dd5a327f6c7f" />


Detail sidebar dan widget:

<img width="300" height="552" alt="07-home-sidebar" src="https://github.com/user-attachments/assets/f380f11d-7b70-4008-97c9-8f6b0b8a721d" />


---

## Perubahan 3 - Halaman Artikel

### Penjelasan

Menambahkan halaman **Artikel** yang memakai ulang stylesheet `style.css`.
Halaman ini berisi tiga artikel dengan class `.entry`:

- Artikel 1 - gambar di kiri (`float: left` bawaan `.entry img`).
- Artikel 2 - gambar di kanan dengan class tambahan `.right-img`.
- Artikel 3 - gambar di kiri.

Isi `#main` diberi inline style `float:none; width:auto;` agar artikel
memakai lebar penuh (tanpa sidebar). Pemisah antar artikel memakai
`<hr class="divider">`.

### Gambar

<img width="1280" height="1046" alt="08-artikel" src="https://github.com/user-attachments/assets/41b0a348-c2ec-4d9b-b14c-5327bf45a6d8" />

---

## Perubahan 4 - Halaman About

**Commit:** `feat: halaman about, portfolio, dan skill bar`, `fix: tambahkan foto profil halaman about`
**File:** `lab4_layout/about.html`, `lab4_layout/PP pemerograman.png`

### Penjelasan

Halaman **About** berisi profil, deskripsi, portfolio, dan keahlian.
CSS tambahan ditulis di dalam `<style>` pada halaman ini:

```css
.about-profile img {
  border-radius: 50%;   /* foto profil menjadi bulat */
  width: 150px;
  height: 150px;
}

.portfolio-grid {
  display: flex;        /* portfolio sejajar dan otomatis wrap */
  flex-wrap: wrap;
  gap: 20px;
}

.portfolio-item {
  flex: 1 1 280px;      /* lebar fleksibel, minimal 280px */
}

.skill-bar span {
  display: block;
  height: 100%;
  background: #428bca;  /* lebar bar diatur inline: 90%, 85%, 70% */
}
```

**Detail CSS:**

- `.about-profile img` memakai `border-radius: 50%` agar foto berbentuk
  lingkaran, dengan ukuran tetap 150 x 150 px.
- `.portfolio-grid` memakai **flexbox** (`display: flex` + `flex-wrap`) sebagai
  alternatif float; `gap: 20px` memberi jarak antar kartu.
- `.portfolio-item` memakai `flex: 1 1 280px` supaya kartu mengisi ruang dan
  turun ke baris baru saat layar sempit.
- `.skill-bar` adalah track abu-abu; `span` di dalamnya adalah isi bar biru yang
  lebarnya diatur inline (`width: 90%`, `85%`, `70%`).
- `#main` diberi inline style `float:none; width:auto;` agar konten About
  memakai lebar penuh.
- Foto profil memakai file lokal `PP pemerograman.png` yang disertakan di
  repositori agar tidak bergantung pada gambar eksternal.

### Gambar

Halaman About secara penuh:
<img width="1280" height="1694" alt="09-about" src="https://github.com/user-attachments/assets/ffb7aee6-7eb5-4855-8c26-bc477406c809" />


Detail portfolio grid (flexbox):

<img width="920" height="548" alt="10-about-portfolio" src="https://github.com/user-attachments/assets/96e35cd7-712f-467c-9d9b-74e92b40410a" />


Detail skill bar (HTML, CSS, JavaScript):

<img width="920" height="154" alt="11-about-keahlian" src="https://github.com/user-attachments/assets/61f31ad3-fb97-415e-b7f4-093b3b59fb92" />


---

## Perubahan 5 - Halaman Kontak


### Penjelasan

Halaman **Kontak** berisi informasi kontak dan form isian dengan field:
**nama**, **email**, **subjek**, dan **pesan**, serta tombol kirim.

CSS tambahan pada halaman ini:

```css
.form-group input,
.form-group textarea {
  width: 100%;
  padding: 10px 15px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;   /* lebar input tidak melebihi container */
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: #428bca;    /* border biru saat field aktif */
  outline: none;
}

.form-group textarea {
  height: 150px;
  resize: vertical;         /* hanya bisa diubah tingginya */
}
```

**Detail CSS:**

- `box-sizing: border-box` membuat `width: 100%` tetap di dalam batas form
  meskipun ada padding dan border.
- `:focus` memberi umpan balik visual saat field sedang diisi.
- `.contact-form` dibatasi `max-width: 600px` dan `margin: 0 auto` agar form
  berada di tengah.
- `.contact-info` memakai background abu-abu muda sebagai kotak informasi.
- Atribut `required` pada nama, email, dan pesan membuat validasi bawaan browser.

### Gambar

Halaman Kontak secara penuh:

<img width="1280" height="1001" alt="12-kontak" src="https://github.com/user-attachments/assets/d6606f85-47f8-4d41-82e9-45599d59f2c6" />


Detail form kontak:

<img width="600" height="530" alt="13-kontak-form" src="https://github.com/user-attachments/assets/f4ad7a11-aa35-4763-b02e-a4e767208a02" />



---
