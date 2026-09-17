# TEK1314-2026-Kel7-KelasA
<h1>Meet The Team of Kelompok 7</h1>
<ul>
  <li>Mohammad Jamil Satrio Wahyudianto (J0404241015)</li>
  <li>Yosep Geovanie Aritonang (J0404241040)</li>
  <li>Januar Dwi Nugroho (J0404241044)</li>
  <li>Alyssa Daniswara (J0404241099)</li>
</ul>

## 7 Skenario Eksploitasi Terpilih

Berikut ini adalah skenario eksploitasi yang akan dilakukan menggunakan <i>platform</i> Metasploitable dan Kali Linux:

| # | Port | Service | Teknik | Tingkat Kesulitan | Tool |
|---|------|---------|--------|--------------------|------|
| 1 | 1524 | Ingreslock  | Root shell langsung tanpa autentikasi (backdoor bawaan) | Sangat mudah | `netcat`/`telnet` |
| 2 | 21   | vsftpd 2.3.4 | Backdoor RCE (CVE-2011-2523) | Sangat mudah | Metasploit |
| 3 | 6667 | UnrealIRCd  | Backdoor RCE | Mudah | Metasploit |
| 4 | 445  | Samba (usermap_script) | RCE (CVE-2007-2447) | Mudah | Metasploit |
| 5 | 5900 | VNC | Weak password (`password`) → remote desktop access | Mudah | `vncviewer` + brute-force |
| 6 | 3306 | MySQL | Default credential (`root` tanpa password) → dump database | Sedang | `mysql` client |
| 7 | 80   | HTTP (DVWA) | SQL Injection / File Upload | Sedang | Burp Suite / manual |
