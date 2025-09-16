# 📄 README: Analisis Sentimen Berita IKN menggunakan IndoBERT dan TF-IDF

## 📌 Judul

**Analisis Sentimen Berita dan Opini terhadap Pemindahan Ibu Kota Nusantara (IKN) melalui Web Scraping pada Media Online**

## 👥 Anggota Kelompok

* Muhammad Alarik Daviarsyah (5026221015)
* Dewi Maharani (5026221046)
* Andika Insan Patria (5026221211)

## 🏢 Institusi

Departemen Sistem Informasi, Fakultas Teknologi Elektro dan Informatika Cerdas (FTEIC), Institut Teknologi Sepuluh Nopember (ITS), 2025

---

## ✨ Abstrak

Penelitian ini mengevaluasi sentimen publik terhadap proyek pemindahan IKN dari Jakarta ke Kalimantan Timur melalui web scraping dan NLP. Model IndoBERT yang telah di-fine-tune digunakan sebagai model utama dan dibandingkan dengan pendekatan tradisional TF-IDF + SVM dan Logistic Regression. Hasil menunjukkan bahwa IndoBERT memberikan performa klasifikasi sentimen tertinggi, terutama dalam menangkap konteks positif dan negatif.

---

## 📚 Struktur Laporan

### 1. Pendahuluan

* Menjelaskan konteks digitalisasi opini publik.
* Menyoroti pentingnya analisis media dalam isu strategis seperti IKN.
* Menetapkan tujuan: memahami persepsi publik melalui sentimen dalam berita daring.

### 2. Tinjauan Pustaka

* Akuisisi Data: Teknik manual dan otomatis (BeautifulSoup, Google Dorking).
* Preprocessing: Tokenisasi, stopwords, stemming, lemmatization.
* Analisis Sentimen: Pendekatan berbasis leksikon dan pembelajaran mesin.
* TF-IDF: Bobot kata penting.
* POS Tagging dan NER: Struktur sintaksis dan pengenalan entitas.
* Transformer dan BERT: Keunggulan arsitektur dan IndoBERT untuk Bahasa Indonesia.

### 3. Akuisisi Data

* Teknik Google Dorking untuk pencarian artikel terkait IKN.
* Scraping menggunakan BeautifulSoup.
* Labeling manual untuk sentimen (positif, netral, negatif).

### 4. Data Preprocessing

* Cleaning konten artikel (emoji, tanda baca, dll).
* Tokenisasi dan penghapusan stopwords.
* Stemming & Lemmatization.
* Filtering kata umum dan langka.
* Augmentasi data (synonym replacement, back translation, dll) untuk penyeimbangan kelas.

### 5. Definisi Dataset

* Dataset terdiri dari: judul, penerbit, tanggal, konten, label sentimen.
* Versi setelah preprocessing disertai fitur: cleaned\_content, content\_without\_stopwords, stemming, lemmatized, wordcount, dll.

### 6. Analisis Data

#### 6.1 Analisis Sentimen

* Mayoritas artikel bersifat netral.
* WordCloud dan distribusi kata pada artikel positif dan negatif memberikan insight naratif yang berbeda.

![WordCloud Sentimen Positif vs Negatif](image/worcloudposnegikn.png)

* Tren pemberitaan meningkat pada bulan tertentu seperti Agustus 2019, Januari 2022, April 2023, dll.

#### 6.2 Analisis TF-IDF

* Mengidentifikasi kata-kata penting per dokumen.
* TF-IDF dominan: "IKN", "bangun", "kota", dst.
* TF-IDF per sentimen:

  * Positif: jokowi, digital, kerja.
  * Negatif: masyarakat adat, tanah, gusur.
* Wordcloud keseluruhan konten terfilter dan 100 kata dengan frekuensi tertinggi divisualisasikan sebagai berikut:

![WordCloud + Histogram TF-IDF](image/wordcloudikntopfrequent.png)

#### 6.3 Analisis POS dan NER

* POS menunjukkan dominasi NOUN dan VERB.
* NER mengenali entitas penting: PER (orang), ORG (organisasi), GPE (lokasi), DAT (tanggal), LAW (undang-undang).
* Visualisasi entitas hasil Named Entity Recognition:

![Contoh Highlight Named Entity (NER)](image/bowikn.png)

* Distribusi label entitas berdasarkan frekuensi kemunculan:

![Distribusi Label Entitas NER](image/nerikn.png)

#### 6.4 Perbandingan Model Sentimen

* IndoBERT outperform TF-IDF+SVM dan Logistic Regression.

* Accuracy IndoBERT: \~82–83%

* F1-Score Positif: 0.87, Negatif: 0.83, Netral: 0.75

* Confusion Matrix TF-IDF + SVM:

![Confusion Matrix - TF-IDF + SVM](image/confmatrixikn.png)

* Distribusi prediksi per model dibandingkan dengan label asli:

![Distribusi Label vs Prediksi per Model](image/grafiklabellingikn.png)

### 7. Kesimpulan

* IndoBERT mampu menangkap konteks sentimen lebih baik.
* Sentimen publik terhadap IKN cenderung netral secara umum, dengan polaritas muncul pada isu-isu sosial dan ekonomi.
* Insight ini dapat dimanfaatkan oleh pemerintah dan media untuk mengelola komunikasi publik secara lebih responsif.

---

## 🛠️ Tools dan Teknologi

* Bahasa Pemrograman: Python
* Library: BeautifulSoup, scikit-learn, HuggingFace Transformers, PyTorch, PySastrawi, NLTK, spaCy
* Model: IndoBERT-base-p1, Logistic Regression, SVM

---

## 📈 Evaluasi Akhir Model

| Model           | Accuracy | F1 (Positif) | F1 (Negatif) | F1 (Netral) |
| --------------- | -------- | ------------ | ------------ | ----------- |
| **IndoBERT**    | 82%      | 0.87         | 0.83         | 0.75        |
| TF-IDF + SVM    | 78%      | 0.88         | 0.79         | 0.67        |
| TF-IDF + LogReg | 76%      | 0.74         | 0.78         | 0.69        |


---

## 📌 Referensi

* Devlin et al. (2019). BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.
* Jurafsky & Martin (2020). Speech and Language Processing.
* Cambria et al. (2013). New Avenues in Opinion Mining and Sentiment Analysis.
* Kowsari et al. (2019). Text Classification Algorithms.
