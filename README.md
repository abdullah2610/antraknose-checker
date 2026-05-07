# Cek Risiko Antraknose Cabai

Web app mobile-first untuk evaluasi risiko penyakit antraknose (*Colletotrichum* spp.) pada tanaman cabai. Pengguna mencentang rekomendasi pengendalian yang sudah diterapkan dan memasukkan kondisi cuaca; dashboard memperbarui skor risiko 0–100 secara dinamis.

Disusun untuk **BRMP Kalimantan Barat** berdasarkan *Petunjuk Pencegahan & Penanganan Antraknose pada Cabai*.

## Fitur

- **Dashboard risiko 0–100** dengan needle gradien (Rendah → Sangat Tinggi) dan saran kontekstual.
- **Input cuaca** segmented control: curah hujan, kelembaban (RH), suhu, riwayat antraknose.
- **Checklist 24 item** dalam 8 kategori: Varietas, Perlakuan Benih, Sanitasi, Budidaya, Air, Hayati, Monitoring, Pasca Panen.
- **Cakupan per kategori** dengan progress bar adaptif warna.
- **Persist otomatis** via `localStorage` — data tersimpan di perangkat.
- **Mobile-first**, tap target besar, bekerja offline setelah load pertama.

## Model Risiko

```
risk = clamp(0..100, 50 + tekanan_cuaca − 0.6 × pencegahan_persen)
```

- Tekanan cuaca maks +50 (hujan 20 + RH 15 + suhu 10 + riwayat 10).
- Pencegahan: total bobot 100, terdistribusi sesuai dampak praktik.
- Centang penuh + cuaca kering → risiko mendekati 0.
- Tanpa praktik + cuaca buruk → risiko 100.

## Menjalankan Lokal

Static HTML — buka langsung:

```bash
xdg-open index.html      # Linux
start index.html         # Windows
open index.html          # macOS
```

Atau serve via HTTP server:

```bash
python3 -m http.server 8080
# buka http://localhost:8080
```

## Deploy

Static site, tidak butuh build step. Bisa dideploy ke Vercel, Netlify, GitHub Pages, atau hosting statis lainnya.

## Lisensi

Bahan rujukan internal BRMP Kalbar. Penggunaan di luar konteks harap menyesuaikan dengan kondisi lapangan setempat.
