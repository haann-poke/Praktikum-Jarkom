**Analisis Protokol HTTP dengan Wireshark - Praktikum Jarkom Week2**

1. Persiapan Packet Sniffing

   Praktikum ini dilakukan dengan menangkap paket data (packet sniffing) menggunakan Wireshark saat mengakses halaman web dari server gaia.cs.umass.edu.

2. Analisis Kakus

   File HTML-1
   Pada percobaan pertama, dilakukan pengambilan file HTML sederhana.

   URL : http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
   Analisis Paket:
   - Terdeteksi request HTTP GET pada frame 9686
   - Server memberikan respons HTTP/1.1 200 OK
   - Data yang diterima berupa teks: "Congratulations. You've downloaded the file..." yang terlihat jelas pada bagian Line-based text data di Wireshark
   <img width="1052" height="120" alt="html1" src="https://github.com/user-attachments/assets/2f1d9038-c7b7-4772-96ee-8c44eea34848" />
   <img width="1592" height="688" alt="http get " src="https://github.com/user-attachments/assets/1d058518-37c7-4352-914e-41002a6955d8" />

   File HTML-2 (Conditional GET & Caching)
   Percobaan ini bertujuan untuk melihat bagaimana browser menangani cache menggunakan header If-Modified-Since

   URL : http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file2.html
   Hasil Analisis :
   - Pada request pertama, server mengirimkan file lengkap (Status 200 OK)
   - Jika file sudah ada di cache dan belum berubah di server, server dapat mengirimkan kode status 304 Not Modified (jika menggunakan mekanisme conditional GET). Namun, pada gambar http get 2.png, terlihat server tetap memberikan 200 OK karena cache telah dibersihkan atau dipaksa melakukan hard reload
   <img width="942" height="287" alt="html2" src="https://github.com/user-attachments/assets/220ea03e-d069-4ec5-bd3b-db06c543a700" />
   <img width="1796" height="885" alt="http get 2" src="https://github.com/user-attachments/assets/b729f68e-87e4-4e20-bd91-dd52fb1da326" />

   File HTML-3 (File Panjang)

   Menganalisis bagaimana HTTP menangani file yang berisi teks cukup panjang (The Bill of Rights).

   URL : http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
   Hasil Analisis :
   - Karena ukuran file yang cukup besar, data tidak dikirimkan dalam satu paket TCP saja, melainkan dipecah menjadi beberapa segmen TCP sebelum disusun kembali oleh browser menjadi satu halaman utuh.
   <img width="1875" height="808" alt="http 3" src="https://github.com/user-attachments/assets/ae6c106d-6763-4959-9e43-a6af4007bff2" />
   <img width="1775" height="512" alt="http3" src="https://github.com/user-attachments/assets/cf8a8d0d-50fb-4e76-90c3-420a177a416c" />

   File HTML-4 (Dokumen dengan Objek Tertanam)

   Menganalisis pengambilan halaman HTML yang berisi gambar (objek eksternal)

   URL : http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
   Hasil Analisis :
   - Halaman ini memuat dua gambar (Logo Pearson dan Cover Buku). Di Wireshark, ini memicu beberapa request GET: satu untuk file HTML, dan request GET terpisah untuk setiap gambar yang tertanam di dalamnya
   <img width="1401" height="687" alt="http4" src="https://github.com/user-attachments/assets/c4f7642f-aad6-43b8-a355-0983c1b95241" />

   File HTML-5
   Analisis Paket :
   - Terjadi request ke suatu direktori
   - Server memberikan respon HTTP/1.1 301 Moved Permanently
   - Di dalam header respons terdapat field Location, yang memberitahu browser untuk melakukan request ulang ke alamat URL yang baru (biasanya penambahan / atau perubahan dari http ke https)
   <img width="1617" height="838" alt="http5" src="https://github.com/user-attachments/assets/674d5d3d-85ce-4b7a-bb5f-cc0cff9c0d1a" />
   <img width="1918" height="517" alt="httpget5" src="https://github.com/user-attachments/assets/861deb5a-5904-4d42-95af-47fe84f5c44a" />

3. Kesimpulan

   Melalui praktikum ini, dapat disimpulkan bahwa:
   - Protokol HTTP bekerja dengan model Request-Response
   - Status kode 200 OK menandakan permintaan berhasil, sementara 301 menandakan pengalihan (redirection)
   - Browser menggunakan mekanisme Caching untuk menghemat bandwidth, yang dapat diamati melalui header If-Modified-Since
   - Satu halaman web yang kompleks (dengan gambar) memerlukan lebih dari satu pasang Request-Response HTTP
