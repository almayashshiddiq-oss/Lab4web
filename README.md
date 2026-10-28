# Dokumentasi Perubahan - Lab4Web

Dokumen ini mencatat setiap perubahan pada proyek **Lab4Web (Praktikum CSS Layout)**.
Setiap perubahan dijelaskan beserta tangkapan layar (screenshot) hasilnya.

- **Mata Kuliah:** Pemrograman Web
- **Materi:** CSS Layout (Box Element, Float, HTML5 Semantic)
- **Nama:** Ash Shiddiq Al May
- **Kampus:** Universitas Pelita Bangsa
- **Screenshot:** diambil dengan Chrome headless, viewport 1280 x 900 px, dan disimpan di `docs/screenshots/`.

---

## Daftar Perubahan

| No | Commit | Perubahan | File | Gambar |
|----|--------|-----------|------|--------|
| 1 | `feat: latihan 1 - box element dengan float dan clear` | Box element: 3 div berjajar + div4 turun ke baris baru | `lab4_box.html` | [Lihat](#perubahan-1---box-element) |
| 2 | `feat: layout sederhana halaman home` | Struktur layout: header, nav, hero, main, sidebar, footer | `lab4_layout/home.html`, `lab4_layout/style.css` | [Lihat](#perubahan-2---layout-sederhana-halaman-home) |
| 3 | `feat: halaman artikel` | Halaman daftar artikel memakai style `.entry` | `lab4_layout/artikel.html` | [Lihat](#perubahan-3---halaman-artikel) |
| 4 | `feat: halaman about, portfolio, dan skill bar` | Profil, deskripsi, portfolio grid, skill bar | `lab4_layout/about.html`, `lab4_layout/PP pemerograman.png` | [Lihat](#perubahan-4---halaman-about) |
| 5 | `feat: halaman kontak dan form` | Info kontak + form (nama, email, subjek, pesan) | `lab4_layout/kontak.html` | [Lihat](#perubahan-5---halaman-kontak) |
| 6 | `docs: dokumentasi perubahan dan screenshot` | README + dokumentasi + screenshot | `README.md`, `DOKUMENTASI.md`, `docs/` | [Lihat](#perubahan-6---dokumentasi) |

---

## Perubahan 1 - Box Element

**Commit:** `feat: latihan 1 - box element dengan float dan clear`
**File:** `lab4_box.html`

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

### Gambar

Tampilan penuh halaman:

![Box element - tampilan penuh](docs/screenshots/01-box-element.png)

Detail area box (div1 - div4):

![Box element - detail div](docs/screenshots/02-box-element-detail.png)

---

## Perubahan 2 - Layout Sederhana Halaman Home

**Commit:** `feat: layout sederhana halaman home`
**File:** `lab4_layout/home.html`, `lab4_layout/style.css`

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

![Home - tampilan penuh](docs/screenshots/03-home.png)

Detail hero panel:

![Home - hero](docs/screenshots/04-home-hero.png)

Detail 3 box konten (float 33.33%):

![Home - box content](docs/screenshots/05-home-box-content.png)

Detail artikel dengan gambar mengambang:

![Home - artikel](docs/screenshots/06-home-artikel.png)

Detail sidebar dan widget:

![Home - sidebar](docs/screenshots/07-home-sidebar.png)

---

## Perubahan 3 - Halaman Artikel

**Commit:** `feat: halaman artikel`
**File:** `lab4_layout/artikel.html`

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

![Artikel - tampilan penuh](docs/screenshots/08-artikel.png)

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

![About - tampilan penuh](docs/screenshots/09-about.png)

Detail portfolio grid (flexbox):

![About - portfolio](docs/screenshots/10-about-portfolio.png)

Detail skill bar (HTML, CSS, JavaScript):

![About - keahlian](docs/screenshots/11-about-keahlian.png)

---

## Perubahan 5 - Halaman Kontak

**Commit:** `feat: halaman kontak dan form`
**File:** `lab4_layout/kontak.html`

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

![Kontak - tampilan penuh](docs/screenshots/12-kontak.png)

Detail form kontak:

![Kontak - form](docs/screenshots/13-kontak-form.png)

---

## Perubahan 6 - Dokumentasi

**Commit:** `docs: dokumentasi perubahan dan screenshot`
**File:** `README.md`, `DOKUMENTASI.md`, `docs/screenshots/*`

### Penjelasan

Menambahkan dokumentasi berupa:

- `README.md` - ringkasan praktikum, materi, struktur file, dan tautan ke
  dokumentasi perubahan.
- `DOKUMENTASI.md` - penjelasan setiap perubahan beserta screenshot (dokumen ini).
- `docs/screenshots/` - 13 gambar hasil tangkapan layar setiap halaman dan
  detail CSS-nya.

Dokumentasi ini memudahkan dosen/pembaca memahami **apa yang berubah, mengapa
diubah, dan bagaimana hasil tampilannya** tanpa harus membuka satu per satu file.

---

## Cara Melihat Riwayat Perubahan

```bash
# Melihat daftar commit
git log --oneline

# Melihat detail satu commit (kode + gambar yang ditambahkan)
git show <hash-commit> --stat
git show <hash-commit>

# Membandingkan commit terakhir dengan sebelumnya
git diff HEAD~1 HEAD
```

## Struktur Repositori

```
Lab4Web/
â”œâ”€â”€ .gitignore
â”œâ”€â”€ README.md
â”œâ”€â”€ DOKUMENTASI.md
â”œâ”€â”€ lab4_box.html
â”œâ”€â”€ docs/
â”‚   â””â”€â”€ screenshots/
â”‚       â”œâ”€â”€ 01-box-element.png
â”‚       â”œâ”€â”€ 02-box-element-detail.png
â”‚       â”œâ”€â”€ 03-home.png
â”‚       â”œâ”€â”€ 04-home-hero.png
â”‚       â”œâ”€â”€ 05-home-box-content.png
â”‚       â”œâ”€â”€ 06-home-artikel.png
â”‚       â”œâ”€â”€ 07-home-sidebar.png
â”‚       â”œâ”€â”€ 08-artikel.png
â”‚       â”œâ”€â”€ 09-about.png
â”‚       â”œâ”€â”€ 10-about-portfolio.png
â”‚       â”œâ”€â”€ 11-about-keahlian.png
â”‚       â”œâ”€â”€ 12-kontak.png
â”‚       â””â”€â”€ 13-kontak-form.png
â””â”€â”€ lab4_layout/
    â”œâ”€â”€ home.html
    â”œâ”€â”€ artikel.html
    â”œâ”€â”€ about.html
    â”œâ”€â”€ kontak.html
    â”œâ”€â”€ style.css
    â””â”€â”€ PP pemerograman.png
```


