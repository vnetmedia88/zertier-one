# 🚀 Zerotier in Docker

Run [ZeroTier One](https://www.zerotier.com/) inside a Docker container for easy, portable, and lightweight networking.

## 📦 Features
- Based on official `zerotier/zerotier` Docker image
- Auto-starts with your system (`--restart unless-stopped`)
- Compatible with Linux hosts
- Enables full peer-to-peer mesh networking inside Docker

---

## 🛠 Installation

### 1. Install Docker (if not installed)
```bash
sudo apt update
sudo apt install docker.io -y
```

---

## ⬇️ 2. Run Zerotier containert
```bash
docker run -d \
  --name zerotier \
  --device=/dev/net/tun \
  --net=host \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_ADMIN \
  --cap-add=SYS_RAWIO \
  --cap-add=NET_RAW \
  --cap-add=SYS_MODULE \
  --restart unless-stopped \
  zerotier/zerotier

```
Pastikan host Anda mengizinkan perangkat TUN dan penerusan IP.

---

## 🌐 Join Zerotier Network
```bash
docker exec zerotier zerotier-cli join <your_network_id>

```
Ganti `<your_network_id>` dengan Network Id Zero-tier.
## CONTOH
```bash
docker exec zerotier zerotier-cli join abcdef1234567890

```
---

## CEK STATUS

```bash
docker exec zerotier zerotier-cli info

```
Anda akan melihat sesuatu seperti:

```
200 info <node_id> ONLINE <version>

```
LANGSUNG GASS PAK EKO





© 2025 vnetmedia88
