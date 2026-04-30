# Artemis II — Trajectory Analysis

> *"We choose to go to the Moon not because it is easy, but because it is hard."* — John F. Kennedy

Pada **1 April 2026**, untuk pertama kalinya sejak program Apollo, manusia kembali menuju Bulan. Bukan untuk mendarat — tapi untuk membuktikan bahwa mereka siap.

Misi **Artemis II** membawa empat astronaut mengelilingi Bulan dalam perjalanan 9 hari menggunakan kapsul Orion yang mereka beri nama *"Integrity"*. Repo ini merekonstruksi perjalanan itu secara matematis, menggunakan data ephemeris nyata dari **NASA JPL Horizons** untuk memvisualisasikan setiap kilometer yang ditempuh.

![Trajectory 2D](trajectory_2d.png)

---

## Tentang Misi

Artemis II adalah misi berawak pertama dalam program Artemis — generasi penerus Apollo. Berbeda dengan Artemis I yang tanpa awak, misi ini membawa empat astronaut dalam lintasan *free-return trajectory*: sebuah jalur yang dirancang sedemikian rupa sehingga jika semua sistem gagal, gravitasi Bulan dan Bumi akan secara alami mengembalikan kapsul ke Bumi tanpa perlu satu pun manuver tambahan.

**Kru:**
- 🧑‍✈️ **Reid Wiseman** — Commander (NASA)
- 🧑‍✈️ **Victor Glover** — Pilot (NASA)
- 👩‍🚀 **Christina Koch** — Mission Specialist (NASA)
- 🧑‍🚀 **Jeremy Hansen** — Mission Specialist (CSA, Kanada)

**Timeline singkat:**

| Hari | Kejadian |
|------|----------|
| 1 | Launch dari KSC, deploy solar array, manuver orbit awal |
| 2 | **Translunar Injection (TLI)** — burn 5m55s, delta-v +388 m/s, arah ke Bulan |
| 5–6 | Masuk Sphere of Influence Bulan, closest approach **8,282 km** dari permukaan |
| 6 | Jarak maks dari Bumi: **413,146 km** |
| 7–9 | Return trajectory, tiga correction burn kecil |
| 10 | Entry interface 122 km, splashdown Samudra Pasifik |

---

## Visualisasi

![Distance Profile](distance_profile.png)

Grafik di atas menunjukkan dua kurva yang saling berkebalikan: saat Orion menjauhi Bumi, ia mendekati Bulan. Puncaknya terjadi pada Hari ke-6 — titik di mana Orion berada sejauh 413 ribu km dari Bumi, namun hanya 8 ribu km dari permukaan Bulan.

![Speed Profile](speed_profile.png)

Profil kecepatan mencerminkan hukum gravitasi: Orion melambat saat mendaki "bukit gravitasi" Bumi, lalu mempercepat saat tertarik Bulan, kemudian mempercepat lagi saat jatuh kembali ke Bumi. Setiap garis vertikal adalah manuver burn yang mengubah jalur.

![Trajectory 3D](trajectory_3d.png)

---

## Dataset

Data diambil langsung dari NASA JPL Horizons System — sistem efemerida resmi NASA yang digunakan para ilmuwan dan insinyur misi.

| File | Isi |
|------|-----|
| `artemis_ephemeris.txt` | Posisi & kecepatan Orion "Integrity" (body ID `-1024`), diperbarui 10 Apr 2026 |
| `moon_ephemeris.txt` | Posisi Bulan (body ID `301`, DE441), step 5 menit |

Format data: setiap baris antara `$$SOE` dan `$$EOE` berisi Julian Date, timestamp, posisi XYZ (km), dan kecepatan VxVyVz (km/s) dalam frame Ekliptika J2000.0 pusat Bumi.

---

## Cara Menjalankan

```bash
pip install -r requirements.txt
jupyter notebook artemis_ii_analysis.ipynb
```

Notebook sudah dieksekusi dengan output tersimpan — bisa langsung dilihat tanpa perlu menjalankan ulang.

---

## Sumber Data

NASA JPL Horizons System — [ssd.jpl.nasa.gov](https://ssd.jpl.nasa.gov/horizons/)
