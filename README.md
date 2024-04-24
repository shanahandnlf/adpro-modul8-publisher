a. How many data your publlsher program will send to the message broker in one run?  

Dalam kode Rust yang diberikan, fungsi main menginisialisasi sebuah publisher p untuk broker pesan CrosstownBus. Kemudian program mem-publish 5 data dengan metode publish_event. Terdapat 5 data yang dikirimkan oleh publisher program ke message broker dalam satu kali run. Data yang dikirim berupa user id dan nama pengguna sesuai struktur pada UserCreatedEventMessage. 

Kesimpulan: Publisher program akan mengirimkan 5 data ke message broker dalam satu kali run.


b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean? 

URL di atas sama dengan URL yang digunakan pada program subscriber. URL yang sama menunjukkan kedua program terhubung ke message broker yang sama. Publisher mengirimkan pesan ke message broker dan subscriber menerima pesan dari message broker. Publisher dan subscriber terhubung ke message broker dengan URL yang sama, sehingga pesan yang dikirimkan oleh publisher dapat diterima oleh subscriber. Dengan kata lain, publisher dan subscriber dapat berkomunikasi dengan baik karena terhubung ke message broker yang sama.


![alt text](image.png)

![alt text](image-2.png)
![alt text](image-1.png)
Penjelasan: Publisher di run da mengirimkan data ke message broker. Subscriber di run kemudian menerima data yang dikirimkan oleh publisher. Data yang dikirim ini sesuai dengan yang telah di-code pada file main.rs publisher.

![alt text](image-3.png)
Penjelasan: Spike terjadi setelah saya melakukan cargo run pada publisher. Spike terjadi karena publisher mengirimkan data ke message broker. RabbitMQ merespon data tersebut dengan menampilkan spike pada grafik message rates. Spike menunjukkan adanya peningkatan jumlah pesan yang diterima oleh RabbitMQ dari publisher.


![alt text](image-4.png)
Penjelasan: Gambar di atas menunjukkan simulasi slow subscriber. Terlihat terdapat message queue yag mencapai angka 20. Hal ini dapat terjadi karena subscriber membutuhkan waktu yang lama untuk menerima pesan sehingga terjadi penumpukan pesan pada message queue. Jadi, publisher dapat mengirim pesan dengan cepat, tetapi subscriber tidak dapat menerima pesan dengan cepat sehingga terjadi penumpukan pesan pada message queue.


![alt text](image-5.png)
![alt text](image-6.png)
![alt text](image-7.png)
![alt text](image-8.png)
Penjelasan: Jumlah subscriber yang dibuat adalah 3 yang berjalan secara bersamaan. Terlihat disini bahwa penambahan julah subscriber membantu message queue menjadi lebih cepat berkurang. Hal ini karena subscriber dapat menerima pesan lebih cepat sehingga message queue tidak terlalu kewalahan. Subscriber yang berjalan secara bersamaan juga bekerja sama untuk menerima pesan yang masuk sehingga beban kerja tiap subscriber lebih terdistribusi. Untuk improvement dari segi code, menurut saya kodenya sudah cukup baik. Namun, mungkin bisa mengimplementasi concurrency pada subscriber menggunakan threads agar program dapat menghandle pesan-pesan dengan lebih baik