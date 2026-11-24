Sistem Verifikasi PD IPG — Google Apps Script
Langkah Deployment
1. Create Google Sheet
Buka sheets.google.com → create blank spreadsheet
Copy Sheet ID dari URL (bahagian selepas /d/ dan sebelum /edit)
Namakan "PD_Verifikasi_IPG"
2. Create Google Drive Folder
Buka drive.google.com → create new foldaer "PD_Uploads_IPG"
Copy Folder ID dari URL (bahagian selepas /folders/)
3. Google Apps Script
Dari Google Sheet: Extensions → Apps Script
Delete semua kod default
Copy seluruh isi Code.gs dan paste
Tukar 3 pembolehubah di atas:
SPREADSHEET_ID → ID Google Sheet awak
DRIVE_FOLDER_ID → ID Google Drive folder awak
DEEPSEEK_API_KEY → API key DeepSeek awak (atau kosongkan, isi kemudian)
4. Enable Drive API
Di Apps Script editor: Services (sidebar kiri) → + Add service
Pilih "Drive API" → Add (version v2)
5. Run Setup
Pilih function "setup" → klik Run
Beri permission (Authorization required → Review permissions → Allow)
6. Create HTML Files
Di Apps Script, create 5 HTML files (File → New → HTML):
Dashboard.html
Hantar.html
Senarai.html
Semak.html (tiada doGet route — perlu tambah)
Konfigurasi.html
Setiap HTML file mengandungi UI dengan CSS inline (UI UX Pro Max style).
7. Deploy as Web App
Deploy → New deployment
Type: Web app
Execute as: Me
Who has access: Anyone with Google account (atau Anyone)
Copy URL deployment
8. Akses
Buka URL deployment di browser
Dashboard akan papar stats
Pensyarah hantar dokumen → fail masuk Google Drive, data masuk Google Sheet
PD semak → klik Analisis AI DeepSeek → AI baca fail dari Drive dan isi senarai semak
PD finalize → laporan dijana
Di mana data disimpan
Data	Lokasi
Maklumat submission (kursus, pensyarah, markah)	Google Sheet — tab "Submissions"
Keputusan senarai semak (21/12 item)	Google Sheet — tab "Checklist_Results"
API key DeepSeek	Google Sheet — tab "Konfigurasi"
Fail JST, Soalan, Skema, Rubrik	Google Drive — folder "PD_Uploads_IPG"
Fail LAM-PT-04-01/02/03/04	Google Drive — folder "PD_Uploads_IPG"
Senarai Semak
Fasa Perancangan (21 item)
Exact dari Manual Kerja PD m/s 16-18.
Dokumen: JST, Soalan Tugasan, Skema Pemarkahan, Rubrik.
Fasa Selepas Moderasi (12 item)
Exact dari Manual Kerja PD m/s 19-20.
Dokumen: LAM-PT-04-01, LAM-PT-04-02, LAM-PT-04-03, LAM-PT-04-04.
AI DeepSeek
AI membaca fail dari Google Drive (auto-convert PDF/DOCX ke teks)
AI semak format, kandungan, tarikh, patuhan Manual Kerja
AI isi senarai semak automatik dengan catatan justifikasi
PD review dan finalize
