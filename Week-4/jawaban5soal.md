**Analisis DNS dengan nslookup mit.edu**

1. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasan DNS?
   
   Jawaban: Sama dengan standar DNS, yaitu Port 53. Meskipun tidak terlihat langsung di CMD, protokol DNS selalu beroperasi di port ini.
2. Ke alamat IP manakah pesan permintaan DNS dikirimkan? Apakah alamat IP tersebut
   merupakan default alamat IP server DNS lokal Anda?

   - Ke alamat IP manakah pesan dikirimkan? Pesan dikirimkan ke 10.217.7.77.
   - Apakah ini IP Server DNS Lokal Anda? Ya, pada screenshot tertulis Address: 10.217.7.77 tepat di bawah nama server tusbind.ac.id. Ini adalah DNS resolver
  
3. Periksa pesan permintaan DNS. Apa ”jenis” atau ”type” dari pesan tersebut? Apakah pesan
   tersebut mengandung ”jawaban” atau ”answers”?

   - Jenis (Type): Type A (dan juga terlihat adanya record IPv6 atau AAAA karena ada alamat dengan format titik dua).
   - Apakah mengandung "Answers"? Tidak. Permintaan hanya berisi pertanyaan (Query).

4. Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau “answers” yang terdapat di
   dalamnya. Apa saja isi yang terkandung dalam setiap jawaban tersebut?

   - Berapa banyak "Answers"? Terdapat 3 alamat (2 alamat IPv6 dan 1 alamat IPv4).
   - Isi Jawaban: * Nama Alias (CNAME): www.mit.edu diarahkan ke www.mit.edu.edgekey.net dan kemudian ke e9566.dscb.akamaiedge.net.
     - Alamat IPV4 : 23.217.163.122
     - Alamat IPV6 : 2600:1417:3f:b97::255e & 2600:1417:3f:bb3::255e
   Penjelasan : MIT menggunakan layanan CDN (Akamai) untuk mendistribusikan kontennya, itulah sebabnya muncul banyak nama alias dan alamat IP.

<img width="758" height="285" alt="nslookup mit edu" src="https://github.com/user-attachments/assets/f1607a15-81ee-496d-b880-ff2807fbbd9c" />
