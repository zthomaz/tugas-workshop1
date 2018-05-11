# Tugas Workshop ke-1

Deployment stateless aplication menggunakan kubernetes

Stateless Application adalah suatu model aplikasi yang selalu memberikan respon sama terhadap setiap client yang mengakses web ataupun aplikasi tertentu. pada stateless tidak ada penyimpanan ataupun perubahan setiap kita mengakses aplikasi nya.

Langkah pertama adalah membuat image atau pull image di docker hub, jika tidak mempunyai docker bisa membuka https://labs.play-with-docker.com/ dan setelah membuat atau pull image yang diinginkan maka bisa kita push di docker hub kita untuk pull bisa dengan perintah ```docker pull httpd``` untuk memberikan tag bisa dengan ```docker tag httpd zthomaz/httpd:2.4```

