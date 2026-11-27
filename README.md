# TEK1314-2026-Kel7-KelasA
<h1>Meet The Team of Kelompok 7</h1>
<ul>
  <li>Mohammad Jamil Satrio Wahyudianto (J0404241015)</li>
  <li>Yosep Geovanie Aritonang (J0404241040)</li>
  <li>Januar Dwi Nugroho (J0404241044)</li>
  <li>Alyssa Daniswara (J0404241099)</li>
</ul>

## 4 Skenario Eksploitasi Terpilih

Berikut ini adalah skenario eksploitasi yang dilakukan menggunakan *platform* Server-IOT Ubuntu 24.04 LTS (Nginx + Supabase/KABITA), Security Onion, dan Kali Linux mengacu pada framework **NIST SP 800-61 Rev. 2**:

| # | Port | Service | Teknik | Tingkat Kesulitan | Tool |
|---|------|---------|--------|-------------------|------|
| 1 | 22, 3223 | OpenSSH (`sshd`) | SSH Brute-Force & Service Enumeration | Mudah | `nmap`, `hydra`, `ssh` |
| 2 | 8080 | Nginx & API KABITA | SQL Injection (SQLi) & API Enumeration | Sedang | `curl`, `sqlmap` |
| 3 | 8080, 443, 3223 & Host Log | Packet Filter & `/var/log/auth.log` | Conceal, Log Tampering & Defense Evasion (`nmap -f`, `truncate`/`rm`) | Sedang | `nmap`, `truncate`, `rm` |
| 4 | 8080 | Nginx & Kernel TCP Stack | Service Disruption / DoS (HTTP Flood & SYN Flood) | Mudah | `ab` (Apache Benchmark), `hping3`, `curl` |
