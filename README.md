# Siena Clinical

Website profil Siena Clinical yang dibangun dengan Astro dan Tailwind CSS. Project ini memuat halaman publik untuk company profile, capability, publication, team, contact, serta detail course.

## Tech Stack

- Astro 6
- Tailwind CSS 4 via `@tailwindcss/vite`
- TypeScript
- Astro Content Collections

## Requirements

- Node.js `>=22.12.0`
- npm

## Menjalankan Project

Install dependency:

```sh
npm install
```

Jalankan development server:

```sh
npm run dev
```

Preview hasil production build:

```sh
npm run preview
```

Build project:

```sh
npm run build
```

Catatan PowerShell di Windows:

Jika `npm run ...` terblokir oleh execution policy, gunakan `npm.cmd` sebagai pengganti, misalnya:

```sh
npm.cmd run build
```

## Struktur Project

```text
/
|-- public/
|   |-- favicon.ico
|   `-- favicon.svg
|-- src/
|   |-- assets/             # logo, ilustrasi, gambar partner, tim, publication
|   |-- components/         # section dan UI Astro components
|   |-- content/            # konten markdown: courses, publications, blogs, team, events
|   |-- layouts/
|   |   `-- Layout.astro    # metadata global, SEO tags, JSON-LD
|   |-- pages/
|   |   |-- index.astro
|   |   |-- capability.astro
|   |   |-- publication.astro
|   |   |-- team.astro
|   |   |-- contact.astro
|   |   |-- robots.txt.ts
|   |   |-- sitemap.xml.ts
|   |   `-- courses/
|   |       `-- [slug].astro
|   `-- content.config.ts   # schema content collections
|-- astro.config.mjs
`-- package.json
```

## Halaman Utama

- `/` : landing page Siena Clinical
- `/capability` : layanan dan kapabilitas
- `/publication` : journal, conference, blog, dan past events
- `/team` : profil tim
- `/contact` : form kontak berbasis `mailto:`
- `/courses/[slug]` : detail course dinamis dari content collection

## Content Management

Sebagian besar konten dikelola dari folder `src/content/`:

- `src/content/courses`
- `src/content/publications`
- `src/content/blogs`
- `src/content/past-events`
- `src/content/past-event-highlights`
- `src/content/research-studies`
- `src/content/team`

Schema untuk seluruh content collection didefinisikan di `src/content.config.ts`.

## SEO

Project ini sudah memiliki fondasi SEO berikut:

- `site` URL di `astro.config.mjs`
- canonical URL global
- meta description
- Open Graph dan Twitter Card
- structured data JSON-LD pada halaman utama dan halaman penting
- `robots.txt` di `/robots.txt`
- `sitemap.xml` di `/sitemap.xml`

## Contact Form

Halaman contact tidak mengirim email otomatis dari server.

Saat form disubmit, halaman akan membuka aplikasi email default user melalui `mailto:` dan menyiapkan draft email ke:

```text
admin@sienaclinical.com
```

Implementasi ini ada di `src/pages/contact.astro`.

## Scripts

| Command | Keterangan |
| :-- | :-- |
| `npm run dev` | Menjalankan local development server |
| `npm run build` | Build static site ke folder `dist/` |
| `npm run preview` | Menjalankan preview hasil build |
| `npm run astro -- --help` | Bantuan Astro CLI |

## Deployment

Output project ini bersifat static dan dihasilkan ke folder:

```text
dist/
```

Pastikan domain production mengarah ke:

```text
https://www.sienaclinical.com
```

karena URL tersebut dipakai untuk canonical tag, sitemap, dan metadata SEO.
