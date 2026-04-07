# Client Update Guide

Panduan ini dibuat untuk membantu tim client melakukan update konten website secara mandiri tanpa mengubah struktur atau desain website.

## Prinsip Dasar

Website ini menggunakan pola `static site`.
Artinya:

- Konten bisa diubah dari file data/konten.
- Layout, desain, dan fitur teknis tidak perlu disentuh saat update rutin.
- Untuk update harian atau berkala, fokus hanya pada folder `src/content`.

## Yang Boleh Diupdate

Client dapat mengupdate konten berikut:

- Team
- Publication
- Blog
- Past Events
- Research Study
- Courses

## Yang Tidak Perlu Diubah

Mohon jangan mengubah file berikut tanpa bantuan developer:

- `src/components/*`
- `src/pages/*`
- `src/layouts/*`
- `src/styles/*`
- file konfigurasi project seperti `package.json`, `astro.config.mjs`, dan `tsconfig.json`

## Lokasi Konten

Berikut lokasi file yang digunakan untuk update konten:

- Team: [src/content/team](d:/projects/siena-clinical/src/content/team)
- Journal and Conference: [src/content/publications](d:/projects/siena-clinical/src/content/publications)
- Blog: [src/content/blogs](d:/projects/siena-clinical/src/content/blogs)
- Past Event Highlights: [src/content/past-event-highlights](d:/projects/siena-clinical/src/content/past-event-highlights)
- Past Events: [src/content/past-events](d:/projects/siena-clinical/src/content/past-events)
- Research Studies: [src/content/research-studies](d:/projects/siena-clinical/src/content/research-studies)
- Courses: [src/content/courses](d:/projects/siena-clinical/src/content/courses)

## Cara Kerja Update

Setiap item konten disimpan sebagai 1 file Markdown (`.md`).

Pola update umumnya:

1. Buka folder konten yang sesuai.
2. Jika ada gambar baru, upload gambar dulu ke repository GitHub pada folder aset yang sesuai.
3. Pilih file yang ingin diubah, atau duplikasi file lama untuk membuat item baru.
4. Edit isi field pada bagian atas file.
5. Simpan perubahan.
6. Lakukan preview / deploy sesuai alur project.

## Struktur Dasar File

Sebagian besar file memakai format seperti ini:

```md
---
title: "Judul"
order: 1
published: true
description: "Isi deskripsi"
---
```

Catatan penting:

- `published: true` artinya konten tampil di website
- `published: false` artinya konten disimpan tapi tidak tampil
- `order` menentukan urutan tampil

## Update Team

Lokasi:
- [src/content/team](d:/projects/siena-clinical/src/content/team)

Subfolder:
- `researchers`
- `clinical-experts`
- `tech-team`
- `operating-officers`

Field yang umum diubah:

- `name`
- `role`
- `category`
- `order`
- `bio`
- `image`
- `links`

Contoh:

```md
---
name: "Nama Tim"
role: "Peran"
category: "researchers"
order: 3
bio: "Deskripsi singkat"
image: "../../../assets/teams/researchers/nama-file.webp"
links:
  - kind: "linkedin"
    label: "LinkedIn"
    href: "https://linkedin.com/in/username"
---
```

Jika ingin menambah member baru:

1. Duplikasi file member yang mirip.
2. Ubah semua isi field.
3. Pastikan `category` sesuai.
4. Pastikan path `image` benar.

## Update Publication

### Journal and Conference

Lokasi:
- [src/content/publications](d:/projects/siena-clinical/src/content/publications)

Field:

- `title`
- `citation`
- `year`
- `kind`
- `order`
- `link`
- `published`

Contoh:

```md
---
title: "Judul publikasi"
citation: "Nama jurnal / konferensi. Tahun."
year: 2026
kind: "journal"
order: 1
link: "https://example.com"
published: true
---
```

Nilai `kind`:

- `journal`
- `conference`

### Blog

Lokasi:
- [src/content/blogs](d:/projects/siena-clinical/src/content/blogs)

Field:

- `title`
- `order`
- `published`
- `description`
- `keyFindings`
- `link`
- `image`
- `imageAlt`

### Past Events

Lokasi:

- highlights carousel: [src/content/past-event-highlights](d:/projects/siena-clinical/src/content/past-event-highlights)
- event list: [src/content/past-events](d:/projects/siena-clinical/src/content/past-events)

Field event:

- `title`
- `order`
- `published`
- `description`
- `link`
- `image`
- `imageAlt`

## Update Research Study

Lokasi:
- [src/content/research-studies](d:/projects/siena-clinical/src/content/research-studies)

Field:

- `title`
- `order`
- `published`
- `description`
- `image`
- `imageAlt`
- `details`

Contoh `details`:

```md
details:
  - label: "Collaboration"
    value: "Nama partner"
  - label: "Timeline"
    value: "2024-2027"
```

## Update Courses

Lokasi:
- [src/content/courses](d:/projects/siena-clinical/src/content/courses)

Field yang umum diubah:

- `title`
- `titleId`
- `badge`
- `badgeId`
- `description`
- `descriptionId`
- `sections`
- `instructor`
- `registerUrl`
- `order`
- `published`

Contoh:

```md
---
order: 1
published: true
title: "Nama Course"
titleId: "Nama Course Indonesia"
badge: "3-Day Workshop"
badgeId: "Lokakarya 3 Hari"
description: "Deskripsi bahasa Inggris"
descriptionId: "Deskripsi bahasa Indonesia"
sections:
  - heading: "Highlighted Materials"
    items:
      - "Item 1"
      - "Item 2"
instructor: "Nama Instructor"
registerUrl: "https://example.com"
icon: "<svg>...</svg>"
---
```

Jika hanya ingin update isi course:

- ubah judul
- ubah deskripsi
- ubah section
- ubah link registrasi

Tidak perlu mengubah layout halaman.

## Cara Menambah Gambar

Jika konten membutuhkan gambar baru:

1. Upload file gambar dulu ke repository GitHub.
2. Simpan file gambar di folder `src/assets/...` yang sesuai.
3. Gunakan nama file yang rapi, misalnya `new-course-poster.webp`
4. Hindari spasi, tanda kurung, dan karakter khusus jika memungkinkan.
5. Setelah gambar sudah ada di repository, baru update path gambar di file `.md`.

Contoh alur sederhana:

1. Upload gambar baru ke folder yang sesuai di GitHub.
2. Copy nama file gambar.
3. Buka file konten `.md`.
4. Ganti field `image` dengan path gambar yang benar.
5. Simpan perubahan.

Contoh:

```md
image: "../../assets/publication/new-course-poster.webp"
```

atau untuk team:

```md
image: "../../../assets/teams/researchers/nama-orang.webp"
```

## Aturan Praktis Untuk File Gambar

Supaya lebih aman saat handover, gunakan aturan ini:

- pakai huruf kecil
- pakai tanda hubung `-` untuk spasi
- gunakan format seperti `.webp`, `.png`, atau `.jpg`
- jangan gunakan nama file terlalu panjang

Contoh nama file yang disarankan:

- `putri-novianti.webp`
- `hpv-webinar-poster.webp`
- `predictive-modeling-course.webp`

Contoh nama file yang sebaiknya dihindari:

- `Foto Final Paling Baru.png`
- `Dr. Henny Putri (Fix Banget).jpg`
- `IMG_20260407_123455.png`

## Jika Update Konten Memakai Gambar

Jika ada konten baru yang memakai gambar, urutannya harus seperti ini:

1. Upload gambar ke GitHub terlebih dahulu.
2. Pastikan gambar masuk ke folder aset yang benar.
3. Edit file konten `.md`.
4. Isi field `image` dengan path gambar yang benar.
5. Simpan dan cek hasilnya.

Jika field `image` diisi tetapi file gambar belum ada di repository, website bisa error atau gambar tidak tampil.

## Tips Aman Saat Edit

- Jangan ubah nama field jika tidak perlu.
- Jangan hapus tanda `---` di atas file.
- Perhatikan indentasi pada list seperti `links`, `sections`, `items`, dan `details`.
- Jika hanya ingin menyembunyikan konten, ubah `published: false`.
- Jika ingin mengatur urutan tampil, ubah angka `order`.

## Rekomendasi Alur Kerja

Untuk update rutin, alur yang disarankan:

1. Jika ada gambar baru, upload gambar ke repository terlebih dahulu.
2. Edit file konten yang dibutuhkan.
3. Simpan perubahan.
4. Cek preview website.
5. Jika sudah benar, lanjutkan publish.

## Kapan Harus Hubungi Developer

Hubungi developer jika ingin:

- mengubah layout halaman
- mengubah desain
- menambah section baru
- menambah fitur baru
- mengubah animasi atau interaksi
- menemukan error setelah edit konten

## Ringkasan

Untuk update rutin, client cukup fokus pada folder `src/content`.
Selama hanya mengubah isi konten dan tidak menyentuh file komponen/layout, update website akan jauh lebih aman dan mudah dikelola.
