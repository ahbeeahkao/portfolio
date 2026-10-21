# Portfolio Konsep — Kantin & Katering

Empat laman web siap, satu halaman portfolio, satu cadangan PDF.
Semuanya dalam **satu repo**, tiada build step, tiada dependency. Buka `index.html` terus dalam browser.

> **Nota jujur:** Keempat-empat laman ini adalah **konsep rekaan sendiri**, bukan kerja berbayar
> untuk klien. Nama syarikat, sijil, angka dan testimoni adalah rekaan. Setiap footer menyatakan
> perkara ini — **jangan buang ayat itu.**

---

## Struktur

```
.
├── index.html                     ← HALAMAN PORTFOLIO (mula di sini)
├── kejora-canteen/index.html      ← Konsep 01: kantin tapak bina
├── serirasa-event/index.html      ← Konsep 02: katering korporat & majlis
├── nutrimas-kitchen/index.html    ← Konsep 03: dapur pusat & institusi
├── kantin-warisan-mockup/index.html ← Mockup untuk Tuan Amir (jangan hantar dulu)
├── cadangan-kantin.pdf            ← Cadangan 1 halaman
├── 404.html
├── LICENSE                        ← Hak cipta proprietari (Jobshore (M) Sdn Bhd)
├── _src-photos/                   ← Gambar sumber (TIDAK digunakan oleh laman; laman guna base64)
└── .github/workflows/deploy.yml   ← Auto-deploy ke GitHub Pages
```

Dilesenkan sebagai hak cipta proprietari — **Jobshore (M) Sdn Bhd (1525686-X)**, semua hak terpelihara.

**Setiap laman = satu fail `index.html`.** Gambar sudah ditanam sebagai base64, jadi tiada
folder `assets/` yang boleh hilang, tiada `src` rosak, tiada CORS. Boleh zip dan hantar
melalui WhatsApp pun jalan.

---

## Satu halaman atau banyak halaman?

Setiap laman ialah **single-page site** — satu fail, scroll panjang, navigasi guna anchor
(`#perkhidmatan`, `#kadar`). Ia ada 7–8 seksyen penuh: hero, jalur sijil, perkhidmatan,
kapasiti, jadual harga, proses, pematuhan, borang sebut harga, FAQ, footer.

**Kenapa satu halaman:**

| | Single-page | Multi-page |
|---|---|---|
| Kos bina | Lebih murah | +30–40% (setiap halaman kena direka) |
| Kelajuan | 1 request, terus nampak semua | Banyak request, pembeli hilang dalam 3 klik |
| Penyelenggaraan | Klien cuma update 1 fail | 8 fail untuk dikemas kini bila harga berubah |
| SEO | Satu halaman, satu keyword | Satu halaman = satu keyword (lebih baik untuk SEO jangka panjang) |

Untuk **vendor kantin**, single-page menang: procurement buka link, scroll 40 saat, nampak sijil,
kapasiti dan harga — terus tekan "Minta Sebut Harga". Tiada halaman kedua untuk meyakinkan dia.

**Bila patut pecah jadi multi-page:** bila ada blog, portal pelanggan, halaman produk melebihi
30 item, atau perlu versi BM/EN berasingan. Itu projek lain — bukan pakej RM4,500.

Kalau nak pecah pun senang nanti: setiap `<section id="...">` dalam fail itu sudah jadi
halaman sendiri bila dipindahkan.

---

## 0. Hubungan awam (disahkan)

| | |
|---|---|
| **Emel** | `hello@jobshore.dpdns.org` |
| **Laman web** | tiada pautan di portfolio (kredit nama syarikat sahaja) |
| **Telefon / WhatsApp** | tiada di laman awam (mengikut arahan) |

Emel disahkan berfungsi: domain `jobshore.dpdns.org` ada rekod MX aktif
(`route1/2/3.mx.cloudflare.net` — Cloudflare Email Routing). Alamat `hello@`
diambil daripada atribut fallback borang di jobshore.dpdns.org sendiri
(`data-fallback-u="hello"` + `data-fallback-d="jobshore.dpdns.org"`).

> ⚠️ **Uji dulu:** hantar satu emel ujian ke `hello@jobshore.dpdns.org` sebelum deploy.
> Cloudflare Email Routing hanya berfungsi kalau alamat tujuan sudah disahkan dalam dashboard.
>
> ✅ **HTTPS jobshore.dpdns.org sudah aktif** (disahkan: Let's Encrypt, `CN=jobshore.dpdns.org`,
> `Verify return code: 0`). Nota: domain itu dimiliki oleh repo **`ahbeeahkao/jobshore`**
> (`public/CNAME` + workflow Astro). Satu custom domain = satu Pages site, jadi portfolio
> **tidak boleh** guna domain yang sama — guna `username.github.io` atau subdomain.

## 1. Hubungan awam — emel sahaja

**Tiada nombor telefon atau WhatsApp di mana-mana laman.** Semua CTA menatal ke borang, dan
borang menghantar melalui emel. Ini tetapan yang paling selamat untuk laman awam: nombor
telefon yang dipaparkan di web akan di-scrape dalam beberapa hari.

Semua tetapan ada dalam satu objek, di dalam `<script>` setiap `index.html`:

```js
var SITE = {
  email:    "hello@jobshore.dpdns.org",
  website:  "",   // kosong = tiada pautan laman web di footer
  whatsapp: "",                   // kosong = borang. Isi "60XXXXXXXXX" untuk hidupkan WhatsApp.
  endpoint: ""                    // kosong = mailto. Isi endpoint Formspree/Web3Forms kalau ada.
};
```

| Keadaan | Apa yang berlaku |
|---|---|
| `whatsapp: ""` (sekarang) | Butang CTA → tatal ke borang · butang WhatsApp terapung **dihapus** · tiada nombor di halaman |
| `whatsapp: "60123456789"` | Butang CTA → buka WhatsApp dengan mesej pra-isi · butang terapung muncul |
| `endpoint: ""` (sekarang) | Borang → buka aplikasi emel klien, sedia ke emel dalam `SITE.email` |
| `endpoint: "https://formspree.io/f/xxxx"` | Borang → hantar senyap, tiada app emel, papar mesej terima kasih |

### Kalau mahu borang hantar senyap (disyorkan)
Percuma sehingga 50 hantar/bulan:

1. Daftar di [formspree.io](https://formspree.io) atau [web3forms.com](https://web3forms.com)
2. Cipta form, salin endpoint (contoh `https://formspree.io/f/mzzabcd`)
3. Tampal ke `endpoint` dalam `SITE` — dalam **5** fail
4. Tambah domain anda dalam tetapan form untuk elak spam

Semak tiada nombor telefon tercicir:
```bash
grep -rnE "tel:|wa\.me|60[0-9]{9,}" --include=*.html .
```

---

## 2. Push ke GitHub (satu repo)

```bash
cd portfolio
git init
git add .
git commit -m "Portfolio konsep: kantin & katering"
git branch -M main
git remote add origin https://github.com/USERNAME/portfolio-kantin.git
git push -u origin main
```

Ganti `USERNAME` dan nama repo. Cipta repo kosong di GitHub dahulu (**jangan** tick
"Add a README" — nanti konflik).

### Hidupkan GitHub Pages
1. Repo → **Settings** → **Pages**
2. **Source**: pilih **GitHub Actions** (bukan "Deploy from a branch")
3. Push ke `main` mencetuskan deploy. Link keluar dalam 1–2 minit:
   `https://USERNAME.github.io/portfolio-kantin/`

Workflow `.github/workflows/deploy.yml` sudah disediakan — tiada konfigurasi lain.

### Domain sendiri (disyorkan sebelum hantar ke klien)
1. Beli domain (`namaanda.my`, `namaanda.com`)
2. Repo → Settings → Pages → **Custom domain** → masukkan domain
3. Di pendaftar domain, tambah rekod:
   - `A` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` untuk `www` → `USERNAME.github.io`
4. Tick **Enforce HTTPS**

> Link `username.github.io/portfolio-kantin` menjatuhkan kredibiliti bila klien sedang
> menimbang antara anda (RM4,500) dan quote RM500 dari luar negara. Domain berharga ~RM50/tahun.
> Itu bukan kos — itu alat jualan.

---

## 3. Alternatif tanpa GitHub

- **Netlify Drop** — seret folder ke [app.netlify.com/drop](https://app.netlify.com/drop). 2 minit, percuma.
- **Vercel** — `npx vercel --prod` dalam folder ini.
- **Hosting cPanel** (Exabytes, Shinjuku) — upload semua ke `public_html`.

Semua jalan tanpa ubah apa-apa, sebab tiada build step.

---

## 4. Cara guna dengan Tuan Amir

**Jangan hantar keempat-empat link.** Hantar dua, dengan sebab kenapa dua itu:

> Tuan, saya dah siapkan dua contoh yang dekat dengan situasi Tuan:
>
> 1. `[link]/kejora-canteen/` — konsep kantin tapak bina. Paling dekat dengan operasi Tuan sekarang.
> 2. `[link]/nutrimas-kitchen/` — konsep dapur pusat untuk kilang & hospital. Ini arah yang Tuan nak pergi.
>
> Dalam kedua-dua, perhatikan tiga benda: sijil di bahagian atas, kadar per pax yang terbuka,
> dan borang "Minta Sebut Harga" yang terus masuk WhatsApp.
>
> Saya juga ada satu mockup untuk nama Kantin Warisan — tapi saya simpan dulu.
> Kalau Tuan nak lihat, saya hantar. Saya tak nak orang lain guna kerja yang saya buat khas untuk Tuan.

Mockup Warisan itu **alat closing**, bukan portfolio. Ia buat dia rasa diutamakan — dan itu
yang menyebabkan orang bayar deposit.

---

## 5. Bila ditanya "ini kerja siapa?"

Jawab terus. Jangan keliru.

> "Ini konsep yang saya reka sendiri, bukan kerja berbayar. Saya buat empat konsep untuk
> industri kantin dan katering sebab itu bidang yang saya nak masuk. Kalau Tuan nak tengok
> kerja berbayar, saya ada company profile dan sistem tempahan — tapi saya tak nak tunjuk
> kerja orang lain dan cakap itu kerja saya."

Sebab ia berkesan: semua orang lain hantar kerja klien mereka. Anda hantar kerja yang dibuat
**khas untuk industri dia**. Itu bukan kelemahan — itu bukti anda faham bisnes dia sebelum dibayar.

---

## 6. Gambar

Semua gambar dalam laman adalah **dijana AI** (bukan gambar klien, bukan gambar stok berlesen).
Bila ditanya:

> "Gambar contoh untuk demo. Untuk laman sebenar, kita guna gambar dapur Tuan sendiri — itu
> yang paling menjual."

Gambar sumber ada dalam `_src-photos/`. Ia tidak dimuatkan oleh laman (laman guna base64),
jadi ia selamat dipadam kalau nak kecilkan repo.

---

## 7. Edit & bina semula (pilihan)

Kandungan dalam `index.html` boleh diedit terus dengan editor teks — tiada compiler.

Kalau anda ubah `build/tpl/*.html` atau `build/base.css`:

```bash
python3 build/build.py     # bina 5 laman (gambar base64)
python3 build/make_hub.py  # bina hub (guna screenshot dalam build/shots/)
python3 build/make_proposal.py  # bina cadangan PDF
```

`build/` **tidak** dimasukkan dalam repo ini — ia alat pembangunan di mesin anda, bukan
bahagian laman yang dihantar.

---

## 8. Senarai semak sebelum hantar ke klien

- [ ] Tiada nombor telefon: `grep -rnE "tel:|wa\.me|60[0-9]{9,}" --include=*.html .`
- [ ] Emel `hello@jobshore.dpdns.org` diuji — hantar satu emel ujian, pastikan sampai
- [ ] (Pilihan) endpoint borang diisi supaya tiada app emel dibuka
- [ ] Domain sendiri dipasang, HTTPS aktif
- [ ] Buka setiap laman di **telefon**, bukan laptop
- [ ] Tekan setiap butang "Minta Sebut Harga" — pastikan mesej pra-isi betul
- [ ] `cadangan-kantin.pdf` — nama, telefon, emel anda betul
- [ ] Nota "concept project" masih ada di footer
- [ ] Nama syarikat klien dieja betul dalam PDF
