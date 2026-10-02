# Panduan Setup Looker Studio — Dashboard Rate Rujukan FKTP Aceh Tenggara

## File yang disiapkan
- `Data_Rate_Rujukan_FKTP_Aceh_Tenggara_Google_Sheets.xlsx`: workbook bersih dengan sheet `Data_Looker_Studio` dan petunjuk.
- `data_rate_rujukan_fktp_aceh_tenggara.csv`: CSV untuk impor alternatif ke Google Sheets.
- Sumber awal: `Dashboard Rate Rujukan FKTP Kab. Aceh Tenggara.xlsx` — sheet `Rate`.
- Jumlah fasilitas yang diekstrak: **36**. Baris total kabupaten dikeluarkan agar tidak dihitung ganda.

## Tahap A — Siapkan Google Sheets
1. Buka Google Drive dengan akun admin yang dikelola sesuai kebijakan organisasi.
2. Unggah `Data_Rate_Rujukan_FKTP_Aceh_Tenggara_Google_Sheets.xlsx` lalu buka sebagai Google Sheets; atau buat spreadsheet baru lalu impor CSV.
3. Gunakan sheet `Data_Looker_Studio` sebagai sumber data. Jangan mengubah nama header tanpa memperbarui field di Looker Studio.
4. Periksa angka dan jumlah fasilitas terhadap Excel sumber sebelum dibagikan.

## Tahap B — Hubungkan Looker Studio
1. Buka https://lookerstudio.google.com/
2. Pilih **Buat → Sumber data → Google Sheets**.
3. Pilih spreadsheet dan worksheet `Data_Looker_Studio`.
4. Pastikan `FASKES`, `Jenis_FKTP`, dan `Status_September` bertipe teks; kolom jumlah, target, capaian, dan persentase bertipe angka.
5. Buat laporan dan tambahkan komponen berikut:
   - Scorecard: jumlah fasilitas.
   - Scorecard: jumlah fasilitas `Di atas target`.
   - Scorecard: jumlah fasilitas `Dalam target`.
   - Scorecard: total `Rujukan_September`.
   - Bar chart: `FASKES` sebagai dimensi; `Target_Jumlah_Rujukan_Bulanan` dan `Rujukan_September` sebagai metrik.
   - Bar/pie chart: `Jenis_FKTP` dengan jumlah fasilitas menurut `Status_September`.
   - Tabel: fasilitas, jenis, peserta, target rate, target bulanan, capaian September, capaian vs target, capaian s.d. 1 Oktober, sisa target, status.
   - Filter kontrol: `Jenis_FKTP` dan `FASKES`.
6. Atur warna status melalui conditional formatting: `Di atas target` merah, `Dalam target` hijau, `Belum dapat dinilai` kuning. Status merupakan indikator pemantauan sesuai aturan yang disepakati, bukan penilaian klinis menyeluruh.

## Tahap C — Publikasi tautan bersama
1. Gunakan menu **Bagikan** pada laporan.
2. Atur pembaca sebagai viewer dan aktifkan akses tautan hanya jika kebijakan Google Workspace mengizinkan.
3. Jangan beri izin Editor kepada FKTP.
4. Uji tautan di jendela privat dan ponsel sebelum dibagikan.
5. Tautan tanpa login bukan akses privat. Bagikan hanya data yang telah disetujui pemilik data.

## SOP pembaruan mingguan oleh admin
1. Simpan Excel baru sebagai arsip internal dengan tanggal/periode.
2. Validasi kolom, periode, duplikasi, data kosong, dan jumlah fasilitas.
3. Perbarui isi sheet `Data_Looker_Studio` tanpa mengubah header atau nama worksheet.
4. Periksa beberapa baris dan total KPI pada laporan.
5. Catat tanggal pembaruan terakhir dan beri tahu FKTP jika ada perubahan penting.

## Catatan indikator
- `Status_September = Di atas target` jika capaian September lebih besar daripada target rujukan bulanan.
- `Status_September = Dalam target` jika capaian sama dengan atau di bawah target.
- Data target dan capaian dipertahankan dari sumber; verifikasi apakah target desimal perlu dibulatkan untuk interpretasi operasional.
