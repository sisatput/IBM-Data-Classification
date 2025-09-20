
# Capstone – Data Classification & Summarization (IBM Granite)

##Granite NewsSense: Klasifikasi & Ringkasan Berita

**Author:** Satria Putra Dharma Prayudha  
**Program:** Student Development Initiative – Hacktiv8 × IBM SkillsBuild  
**Deadline:** Minggu, 21 September 2025 | 23.59 WIB

## 1) Overview
Proyek ini mengimplementasikan **klasifikasi teks** dan **summarization** menggunakan **IBM Granite** (via Replicate).
Tujuan:
- Klasifikasikan headline/teks berita ke label tetap (*World, Sports, Business, Sci/Tech*).
- Hasilkan ringkasan singkat yang menyoroti poin inti agar mudah dicerna.

Mengapa Granite (prompt-based)? Minim setup/fine-tune, cepat iterasi, cocok untuk label terdefinisi.

## 2) Dataset (Publik)
- **Nama**: AG News Classification Dataset
- **Link**: https://www.kaggle.com/datasets/amananandrai/ag-news-classification-dataset
- **Skema label**: World, Sports, Business, Sci/Tech (4 kelas)
- **Catatan**: Data publik/non-rahasia; patuhi lisensi pada halaman dataset.

## 3) Problem Statement & Objective
- **Masalah**: Kurasi & pemahaman cepat pada arus berita besar.
- **Objective**: (1) Klasifikasikan ke 4 label; (2) Ringkas konten untuk *key points*.

## 4) Analysis Process
1. **EDA**: distribusi kelas (train/test), panjang teks per kelas (boxplot), **TF-IDF top terms per class**.
2. **IBM Granite – Classification**: zero-/few-shot prompting, *temperature* rendah (0.0–0.2), normalisasi output label.
3. **IBM Granite – Summarization**: ringkasan bullet; kontrol `max_tokens`; cek coverage entitas.
4. **(Opsional) Baseline**: model ringan (LogReg/DistilBERT) untuk pembanding.
5. **Evaluasi**: Accuracy, Macro-F1, dan **Confusion Matrix**; cek kualitatif prediksi & ringkasan.
6. **Visualisasi**: simpan plot ke `reports/figures/` untuk dimasukkan ke slide.

## 5) Hasil Utama (Metrics)
- **Accuracy**: **0.900**
- **Macro-F1**: **0.868**
- **Confusion Matrix**: tersedia pada visual evaluasi (notebook/slide).

## 6) Insight & Findings
- **TF-IDF/top terms** memperjelas pembeda antarkelas (vocab sports vs bisnis/tekno).
- **Misclassifications** cenderung pada kelas dengan overlap semantik (Business vs Sci/Tech).
- **Few-shot prompting** meningkatkan konsistensi dibanding zero-shot.

## 7) Conclusion & Recommendation
- **Granite** efektif untuk pipeline cepat klasifikasi + summarization tanpa training berat.
- Produksi: kombinasikan **LLM prompt-based** + **classifier ringan**; gunakan **confidence threshold** & **human-in-the-loop** untuk kasus ambigu; maintain **prompt library** & monitoring kualitas.

## 8) AI Support Explanation (IBM Granite)
- **Classification**: zero-/few-shot; schema label tetap; `temperature=0.0–0.2`; normalisasi label.
- **Summarization**: bullet points; batasi `max_tokens`; cek factual consistency.
- **Quality control**: Accuracy, Macro-F1, Confusion Matrix, dan uji contoh ringkasan.
- **Replicate invite**: https://replicate.com/invites/a8717bfe-2f3d-4a52-88ed-1356231cdf03

## 9) Cara Menjalankan
**Prasyarat:**
```
pip install pandas matplotlib scikit-learn replicate
```
**Token Replicate:**
```python
import os
os.environ["REPLICATE_API_TOKEN"] = "PASTE_YOUR_TOKEN"
```
**Langkah:**
1) Buka notebook di **Colab/WatsonX/LM Studio**.  
2) Jalankan bagian load data + preprocess.  
3) Jalankan **Granite Classification** (zero-/few-shot).  
4) Jalankan **Summarization** (beberapa sampel).  
5) Jalankan **EDA & Evaluation** untuk menghasilkan distribusi kelas, boxplot, TF-IDF, Confusion Matrix, dan analisis ringkasan.  
6) Simpan plot ke `reports/figures/`.

## 10) Prompts (Ringkas)
**Classification – System**
> You are a helpful data analyst. Classify the given text strictly into one of these labels: World, Sports, Business, Sci/Tech. Return only the label.
**Few-shot**: tambahkan 3–5 contoh berlabel sebelum teks target.  
**Summarization – Instruction**
> Summarize the following text into concise bullet points capturing key facts, entities, sentiment cues, and actionable insights.

## 11) Submission (Sesuai Brief)
1) **GitHub Repository**: notebook analytics; **raw dataset** (atau **link** publik); **README** (judul, overview, dataset link, **insight & findings**, **AI support**).  
2) **Link Notebook**: Colab/WatsonX/LM Studio (akses publik).  
3) **File Presentasi (PPT/Slide/PDF)**: judul; **dataset link**; overview & proses; **insight & visual**; **kesimpulan & rekomendasi**; **AI support explanation**.  
4) **Form Submission**: https://bit.ly/SDIProjectData  
5) **Deadline**: Minggu, 21 September 2025 | 23.59 WIB
