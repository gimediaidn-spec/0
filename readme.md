
---

# 🌟 Setup - Tools

```bash
export PATH="/app/local/bin:$PATH"
```Redis & Postgres CLI Setup (Interactive & Modern)

---

## 📌 Table of Contents

1. [Redis CLI](#-redis-cli)
2. [Postgres CLI (pgcli)](#-postgres-cli-pgcli)
3. [Stylish Logs (ccze)](#-stylish-logs-ccze)
4. [Tips & Tricks](#-tips--tricks)

---

## 🟢 Redis CLI

<details>
<summary>Step 1️⃣: Install Dependencies</summary>

```bash
sudo apt update
sudo apt install build-essential tcl -y
```

</details>

<details>
<summary>Step 2️⃣: Download & Build redis-cli</summary>

```bash
cd /app
mkdir -p local/bin
curl -O https://download.redis.io/redis-stable.tar.gz
tar xzvf redis-stable.tar.gz
cd redis-stable
make redis-cli
cp src/redis-cli ../local/bin/
```

</details>

<details>
<summary>Step 3️⃣: Test Binary</summary>

```bash
/app/local/bin/redis-cli --version
file /app/local/bin/redis-cli
```

> ✅ Expected: `ELF 64-bit LSB executable, ARM aarch64` (ARM)

</details>

<details>
<summary>Step 4️⃣: Test Connection</summary>

```bash
/app/local/bin/redis-cli -h redis.redis -p 6379 ping
/app/local/bin/redis-cli -h redis.redis -p 6379 info memory
/app/local/bin/redis-cli -h redis.redis -p 6379 info stats
```

> 🟢 Should return `PONG` & memory/stats info

</details>

---

## 🟡 Postgres CLI (pgcli)

<details>
<summary>Install pgcli</summary>

```bash
sudo apt-get install pgcli -y
```

</details>

<details>
<summary>Connect to Database</summary>

```bash
pgcli postgres://postgres:postgres@postgres.postgres:5432/app
```

> 🔹 Interactive SQL with auto-complete

</details>

---

## 🔵 Stylish Logs (ccze)

<details>
<summary>Install ccze</summary>

```bash
sudo apt-get install ccze -y
```

</details>

<details>
<summary>Realtime Log Monitoring</summary>

```bash
tail -f s.log | ccze -A
```

</details>

<details>
<summary>Full File + Realtime Update</summary>

```bash
cat s.log | ccze -A && tail -f s.log | ccze -A
```

> 🎨 Logs become colorized & easy to read

</details>

---

## 💡 Tips & Tricks

> 🔹 Keep binaries local → `local/bin` for redis-cli
> 🔹 Shared path for multi-process → avoid duplicate node warnings
> 🔹 pgcli is faster & interactive than `psql`
> 🔹 Use ccze for long logs → color makes debugging fun
> 🔹 Always run from `/app` for relative paths to work

---

✅ **Outcome**:

* Clear visual sections
* Collapsible code for neat reading
* Modern, GitHub-ready, interactive
* Easy copy-paste for all commands

---

