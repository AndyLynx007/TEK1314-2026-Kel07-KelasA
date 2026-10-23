# Hardening Progress

## ✅ Hardening Check Lists

| Categories | Control | Check | Traffic Baseline |
| :--- | :--- | :---: | :--- |
| **Access & Authentication** | <ul><li>SSH Key-based Authentication (Tanpa Password)</li><li>Ubah port SSH ke nomor selain default</li><li>Login Root nonaktif</li><li>Rate limit percobaan login SSH (Fail2Ban)</li></ul> | ✅ | Terlihat sesi koneksi TCP yang stabil pada port SSH baru (3223) dan hanya berasal dari IP Monitoring/Admin. Tidak tercatat adanya lonjakan upaya koneksi gagal dalam log Security Onion. |
| **Service & Attack Surface** | <ul><li>Nonaktifkan port & layanan tak terpakai</li><li>Gunakan firewall dan perbolehkan traffic yang diperlukan saja.</li><li>Update & Upgrade</li><li>Hapus user default DB</li></ul> | ❌ | Aliran traffic jaringan murni hanya mengalir pada port layanan yang di-whitelist (contoh: Port 3223 untuk SSH, 1883 untuk MQTT). Seluruh paket scanning atau traffic yang menuju port lain otomatis di-drop dan tidak memicu balasan. |
| **Data & Application** | <ul><li>Enkripsi kredensial tidak hard-coded</li><li>Logging aktivitas mencurigakan</li><li>Validasi input di endpoint API/MQTT</li></ul> | ❌ | Aktivitas pengiriman request API dan publish topik MQTT berjalan periodik dengan ukuran payload data yang kecil/standar. Log aplikasi bersih dari request HTTP malformasi atau parameter injeksi. |
