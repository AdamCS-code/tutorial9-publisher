Nama: Adam Caldipawell Sembiring Kelas: ADPRO B NPM: 2306227160

a. Berapa banyak data yang akan dikirimkan oleh program publisher Anda ke message broker dalam satu kali berjalan?
Jawaban:
Program publisher akan mengirimkan **lima** buah pesan ke message broker dalam satu kali berjalan. Setiap pesan memiliki struktur `UserCreatedEventMessage` dengan dua field string: `user_id` dan `user_name`. Berikut adalah detail setiap pesan:

1.  `user_id`: "1", `user_name`: "12950004y-Amir"
2.  `user_id`: "2", `user_name`: "12950004y-Budi"
3.  `user_id`: "3", `user_name`: "12950004y-Cica"
4.  `user_id`: "4", `user_name`: "12950004y-Dira"
5.  `user_id`: "5", `user_name`: "12950004y-Emir"

Jadi, total ada lima instance dari struct `UserCreatedEventMessage` yang akan diserialisasi dan dikirim sebagai pesan. Ukuran pasti dari setiap pesan akan bergantung pada panjang string `user_id` dan `user_name` setelah proses serialisasi oleh `borsh`, namun secara konseptual, lima buah data pesan akan dikirimkan.

b. URL dari “amqp://guest:guest@localhost:5672” sama dengan yang ada di program subscriber, apa artinya?
Jawaban:
Kesamaan URL “amqp://guest:guest@localhost:5672” antara program publisher dan subscriber memiliki arti bahwa **kedua program tersebut dikonfigurasi untuk terhubung ke broker AMQP yang sama**.

Berikut adalah rinciannya:

* **`amqp://`**: Keduanya menggunakan protokol AMQP untuk berkomunikasi.
* **`guest:guest`**: Keduanya menggunakan kredensial autentikasi yang sama (nama pengguna "guest" dan kata sandi "guest") untuk terhubung ke broker. Ini berarti keduanya mencoba untuk login ke broker dengan identitas yang sama. **Penting untuk diingat bahwa penggunaan kredensial default seperti ini tidak disarankan untuk lingkungan produksi karena alasan keamanan.**
* **`localhost`**: Keduanya mengarah ke host yang sama, yaitu `localhost`. Ini berarti kedua program diasumsikan terhubung ke broker AMQP yang berjalan di mesin yang sama dengan tempat mereka dijalankan.
* **`5672`**: Keduanya menggunakan port yang sama, yaitu `5672`. Ini adalah port standar untuk komunikasi AMQP, sehingga kedua program mencoba untuk terhubung ke layanan AMQP di port yang sama pada host `localhost`.

Dengan kata lain, publisher mengirimkan pesan ke broker AMQP yang sama tempat subscriber mendengarkan pesan. Ini adalah pola komunikasi yang umum dalam sistem berbasis pesan, di mana satu atau lebih publisher mengirimkan pesan ke broker, dan satu atau lebih subscriber menerima dan memproses pesan-pesan tersebut dari broker. Dalam kasus ini, publisher mengirimkan event `UserCreatedEventMessage` ke broker, dan subscriber yang terhubung ke broker yang sama akan menerima dan memproses event tersebut.

### RABBITMQ SCREEN
![picture](https://ibb.co/jktVLR5T)
