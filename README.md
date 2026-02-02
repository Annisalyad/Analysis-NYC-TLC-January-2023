# Analysis-NYC-TLC-January-2023
Analisis data NYC-TLC bulan januari 2023 untuk meningkatkan profit


## **1. Latar Belakang**

Perkembangan transportasi perkotaan di Kota New York menuntut pengelolaan layanan taksi yang semakin efisien, adaptif, dan berbasis data. Tingginya mobilitas masyarakat, variasi waktu perjalanan, serta perbedaan karakteristik wilayah menyebabkan permintaan layanan taksi tidak merata baik dari sisi waktu, lokasi, maupun jenis perjalanan. Kondisi ini menuntut perusahaan dan vendor taksi untuk mampu mengoptimalkan operasional armada agar tetap kompetitif dan berkelanjutan.

Sebagai regulator dan penyedia data, NYC Taxi and Limousine Commission (NYC-TLC) memiliki peran strategis dalam menyediakan informasi yang dapat dimanfaatkan oleh vendor taksi untuk meningkatkan kinerja operasional dan pendapatan. Data perjalanan taksi yang tercatat oleh NYC-TLC menyimpan potensi besar untuk dianalisis guna memahami pola perjalanan, tren permintaan, distribusi wilayah, serta perilaku pembayaran penumpang.

Namun, dalam praktiknya, banyak vendor taksi masih menghadapi tantangan dalam menentukan waktu operasional optimal, penempatan armada yang tepat, serta strategi peningkatan pendapatan, khususnya terkait metode pembayaran dan jenis perjalanan yang paling menguntungkan. Tanpa analisis data yang komprehensif, pengambilan keputusan sering kali dilakukan secara intuitif dan kurang efisien.


## **2. Rumusan Masalah**

Berdasarkan latar belakang tersebut, maka rumusan masalah dalam analisis ini adalah sebagai berikut:

- Bagaimana pola dan tren perjalanan taksi di Kota New York selama Januari 2023 berdasarkan waktu harian dan mingguan?

- Pada waktu dan jam berapa permintaan perjalanan serta pendapatan taksi mencapai tingkat tertinggi?

- Wilayah mana saja yang menjadi lokasi penjemputan dan pengantaran dengan volume dan pendapatan tertinggi?

- Bagaimana distribusi pendapatan taksi berdasarkan metode pembayaran, kode tarif, dan jenis perjalanan?

- Bagaimana hubungan antara metode pembayaran dengan besaran tip yang diterima pengemudi?

- Insight strategis apa yang dapat diambil dari pola perjalanan dan pendapatan tersebut untuk mendukung pengambilan keputusan operasional vendor taksi?

- Rekomendasi apa yang dapat diberikan kepada vendor taksi agar dapat meningkatkan efisiensi armada dan pendapatan berbasis data NYC-TLC?


## **3. Data**

Untuk menjawab pertanyaan di atas, kita akan menganalisa data catatan perjalanan TLC yang sudah dikumpulkan oleh perusahaan. Dataset dapat diakses [di sini](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page). 


Taksi Hijau: Secara hukum hanya boleh mengambil penumpang di wilayah luar Manhattan (The Bronx, Brooklyn, Queens, Staten Island) dan Manhattan bagian utara (di atas 96th St)

Dataset ini berisi informasi terkait rute perjalanan taksi TLC, ada 20 kolom didalam dataset NYC TLC Trip Record, yaitu:

- VendorID : Id penyedia LPEP 

    1 = Creative Mobile Technologies LLC. 

    2 = VeriFone Inc. 

- Waktu & Durasi:

    - lpep_pickup_datetime : Tanggal & waktu penjemputan
    - lpep_dropoff_datetime : Tanggal & waktu penumpang turun
    - Durasi_perjalanan: lpep_dropoff_datetime - lpep_pickup_datetime

- Lokasi (Taxi Zones):

    - PULocationID : Zona taksi TLC ketika penjemputan
    - DOLocationID : Zona taksi TLC ketika penumpang turun

- Detail Perjalanan:

    - Passenger_count : Jumlah penumpang dalam kendaraan
    - Trip_distance : Jarak tempuh (dalam mill)
    - RateCodeID : Kode tarif akhir perjalanan

        1 = Tarif standar   --> $3.00

        2 = Bandara John F. Kennedy (JFK)  --> $70.00

        3 = Bandara Newark (EWR) --> $20.00

        4 = Tarif luar kota Nassau / Westchester --> dua kali lipat tarif standar

        5 = Tarif negosiasi

        6 = Tarif perjalanan kelompok

    - Store_and_fwd_flag : Menunjukkan apakah catatan perjalanan disimpan dalam memori kendaraan sebelum dikirim ke vendor

        Y = Tidak disimpan dan teruskan

        N = Simpan dan teruskan

    - Payment_type : Kode yang menunjukkan jenis pembayaran yang di lakukan oleh penumpang

        1 = Kartu Kredit

        2 = Tunai

        3 = Gratis

        4 = Dispute

        5 = Tidak diketahui
      
        6 = Perjalanan dibatalkan

    - Trip_type : Kode yang menunjukkan jenis perjalanan

        1 = Street-hail

        2 = Dispatch

- Rincian Biaya:

    - Total_amount : Total biaya yang dibayar penumpang, selain tip tunai
    - Fare_amount : Tarif dasar perjalanan berdasarkan waktu/jarak (belum termasuk biaya tambahan)

        $0.50 = Waktu jam sibuk

        $1 = Waktu malam hari

    - MTA_tax : $ 0.50 Pajak otomatis yang dikenakan perpejalanan
    - Improvement_surcharge : $0.30 Biaya tambahan saat menurunkan penumpang diwaktu hujan, peraturan dimutai ditetapkan pada tahun 2015
    - Tip_amount : Jumlah tip yang tercatat saat menggunakan kartu kredit, tip tunai tidak termasuk
    - Tolls_amount : Jumlah total biaya tol yang digunakan dalam perjalanan
    - extra : Biaya tambahan lainnya, seperti jam sibuk atau tengah malam

        $5.00 untuk jam sibuk (jam 16.00 - 20.00 pada hari kerja, tidak termasuk libur nasional)

    - congestion_surcharge : 
        - biaya tambahan karena kemacetan, yang dimulai/berakhir/melewati Manhattan diselatan jalan ke-96

            taksi kuning : $2.50

            taksi hijau : $2.75 / FWV

            semua perjalanan berbagi tumpangan : $0.75
    - ehail_fee : Biaya pemesanan
Oleh karena itu, diperlukan suatu analisis berbasis data perjalanan taksi NYC-TLC untuk mengidentifikasi pola waktu, lokasi, dan pendapatan, serta menyusun rekomendasi strategis yang dapat digunakan oleh vendor taksi dalam mengoptimalkan operasional armada dan meningkatkan pendapatan.
