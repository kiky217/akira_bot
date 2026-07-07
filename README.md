# akira_bot_trading
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9
# 10

akira_bot_trading adalah bot trading Indodax berbasis Docker untuk gaya scalping fleksibel.

Fokus utama:
- Memberikan informasi pasar yang akurat
- Mendukung multi-pair
- Bisa berjalan 24/7 di VPS
- Bisa mode simulasi / dry-run
- Bisa eksekusi order jika live trading diaktifkan
- Notifikasi menggunakan Telegram

---

## 1. Struktur Folder

Direkomendasikan menggunakan path: /opt/akira_bot

```bash
/opt/akira_bot
├── docker-compose.yml
├── .env
├── .env.example
├── app
│   ├── main.py
│   └── requirements.txt
└── logs

---

### 2. Masuk ke Folder Project
sudo mkdir -p /opt/akira_bot/app
sudo mkdir -p /opt/akira_bot/logs
cd /opt/akira_bot

---

#### 3. Buat File Konfigurasi
cp .env.example .env
nano .env

Isi bagian penting:

INDODAX_API_KEY=isi_api_key_kamu
INDODAX_API_SECRET=isi_secret_key_kamu
PAIRS=BTC_IDR,ETH_IDR,XRP_IDR
ENABLE_LIVE_TRADING=false
DRY_RUN=true

Untuk awal, gunakan:

ENABLE_LIVE_TRADING=false
DRY_RUN=true

Jangan langsung live trading sebelum bot diuji.

---

##### 4. Jalankan Bot
docker compose up -d

Cek status:

docker ps

Lihat log:

docker compose logs -f akira_bot

Atau:

tail -f logs/trading.log

---

###### 5. Matikan Bot
docker compose down

Atau stop saja:

docker compose stop akira_bot

---

####### 6. Mode Aman

Mode aman untuk testing:

ENABLE_LIVE_TRADING=false
DRY_RUN=true

Mode live:

ENABLE_LIVE_TRADING=true
DRY_RUN=false

Gunakan mode live hanya setelah strategi diuji.

---

######## 7. Telegram

Tambahkan token bot Telegram:

TELEGRAM_ENABLED=true
TELEGRAM_BOT_TOKEN=isi_token_bot
TELEGRAM_CHAT_ID=isi_chat_id

Telegram dipakai untuk:

Notifikasi sinyal
Notifikasi order
Error penting
Status bot

---

######### 8. Catatan Keamanan
Jangan upload file .env ke GitHub
Jangan bagikan API secret
Gunakan API key Indodax dengan izin seperlunya
Mulai dari nominal kecil
Aktifkan live trading hanya jika sudah paham risikonya

---

########## 9. Perintah Update

Jika ada perubahan kode:

docker compose down
docker compose up -d --build

---

########### 10. Catatan Risiko

Trading crypto memiliki risiko tinggi.
Bot ini adalah alat bantu otomasi, bukan jaminan profit.


Itu fondasi Docker Compose dan README awal yang paling aman untuk VPS kamu.
