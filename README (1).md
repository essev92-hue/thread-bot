# 🧵 Twitter Thread Generator Bot — Multi-AI Pro

Bot Telegram yang secara otomatis **meriset semua media publik sebuah project** (website, Twitter/X, GitHub, Telegram, Discord, Medium, Reddit, CoinGecko) lalu **menuliskan Twitter thread** menggunakan AI pilihan kamu.

---

## ✨ Fitur

- **Multi-media research** — scraping website, Twitter/X, GitHub, Telegram, Discord, Medium/Substack, Reddit, CoinGecko, dan web search
- **3 AI Provider** — Groq (LLaMA 3.3 70B), DeepSeek (R1), OpenAI (GPT-4o) dengan fallback otomatis
- **Pilihan bahasa** — English atau Bahasa Indonesia
- **Ingat preferensi** — provider & bahasa terakhir disimpan per user
- **Rate limiting** — maks 5 request per jam per user
- **Status update real-time** — tampilkan progress riset step by step

---

## 🗂️ Struktur File

```
.
├── bot.py                # Entry point — Telegram bot handler
├── thread_generator.py   # Orkestrasi generate thread (riset + AI)
├── media_researcher.py   # Scraping multi-media (GitHub, Telegram, dll)
├── twitter_scraper.py    # Scraping Twitter/X (Nitter → x.com → Search)
├── ai_providers.py       # Abstraksi Groq / DeepSeek / OpenAI
├── requirements.txt      # Dependencies Python
├── .env.example          # Template konfigurasi
└── .env                  # Konfigurasi kamu (buat dari .env.example)
```

---

## 🚀 Instalasi

### 1. Clone / download project

```bash
git clone <repo-url>
cd webthreadv2
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

> Di Termux, tambahkan flag: `pip install -r requirements.txt --break-system-packages`

### 3. Buat file `.env`

```bash
cp .env.example .env
```

Lalu edit `.env` dan isi token & API key yang dibutuhkan (lihat bagian [Konfigurasi](#️-konfigurasi) di bawah).

### 4. Jalankan bot

```bash
python bot.py
```

---

## ⚙️ Konfigurasi

Salin `.env.example` menjadi `.env`, lalu isi nilai berikut:

| Variable | Wajib | Keterangan |
|---|---|---|
| `TELEGRAM_BOT_TOKEN` | ✅ | Token dari [@BotFather](https://t.me/BotFather) |
| `GROQ_API_KEY` | ⚠️ satu wajib | API key dari [console.groq.com](https://console.groq.com) — **gratis** |
| `DEEPSEEK_API_KEY` | ⚠️ satu wajib | API key dari [platform.deepseek.com](https://platform.deepseek.com) |
| `OPENAI_API_KEY` | ⚠️ satu wajib | API key dari [platform.openai.com](https://platform.openai.com) |

> Minimal isi **satu** dari tiga API key AI. Isi semua ketiganya untuk fallback otomatis.

---

## 🤖 AI Providers

| Provider | Model | Karakter | Biaya |
|---|---|---|---|
| ⚡ Groq | LLaMA 3.3 70B | Tercepat, cocok untuk draft cepat | **Gratis** |
| 🧠 DeepSeek | R1 (Reasoner) | Paling analitis & detail | Sangat murah |
| ✨ OpenAI | GPT-4o | Paling kreatif & natural | Berbayar |

Jika provider yang dipilih gagal, bot otomatis fallback ke provider berikutnya (Groq → DeepSeek → OpenAI).

---

## 📖 Cara Pakai

1. Start bot: `/start`
2. Kirim URL website project (contoh: `https://uniswap.org`)
3. Input Twitter/X handle project — opsional (contoh: `@Uniswap`) atau skip
4. Pilih AI provider
5. Pilih bahasa (English / Bahasa Indonesia)
6. Tunggu 60–120 detik — bot riset semua sumber
7. Thread siap! 🔥

### Commands

| Command | Fungsi |
|---|---|
| `/start` | Mulai dari awal |
| `/help` | Panduan lengkap |
| `/cancel` | Batalkan proses yang sedang berjalan |
| `/prefs` | Lihat preferensi provider & bahasa tersimpan |
| `/status` | Cek sisa rate limit |

---

## 🔍 Sumber Riset

Bot meriset semua sumber publik berikut secara otomatis:

- 🌐 **Website** — halaman utama, docs, whitepaper, roadmap
- 🐦 **Twitter/X** — 3 metode: Nitter → x.com → Web Search
- 🐙 **GitHub** — repo, README, stars, aktivitas terbaru
- 📱 **Telegram** — channel publik, pesan terbaru
- 💬 **Discord** — info server, jumlah member
- 📝 **Medium / Substack** — artikel terbaru
- 🔴 **Reddit** — diskusi komunitas
- 📊 **CoinGecko** — data token (untuk project crypto)
- 🔍 **Web Search** — review & artikel media

---

## ⚡ Menjalankan di Termux (Android)

```bash
# Install Python
pkg install python

# Install dependencies
pip install -r requirements.txt --break-system-packages

# Jalankan
python bot.py

# Jalankan di background (tetap jalan setelah Termux ditutup)
nohup python bot.py &
```

---

## 🔧 Kustomisasi

Edit langsung di `bot.py`:

```python
RATE_LIMIT_MAX    = 5     # Maks request per user per jam
RATE_LIMIT_WINDOW = 3600  # Window waktu rate limit (detik)
```

---

## 📝 Lisensi

MIT License — bebas digunakan dan dimodifikasi.
