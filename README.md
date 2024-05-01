1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

> Unary RPC, sesuai dengan nanmnya, hanya mengirim satu permintaan dari klien ke server dan menerima satu respon dari server ke klien. Unary RPC cocok digunakan ketika klien hanya perlu mengirimkan satu permintaan dan menerima satu respon, tanpa perlu interaksi lebih lanjut dengan server.

> Server streaming RPC, klien mengirimkan satu permintaan ke server dan menerima serangkaian respon dari server. Sesuai namanya, sesuai untuk kasus di mana klien perlu menerima data dalam bentuk stream dari server, seperti streamaing video

> Bi-directional streaming RPC, klien dan server saling berinteraksi dengan mengirimkan serangkaian pesan dalam bentuk stream. Speerti server streaming RPC, tetapi client dan server sama-sama memberikan data berulang kali.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

> Authentication: Memastikan klien yang terhubung ke layanan adalah klien yang sah dengan menggunakan mekanisme otentikasi yang sesuai, seperti token JWT atau sertifikat SSL.

> Authorization: Memastikan bahwa klien yang terotentikasi memiliki izin yang sesuai untuk mengakses layanan tertentu.

> Data Encryption: Memastikan bahwa data terenkripsi dengan baik. Data tersebut adalah data yang dikirim antara klien dan server untuk melindungi kerahasiaan dan integritas data.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?

> Concurrent Access: Memastikan bahwa akses ke data yang dibagikan antara klien dan server diatur dengan benar untuk menghindari racing conditions ataupaun data konflik.

> Managing Connections: Memastikan bahwa koneksi antara klien dan server dikelola dengan baik.  Seperti pengelolaan skenario seperti connection interruptions dan reconnects.

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?

> Advantages: ReceiverStream memiliki fleksibilitas yang baik dalam mengelola stream data. ReceiverStream dapat mengirim berbagai jenis data melalui stream.

> Disadvantages: ReceiverStream memiliki kompleksitas yang tinggi, hal ini dikarenakan adanya aspek asynchronous programming yang harus dikelola dengan baik


5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?

> Modularization: Memisahkan kode ke dalam modul-modul yang terpisah berdasarkan fungsionalitasnya, sehingga menjadi maintanable.

> Reusability: Menggunakan trait dan generics untuk memungkinkan kode yang dapat digunakan kembali di berbagai bagian dari aplikasi

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?

> Error Handling: Menangani error yang mungkin terjadi selama proses pembayaran, seperti transaksi gagal, pembayaran ganda, validasi jumlah, dll

> Integration: Mengintegrasikan dengan sistem pembayaran pihak ketiga atau layanan lain yang diperlukan untuk menyelesaikan proses pembayaran

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?

> Interoperability: gRPC menggunakan Protocol Buffers sebagai format pesan default, yang memungkinkan komunikasi dengan menggunakan teknologi atau platform lain.

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?

> Kelebihan HTTP/2: Kinerja yang lebih baik, multiplexing yang efisien, dan dukungan bawaan untuk streaming membuatnya lebih cocok untuk aplikasi real-time.

> Kekurangan HTTP/2: Kompleksitas implementasi yang lebih tinggi dan ketergantungan pada dukungan server.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?

> REST API menggunakan model request-response, di mana klien mengirim permintaan ke server dan server merespons dengan data. gRPC, di sisi lain, mendukung streaming data dalam kedua arah, yang memungkinkan komunikasi real-time dan responsif.

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?

> Schema-based approach of gRPC memungkinkan definisi pesan yang ketat dan validasi otomatis, yang dapat meningkatkan keamanan dan keandalan aplikasi.