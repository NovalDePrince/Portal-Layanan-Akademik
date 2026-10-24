# Portal Layanan Akademik

Halaman web client responsif dan aksesibel untuk layanan akademik kampus (HTML + CSS, tanpa JavaScript).

## Struktur
```
index.html
css/styles.css
README.md
```

## Keputusan desain
- **Semantik:** `header`, `nav`, `main`, `section`, `article` (per kartu), `form`, `footer`. Heading: h1 (portal) > h2 (bagian) > h3 (kartu).
- **Mobile-first:** satu kolom default. Breakpoint 40rem (kartu 2 kolom) dan 64rem (kartu 4 kolom) dipilih karena konten mulai lapang, bukan karena nama perangkat.
- **Layout:** CSS Grid untuk kartu dan form, Flexbox untuk header, nav, dan isi kartu.
- **Form:** label terasosiasi (`for`/`id`), `type=email`, `pattern` NIM, `required`, `minlength`/`maxlength`, `fieldset`+`legend` untuk pengelompokan dan radio, `<button type="submit">`.
- **Aksesibilitas:** skip link, focus ring 3px, target sentuh min 44px, kontras teks lebih dari 4.5:1 (tema terang dan gelap), `prefers-reduced-motion`, ARIA minimal (hanya `aria-label` pada link kartu dan `aria-describedby` pada petunjuk).
- **Gambar:** logo SVG bersifat dekoratif (`aria-hidden="true"`, tanpa alt) karena nama kampus sudah ada dalam teks di sebelahnya.

## Hasil pemeriksaan DevTools (isi setelah menguji)
| Pemeriksaan | Cara | Hasil / temuan |
|---|---|---|
| Viewport 360 px | Responsive Mode | Tidak ada horizontal scroll: ☐ |
| Viewport 768 px | Responsive Mode | Kartu 2 kolom, terbaca: ☐ |
| Viewport 1280 px | Responsive Mode | Kartu 4 kolom, terbaca: ☐ |
| Elements/Inspector | Periksa DOM dan box model kartu | |
| Network | Reload, cek status resource | index.html 200, styles.css 200, tanpa resource gagal: ☐ |
| Accessibility tree | Chrome: Accessibility; Firefox: Accessibility Inspector | Landmark dan label form terbaca: ☐ |
| Keyboard | Tab dari awal halaman | Semua kontrol terjangkau, fokus terlihat: ☐ |
| Validasi | Submit kosong dan email salah | Browser menolak dengan pesan: ☐ |

## Cara menjalankan
Buka `index.html` di browser, atau deploy ke GitHub Pages (Settings > Pages > branch `main`, folder `/root`).

## Tautan
- URL aplikasi: https://novaldeprince.github.io/Portal-Layanan-Akademik/
- GitHub: https://github.com/NovalDePrince/Portal-Layanan-Akademik

## Hasil pengujian (tambahan dari pengujian di DevTools)
Pengujian dilakukan pada URL GitHub Pages dengan Chrome DevTools. Screenshot lengkap ada di file PDF bukti yang dikumpulkan bersama tugas ini.

| No | Pemeriksaan | Hasil |
|---|---|---|
| 1 | Viewport 1280 px (Responsive Mode) | Kartu layanan tersusun 4 kolom sejajar, terbaca, tidak ada horizontal scroll. |
| 2 | Viewport 360 px (Responsive Mode) | (isi hasil: layout satu kolom, ada/tidak horizontal scroll) |
| 3 | Viewport 768 px (Responsive Mode) | (isi hasil: kartu 2 kolom, terbaca) |
| 4 | Elements dan Accessibility (input email) | Input email terhubung ke label lewat `for`/`id`. Accessibility menampilkan Name "Email", Role textbox, dan Keyboard-focusable. Diuji sebelum label diubah menjadi "Email Kampus". |
| 5 | Network (Disable cache aktif, hard reload) | 2 request (document dan `styles.css`), keduanya berstatus 200. Tidak ada resource gagal. |
| 6 | Keyboard | Kolom form menampilkan outline fokus yang jelas (cincin kuning). Fokus terlihat saat kolom Email aktif. |
| 7 | Validasi form | Email tanpa `@` ditolak browser dengan pesan "Please include an '@' in the email address", jadi validasi HTML (`type="email"` dan `required`) berfungsi. |
