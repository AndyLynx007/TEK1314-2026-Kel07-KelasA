# IP Plan — Kelompok 7

## Skema Subnet
- **Network**: `192.168.7.0/24`
- **Subnet Mask**: `255.255.255.0`
- **Broadcast**: `192.168.7.255`

## Tabel Alokasi IP

| Hostname              | IP Address     | OS Direncanakan | Peran / Catatan                                   |
|-----------------------|----------------|-------------------|------------------------------------------------------|
| Server-IOT            | 192.168.7.1    |  Ubuntu Server 24.04 LTS |  Deployment Website dan Database              |
| Attacker-1         | 192.168.7.10 | Kali Linux        | Menjalankan Nmap, Metasploit, Burp Suite, Hydra       |
| Attacker-2         | 192.168.7.11 | Kali Linux        | Menjalankan Nmap, Metasploit, Burp Suite, Hydra       |
| Monitoring       | 192.168.7.13 | Security Onion    | IDS/IPS (Suricata/Zeek), traffic mirrored dari switch |
