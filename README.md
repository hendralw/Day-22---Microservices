# Day-22-Microservices

![image](https://user-images.githubusercontent.com/49546149/216828240-8ae31d85-a86c-473e-9a40-e4a96e8e584c.png)


Terdapat 5 service antara lain :
- User service : menggunakan sharing database PostgreSql untuk menyimpan data
- Order service : menggunakan sharing database PostgreSql untuk menyimpan data
- Procurement service : menggunakan sharing database PostgreSql untuk menyimpan data
- Product service : menggunakan database MongoDB karena atribut setiap product bisa berbeda agar tidak terdapat column yang null jika menggunakan database transactional seperti PostgreSql. Sehingga atribute untuk setiap product akan bervariasi sesuai dengan yang dibutuhkan dengan menggunakan database document oriented MongoDB.
- Catalog service : menggunakan database Elastic search agar ketika melakukan pencarian product lebih cepat.


Komunikasi antar service melalui RPC: 
- Procurement service melakukan get data User melalui User service melalui RPC 
- Catalog service melakukan get data Product melalui Product service melalui RPC
- Procurement service melalukan insert data Order melalui Order service melalui RPC

Komunikasi antar service melalui messaging: 
- Order service mengirimkan data ke Kafka Server agar Email service bisa mengirimkan data ke User jika ada proses order. Sehingga product service tidak perlu melakukan komunikasi melalui RPC.
