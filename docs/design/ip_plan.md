# IP Plan — Kelompok 7

## Skema Subnet
## INTERNAL
- **Network**: `192.168.7.0/25`
- **Subnet Mask**: `255.255.255.128`
- **Gateway** (Bridge Network): `192.168.7.1`
- **Broadcast**: `192.168.7.127`

## EXTERNAL / ATTACKER
- **Network**: `192.168.7.128/25`
- **Subnet Mask**: `255.255.255.128`
- **Gateway** (Bridge Network): `192.168.7.129`
- **Broadcast**: `192.168.7.255`

## Tabel Alokasi IP

| Hostname              | IP Address     | OS Direncanakan | Peran / Catatan                                   |
|-----------------------|----------------|-------------------|------------------------------------------------------|
| Target Server (Korban)| 192.168.7.30   | Metasploitable 2  | Berisi banyak service rentan siap pakai              |
| Attacker Node         | 192.168.7.15 | Kali Linux        | Menjalankan Nmap, Metasploit, Burp Suite, Hydra       |
| Monitoring Node       | 192.168.7.130 | Security Onion    | IDS/IPS (Suricata/Zeek), traffic mirrored dari switch |

## 7 Skenario Eksploitasi Terpilih (Red Team)

| # | Port | Service | Teknik | Tingkat Kesulitan | Tool |
|---|------|---------|--------|--------------------|------|
| 1 | 1524 | Ingreslock  | Root shell langsung tanpa autentikasi (backdoor bawaan) | Sangat mudah | `netcat`/`telnet` |
| 2 | 21   | vsftpd 2.3.4 | Backdoor RCE (CVE-2011-2523) | Sangat mudah | Metasploit |
| 3 | 6667 | UnrealIRCd  | Backdoor RCE | Mudah | Metasploit |
| 4 | 445  | Samba (usermap_script) | RCE (CVE-2007-2447) | Mudah | Metasploit |
| 5 | 5900 | VNC | Weak password (`password`) → remote desktop access | Mudah | `vncviewer` + brute-force |
| 6 | 3306 | MySQL | Default credential (`root` tanpa password) → dump database | Sedang | `mysql` client |
| 7 | 80   | HTTP (DVWA) | SQL Injection / File Upload | Sedang | Burp Suite / manual |

## Catatan Tim
- Segmen IP `192.168.7.0/24` dipilih agar unik dan tidak bentrok dengan kelompok lain (sesuai Kontrak Kuliah Poin 3a) dan disesuaikan dengan jaringan subnet yang dibangun yaitu 192.168.7.0/25 (Internal) dan 192.168.7.128/25 (External/Attacker).
- Setiap segmen dipisahkan oleh router MikroTik v7.
- Skenario pengujian dilakukan menggunakan 2 / 3 Device terpisah dimana Laptop 1 bertindak sebagai Attacker (Kali Linux), Laptop 2 bertindak sebagai Defender dan Monitoring (Security Onion), Laptop 3 bertindak sebagai Server Target (Metasploitable).
- Semua service target **hanya listen di subnet lab** (`192.168.7.0/25`) — tidak boleh ter-expose ke jaringan kampus/internet.
- Monitoring Node ditempatkan agar dapat menerima *mirrored traffic* (port mirroring/SPAN) dari switch / router yang menghubungkan Attacker Node dan Target Server, sehingga dapat memantau seluruh segmen.
- Urutan demo disarankan mengikuti nomor #1–7 di atas: dimulai dari "quick win" (backdoor RCE), lalu weak credential, ditutup dengan skenario web app yang butuh analisis lebih (SQLi).
