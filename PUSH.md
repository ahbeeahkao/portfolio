# Push ke repo baharu — copy & paste

Repo: **https://github.com/ahbeeahkao/portfolio**
Status folder ini: **8 commit sedia**, di-rebase di atas `Initial commit` anda → **fast-forward, tiada force push**.

---

## Langkah 1 — Push (jalankan di mesin anda)

Folder `portfolio/` mesti ada `.git` di dalamnya. Kalau anda download zip, `.git` tiada —
dalam kes itu guna **Langkah 1B**.

```bash
cd portfolio
git remote -v                      # pastikan origin = .../ahbeeahkao/portfolio.git
git push -u origin main
```

Bila diminta password, masukkan **Personal Access Token** (bukan password GitHub):
GitHub → Settings → Developer settings → Personal access tokens → **Tokens (classic)**
→ Generate new token → scope: `repo` + `workflow` → salin token.

### Langkah 1B — kalau tiada `.git` (guna zip)

```bash
git clone https://github.com/ahbeeahkao/portfolio.git
cd portfolio
# salin SEMUA isi folder portfolio ke sini (termasuk fail tersembunyi .nojekyll, .github/)
cp -r /path/to/portfolio/. .
git add -A
git commit -m "Tambah portfolio konsep kantin & katering"
git push origin main
```

Semak `.github/workflows/deploy.yml` dan `.nojekyll` benar-benar masuk:
```bash
git ls-files | grep -E "deploy.yml|nojekyll|CNAME|robots.txt"
```
Mesti keluar 4 baris.

---

## Langkah 2 — Hidupkan Pages

1. Repo → **Settings** → **Pages**
2. **Source**: `GitHub Actions`
3. Tunggu workflow "Deploy portfolio to GitHub Pages" selesai (tab **Actions**)
4. Uji: `https://ahbeeahkao.github.io/portfolio/` — mesti keluar halaman portfolio

**Jangan** set custom domain lagi. Sahkan yang ini berfungsi dahulu.

---

## Langkah 3 — Subdomain (Cloudflare)

Cloudflare → pilih zone **jobshore.dpdns.org** → **DNS** → **Records** → **Add record**

| Field | Nilai |
|---|---|
| Type | `CNAME` |
| Name | `portfolio` |
| Target | `ahbeeahkao.github.io` |
| Proxy status | **DNS only (awan kelabu)** ← WAJIB kelabu |
| TTL | Auto |

> Awan oren akan menghalang GitHub daripada mengeluarkan sijil SSL.
> Jangan sekali-kali pilih "Flexible" dalam SSL/TLS — ia menyebabkan redirect loop.

---

## Langkah 4 — Custom domain

1. Repo → Settings → Pages → **Custom domain** → taip `portfolio.jobshore.dpdns.org` → **Save**
2. Tunggu semakan DNS jadi hijau (5–30 minit)
3. Tick **Enforce HTTPS**
4. Uji `https://portfolio.jobshore.dpdns.org/`

Fail `CNAME` sudah ada dalam repo — GitHub akan kekalkannya.

---

## Langkah 5 — Sahkan

```bash
# DNS
curl -s "https://cloudflare-dns.com/dns-query?name=portfolio.jobshore.dpdns.org&type=A" \
  -H "accept: application/dns-json"

# HTTPS mesti 200
curl -sI https://portfolio.jobshore.dpdns.org/ | head -1

# Robots (konsep mesti noindex)
curl -s https://portfolio.jobshore.dpdns.org/kejora-canteen/ | grep -o 'name="robots" content="[^"]*"'

# OG image mesti wujud
curl -sI https://portfolio.jobshore.dpdns.org/assets/og/hub.jpg | head -1
```

Ujian WhatsApp: hantar `https://portfolio.jobshore.dpdns.org/` kepada diri sendiri —
mesti keluar **kad dengan gambar**, bukan URL kosong.

---

## Kalau tersekat

| Gejala | Punca biasa |
|---|---|
| "DNS check unsuccessful" berhari-hari | Custom domain sudah dipakai repo lain, **atau** awan oren |
| `ERR_TOO_MANY_REDIRECTS` | SSL/TLS mode = Flexible → tukar ke **Full (strict)** |
| "Not secure" berterusan | Cert belum terbit, atau awan masih oren |
| 404 selepas deploy | `index.html` tiada di root repo, atau Pages source bukan Actions |
| Gambar OG tak keluar | Fail di `assets/og/` belum di-push, atau cache WhatsApp (tunggu / guna `?v=2`) |

---

## Belum selesai (perlu keputusan anda)

- **No. syarikat `1525686-X`** — diambil dari laman lama yang mati. Sahkan dengan dokumen SSM sebelum hantar `cadangan-kantin.pdf`.
- **`hello@jobshore.dpdns.org`** — hantar satu emel ujian. Cloudflare Email Routing senyap menggugurkan emel kalau alamat tujuan belum disahkan dalam dashboard.
- **Domain `dpdns.org`** ialah penyedia subdomain percuma — anda tidak mengawal reputasi root domain itu. Untuk aset komersial jangka panjang, domain sendiri (~RM50/tahun) lebih selamat.
