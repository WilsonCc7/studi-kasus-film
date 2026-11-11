# Studi Kasus Film

Halaman pembelajaran produksi film (Bahasa Indonesia) dari dua studi kasus:

- **Studi Kasus 9 — Musik Latar Menutupi Dialog**: kesalahan volume musik latar, keseimbangan dialog (−12 s.d. −6 dB) vs musik (−24 s.d. −18 dB), EQ 1–4 kHz, dan fungsi audio mixing. Dilengkapi simulator **Ruang Mixing** interaktif (fader + meter dB + penilaian langsung + toggle EQ).
- **Studi Kasus 14 — Alur Tidak Jelas**: kontinuitas antaradegan dan storyboard, dengan storyboard interaktif **"Dompet yang Hilang"** (7 frame, bisa dialihkan antara versi runtut dan versi kacau dengan animasi FLIP).

## Menjalankan

Situs statis murni — tidak ada build step. Cukup buka `index.html` di browser, atau sajikan folder ini dengan server statis apa pun:

```sh
npx serve .
```

Folder `assets/` berisi foto-foto yang dipakai halaman (lihat tabel sumber di bawah) dan harus berada di samping `index.html`.

## Animasi

Gerak mengikuti filosofi animasi Emil Kowalski (skill `animate`):

- Token easing: `--ease-out: cubic-bezier(0.23, 1, 0.32, 1)` dan `--ease-in-out: cubic-bezier(0.77, 0, 0.175, 1)`; durasi UI di bawah 300 ms.
- Hanya `transform` dan `opacity` yang dianimasikan (meter dB memakai `scaleX`, bukan `width`).
- Parallax foto hero & clapperboard (transform, digerakkan `requestAnimationFrame`).
- Indikator progres baca (`scaleX`), reveal sekali per elemen via `IntersectionObserver` dengan stagger 60 ms, dan animasi FLIP saat urutan storyboard diubah (konsistensi spasial).
- Semua gerak nonaktif / diperhalus saat `prefers-reduced-motion: reduce`; efek hover hanya pada `@media (hover: hover) and (pointer: fine)`.

## Sumber foto (sumber terbuka)

| File | Isi | Sumber |
| --- | --- | --- |
| `assets/mixer.jpg` | Konsol audio mixing | CC0 via Openverse — https://pd.w.org/2025/03/79467d722939b8503.11433713-2048x1365.jpg |
| `assets/clapperboard.jpg` | Clapperboard & peralatan film | Pajno Films — https://pajno-films.b-cdn.net/blog/import_differenza_tra_produttore_e_produttore_esecutivo_cover_2414e45260.jpg |
| `assets/frame-kelas.jpg` | Suasana ruang kelas | Flickr CC BY "hope classroom student" — https://live.staticflickr.com/6011/5982659068_d0b8a34e88_b.jpg |
| `assets/frame-tas.jpg` | Tas ransel di meja kelas | Materinstvo — https://materinstvo.ru/userfiles/picfullsize/image-1756286499_6742.jpg |
| `assets/frame-kantin.jpg` | Kantin sekolah | Flickr CC BY-NC-SA "School Canteen" — https://live.staticflickr.com/4041/4472855454_3ee9d92c06_b.jpg |
| `assets/frame-tanya.jpg` | Berbincang di ambang pintu | Flickr CC BY-NC-ND "Student have a conversation in doorway" — https://live.staticflickr.com/1437/4724388981_a4d1afddd2_b.jpg |
| `assets/frame-kembali.jpg` | Koridor sekolah | Flickr CC BY-NC "School Hallway" — https://live.staticflickr.com/5063/5601192190_f0d8dcd52f.jpg |
| `assets/frame-dompet.jpg` | Dompet kulit cokelat | Shopy Official — https://shopyofficial.com/cdn/shop/files/dc4398af7c0477056e71279d01b20adf.jpg?v=1742807672&width=900 |
| `assets/frame-lega.jpg` | Siswa tersenyum lega | Yabbu — https://yabbu.com/wp-content/uploads/2021/02/happy-student-scaled.jpg |
