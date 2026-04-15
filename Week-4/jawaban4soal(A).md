**Analisis DNS Query - MIT Name Server (NS)**

Pada percobaan nslookup -type=NS mit.edu, terjadi timeout yang kemungkinan disebabkan oleh gangguan jaringan atau pemblokiran paket UDP pada port 53 oleh firewall, sehingga tidak ada data balasan (answers) yang dapat dianalisis.

1. Alamat IP Tujuan Permintaan
   Ke alamat IP manakah pesan dikirimkan? Pesan dikirimkan ke 173.222.144.77
   Apakah ini IP Server DNS Lokal Anda? Ya, pada saat pengambilan data tersebut, IP 173.222.144.77 bertindak sebagai DNS resolver yang mencoba melayani permintaan kamu (meskipun akhirnya timed out)

2. Jenis (Type) dan Isi Jawaban pada Permintaan (Query)
   Jenis (Type): NS (Name Server). Hal ini sesuai dengan perintah yang kamu ketik yaitu -type=NS. Tujuannya adalah mencari server yang bertanggung jawab atas domain mit.edu
   Apakah mengandung "Answers"? Tidak. Seperti paket query pada umumnya, bagian Answers masih kosong (0) karena ini adalah tahap bertanya

3. Pemeriksaan Pesan Balasan (Response)
   Nama server MIT yang diberikan: Karena statusnya "DNS request timed out" dan "Request to UnKnown timed-out", maka tidak ada nama server yang diberikan dalam percobaan ini
   Apakah memberikan alamat IP? Tidak, karena server tidak merespons tepat waktu, sehingga tidak ada informasi nama server (NS) maupun alamat IP pendamping (glue records) yang berhasil diterima

<img width="595" height="275" alt="image" src="https://github.com/user-attachments/assets/a2296db0-6a21-437c-b0a9-6fe79baf3c3b" />
