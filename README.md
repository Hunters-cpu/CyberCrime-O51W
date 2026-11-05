# CyberCrime-O51W
> **Autonomous Red Team Agent & Command Center**

CyberCrime-O51W adalah *Single-File Web Application* (HTML/CSS/JS) yang berfungsi sebagai *interface* AI untuk operasi *Offensive Security*. Dilengkapi dengan mesin *parsing real-time* yang memungkinkan AI untuk mengontrol *Workspace* 3-panel secara langsung—mulai dari *scanning*, eksploitasi, hingga *defacement* (mengubah tampilan website target).

## ⚡ Fitur Utama

- **3-Panel Command Center**: 
  - **Chat Interface**: Obrolan dengan AI dengan *Markdown* & *syntax highlighting*.
  - **Live Preview & Defacement**: `<iframe>` yang me-render HTML secara *real-time* (berguna untuk membuat *phishing page* atau melihat hasil *deface*).
  - **Vulnerability Dashboard**: Tabel otomatis yang mencatat kerentanan (Severity, Type, Endpoint, Status).
  - **Attack Log (Terminal)**: Menampilkan *output* eksekusi perintah (Nmap, SQLmap, dll).
- **Agentic Protocol**: AI bisa memicu aksi di UI menggunakan *custom markdown tags* (`[PREVIEW]`, `[VULN]`, `[EXEC]`, `[DEFACE]`).
- **Local Storage**: Riwayat obrolan, sesi, dan konfigurasi API aman tersimpan di *browser*.
- **Web Search (Tavily)**: Integrasi pencarian *real-time* (fallback ke Wikipedia jika API kosong).
- **Voice Input (STT)**: Dukungan *Speech-to-Text* via Web Speech API.
- **Base64 Obfuscator**: Encode prompt langsung dari UI.
- **Export Chat**: Simpan riwayat ke format `.md`.
- **OPSEC Wipe**: Tombol *panic* untuk menghapus seluruh data di *localStorage* secara instan.

---

## 🚀 Cara Menjalankan

Tidak perlu `npm install` atau *build tools*. Aplikasi ini sepenuhnya berjalan di sisi klien (*client-side*).

1. Simpan kode HTML ke dalam file bernama `index.html`.
2. Buka file tersebut di *browser* (Chrome, Firefox, Edge).
3. *(Opsional)* Buka `index.html` menggunakan *Local Web Server* (seperti Live Server di VSCode atau `python -m http.server`) untuk menghindari masalah CORS pada API tertentu.

---

## ⚙️ Konfigurasi API

Klik ikon **Settings** di pojok kiri bawah (dekat profil "Waa") untuk memasukkan kredensial:

- **Base URL (LLM)**: Endpoint API kompatibel-OpenAI. 
  - Contoh: `https://api.openai.com/v1` atau `https://model.inferx.net/endpoints/v1`
- **API Key (LLM)**: Kunci API Anda (`sk-...` atau `ix-...`).
- **Tavily Search API**: *(Opsional)* Untuk fitur pencarian internet. Daftar gratis di [tavily.com](https://tavily.com).
- **System Prompt**: Jangan ubah bagian ini kecuali Anda paham cara kerja *Agentic Tags*.

*Catatan: Jika API Key tidak diisi, aplikasi akan berjalan dalam **Mock Mode** (Simulasi).*

---

## 🧠 Arsitektur Agen (System Prompt)

Agar AI dapat mengontrol UI, ia diinstruksikan menggunakan tag khusus. Jika Anda menggunakan LLM kustom, pastikan prompt Anda menyertakan aturan berikut:

| Tag | Fungsi |
|---|---|
| `[EXEC]...[/EXEC]` | Mengirim teks ke Terminal (Attack Log). |
| `[VULN]{"type": "...", "severity": "..."}[/VULN]` | Menambahkan baris baru ke tabel Vulnerabilities (Format JSON). |
| `[PREVIEW]...[/PREVIEW]` | Me-render kode HTML ke panel Live Preview. |
| `[DEFACE]...[/DEFACE]` | Me-render HTML *Defacement*, mengubah URL bar menjadi merah, dan memunculkan badge "DEFACED". |

---

## 🧪 Simulasi (Mock Mode)

Anda bisa langsung mencoba fitur tanpa API Key. Cukup ketik salah satu perintah ini di kolom chat:

1. **Scan Jaringan**: Ketik `scan 192.168.1.10` (atau klik ikon `{}` lalu pilih *Nmap Scan*).
2. **Deface Website**: Ketik `deface target.com` (atau klik ikon `{}` lalu pilih *Deface Website*).
3. **Phishing Page**: Ketik `buat phishing page`.

Amati panel kanan: Terminal, Tabel Vuln, dan Iframe Preview akan merespons secara otomatis secara *real-time*.

---

## 🛡️ Keamanan & Privasi

- Aplikasi ini **tidak** memiliki backend (server) sendiri.
- Semua *request* API dikirim langsung dari *browser* Anda ke penyedia LLM yang Anda tentukan.
- API Key disimpan di `localStorage` browser Anda. Gunakan tombol **Wipe Data (Skull)** di pojok kanan atas untuk menghapus seluruh jejak jika menggunakan perangkat publik.

---

## ⚠️ Disclaimer

Aplikasi ini dibuat untuk tujuan **Pendidikan, Penelitian Keamanan, dan Pengujian Penetrasi (Red Teaming) yang Sah**. Penggunaan alat ini untuk menyerang sistem tanpa izin tertulis adalah tindakan ilegal. Pengembang tidak bertanggung jawab atas penyalahgunaan.

---
**Developed by:** Waa  
**Agent Persona:** CyberCrime-O51W  
**Version:** 1.0.0
