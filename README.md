# Voice LMS Automation System

Sistem internal untuk mengotomatisasi produksi materi LMS dari file PowerPoint dan PDF. Dibangun selama program magang sebagai solusi end-to-end yang menggabungkan AI generatif, text-to-speech, dan workflow orkestrasi.

---

## Latar Belakang

Proses produksi materi Modul LMS secara manual membutuhkan waktu yang signifikan, mulai dari menulis narasi per slide, merekam audio voice-over, hingga membuat soal kuis. Sistem ini hadir untuk mengotomatisasi seluruh proses tersebut sehingga tim Center of Expertise dapat fokus pada kualitas materi, bukan proses teknis yang berulang.

---

## Gambaran Fitur

### 🎙️ Workflow 1 — PPT to Voice

#### Halaman Upload Voice-Over
Pengguna mengunggah file `.pptx` dan memilih voice yang akan digunakan untuk narasi.

<!-- IMG: screenshot halaman upload voice-over (form upload + pilihan voice) -->
<img width="1000" height="975" alt="image" src="https://github.com/user-attachments/assets/bb7141fe-5f1c-4e12-9de1-f15af79546d5" />


---

#### Daftar Job Voice-Over
Setelah upload, job masuk ke daftar dengan status real-time yang diperbarui otomatis.

<!-- IMG: screenshot halaman daftar job voice-over (tabel job dengan status badge) -->
<img width="1362" height="782" alt="image" src="https://github.com/user-attachments/assets/387b93eb-5e30-4f79-8fe1-e420fb91bf0d" />


---

#### Detail Job & Download
Pengguna dapat memantau progress setiap job dan mengunduh hasilnya setelah selesai.

<!-- IMG: screenshot halaman detail job voice-over (status, log, tombol download PPT & ZIP) -->
<img width="1272" height="976" alt="image" src="https://github.com/user-attachments/assets/ef0a2f83-61ca-4536-91f2-b9c01ba995e8" />

---

### 📝 Workflow 2 — PPT/PDF to Quiz

#### Halaman Upload Quiz
Pengguna mengunggah file materi dan mengonfigurasi parameter kuis: level, tipe soal, dan format jawaban.

<!-- IMG: screenshot halaman upload quiz (form upload + parameter level/tipe/format) -->
<img width="1346" height="827" alt="image" src="https://github.com/user-attachments/assets/e2eee6e6-2312-4191-8298-7bbaca8dda4c" />


---

#### Daftar Job Quiz
Semua quiz job ditampilkan dengan status, nama file, dan konfigurasi yang digunakan.

<!-- IMG: screenshot halaman daftar job quiz (tabel dengan kolom status, nama file, level, tipe) -->
<img width="1290" height="727" alt="image" src="https://github.com/user-attachments/assets/0d414806-cd37-4bd0-b997-eb97dc32484d" />


---

#### Review Soal Per Butir
Setelah soal selesai digenerate, pengguna dapat mereview setiap soal satu per satu — mengedit teks, pilihan jawaban, jawaban benar, dan penjelasan.

<!-- IMG: screenshot halaman review soal (card soal dengan textarea question, options, correct answer, explanation) -->
<img width="1310" height="777" alt="image" src="https://github.com/user-attachments/assets/164024f3-be7b-42fb-a1f6-f01ca7dddb9d" />


---

#### Regenerate Soal dengan Feedback
Jika soal kurang tepat, pengguna dapat meminta regenerasi ulang dengan memberikan feedback spesifik ke AI.

<!-- IMG: screenshot tombol regenerate + field feedback + status "regenerating" pada soal -->
<img width="1310" height="777" alt="image" src="https://github.com/user-attachments/assets/3d3a8ce5-65f2-429f-8e29-1ccc6f842210" />


---

#### Finalisasi & Download Hasil
Setelah semua soal disetujui, pengguna memfinalisasi dan mengunduh hasilnya dalam format Word, PDF, atau TXT.

<!-- IMG: screenshot tombol "Finalize & Generate PDF" + tombol download PDF, TXT yang muncul setelah completed -->
<img width="1357" height="427" alt="image" src="https://github.com/user-attachments/assets/50a6f6aa-8e29-4dca-809a-17844bd05647" />


---

### 🔊 Fitur 3 — Text to Speech

#### Halaman Generate TTS
Pengguna mengetik atau menempelkan teks bebas (maksimal 5.000 karakter), memilih engine TTS dan voice style, lalu klik Generate Voice untuk menghasilkan audio MP3.

Engine yang tersedia:
- **ElevenLabs via Kie.ai** — kualitas premium, model `text-to-dialogue-v3`
- **ElevenLabs Direct** — koneksi langsung ke ElevenLabs API
- **Gemini 3.1 Flash TTS** — pilihan voice laki-laki dan perempuan
- **Edge TTS** — alternatif ringan berbasis Microsoft Edge

<!-- IMG: screenshot halaman Text to Speech (textarea input teks + panel Voice Settings dengan pilihan engine dan voice) -->
<img width="1365" height="727" alt="image" src="https://github.com/user-attachments/assets/cc88471d-651a-482a-9c84-4aeeae0a1ba7" />


---

#### Hasil Audio & Download
Setelah selesai, audio langsung bisa diputar di halaman yang sama via audio player bawaan browser, atau diunduh sebagai file MP3.

<!-- IMG: screenshot hasil generate TTS (audio player muncul + tombol Download MP3 + status "completed") -->
<img width="1326" height="777" alt="image" src="https://github.com/user-attachments/assets/21732f3d-4aaa-44b8-9c18-d12229b6f995" />

---

#### Riwayat TTS Jobs
Semua job TTS tersimpan di halaman TTS Jobs — menampilkan teks, voice, engine, durasi, status, dan tombol download per job.

<!-- IMG: screenshot halaman TTS Jobs (daftar job dengan teks preview, badge status, tombol Download MP3) -->
<img width="1282" height="751" alt="image" src="https://github.com/user-attachments/assets/dcf4ff84-4d29-4b0c-9509-e47614e6f625" />


---

### 📊 Fitur 4 — LMS Analytics Dashboard

#### Dashboard Monitoring
Dashboard monitoring terhubung langsung ke database LMS internal, menampilkan data partisipasi dan capaian pembelajaran seluruh karyawan secara real-time.

KPI utama yang ditampilkan:
- **Total Employee** aktif
- **Complete / Not Complete by Modul**
- **Avg. Pre Test & Post Test**

---

#### Visualisasi per Business Unit & Job Level
Grafik batang grouped untuk membandingkan jumlah karyawan total, yang complete, dan yang belum complete — dikelompokkan per Business Unit dan Job Level.

---

#### Filter & Tabel Detail
Data dapat difilter berdasarkan Business Unit, Departemen, Course, Employee ID, Nama, dan Kategori Completion. Tabel detail menampilkan data per employee per course lengkap dengan nilai Pre Test, Post Test, target modul, dan persentase modul.

---

## Arsitektur Sistem

```
Frontend (React + Tailwind)
         │
         ▼
FastAPI Backend
         │
         ├── PostgreSQL       → penyimpanan job, soal, log
         ├── Cloudflare R2    → penyimpanan file input & output
         ├── Celery + Redis   → async worker untuk embed & quiz tasks
         └── n8n              → orkestrasi AI workflow
                  │
                  ├── Kie.ai (Gemini)     → narasi & soal kuis
                  └── Kie.ai (ElevenLabs) → audio TTS voice-over
```

Seluruh proses berjalan secara **asynchronous** dengan status tracking real-time di frontend (polling setiap 3–5 detik).

---

## Tech Stack

| Layer | Teknologi |
|---|---|
| Frontend | React 19, Tailwind CSS 4, Axios, React Router 7 |
| Backend | FastAPI, SQLAlchemy, Alembic, Python 3 |
| Database | PostgreSQL 15 |
| Queue | Celery, Redis 7 |
| AI Orchestration | n8n 1.91.3 |
| AI Model | Gemini via Kie.ai (chat completions & native API) |
| TTS | ElevenLabs via Kie.ai Market (`text-to-dialogue-v3`) |
| Storage | Cloudflare R2 |
| Infrastructure | Docker Compose |
| Document Export | python-docx, WeasyPrint + Jinja2 |

---

## Struktur Project

```
voice-lms-automation/
├── backend/
│   ├── app/
│   │   ├── api/v1/endpoints/   # upload, jobs, quiz, webhooks
│   │   ├── db/models/          # job, quiz models
│   │   ├── services/           # TTS, PPT engine, storage, n8n client
│   │   └── workers/            # Celery tasks
│   └── alembic/                # database migrations
├── frontend/
│   └── src/
│       ├── pages/              # Upload, JobList, JobDetail, Quiz pages
│       ├── components/         # Layout, StatusBadge
│       └── services/           # API client
├── n8n/
│   └── workflows/
│       ├── ppt-to-voice.json
│       └── ppt-to-questions.json                
└── docker-compose.yml
```

---

## Alur Kerja

### Voice-Over
```
Upload PPT → Ekstrak teks → Kirim ke n8n → Gemini generate narasi
→ ElevenLabs generate audio → Upload ke R2 → Validasi audio
→ Celery embed audio ke PPT → Download hasil
```

### Quiz Generation
```
Upload PPT/PDF → Ekstrak & chunk teks → Kirim ke n8n
→ Gemini generate 10 soal → Review per butir (approve/regenerate)
→ Finalisasi → Export DOCX + PDF + TXT → Download
```

---

## Konfigurasi Parameter Quiz

| Parameter | Pilihan |
|---|---|
| **Level** | `umum`, `manajerial` |
| **Tipe Soal** | `process`, `analytical`, `case_study`, `scenario`, `mixed` |
| **Format** | `multiple_choice`, `true_false` |

Level **manajerial** secara otomatis menerapkan aturan penulisan soal yang berfokus pada dilema strategis, bukan instruksi kerja teknis.

---

## Status Lifecycle

### Voice-Over Job
`processing` → `waiting_embed` → `validating` → `embedding` → `completed` / `failed`

### Quiz Job
`pending` → `extracting` → `generating` → `review_ready` → `finalizing` → `completed` / `failed`

---

## Noted

- Proyek ini dikembangkan selama program **magang** sebagai solusi internal
- Model LLM yang digunakan dapat diganti melalui konfigurasi di `n8n/workflows/ppt-to-questions.json` tanpa mengubah kode backend
- Sistem mendukung berbagai endpoint Kie.ai: Chat Completions, Claude Messages API, Gemini Native API, dan OpenAI Responses API
- Prompt generasi soal dirancang **AI-resistant** untuk menghasilkan soal yang menuntut pemahaman mendalam, bukan sekadar hafalan
