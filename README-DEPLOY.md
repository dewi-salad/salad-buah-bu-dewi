# Panduan Deploy — Website Salad Buah Bu Dewi (+ Panel Admin)

Paket ini berisi website lengkap dengan **panel admin** supaya Suminto/istri bisa upload foto atau video baru sendiri tanpa coding. Caranya sama seperti waktu bikin website Atomy dulu: GitHub → Netlify → Decap CMS.

---

## Bagian 1 — Upload ke GitHub

1. Buka [github.com](https://github.com), login ke akun yang biasa dipakai.
2. Buat repository baru, misal nama: `salad-buah-bu-dewi`. Set **Public** atau **Private** (keduanya bisa).
3. Upload semua isi folder ini (jangan folder-nya, isinya saja) ke repo tersebut. Bisa lewat GitHub Desktop (seperti tutorial yang pernah dibuat) atau upload manual lewat web GitHub.

Struktur file yang harus ada di repo:
```
index.html
admin/
  ├── index.html
  └── config.yml
content/
  ├── gallery.json
  └── settings.json
images/
  ├── logo.png
  └── gallery/
      ├── hero1.jpg
      ├── hero2.jpg
      ├── hero3.jpg
      └── hero4.jpg
```

---

## Bagian 2 — Deploy ke Netlify

1. Buka [app.netlify.com](https://app.netlify.com), login (bisa pakai akun GitHub).
2. Klik **Add new site → Import an existing project**.
3. Pilih repo `salad-buah-bu-dewi` yang baru dibuat.
4. Build settings: **kosongkan saja** (tidak perlu build command, tidak perlu publish directory — atau isi `.` / root). Klik **Deploy**.
5. Setelah selesai, situs akan punya alamat seperti `nama-acak-123.netlify.app`. Bisa diganti nama di **Site settings → Change site name**, misal jadi `salad-buah-bu-dewi.netlify.app`.

---

## Bagian 3 — Aktifkan Panel Admin (Identity + Git Gateway)

Ini yang bikin `/admin` bisa dipakai untuk upload foto tanpa coding.

1. Di dashboard Netlify situs ini, buka **Site configuration → Identity** → klik **Enable Identity**.
2. Scroll ke **Registration preferences** → pilih **Invite only** (supaya orang luar tidak bisa daftar sembarangan).
3. Scroll ke **Services → Git Gateway** → klik **Enable Git Gateway**.
4. Kembali ke tab **Identity** → klik **Invite users** → masukkan email Suminto/istri → kirim undangan.
5. Cek email, klik link undangan, buat password. Setelah itu otomatis diarahkan untuk melengkapi login.

---

## Bagian 4 — Cara Pakai Panel Admin

1. Buka `https://[nama-situs-anda].netlify.app/admin/`
2. Login pakai email & password yang tadi dibuat.
3. Akan muncul 2 menu:
   - **🖼️ Galeri Foto & Video** — tambah/hapus/urutkan foto atau video (isi link YouTube untuk video).
   - **⚙️ Widget Instagram** — tempat menempel kode widget Instagram (lihat Bagian 5).
4. Setiap selesai edit, klik **Publish** — perubahan otomatis muncul di website dalam 1-2 menit.

---

## Bagian 5 — Pasang Widget Instagram (Opsional, biar feed IG otomatis muncul)

Supaya postingan terbaru dari **@dewi_salad** otomatis tampil di website tanpa upload ulang:

1. Buka [snapwidget.com](https://snapwidget.com) (gratis).
2. Pilih **Create a Widget → Instagram Feed**.
3. Hubungkan/masukkan akun Instagram **@dewi_salad**.
4. Atur tampilan sesukanya (jumlah foto, warna, dsb), lalu klik **Get Widget Code**.
5. Copy kode embed yang diberikan (biasanya berupa tag `<iframe>`).
6. Masuk ke `/admin/` di website → menu **⚙️ Widget Instagram** → tempel kode di kolom **Kode Embed Instagram** → **Publish**.
7. Refresh website, widget IG akan muncul otomatis di bawah galeri.

Alternatif lain selain SnapWidget: [Elfsight](https://elfsight.com) atau [LightWidget](https://lightwidget.com) — caranya mirip.

---

## Catatan Penting

- Video di galeri saat ini mendukung **link YouTube** (paling gampang & hemat kuota, karena video-nya tetap disimpan di YouTube, bukan di website).
- Kalau mau upload video langsung (file .mp4), bisa juga — tapi ukuran file besar bisa memperlambat loading web. Untuk mulai, disarankan upload video ke YouTube (bisa "Unlisted" biar tidak publik di channel) lalu tempel linknya.
- Kalau ada kendala saat setup (GitHub/Netlify/Identity), tinggal kirim pesan error-nya ke Claude, nanti dibantu troubleshoot.
