# 🚀 Zerotier in linux / stb juga bisa


## 📦 Features
- Compatible with Linux hosts
- Enables full peer-to-peer mesh networking inside 

---

## 🛠 Installation

### 1. Install open terminal
```bash
ssh root@192.168.1.1
```

sesuaikan IP masing masing
Kemudian setelah berhasil masuk menggunakan ssh langkah selanjutnya kita harus menginstall aplikasi zerotier di STB Armbian linux.

---

## ⬇️ 2. Run Zerotier containert
```bash
curl -s https://install.zerotier.com | sudo bash
```
jika error masukan ini
```bash
curl -s 'https://raw.githubusercontent.com/zerotier/ZeroTierOne/master/doc/contact%40zerotier.com.gpg' | gpg --import && \
if z=$(curl -s 'https://install.zerotier.com/' | gpg); then echo "$z" | sudo bash; fi
```
Setelah paste dan klik enter maka otomatis aplikasi zerotier akan terinstall di server/stb.
---

## 
jika instalasi berhasil maka akan muncul sperti ini
```bash
*** Enabling and starting ZeroTier service...
Synchronizing state of zerotier-one.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable zerotier-one*** Waiting for identity generation...*** Success! You are ZeroTier address [ cae017849e ].>

```

## CEK STATUS

```bash
zerotier-cli info

```
## join network 

```
zerotier-cli join 8056c2e21c620f8a

```
##  a. Enable IP forwarding

```
sudo sysctl -w net.ipv4.ip_forward=1

```

## b. Configure iptables

```
PHY_IFACE=eth0; ZT_IFACE=ztmjfkb3mw

```
## c. Add rules to iptables 

```
sudo iptables -t nat -A POSTROUTING -o $PHY_IFACE -j MASQUERADE
sudo iptables -A FORWARD -i $PHY_IFACE -o $ZT_IFACE -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i $ZT_IFACE -o $PHY_IFACE -j ACCEPT

```
## d. Simpan iptables agar berjalan ketika reboot

```
sudo apt install iptables-persistent
sudo bash -c iptables-save > /etc/iptables/rules.v4

```
LANGSUNG GASS PAK EKO





© 2025 vnetmedia88
