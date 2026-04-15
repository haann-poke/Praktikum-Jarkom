**Laporan Analisis Protokol DNS dan TCP - Wireshark**

1. Protokol Transport DNS
   Cari pesan permintaan DNS dan balasannya. Apakah pesan tersebut dikirimkan melalui UDP atau TCP?
   Jawaban: Pesan permintaan (Query) dan balasan (Response) DNS dikirimkan melalui protokol UDP (User Datagram Protocol). Hal ini terlihat pada detail paket di Wireshark yang menunjukkan layer User Datagram Protocol sebelu
   layer Domain Name System.

3. Port Tujuan dan Sumber
   Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasannya?
   Jawaban: Port Tujuan pada permintaan DNS adalah 53 (Port standar untuk layanan DNS).
   - Port Sumber pada pesan balasannya adalah 53
   - Komputer pengirim (host) menggunakan port dinamis (misalnya 58783) untuk mengirim permintaan, namun server DNS selalu merespons melalui port 53

4. Alamat IP Tujuan dan Server DNS Lokal
   Pada pesan permintaan DNS, apa alamat IP tujuannya? Apa alamat IP server DNS lokal anda? Apakah kedua alamat IP tersebut sama?
   Jawaban: Alamat IP Tujuan pada paket DNS Query adalah 10.217.7.77
   - Berdasarkan hasil perintah "ipconfig /all", alamat IP server DNS lokal saya adalah 10.217.7.77
   - Kesimpulan: Ya, kedua alamat tersebut sama, karena komputer mengirimkan permintaan DNS langsung ke resolver/DNS server yang terkonfigurasi di sistem
  
4. Jenis Pesan dan Isi Jawaban (Query)
   Periksa pesan permintaan DNS. Apa “jenis” atau ”type” dari pesan tersebut? Apakah pesan permintaan tersebut mengandung ”jawaban” atau ”answers”?

   Jawaban: Jenis (Type): Tipe pesan tersebut adalah Type A (Host Address), yang berarti komputer meminta alamat IPv4 dari sebuah domain.
   Tidak, pesan permintaan tidak mengandung jawaban (Answer RRs: 0). Pesan ini hanya berisi bagian Questions.
   <img width="857" height="693" alt="step1" src="https://github.com/user-attachments/assets/e8b0b766-5510-4ff0-8869-354cf978dcf3" />
   <img width="1910" height="411" alt="step2" src="https://github.com/user-attachments/assets/986749ee-7c47-480d-81bc-ec831a30c21b" />
   
5. Analisis Balasan DNS (Response)
   Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau ”answers” yang terdapat di dalamnya? Apa saja isi yang terkandung dalam setiap jawaban tersebut?
   
  Jawaban: Jumlah Jawaban: Terdapat 4 jawaban (Answers)
  Isi Jawaban: Setiap jawaban berisi nama domain yang dicari, tipe (A), kelas (IN), TTL (Time to Live), dan Alamat IP (Address) dari server tujuan. Contoh alamat IP yang didapat adalah 103.10.124.122, 103.10.124.125,
  103.10.124.124, dan 103.10.124.123

   <img width="1037" height="298" alt="soal6" src="https://github.com/user-attachments/assets/bf910495-4ce4-4a8a-b049-4a86e158e332" />


6. Kesesuaian IP pada TCP SYN
   Perhatikan paket TCP SYN yang selanjutnya dikirimkan oleh host Anda. Apakah alamat IP pada paket tersebut sesuai dengan alamat IP yang tertera pada pesan balasan DNS?

   Jawaban: Ya, alamat IP tujuan pada paket TCP SYN sesuai dengan salah satu alamat IP yang diberikan oleh server DNS pada pesan balasan sebelumnya (misalnya mengarah ke IP 118.98.95.193 untuk HTTP port 80). Ini
   menunjukkan host berhasil menggunakan resolusi nama dari DNS untuk memulai koneksi TCP.

  <img width="1905" height="551" alt="step3" src="https://github.com/user-attachments/assets/2c9b7166-6efb-4e77-a0f9-273ec1a44539" />
   
7. Efisiensi Permintaan DNS pada Halaman Web
   Halaman web yang sebelumnya anda akses memuat beberapa gambar. Apakah host Anda perlu mengirimkan pesan permintaan DNS baru setiap kali ingin mengakses suatu gambar?

   Jawaban: Tidak perlu. Setelah host mendapatkan alamat IP dari permintaan DNS pertama, alamat tersebut akan disimpan dalam DNS Cache lokal untuk sementara waktu. Karena gambar-gambar tersebut berada pada domain yang
   sama, host cukup menggunakan alamat IP yang sudah ada di memori tanpa harus melakukan query DNS berulang kali.
