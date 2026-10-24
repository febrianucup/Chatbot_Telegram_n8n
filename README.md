# Asisten Tutor AI Telegram (n8n Workflow)

Chatbot asisten pembelajaran cerdas untuk Telegram yang ditenagai oleh **n8n**, **DeepSeek AI**, dan **Google Gemini**, berfungsi sebagai mentor bimbingan belajar yang ramah, sabar, dan suportif dalam membimbing siswa memahami konsep soal langkah demi langkah.

---

## Fitur Utama

1. **Karakter & Persona Pendidik**:
   - Membimbing siswa memahami konsep soal secara runtut dan bertahap, bukan sekadar memberikan jawaban instan.
   - Menggunakan sapaan yang konsisten dan ramah sesuai instruksi sistem.

2. **Dukungan Multimodal**:
   - **Pesan Teks**: Menanggapi sapaan, percakapan umum, atau pertanyaan materi pelajaran.
   - **Gambar/Foto**: Menerima dan memproses lampiran foto atau tangkapan layar soal dari siswa.
   - **Dokumen/PDF**: Mengekstrak dan menganalisis teks serta soal dari dokumen PDF yang dikirimkan menggunakan Google Gemini.

3. **Memori & Konteks Percakapan**:
   - Menyimpan riwayat percakapan per pengguna menggunakan n8n Memory Buffer Window yang diidentifikasi berdasarkan ID Telegram chat.

4. **Integrasi Google Sheets**:
   - Melakukan pengecekan data siswa, nomor telepon, dan rekap nilai secara otomatis melalui node dan tool Google Sheets.

---

## Struktur Workflow

- **Telegram Trigger**: Menerima pesan, foto, dan dokumen yang masuk dari bot Telegram.
- **Message Sorter (Switch/If)**: Memilah jenis pesan (teks, gambar, atau dokumen).
- **Google Gemini (Analyze Document)**: Mengekstrak isi teks dan soal dari dokumen PDF.
- **Final Prompt**: Menggabungkan pesan siswa, ID gambar, dan hasil ekstraksi dokumen menjadi *prompt* terstruktur untuk AI Agent.
- **AI Agent & LLM (DeepSeek Chat Model)**: Menghasilkan respons pedagogis yang sesuai dengan instruksi sistem.
- **Simple Memory**: Mengelola memori riwayat percakapan singkat.
- **Google Sheets Tool**: Memungkinkan agen untuk mengakses dan query data siswa/nilai saat dibutuhkan.
- **Error Handler**: Menangani gangguan sistem atau error secara elegan dengan pesan cadangan yang ramah.

---

## Panduan Instalasi & Penggunaan

1. Impor file `Chatbot Telegram.sanitized.json` ke dalam instance **n8n** Anda.
2. Konfigurasikan kredensial yang diperlukan:
   - Token Bot Telegram
   - DeepSeek API
   - Google Gemini (PaLM) API
   - Akun Layanan (Service Account) Google Sheets
3. Sesuaikan parameter ID Spreadsheet dan pengaturan lainnya pada node workflow agar sesuai dengan lingkungan Anda.
4. Aktifkan workflow dan uji coba bot melalui Telegram.
