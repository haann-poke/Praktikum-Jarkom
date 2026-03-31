**Packet Sniffing Secara Real-Time Menggunakan Wireshark - Praktikum Jarkom Week1**

Berikut adalah langkah-langkah melakukan analisis lalu lintas jaringan menggunakan Wireshark: 

1. **Memilih Interface Jaringan**
   <img width="1920" height="1080" alt="step 1" src="https://github.com/user-attachments/assets/08b77791-7d05-4191-be3a-39b32ab2ee92" />
   Buka Aplikasi Wireshark, lalu klick interface 'Wi-Fi' untuk memulai proses Packet Sniffing
2. **Proses Capturing Secara Real-Time**
   <img width="1920" height="1080" alt="step 2" src="https://github.com/user-attachments/assets/b1ced95e-dfd8-4a6f-9ea5-b3ea992aad75" />
   Berikut merupakan tampilan awal ketika Wireshark ketika kita sudah klick interface 'Wi-Fi', akan terlihat masing masing trafic jaringan yang terhubung pada interface Wifi
   Analisis MOSI :
   1. Frame: Lapisan Physical/Data Link.
   2. Ethernet II: Alamat MAC asal dan tujuan.
   3. Internet Protocol (IPv4/IPv6): Alamat IP asal dan tujuan.
   4. Transmission Control Protocol (TCP/UDP): Port yang digunakan (misalnya port 443 untuk HTTPS).
3. **Pengujian : Mengakses Packet dengan URL**

   Untuk mempermudah analisis, kita akan mencoba menangkap trafik HTTP yang spesifik dengan link berikut : gaia.cs.umass.edu/wireshark-labs/INTRO-wireshark-file1.html
   linknya bisa kita buka pada web browser apapun, dan pastikan menggunakan protocol 'HTTP' bukan 'HTTPS'
   
   <img width="910" height="140" alt="isi" src="https://github.com/user-attachments/assets/77d310cb-dd39-4a8a-8b5c-c7699469ea36" />
4. **Memfilter dan Menganalisis Isi Paket HTTP**

   Setelah sudah mengakses link tersebut di web browser, kembali ke Wireshark dan gunakan fitur 'Display Filter' dengan cara ketik 'HTTP' pada kolam fiturnya
   karena yang kita cari merupakan protocol 'HTTP', lalu cek packet yang '495 HTTP/1.1 200 OK (text/html)' dan kita akan menemukan isi konten html yang sesuai dengan langkah 3

   <img width="1920" height="1080" alt="step 3" src="https://github.com/user-attachments/assets/eb975b48-74c0-4ae4-85f3-340a6a8f8f59" />
