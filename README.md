# Bijak Sampah

Website Edukasi Pengelolaan Sampah Rumah Tangga
**SDG 11 (Kota dan Permukiman Berkelanjutan) dan SDG 12 (Konsumsi dan Produksi Bertanggung Jawab)**

Proyek UTS Mata Kuliah Pemrograman Web: *Responsive Educational Website*.

## Anggota Kelompok

Kelompok [nomor], [nama kampus / program studi]

| No | Nama | NIM | Tugas |
|----|------|-----|-------|
| 1 | [Nama Anggota 1] | [NIM] | Struktur HTML Beranda dan Edukasi |
| 2 | [Nama Anggota 2] | [NIM] | CSS, layout, media queries |
| 3 | [Nama Anggota 3] | [NIM] | Konten Panduan dan Artikel, riset sumber |
| 4 | [Nama Anggota 4] | [NIM] | GitHub, README, pengujian responsif |

## Deskripsi Website

- **Tujuan:** membantu masyarakat memahami jenis sampah, dampaknya, dan langkah praktis mengelolanya dari rumah.
- **Manfaat:** menambah pengetahuan, memberi panduan yang bisa langsung dipraktikkan, dan mendukung SDG 11 dan 12.
- **Sasaran pengguna:** keluarga, remaja, dan warga yang baru mulai memilah sampah.

## Halaman Website

| Halaman | File | Isi |
|---------|------|-----|
| Beranda | `index.html` | Hero + ajakan, pengantar isu SDG 11 dan 12, kartu menuju halaman lain |
| Edukasi | `edukasi.html` | Jenis sampah (organik, anorganik, B3), fakta dan dampak, prinsip 5R |
| Panduan Praktis | `panduan.html` | Langkah memilah, tutorial kompos, tips kreatif dan peluang usaha |
| Artikel dan Inisiatif | `artikel.html` | Artikel mikroplastik dan bank sampah, infografis, studi kasus |
| Tentang dan Referensi | `tentang.html` | Profil proyek, identitas kelompok, referensi dan atribusi aset |

## Teknologi

HTML5 semantik, CSS3 eksternal, Flexbox, CSS Grid, CSS Media Queries. Tanpa framework, tanpa template, tanpa JavaScript.

## Penjelasan Implementasi

### 1. HTML semantik
Setiap halaman memakai `header`, `nav`, `main`, `section`, `article`, dan `footer`. Elemen semantik membuat struktur halaman jelas bagi pembaca layar dan mesin pencari. Heading disusun berurutan (satu `h1`, lalu `h2`, `h3`).

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
Baris ini wajib agar browser HP memakai lebar layar sebenarnya. Tanpa ini, halaman tampil seperti versi desktop yang diperkecil.

### 2. Navigasi konsisten
Menu yang sama ada di kelima halaman. Halaman yang sedang dibuka ditandai dengan `aria-current="page"`, lalu diberi gaya khusus lewat CSS.

```css
.menu a[aria-current="page"] { background: var(--krem); color: var(--hijau-tua); }
```

### 3. Variabel CSS
Warna dan font disimpan di `:root` sehingga seluruh tema bisa diubah dari satu tempat.

```css
:root { --hijau-tua: #1f4d2b; --krem: #f7f3e8; }
body  { background: var(--krem); }
```

### 4. Flexbox
Dipakai untuk bar navigasi: logo di kiri, menu di kanan, sejajar vertikal.

```css
.bar-nav { display: flex; align-items: center; justify-content: space-between; }
```

### 5. CSS Grid
Kartu otomatis menyesuaikan jumlah kolom tanpa media query. Kolom minimal 250 px, sisanya dibagi rata.

```css
.grid { display: grid; gap: 1.25rem; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); }
```

### 6. Media Queries
Pada lebar 900 px ke bawah (tablet), layout dua kolom menjadi satu kolom dan menu berubah menjadi tombol "Menu". Pada 640 px ke bawah (smartphone), tombol dibuat selebar layar dan batang infografis disusun ulang.

```css
@media (max-width: 900px) {
  .grid-2 { grid-template-columns: 1fr; }
  .tombol-menu { display: block; }
  .menu { display: none; }
  .cek-menu:checked ~ .menu { display: flex; }
}
```

### 7. Menu hamburger tanpa JavaScript
Checkbox tersembunyi menyimpan status buka/tutup. Saat dicentang (`:checked`), menu ditampilkan. Selektor `~` memilih saudara yang muncul setelah checkbox.

### 8. Infografis dengan CSS murni
Lebar batang dihitung dari variabel `--nilai` yang ditulis di HTML.

```html
<div class="isi" style="--nilai:40"></div>
```
```css
.isi { width: calc(var(--nilai) * 1%); }
```

### 9. Pencegahan horizontal scroll
Gambar dibatasi `max-width: 100%`. Tabel lebar dibungkus `overflow-x: auto` sehingga hanya tabel yang bisa digeser, bukan seluruh halaman.

## Struktur Folder

```
bijak-sampah/
|-- index.html
|-- edukasi.html
|-- panduan.html
|-- artikel.html
|-- tentang.html
|-- css/
|   `-- style.css
|-- images/
|   |-- logo.svg
|   |-- hero.svg
|   |-- icon-organik.svg
|   |-- icon-anorganik.svg
|   |-- icon-b3.svg
|   `-- kompos.svg
`-- README.md
```

## Website dan Repository

- Website: https://[username].github.io/bijak-sampah/
- Repository: https://github.com/[username]/bijak-sampah

## Referensi

- Kementerian LHK. Sistem Informasi Pengelolaan Sampah Nasional (SIPSN). sipsn.menlhk.go.id
- UU No. 18 Tahun 2008 tentang Pengelolaan Sampah
- Perpres No. 97 Tahun 2017 tentang Jakstranas Pengelolaan Sampah Rumah Tangga
- Pergub Bali No. 47 Tahun 2019 tentang Pengelolaan Sampah Berbasis Sumber
- United Nations. Sustainable Development Goals. sdgs.un.org/goals
- Jambeck, J. R. dkk. (2015). Plastic waste inputs from land into the ocean. *Science*, 347(6223)
- Aset gambar: seluruh SVG dibuat sendiri oleh kelompok. Font memakai font sistem.
