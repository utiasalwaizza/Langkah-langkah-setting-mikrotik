# Langkah-langkah-setting-mikrotik
1. Langkah pertama adalah, koneksikan port 2 ke modem mikrotik, dan port 3 ke pc Anda. Jalankan winboxnya, kemudian buka tab Neighbors.
Buka aplikasi winbox,      kemudian  isi kolom di winbox seperti ini:
• Connect To = MAC address
• Login = admin
• Password = Silahkan di kosongkan
• Kemudian Klik “Connect”

2. Setelah Anda masuk ke gui nya mikrotik, pertama-tama kita akan mulai dengan merubah nama interface, agar tidak menyulitkan Anda untuk mencari port mana untuk mana.
• Klik tombol Interface maka akan muncul jendela baru, yaitu list interface.
• Double klik pada salah satu interface untuk merubah nama interface tersebut. Kita beri nama  “Ethernet 2” (WAN) ini adalah link ke ISP/Modem
• Kemudian pada “Ethernet 3” (LAN)

3. Selanjutnya memberi IP pada setiap Ethernet, pertama kita beri IP pada interfaces internet (IP yang diberikan oleh ISP), berikut caranya:
• Klik IP > address > “+“
• Address : 192.168.22.2/30
• Network : (Di kosongkan)
• Interface : ether2
• Kemudian klik “OK”

4. Kemudian langkah selanjutnya adalah memberikan IP pada interfaces LAN, isi kolom seperti ini:
• Address : 10.22.22.1/24
• Network : (Di kosongkan saja karena akan mengikuti subnet diatas)
• Interface : ether3
• Kemudian klik OK

5. Langkah selanjutnya membuat route dengan gateway yang diberikan oleh provider ISP, berikut caranya:
• “Klik IP” > “ROUTES” > “+”
• Dst-address : 0.0.0.0/0
• Gateway : 192.168.22.1
• Klik OK

6. Setelah itu, kita akan setting DNS server. DNS ini biasanya sudah diberikan juga bersamaan dengan IP Public, jika Anda memiliki IP DNS ini, silahkan masukkan pada DNS tersebut. Jika tidak memiliki IP DNS tersebut, maka kita akan menggunakan IP DNS Google yaitu:
• 8.8.8.8
• 9.9.9.9
Setelah itu Centang : “Allow-remote-request”, Kemudian klik “OK”

7. Untuk mengecek status koneksi internet. Buka New terminal kemudian cek dengan PING
GOOGLE.COM. Apabila status replay maka router sudah konek internet.

8. Untuk langkah selanjutnya adalah membuat NAT=MASQUERADE yang digunakan agar IP
LOCAL atau area local dapat terhubung internet. Cara seperti dibawah ini:
• Klik IP > FIREWALL > NAT > +
Tab general.
• Chain= srcnat
• Out-interface= ether2(etherwan)
• Tab action.
• Action=Masquerade
• Kemudian klik OK

9. Kemudian setting IP pada laptop anda masuk ke menu network and sharing center
• Klik Local area connection – properties – network protocol version 4
• IP address: 10.22.22.2
• Subnet mask: 255.255.255.0
• Default gateway: 10.22.22.1
• preferred DNS serve : 8.8.8.8
• alternate DNS Server : 9.9.9.9
• Kemudian klik OK

Untuk meyakinkan bahwa inter sudah berjalan di laptop kita, selanjutnya bisa kita buka command prompt caranya klik tampilan windows didalam kotak search programs, ketik CMD – enter  lalu ketik ping google.com jika setatus replay maka menunjukan bahwa laptop kita  sudah terkoneksi internet.
