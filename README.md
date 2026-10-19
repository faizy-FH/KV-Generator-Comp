# KV-Generator-Comp

Hub satu pintu buat semua **KV Generator** tim Marketing FIT HUB. Masuk sekali, pilih mau bikin KV apa, langsung kebuka tool-nya.

**Live:** https://faizy-fh.github.io/KV-Generator-Comp/

---

## Isi repo

| File | Tool | Buat apa |
|---|---|---|
| `index.html` | **Menu depan** | gate passcode + pilihan 3 generator |
| `bau.html` | Promo BAU (FHR) | promo bulanan reguler, 5 format |
| `flashsale.html` | Flash Sale FHG | Flash Sale FIT HUB GO, 3 format + 11 scene |
| `rtc.html` | Renewal RTC | KV renewal per-club pas launch RTC |

Semua tool **self-contained** (aset ke-embed di dalam HTML, nggak ada dependency file lain).

---

## Cara akses

1. Buka link live di atas.
2. Masukin **passcode internal** (sama kayak tool KV lama — tanya Jih kalo belum tau).
3. Pilih generator → kebuka di halamannya sendiri.
4. Tombol **"← Menu KV"** di pojok kiri-bawah buat balik ke menu.

> Akses cukup **sekali di depan**. Selama tab browser masih kebuka, pindah-pindah generator nggak perlu masukin passcode lagi.

---

## Cara update

Mau ganti/upgrade salah satu generator? **Replace satu file-nya aja** di repo ini — nggak usah sentuh yang lain.

1. Siapin file HTML versi baru.
2. Rename sesuai nama di tabel (`bau.html` / `flashsale.html` / `rtc.html`).
3. Replace file lama di repo (upload/commit ke branch `main`).
4. GitHub Pages auto-redeploy dalam ~1 menit.

> ⚠️ **Jangan ubah nama file.** Menu depan nge-link ke nama file persis di atas — kalo diubah, tombolnya mati.

### Kalau generator-nya belum punya gate sendiri

`flashsale.html` & `rtc.html` udah dikasih **guard** di bagian paling atas `<head>`:

```html
<script>if(sessionStorage.getItem('kvgen_ok')!=='1'){location.replace('index.html');}</script>
```

Kalau lu ganti file-nya dengan versi baru, **pastikan baris guard ini ikut dibawa** (taruh tepat setelah `</title>`), biar akses langsung tanpa lewat menu tetep kebalikin ke gate. `bau.html` nggak butuh ini karena punya gate sendiri.

---

## Catatan teknis

- **Gate ini soft, bukan security beneran.** Passcode dicek di browser (client-side). Fungsinya cuma nyegah orang iseng yang nemu link — jangan taruh apa pun yang beneran rahasia di balik ini.
- **Copy & Download** gambar cuma jalan di **tab browser asli** (Chrome). Di GitHub Pages udah pasti aman; cuma kalo dibuka di dalam preview/iframe doang yang keblokir.
- Semua generator pakai **key sessionStorage yang sama** (`kvgen_ok`) biar akses kebawa antar-tool dalam satu tab.
