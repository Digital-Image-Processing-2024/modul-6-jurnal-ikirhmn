# Resume Finger Simulation Experiment - NIM


## Data Understanding

_Jelaskan mengenai data yang digunakan dalam project kalian, seperti jumlah data, jumlah kelas, serta bagaimana cara kalian mendapatkan data tersebut._

Dataset yang saya gunakan merupakan kumpulan jari dari semua praktikan pada angkatan 22. Jumlah data tersebut sekitar 2164 data yang terdiri dari beberapa kelas yaitu : finger_1, finger_2, finger_3, finger_4, dan finger_5.

## Data Preparation

### Image Augmentation

_Jelaskan kombinasi teknik augmentasi gambar apa saja yang kalian gunakan, serta berapa gambar yang dihasilkan dari 1 gambar asli._

Kombinasi teknik augmentasi yang akan digunakan adalah rotasi dengan sudut 90, 180, dan 270 derajat. Setiap gambar asli akan menghasilkan tiga gambar baru, sehingga memperkaya dataset dengan variasi yang berbeda dari setiap gambar.

Alasan Penggunaan Teknik Rotasi
1. Variasi Data
   
   Dengan melakukan rotasi, kita dapat menciptakan variasi pada dataset yang dapat membantu model dalam generalisasi dan mengenali pola yang berbeda.
2. Keseragaman Arah
    
   Rotasi gambar dapat membantu dalam mengatasi masalah keseragaman arah pada dataset yang mungkin mempengaruhi performa model.
3. Menghindari Overfitting
   
   Augmentasi data dengan rotasi dapat membantu dalam menghindari overfitting dengan memperkenalkan variasi yang lebih luas pada data latih.

### Preprocessing

_Dari setiap percobaan yang telah kalian lakukan, jelaskan bagaimana cara kalian menemukan preprocessing yang paling tepat. Jelaskan alasan kalian menggunakan teknik tersebut dan berikan alasan mengapa preprocessing diperlukan._

Setelah mengevaluasi hasil dari setiap teknik, saya menemukan bahwa Median Filtering adalah teknik preprocessing yang paling tepat untuk dataset ini. Berikut adalah alasan kami memilih teknik tersebut:
- Pengurangan Noise
  Median filtering secara efektif mengurangi noise pada gambar tanpa mengaburkan detail penting, yang sangat penting untuk gambar jari yang mengandung banyak detail halus.
- Kualitas Visual
  Gambar hasil median filtering memiliki kualitas visual yang lebih baik dengan tepi dan detail yang jelas. Ini penting untuk tugas klasifikasi yang mengandalkan fitur visual yang jelas.
- Distribusi Piksel
  Meskipun histogram dari median filtering tidak setersebar ekualisasi histogram, hasil visual menunjukkan bahwa detail penting tetap terjaga, yang lebih kritis untuk akurasi model klasifikasi.

### Feature Selection

_Jelaskan bagaimana kalian menemukan fitur yang paling tepat untuk digunakan. Jelaskan alasan kalian menggunakan fitur tersebut dan berikan alasan mengapa fitur tersebut diperlukan._

Pada tahap ini, kita akan melakukan ekstraksi fitur menggunakan metode Gray Level Co-occurrence Matrix (GLCM) pada dataset yang telah difilter dengan median filtering. Fitur-fitur yang akan dihitung meliputi Contrast, Dissimilarity, Homogeneity, Energy, Correlation, Entropy, dan ASM. Penghitungan GLCM akan dilakukan pada sudut 0, 45, 90, dan 135 derajat dengan jarak 1-5.

Fitur GLCM seperti Contrast, Dissimilarity, Homogeneity, Energy, Correlation, Entropy, dan ASM penting karena mereka mengungkap detail tekstur citra yang tidak terlihat oleh analisis biasa. Contrast dan Dissimilarity mengukur variasi intensitas, sementara Homogeneity, Energy, dan ASM menunjukkan keseragaman. Correlation menunjukkan hubungan antara piksel, dan Entropy mengukur kerumitan tekstur. Fitur-fitur ini meningkatkan akurasi klasifikasi citra dan membantu dalam berbagai aplikasi seperti deteksi objek.


## Modeling

_Jelaskan bagaimana kalian melakukan hyperparameter tuning pada model tersebut._

Hyperparameter tuning pada model K-Nearest Neighbors (KNN) meningkatkan kinerja klasifikasi dengan menemukan kombinasi parameter optimal, seperti jumlah tetangga (k), jenis jarak, dan metode penimbangan. Teknik ini membantu menghindari overfitting, meningkatkan akurasi, dan memastikan model bekerja baik pada data baru. Validasi silang digunakan untuk memberikan estimasi kinerja yang andal. Proses ini memungkinkan eksplorasi efisien dan sistematis berbagai kombinasi parameter untuk hasil terbaik.

## Evaluation
 
_Jelaskan bagaimana peningkatan performa model dari metrics yang kalian gunakan pada berbagai percobaan yang telah kalian lakukan._



_Catatan:_

- _Tutorial mengenai penggunaan Markdown dapat dibaca [di sini](https://guides.github.com/features/mastering-markdown/)_
- _Kalian dapat melakukan copy untuk file `percobaan_n.ipynb` (ganti `n` dengan nomor percobaan) untuk setiap percobaan yang kalian lakukan._