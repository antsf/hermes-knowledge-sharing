# Mengenal Hermes — Knowledge Sharing Deck & Usecase Form

Knowledge-sharing deck untuk memperkenalkan Hermes ke staff Prahu Hub,
Sabtu 12 September 2026. Dihosting via GitHub Pages.

## Halaman

- **[`home.html`](https://antsf.github.io/hermes-knowledge-sharing/home.html)** — landing page navigasi
- **[`index.html`](https://antsf.github.io/hermes-knowledge-sharing/index.html)** — deck utama, tema Prahu Hub (hijau-oranye)
- **[`index-hermes-theme.html`](https://antsf.github.io/hermes-knowledge-sharing/index-hermes-theme.html)** — variant tema situs Hermes Agent (biru elektrik)
- **[`index-combo.html`](https://antsf.github.io/hermes-knowledge-sharing/index-combo.html)** — variant kombinasi Prahu Hub × Hermes
- **[`usecase-form.html`](https://antsf.github.io/hermes-knowledge-sharing/usecase-form.html)** — form isian usecase kerjaan staff, submit langsung
  ke `usecases/*.json` di repo ini via GitHub Contents API

## Navigasi Deck

Panah kiri/kanan atau klik kiri/kanan layar untuk pindah slide. `N` untuk
toggle catatan presenter.

## Hasil Usecase

Tiap submission form tersimpan sebagai file JSON individual di `usecases/`,
nama file `{timestamp}-{nama-staff}.json`, berisi:

```json
{
  "nama": "...",
  "divisi": "...",
  "produk": "...",
  "kerjaan": "...",
  "makanwaktu": "...",
  "ceklokasi": "...",
  "laporan": "...",
  "ide": "...",
  "submittedAt": "2026-09-12T..."
}
```

## Setup (sekali saja)

Form submit butuh GitHub token untuk menulis ke repo dari browser staff.
**GitHub tidak punya API untuk generate token** — harus lewat UI:

1. https://github.com/settings/personal-access-tokens/new
2. **Token name**: `hermes-knowledge-sharing-form`
3. **Expiration**: 90 hari
4. **Repository access**: Only select repositories → `antsf/hermes-knowledge-sharing`
5. **Permissions** → Repository permissions → **Contents: Read and write** (yang lain biarkan No access)
6. Generate token, copy nilainya
7. Masuk ke Settings repo ini → Secrets and variables → Actions → New repository secret
   - Name: `HERMES_FORM_TOKEN`
   - Value: (token yang di-copy tadi)
8. Push ke `main` (atau jalankan workflow manual) — GitHub Actions akan
   generate `config.js` saat build, inject token ke situs live tanpa
   pernah menyentuh git history.

Token bisa dicabut/dirotasi kapan saja di halaman token settings tanpa
perlu ubah kode.
