# 🚀 NgAppID Deploy

Aplikasi desktop buat **deploy project dari PC ke berbagai platform** — semua dari satu aplikasi. Gak perlu buka terminal.

![Status](https://img.shields.io/badge/status-active-brightgreen)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blue)
![Go](https://img.shields.io/badge/Go-1.26-00ADD8)
![React](https://img.shields.io/badge/React-19-61DAFB)
![Wails](https://img.shields.io/badge/Wails-v3-red)
![License](https://img.shields.io/badge/license-MIT-green)

---

## 📑 Daftar Isi

- [Tentang](#-tentang)
- [Fitur](#-fitur)
- [Platform yang Didukung](#-platform-yang-didukung)
- [Instalasi](#-instalasi)
- [Cara Pakai](#-cara-pakai)
- [Struktur Data](#-struktur-data)
- [Contoh Kasus](#-contoh-kasus)
- [Deploy Flow](#-deploy-flow)
- [Environment Variables](#-environment-variables)
- [Troubleshooting](#-troubleshooting)
- [Tips & Trik](#-tips--trik)
- [Roadmap](#-roadmap)
- [FAQ](#-faq)
- [Tech Stack](#️-tech-stack)
- [Struktur File](#-struktur-file)
- [Kontribusi](#-kontribusi)
- [Dukungan](#-dukungan)
- [Kontak](#-kontak)
- [Lisensi](#-lisensi)
- [Pesan dari Pengembang](#-pesan-dari-pengembang)

---

## 📖 Tentang

**NgAppID Deploy** adalah aplikasi desktop yang dibuat dengan **Wails v3** (Go + React) untuk mempermudah proses deploy project dari PC lokal ke berbagai platform hosting & cloud.

Cukup pilih project, pilih server, klik **Deploy** — selesai. Gak perlu buka banyak terminal, gak perlu hafal command CLI yang beda-beda.

**NgAppID** adalah **inisiatif open-source murni** yang berfokus menciptakan berbagai alat untuk workflow yang ringan dan super cepat.

---

## ✨ Fitur

- 🌐 **Multi-platform deploy** — Vercel, Netlify, Cloudflare Pages, Railway
- 🖥️ **VPS deploy** — SSH (dengan post-deploy command), SFTP, FTP
- ☁️ **AWS EC2** — deploy via `.pem` key
- 📦 **Auto-install CLI** — kalau CLI belum ada, aplikasi install sendiri
- 🔐 **Auto-login** — cukup paste token, langsung login
- 🔨 **Build pipeline otomatis** — `npm run build`, `go build`, dll
- 📂 **Browse folder server** — pilih folder remote via UI
- 📊 **Log realtime** — lihat progress deploy langsung
- 📜 **History deploy** — riwayat 100 deploy terakhir
- 🎨 **Theme Dark/Light** — pilih sesuai selera
- 👤 **Login lokal** — data disimpan di PC sendiri
- 🖥️ **Multi server & project** — kelola banyak server dan project
- 📋 **Modal 2 kolom** — form kiri, panduan kanan
- 📋 **Copy/Save log** — simpan log deploy ke clipboard/file
- 🔒 **Enkripsi credential** — password disimpan dengan AES-GCM

---

## 🎯 Platform yang Didukung

| Platform | Auth | CLI | Status |
|----------|------|-----|--------|
| **Vercel** | Token | `vercel` | ✅ |
| **Netlify** | Token | `netlify-cli` | ✅ |
| **Cloudflare Pages** | API Token | `wrangler` | ✅ |
| **Railway** | Account Token | `railway` | ✅ |
| **SSH (VPS)** | Password | - | ✅ |
| **SFTP** | Password | - | ✅ |
| **FTP** | Password | - | ✅ |
| **AWS EC2** | `.pem` Key | - | ✅ |
| **AWS S3** | Access Key | - | 🔜 |
| **Google Apps Script** | OAuth | `clasp` | 🔜 |

---

## 📥 Instalasi

### Prasyarat

- **Node.js** 20+ — [download](https://nodejs.org)
- **Go** 1.25+ — [download](https://go.dev)
- **Wails v3** — `go install github.com/wailsapp/wails/v3/cmd/wails3@latest`

### Build dari Source

```bash
git clone https://github.com/yedincoder/ngappiddeploy.git
cd ngappiddeploy
go mod tidy
wails3 build
```

Binary ada di `bin/ngappid-deploy.exe`

### Jalanin Dev

```bash
wails3 dev
```

---

## 🚀 Cara Pakai

### 1️⃣ Setup Akun

**Pertama Buka:**

1. Double-click `ngappid-deploy.exe`
2. Muncul halaman **Setup Awal**
3. Isi:
   - **Username:** bebas (contoh: `admin`)
   - **Password:** min 4 karakter
   - **Konfirmasi Password:** ulangi
4. Klik **✅ Buat Akun**

**Buka Lagi:**

1. Muncul halaman **Login**
2. Isi username + password
3. Klik **🔐 Login**

Data disimpan di `~/.ngappid/auth.json`

---

### 2️⃣ Tambah Server

**Server = tempat deploy.**

- Sidebar kiri → klik **🖥️ Servers**
- Klik **+ Tambah Server**
- Modal kebuka 2 kolom: **Kiri** form, **Kanan** panduan

#### Contoh: Vercel

**Langkah 1 — Isi Nama**
- **Nama:** `Vercel Saya`

**Langkah 2 — Pilih Tipe**
- Dropdown → **Vercel**
- App otomatis cek CLI

**Kalau CLI Belum Ada:**
- Muncul: `⚠️ vercel CLI belum keinstall`
- Klik **📦 Install vercel Sekarang**
- Overlay loading muncul (spinner + timer)
- Tunggu 3-5 menit
- Selesai: `✅ vercel CLI terinstall`

**Langkah 3 — Dapet Token**

Di kolom kanan ada panduan:

1. Klik **🌐 Buka Dashboard**
2. Login Vercel
3. Klik **Create Token**
4. Scope: **Full Account**
5. Expiration: **No Expiration**
6. Klik **Create**
7. **Copy token**

**Langkah 4 — Paste Token**
- Paste di field **Token**
- **Project Name:** biarin kosong

**Langkah 5 — Login**
- Klik **🔐 Login**
- Status: `✅ Login sebagai: username`

**Langkah 6 — Simpan**
- Klik **Simpan** → toast ijo

#### Contoh: Netlify

- Token: https://app.netlify.com/user/applications#personal-access-tokens
- CLI: `netlify-cli`

Cara sama kayak Vercel.

#### Contoh: Cloudflare Pages

- Token: https://dash.cloudflare.com/profile/api-tokens
- Pilih **Create Token** → **Edit Cloudflare Workers**
- CLI: `wrangler`

**Penting:** Isi **Project Name** (huruf kecil, contoh: `ngappid-test`)
App auto-create project kalau belum ada.

#### Contoh: Railway

- Token: https://railway.app/account/tokens
- CLI: `railway`
- **Penting:** Isi **Project Name**

#### Contoh: SSH (VPS)

- **Host:** `123.456.789.0`
- **Port:** `22`
- **User:** `root`
- **Password:** `••••••••`
- **Remote Path:** `/var/www/app`
- **Post-Deploy:** `pm2 restart app` (opsional)

#### Contoh: SFTP

- **Host:** IP VPS
- **Port:** `22`
- **User:** `root`
- **Password:** password VPS
- **Remote Path:** `/var/www/app`

#### Contoh: FTP

- **Host:** `ftp.domainlu.com`
- **Port:** `21`
- **User:** cPanel username
- **Password:** cPanel password
- **Remote Path:** `/public_html`

#### Contoh: AWS EC2

- **Host:** IP public EC2
- **Port:** `22`
- **User:** `ec2-user` / `ubuntu`
- **Private Key:** klik **📁** → pilih file `.pem`
- **Remote Path:** `/var/www/html`

---

### 3️⃣ Tambah Project

**Project = folder di PC lu yang mau di-deploy.**

- Sidebar → **📦 Projects**
- Klik **+ Tambah Project**

| Field | Contoh | Keterangan |
|-------|--------|------------|
| **Nama** | `portfolio` | Bebas |
| **Path** | `D:\projects\portfolio` | Klik 📁 buat browse |
| **Server** | `Vercel Saya` | Pilih dari dropdown |
| **Build Command** | `npm run build` | Opsional |
| **Output Dir** | `dist` | Opsional |

**Tips Path:**
- Node.js → harus ada `package.json`
- Golang → harus ada `go.mod`
- Static → harus ada `index.html`

**Tips Build:**
- React/Vue/Vite → `npm run build` + output `dist`
- Next.js → `npm run build` + output `out`
- Golang → `go build -o app` + output `.`
- Static HTML → kosongin dua-duanya

---

### 4️⃣ Deploy

- Di list → **klik project**
- Klik **🚀 Deploy** (kanan atas)

Log muncul:

```text
=== Deploy dimulai ===
Project: portfolio
Server: Vercel Saya (vercel)

Build: npm run build
  ✓ built in 1.2s
Build sukses

CLI: vercel --prod --yes
  ✓ Deployed to production
  https://portfolio-xxx.vercel.app

Deploy sukses
```

**Setelah Selesai:**
- Toast ijo: "Deploy sukses"
- URL live muncul → klik buka di browser
- History ke-update

**Log Actions:**
- **📋 Copy** → copy ke clipboard
- **💾 Save** → download `.txt`
- **🗑️ Clear** → hapus tampilan

---

## 📁 Struktur Data

Semua data di **`C:\Users\<username>\.ngappid\`**:

```text
.ngappid/
├── auth.json         # Username + password (hash)
├── servers.json      # Daftar server
├── projects.json     # Daftar project
├── history.json      # Riwayat deploy (max 100)
├── settings.json     # Pengaturan tema, dll
└── account.json      # Profile
```

**Token CLI:**

| Tool | Lokasi |
|------|--------|
| Vercel | `~/.vercel/auth.json` |
| Netlify | `~/.netlify/config.json` |
| Cloudflare | `~/.wrangler/cf_token` |

---

## 🎯 Contoh Kasus

### React App → Vercel

1. **Server:** Vercel + token dari vercel.com
2. **Project:**
   - Path: `D:\projects\my-react`
   - Build: `npm run build`
   - Output: `dist`
3. **Deploy** → URL muncul

### Static HTML → Netlify

1. **Server:** Netlify
2. **Project:**
   - Path: `D:\projects\landing`
   - Build: *(kosong)*
   - Output: *(kosong)*
3. **Deploy** → URL muncul

### Golang → VPS (SSH)

1. **Server:** SSH + password VPS
2. **Project:**
   - Path: `D:\projects\go-api`
   - Build: `go build -o app`
   - Output: `.`
   - Post-Deploy: `pm2 restart app`
3. **Deploy** → binary ke-upload → service restart

### PHP → Shared Hosting (FTP)

1. **Server:** FTP + credential cPanel
2. **Project:**
   - Path: `D:\projects\php-app`
   - Build: *(kosong)*
   - Output: *(kosong)*
3. **Deploy** → upload ke `/public_html`

### Next.js → Cloudflare

1. **Server:** Cloudflare
   - Token: Edit Cloudflare Workers
   - Project Name: `my-nextjs`
2. **Project:**
   - Path: `D:\projects\my-nextjs`
   - Build: `npm run build`
   - Output: `out`
3. **Deploy** → auto-create → URL

### Static Site → AWS EC2

1. **Server:** AWS EC2 + file `.pem`
2. **Project:**
   - Path: `D:\projects\static`
   - Build: *(kosong)*
   - Output: *(kosong)*
3. **Deploy** → upload ke `/var/www/html`

---

## 🔄 Deploy Flow

```text
Klik 🚀 Deploy
   ↓
Build lokal (kalau ada buildCommand)
   ↓
Pass token ke CLI (env)
   ↓
CLI deploy ke platform
   ↓
URL live muncul
   ↓
Simpan ke history
```

**Command per platform:**

| Platform | Command |
|----------|---------|
| Vercel | `vercel --prod --yes` |
| Netlify | `netlify deploy --prod --dir=<output>` |
| Cloudflare | `wrangler pages deploy <output> --project-name=<name>` |
| Railway | `railway init -n <name>` + `railway up --detach` |
| SSH | SFTP upload + `postCommand` |
| SFTP | SFTP upload |
| FTP | FTP upload |
| AWS EC2 | SFTP upload (`.pem` auth) |

---

## 🔐 Environment Variables

App ini pakai env variable untuk autentikasi CLI:

| Platform | Env Variable |
|----------|--------------|
| Vercel | `VERCEL_TOKEN` |
| Netlify | `NETLIFY_AUTH_TOKEN` |
| Cloudflare | `CLOUDFLARE_API_TOKEN` |
| Railway | `RAILWAY_API_TOKEN` |

Env variable di-set otomatis oleh aplikasi waktu klik **Login**.

---

## ❓ Troubleshooting

| Masalah | Solusi |
|---------|--------|
| **CLI gak kedetect** | Klik 📦 Install di modal, tunggu 3-5 menit |
| **Token invalid** | Bikin token baru di dashboard platform |
| **Build failed** | Coba `npm run build` manual, cek error |
| **Cloudflare "project does not exist"** | Cek Project Name, app auto-create |
| **Login gagal** | Cek log, biasanya token salah |
| **Lupa password** | Hapus `~/.ngappid/auth.json`, setup ulang |
| **SSH connection refused** | Cek firewall VPS, port 22 open |
| **FTP timeout** | Cek port 21, pastikan FTP server jalan |
| **Folder gak ketemu** | Cek Path project & Output Dir |
| **Theme gak ganti** | Restart app setelah ganti theme |

**Error umum Cloudflare:**

- `Invalid access token` → token salah / salah scope
- `project does not exist` → project name salah, app auto-create
- `You are not authenticated` → token gak ke-passing

**Error umum Railway:**

- `Unauthorized` → pakai `RAILWAY_API_TOKEN`, bukan `RAILWAY_TOKEN`
- `could not find the CLI binary` → postinstall gagal, reinstall via app
- `No linked project` → `railway init` gagal, cek Project Name

---

## 💡 Tips & Trik

- **Token** disimpan di file config CLI masing-masing
- **Log** bisa di-copy → paste di notepad
- **History** max 100 entries
- **Build command** opsional
- **Output dir** harus sesuai hasil build
- **Browse folder server** — klik 📂 di field Remote Path (server harus disimpan dulu)
- **Theme** — ganti di Settings, langsung berubah
- **Shortcut** — Ctrl+C di log buat copy

---

## 🗺️ Roadmap

### ✅ Selesai
- [x] Login lokal (setup + login)
- [x] Dashboard (stats + history + info)
- [x] Servers (9 tipe)
- [x] Projects + Project Detail
- [x] Deploy: Vercel, Netlify, CF, Railway
- [x] Deploy: SSH, SFTP, FTP, AWS EC2
- [x] Auto-install CLI
- [x] Auto-login token
- [x] Browse folder server
- [x] Theme Dark/Light
- [x] History deploy
- [x] About page
- [x] Toast notif

### 🚧 Sedang Dikerjakan
- [ ] AWS S3 deployer
- [ ] Google Apps Script deployer

### 📋 Rencana
- [ ] Git integration (clone/pull/push)
- [ ] SSH key auth (bukan cuma password)
- [ ] Custom post-deploy script
- [ ] Multi-branch deploy
- [ ] Auto-deploy via file watcher
- [ ] Notifikasi desktop
- [ ] Export/import config
- [ ] Docker support

---

## ❔ FAQ

**Q: Apakah aplikasi ini gratis?**
A: Ya, gratis dan selamanya gratis. Open-source.

**Q: Apakah data saya dikirim ke server?**
A: Tidak. Semua data tersimpan lokal di PC kamu (`~/.ngappid/`).

**Q: Apakah bisa dipakai di Mac/Linux?**
A: Ya. Wails v3 support Windows, macOS, dan Linux.

**Q: Apakah butuh Node.js?**
A: Ya, buat install CLI (Vercel, Netlify, dll). Minimal Node.js 20.

**Q: Bagaimana kalau lupa password?**
A: Hapus file `~/.ngappid/auth.json`, buka app lagi, setup ulang.

**Q: Apakah bisa deploy ke multiple server sekaligus?**
A: Belum. Satu project = satu server. Fitur multi-target sedang direncanakan.

**Q: Apakah log bisa disimpan?**
A: Ya. Klik **💾 Save** di panel log → file `.txt` ke-download.

---

## 🛠️ Tech Stack

- **[Wails v3](https://wails.io)** — Desktop framework (beta.27)
- **[Go 1.26](https://go.dev)** — Backend
- **[React 19](https://react.dev)** — Frontend
- **[TypeScript](https://typescriptlang.org)** — Type safety
- **[Vite 8](https://vitejs.dev)** — Build tool
- **[pkg/sftp](https://github.com/pkg/sftp)** — SFTP client
- **[golang.org/x/crypto/ssh](https://pkg.go.dev/golang.org/x/crypto/ssh)** — SSH client
- **[jlaffaye/ftp](https://github.com/jlaffaye/ftp)** — FTP client

---

## 📂 Struktur File

```text
ngappid-deploy/
├── main.go                  # Entry point Wails
├── deployservice.go         # Service utama
├── authstore.go             # Auth lokal
├── credential.go            # Credential (AES-GCM)
├── json.go                  # Helper JSON
├── go.mod
├── go.sum
├── frontend/
│   ├── public/
│   │   ├── appicon.png
│   │   ├── devicon.png
│   │   └── qris.png
│   ├── src/
│   │   ├── App.tsx          # UI utama
│   │   ├── App.css          # Styling
│   │   └── main.tsx         # Entry React
│   └── bindings/            # Auto-generated
├── bin/                     # Binary output
└── README.md
```

---

## 🤝 Kontribusi

Kontribusi sangat diterima! Caranya:

1. **Fork** repository ini
2. **Buat branch** baru (`git checkout -b fitur-baru`)
3. **Commit** perubahan (`git commit -m 'Tambah fitur X'`)
4. **Push** ke branch (`git push origin fitur-baru`)
5. **Buat Pull Request**

**Jenis kontribusi yang diterima:**
- 🐛 Fix bug
- ✨ Fitur baru
- 📝 Perbaikan dokumentasi
- 🎨 Perbaikan UI/UX
- 🌐 Terjemahan
- 💡 Saran ide

---

## 💝 Dukungan

Aplikasi ini **gratis** dan **selamanya gratis**. Kalau berguna:

| Dukungan | Cara |
|----------|------|
| ⭐ **Bintang Repo** | Kasih bintang di GitHub |
| 🐛 **Lapor Bug** | Buat issue di GitHub |
| 💡 **Kasih Masukan** | Saranin fitur baru |
| 📢 **Share** | Bagikan ke developer lain |
| ☕ **Traktir Kopi** | Scan QRIS di halaman About |

---

## 📞 Kontak

**YedinCoder** — Full-stack Developer

- 📧 Email: [yedicoder@gmail.com](mailto:yedicoder@gmail.com)
- 💬 WhatsApp: [08977487315](https://wa.me/628977487315)
- 🌐 Website: [yedin.my.id](https://yedin.my.id)
- 🔗 GitHub: [@yedincoder](https://github.com/yedincoder)
- 📦 Repo: [ngappiddeploy](https://github.com/yedincoder/ngappiddeploy)
- 🚀 Ecosystem: [dev.ngappid.com](https://dev.ngappid.com)

---

## 📄 Lisensi

MIT License — bebas dipakai, dimodifikasi, dan dibagikan.

```
MIT License

Copyright (c) 2026 YedinCoder

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 💌 Pesan dari Pengembang

> **Halo, developer!** 👋
>
> Terima kasih sudah mampir ke **NgAppID Deploy**.
>
> Aplikasi ini gue bikin karena **capek** buka banyak terminal tiap kali deploy project. FTP manual, SSH manual, Vercel CLI, Netlify CLI — semua beda-beda. Akhirnya gue bikin satu alat yang bisa handle semuanya.
>
> **NgAppID** adalah **inisiatif open-source murni** — gak ada iklan, gak ada tracking, gak ada data yang dikirim ke server. Semua berjalan lokal di PC kamu.
>
> Kalau aplikasi ini **membantu pekerjaan kamu**, tolong:
>
> - ⭐ Kasih bintang di GitHub
> - 🐛 Laporkan bug yang kamu temuin
> - 💡 Saranin fitur baru
> - 📢 Bagikan ke developer lain
>
> **Feedback kamu** adalah motivasi terbesar gue untuk terus ngembangin project ini.
>
> Jangan takut buat kontribusi — mau itu fix typo, tambah fitur, atau bantu dokumentasi. Semua bermanfaat. 🙏
>
> **Selamat deploy!** 🚀
>
> — **YedinCoder**
> *Banten, Indonesia*

---

**Dibuat dengan 🔥 oleh [@yedincoder](https://github.com/yedincoder)**

*Terakhir update: 4 Oktober 2026*
