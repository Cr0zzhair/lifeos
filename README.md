# ⚡ LIFE OS v3.0

> **No Zero Days** — Gamified daily quest tracker buat yang mau level up tiap hari.

![version](https://img.shields.io/badge/version-3.0-purple)
![stack](https://img.shields.io/badge/stack-Vanilla%20JS-yellow)
![deploy](https://img.shields.io/badge/deploy-GitHub%20Pages-black)

---

## Apa ini?

LIFE OS adalah personal quest tracker berbasis browser — tanpa app store, tanpa subscription, tanpa tracking. Dibangun dengan Vanilla JS murni, bisa diinstall di HP seperti app biasa (PWA).

Konsepnya simpel: **setiap hari kamu dapat quest**. Selesaikan minimal satu per kategori → itu bukan Zero Day.

---

## Fitur

- 🎮 **5 kategori quest** — Knowledge, Speech, Health, Purpose, Finances
- ⚡ **XP & Level system** — tiap quest kasih XP, level up unlock shield
- 🔥 **Streak tracker** — streak harian per kategori
- 🛡️ **Shield system** — lewat 1 hari? shield kepake, streak aman
- 😴 **Energy mode** — Lazy / Normal / Power (sesuai mood hari ini)
- 📊 **Stats dashboard** — weekly XP, best streak, progress per kategori
- 📱 **PWA ready** — install di home screen HP seperti app native
- 🔐 **Private login** — akses terkunci, data tersimpan per user
- 💾 **Offline first** — data di localStorage, tetap jalan tanpa internet

---

## Tech Stack

| Layer | Teknologi |
|-------|-----------|
| Frontend | Vanilla JS, HTML, CSS |
| Storage | localStorage (offline) |
| Auth | Hardcode + XOR obfuscation |
| Font | JetBrains Mono (Google Fonts) |
| Deploy | GitHub Pages |
| PWA | Web App Manifest |

---

## Struktur File

```
lifeos/
├── index.html      # Semua logic app (single file)
├── manifest.json   # PWA config
└── README.md       # Ini
```

---

## Deploy

### GitHub Pages

1. Fork / upload ke repo GitHub
2. Masuk **Settings → Pages**
3. Source: `Deploy from a branch` → branch `main` → folder `/root`
4. Tunggu 1-2 menit → buka `https://username.github.io/lifeos/`

### Netlify (alternatif)

1. Buka [netlify.com/drop](https://app.netlify.com/drop)
2. Drag folder project → dapat URL langsung

---

## Install sebagai App (PWA)

**Android (Chrome):**
tap menu ⋮ → *Install app* atau *Add to Home Screen*

**iPhone (Safari):**
tap Share → *Add to Home Screen*

---

## Menambah / Mengubah User

Buka `index.html`, cari bagian `_0xSys`. Untuk generate kredensial baru, jalankan script ini di terminal:

```python
import base64

def obfuscate(text, key=7):
    b64 = base64.b64encode(text.encode()).decode()
    xored = [ord(c) ^ key for c in b64]
    n = len(xored)
    return [xored[:n//3], xored[n//3:2*n//3], xored[2*n//3:]]

username = "namauser"
password = "passwordkamu"

print("u:", obfuscate(username))
print("p:", obfuscate(password))
```

Paste hasilnya ke array `_cfg` di `index.html`.

---

## Catatan Keamanan

Project ini pakai **obfuscation**, bukan enkripsi. Cukup untuk pemakaian pribadi — jangan simpan data sensitif (nomor rekening, password penting, dll) di dalam app ini.

Kalau mau upgrade ke auth yang proper → pelajari **Firebase Auth** atau **backend session dengan JWT**.

---

## Roadmap

- [ ] Tambah custom quest (user-defined)
- [ ] Export data ke CSV
- [ ] Dark/light theme toggle
- [ ] Notifikasi reminder harian
- [ ] Backend auth dengan JWT

---

## Author

**Crozzhair** — IT student, belajar cybersecurity & backend.

> *"The secret of getting ahead is getting started."*
