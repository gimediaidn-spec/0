
---

# Setup - Tools
```bash
export PATH="/app/local/bin:$PATH"
```
---

## 📌 Redis CLI

### 1. Install Dependencies

```bash
sudo apt update
sudo apt install build-essential tcl -y
```

### 2. Download dan Build `redis-cli` Saja

```bash
cd /app
mkdir -p local/bin
curl -O https://download.redis.io/redis-stable.tar.gz
tar xzvf redis-stable.tar.gz
cd redis-stable

# Build hanya redis-cli
make redis-cli
```

### 3. Copy Binary ke Folder Lokal

```bash
cp src/redis-cli ../local/bin/
```

### 4. Tes Binary

```bash
redis-cli --version
file redis-cli
```

> Output harus mengandung: `ELF 64-bit LSB executable, ARM aarch64` jika sistemmu ARM64.

### 5. Tes Koneksi ke Redis Server

```bash
redis-cli -h redis.redis -p 6379 ping
redis-cli -h redis.redis -p 6379
redis-cli -h redis.redis -p 6379 info memory
redis-cli -h redis.redis -p 6379 info stats
```

---

## 📌 Postgres CLI (`pgcli`)

### 1. Install `pgcli`

```bash
sudo apt-get install pgcli -y
```

### 2. Connect ke Database

```bash
pgcli postgres://postgres:postgres@postgres.postgres:5432/app
```

---

## 📌 Log Styling

### 1. Install `ccze` (colorize logs)

```bash
sudo apt-get install ccze -y
```

### 2. Realtime Log Update

```bash
tail -f s.log | ccze -A
```

### 3. Realtime Full Logs File

```bash
cat s.log | ccze -A && tail -f s.log | ccze -A
```

---

💡 **Tips**

* `redis-cli` yang dibuild lokal berguna jika environment kamu **tidak punya paket Redis default** atau harus kompatibel dengan arsitektur ARM.
* `pgcli` memudahkan query interaktif ke Postgres.
* `ccze` membantu membaca log panjang secara realtime dengan warna untuk memudahkan debugging.

---

