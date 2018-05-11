# Tugas Workshop ke-1

Deployment stateless aplication menggunakan kubernetes

Stateless Application adalah suatu model aplikasi yang selalu memberikan respon sama terhadap setiap client yang mengakses web ataupun aplikasi tertentu. pada stateless tidak ada penyimpanan ataupun perubahan setiap kita mengakses aplikasi nya.

Langkah pertama adalah membuat image atau pull image di docker hub, jika tidak mempunyai docker bisa membuka https://labs.play-with-docker.com/ dan setelah membuat atau pull image yang diinginkan maka bisa kita push di docker hub kita untuk pull bisa dengan perintah ```docker pull httpd``` untuk memberikan tag bisa dengan ```docker tag httpd zthomaz/httpd:2.4```

![push docker()](https://github.com/zthomaz/tugas-workshop1/blob/master/docker_push.png)

Langkah kedua membuat file deployment yaitu httpd.yml dan setelah itu berikan perintah

```kubectl create -f httpd.yml```

![create httpd()](https://github.com/zthomaz/tugas-workshop1/blob/master/create_httpd.png)

selanjutnya cek apakah sudah berhasil membuat pods, cara mengeceknya dengan menjalankan perintah
```kubectl get pods```

![get pods()](https://github.com/zthomaz/tugas-workshop1/blob/master/get_pods.png)

maka akan terlihat ada 2 pods yang sedang berjalan dan kita akan mencoba menghapus salah satu pods tersebut dengan melakukan perintah
```kubectl delete pods httpd-6b7457d998-z4cth```

![del pods()](https://github.com/zthomaz/tugas-workshop1/blob/master/delete_pods.png)
setelah dihapus kita coba cek lagi apakah pods yang dihapus masih ada atau tidak
```kubectl get pods```

![after del pods()](https://github.com/zthomaz/tugas-workshop1/blob/master/getpods_afterdelete.png)
maka terlihat pods z4cth sudah terhapus

langkah ketiga yaitu membuat file  service.yml dan mengcreate nya
```kubectl create -f service.yml```

![create service()](https://github.com/zthomaz/tugas-workshop1/blob/master/create_service.png)

isetelah itu kita cek servicenya dengan perintah
```kubectl get service```

![get service()](https://github.com/zthomaz/tugas-workshop1/blob/master/get_service.png)
maka terlihat service sudah berjalan di port 30305

selanjutnya kita akan merubah index.html pada httpd tersebut yaitu dengan cara masuk ke bashnya
```kubectl exec -i -t httpd-6b7457d998-szqh6 bash ```

![exec bash()](https://github.com/zthomaz/tugas-workshop1/blob/master/exec_bash.png)
setelah masuk kita update dan install nano karena untuk mengedit index.html membutuhkan nano editor
```apt-get update``` dan ```apt-get install nano```

![install nano()](https://github.com/zthomaz/tugas-workshop1/blob/master/install_nano.png)
setelah itu pindah ke folder htdocs dan edit index.htmlnya
```cd htdocs``` dan ```nano index.html```

![edit htdocs()](https://github.com/zthomaz/tugas-workshop1/blob/master/edit_htdocs.png)
setelah masuk ke editor maka rubah sesuai kebutuhan 

![nano index()](https://github.com/zthomaz/tugas-workshop1/blob/master/nano_index.png)
setelah selesai maka simpan dengan cara ```ctrl+x``` kemudian ```Y``` dan ```enter```
untuk melihat perubahan kita bisa coba jalankan misal di katakoda bisa dengan ```klik +``` atau newtab dan pilih ```view HTTP port 80 on host 1``` maka akan membuka tab baru dan rubah port menjadi ```30305``` dan klik display port maka akan terlihat

![result edit()](https://github.com/zthomaz/tugas-workshop1/blob/master/result_edit.png)

maka akan berubah sesuai dengan apa yang sudah kita rubah tadi tetapi apabila kita hapus dan coba buka kembali data akan hilang karena aplikasi ini bersifat stateless
