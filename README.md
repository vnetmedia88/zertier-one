
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
---

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
