# akira_bot_trading
akira_bot_trading adalah bot trading Indodax berbasis Docker untuk gaya scalping fleksibel.

Fokus utama:
- Memberikan informasi pasar yang akurat
- Mendukung multi-pair
- Bisa berjalan 24/7 di VPS
- Bisa mode simulasi / dry-run
- Bisa eksekusi order jika live trading diaktifkan
- Notifikasi menggunakan Telegram

akira_bot - Landing Page Copy

HERO SECTION

Headline
rading Indodax Otomatis - Tanpa Harus Menatap Layar Seharian**

Subheadline
akira_bot adalah trading bot multi-pair untuk Indodax yang berjalan 24/7 di VPS kamu.
Ia memilih sendiri antara *market order* atau *limit order* berdasarkan spread - secara otomatis, real-time, dan siap deploy dalam hitungan menit menggunakan Docker.

CTA (Primary) 
[Mulai deploy di VPS (Docker)]

Supporting copy
Tidak perlu pengalaman trading profesional.
Tidak perlu server mahal. Cukup VPS, Docker, dan akun Indodax.

SOCIAL PROOF BAR *(placeholder - isi dengan data nyata)*
- Multi-pair aktif secara bersamaan
- Order dieksekusi dalam hitungan detik
- API key disimpan lokal di server kamu - tidak keluar ke mana pun
- Deploy path: `/opt/akira_bot`

BENEFITS SECTION

Mengapa akira_bot berbeda dari bot trading biasa?


✅ Pilih order secara cerdas, bukan asal eksekusi
Banyak bot hanya pakai satu jenis order. akira_bot membaca spread pasar secara real-time - kalau spread sempit, pakai *limit order* untuk biaya lebih hemat; kalau spread lebar, langsung eksekusi dengan *market order* agar tidak ketinggalan momentum. Hasilnya: eksekusi yang lebih efisien, bukan sekadar lebih cepat.


✅ Berjalan terus selagi kamu tidur
Begitu berjalan di VPS, akira_bot tidak butuh kamu online. Ia memantau pasangan trading yang kamu pilih, menganalisis kondisi pasar, dan mengeksekusi order sesuai strategi - terus-menerus, tanpa jeda.


✅ Multi-pair dalam satu instance
Pantau dan tradingkan BTC/IDR, ETH/IDR, USDT/IDR, dan pasangan lainnya secara bersamaan - semua dari satu container Docker yang ringan.


✅ Kontrol penuh ada di tangan kamu
Bot berjalan di VPS-mu sendiri, di dalam folder `/opt/akira_bot`. API key Indodax kamu tidak pernah keluar dari server. Tidak ada pihak ketiga yang menyimpan kredensial kamu.


✅ Ramah pemula, tidak butuh coding
Konfigurasi lewat file `.env` yang sederhana. Tidak ada kode yang perlu ditulis. Tidak ada dashboard berbayar. Hanya Docker, tiga perintah, dan bot kamu sudah live.


 Fitur Lengkap akira_bot:
| Fitur | Detail |
|---|---|
| **Smart Order Routing** | Otomatis memilih market atau limit order berdasarkan spread real-time |
| **Multi-pair Trading** | Jalankan beberapa pasangan crypto sekaligus |
| **Docker-native** | Satu `docker compose up` sudah cukup |
| **Konfigurasi via `.env`** | Semua pengaturan di satu file, tidak ada GUI yang rumit |
| **Stop-loss & Take-profit** | Batas proteksi bawaan untuk setiap posisi |
| **Logging terstruktur** | Semua aktivitas tercatat di `/opt/akira_bot/logs` |
| **Reconnect otomatis** | Jika koneksi ke Indodax putus, bot menyambung kembali sendiri |
| **Mode dry-run** | Test strategi tanpa eksekusi order nyata |
| **Indodax API v2** | Integrasi langsung ke endpoint resmi Indodax |

----------------------------------------------------
# 1. Instalation

```
git clone https://github.com/kiky217/akira_bot.git
mkdir /opt/akira_bot
cd /opt/akira_bot
cp -r akira_bot/ akira_bot_trading
```
# 1. Struktur Folder
Direkomendasikan menggunakan path: ```/opt/akira_bot```

```bash
/opt/akira_bot
├── docker-compose.yml
├── .env
├── .env.example
├── app
│   ├── main.py
│   └── requirements.txt
└── logs
```

# 2. Masuk ke Folder Project

```
sudo mkdir -p /opt/akira_bot/app
sudo mkdir -p /opt/akira_bot/logs
cd /opt/akira_bot
```

# 3. Buat File Konfigurasi
```cp .env.example .env``` 

```nano .env```

Isi bagian penting:

```
INDODAX_API_KEY=isi_api_key_kamu
INDODAX_API_SECRET=isi_secret_key_kamu
PAIRS=BTC_IDR,ETH_IDR,XRP_IDR
ENABLE_LIVE_TRADING=false
DRY_RUN=true
```

Untuk awal, gunakan:

```
ENABLE_LIVE_TRADING=false
DRY_RUN=true
```

Jangan langsung live trading sebelum bot diuji.

# 4. Jalankan Bot
```docker compose up -d```

Cek status:

```docker ps```

Lihat log:

```docker compose logs -f akira_bot```

Atau:

```tail -f logs/trading.log```

# 5. Matikan Bot
```docker compose down```

Atau stop saja:

```docker compose stop akira_bot```

# 6. Mode Aman

Mode aman untuk testing:

```
ENABLE_LIVE_TRADING=false
DRY_RUN=true
```

Mode live:

```
ENABLE_LIVE_TRADING=true
DRY_RUN=false
```

Gunakan mode live hanya setelah strategi diuji.

# 7. Telegram

Tambahkan token bot Telegram:

```
TELEGRAM_ENABLED=true
TELEGRAM_BOT_TOKEN=isi_token_bot
TELEGRAM_CHAT_ID=isi_chat_id
```

Telegram dipakai untuk:

Notifikasi sinyal
Notifikasi order
Error penting
Status bot

# 8. Catatan Keamanan
Jangan bagikan API secret
Gunakan API key Indodax dengan izin seperlunya
Mulai dari nominal kecil
Aktifkan live trading hanya jika sudah paham risikonya

# 9. Perintah Update

Jika ada perubahan kode:

```
docker compose down
docker compose up -d --build
```

# 10. Catatan Risiko

Trading crypto memiliki risiko tinggi.
Bot ini adalah alat bantu otomasi, bukan jaminan profit.


salam sukses @kiky.yudiansyah.
