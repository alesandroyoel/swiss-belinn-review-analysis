# Hotel Review Topic Modeling & Aspect-Based Sentiment Analysis

Analisis ulasan pelanggan **Hotel Swiss-Belinn Manyar Surabaya** dari Traveloka menggunakan **Topic Modeling (LDA vs BERTopic)** dan **Aspect-Based Sentiment Analysis** berbasis IndoBERT.

> Proyek akhir mata kuliah Metode Data Mining dan Text Mining (MDTT), Departemen Statistika Bisnis, Fakultas Vokasi, Institut Teknologi Sepuluh Nopember (ITS).

## Latar Belakang

Persaingan industri perhotelan di kota besar menuntut manajemen memahami suara pelanggan secara cepat. Ulasan di platform daring bersifat tidak terstruktur sehingga sulit dianalisis secara manual. Proyek ini mengubah 1.000 ulasan menjadi insight yang dapat ditindaklanjuti.

**Pertanyaan yang dijawab:**
1. Topik apa yang paling sering dibicarakan pelanggan?
2. Aspek layanan mana yang perlu ditingkatkan?
3. Metode topic modeling mana yang paling cocok: LDA atau BERTopic?

## Alur Analisis

1. **Data collection**: scraping 1.000 ulasan dari Traveloka (Selenium + BeautifulSoup), dikumpulkan 26 Juni 2025
2. **Preprocessing**: case folding, tokenisasi, stopword removal, dan stemming bahasa Indonesia (Sastrawi)
3. **Exploratory analysis**: distribusi rating, word cloud, bigram dan trigram
4. **Topic modeling**: LDA (8 topik) dan BERTopic
5. **Aspect-based sentiment analysis**: 6 aspek (pelayanan, kebersihan, harga, sarapan/makanan, kamar, fasilitas) menggunakan model `ayameRushia/bert-base-indonesian-1.5G-sentiment-analysis-smsa`
6. **Evaluasi**: coherence score (C_v) untuk membandingkan LDA dan BERTopic

## Hasil Utama

**Distribusi rating:** mayoritas ulasan berada pada rentang rating 9 sampai 10, dengan kategori "Pengalaman Luar Biasa" sebesar 56,5% dan "Pengalaman Baik" 31,2%.

**Skor sentimen per aspek** (skala -1 sampai +1):

| Aspek | Skor |
|---|---|
| Pelayanan | 0,74 |
| Kebersihan | 0,73 |
| Harga | 0,71 |
| Sarapan/Makanan | 0,66 |
| Kamar | 0,56 |
| Fasilitas | 0,29 |

**Perbandingan model topik:**

| Model | Coherence (C_v) |
|---|---|
| LDA | 0,5318 |
| BERTopic | 0,4920 |

**Insight bisnis:**
- Pelayanan staf dan kebersihan kamar adalah kekuatan utama hotel.
- **Fasilitas umum** adalah aspek dengan skor terendah, sehingga menjadi prioritas perbaikan.
- LDA menghasilkan topik yang sedikit lebih koheren pada dataset ini, sedangkan BERTopic tetap relevan sebagai alternatif karena pendekatan berbasis embedding.

## Struktur Repository

```
.
├── notebooks/
│   └── 035_136_PROYEK_AKHIR_MDTT.ipynb  
├── report/
│   └── Topic_Modeling_Alesandro_Farhan.pdf
└── README.md
```

## Tech Stack

Python · Selenium · BeautifulSoup · Pandas · NumPy · Sastrawi · NLTK · scikit-learn · Gensim · BERTopic · Hugging Face Transformers · Matplotlib · Seaborn · WordCloud

## Cara Menjalankan

1. Clone repository ini.
2. Buka notebook di Google Colab atau Jupyter.
3. Jalankan sel instalasi library di bagian awal notebook.
4. Siapkan dataset ulasan (lihat catatan di bawah), lalu jalankan sel secara berurutan.

**Catatan data:** dataset hasil scraping tidak disertakan dalam repository ini. Notebook membaca file `review_swissbelinn_manyar_cleaned.csv` yang dihasilkan dari tahap scraping dan preprocessing. Untuk mereproduksi, jalankan bagian *Scraping Data* di notebook (struktur halaman Traveloka dapat berubah sewaktu-waktu).

## Keterbatasan

- Data hanya berasal dari satu hotel dan satu platform (Traveloka).
- Penentuan aspek menggunakan pencocokan kata kunci, sehingga ulasan dengan kata tidak umum bisa terlewat.
- Dataset sangat condong positif, sehingga ulasan negatif relatif sedikit untuk dianalisis.

## Penulis

- **Alesandro Yoel Deca Putranto**
- **Farhan Muhammad Rizqi** 
