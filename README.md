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