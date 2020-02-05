## Modul 1 Sistem Operasi

# Shell Scripting, Cron, dan AWK

## 2. Cron
Cron adalah sebuah service daemon yang memungkinkan user Linux dan Unix untuk menjalankan perintah atau _script_ pada waktu tertentu secara otomatis. Perintah-perintah dan/atau script-script yang dijalankan cron disebut cron jobs.
Syntax crontab :
`crontab [-u user] [-l | -r | -e] [-i]`
Penjelasan :
* `-l` untuk menampilkan isi file crontab
* `-r` untuk menghapus file crontab
* `-e` untuk mengubah atau membuat file crontab jika belum ada
* `-i` untuk memberikan pertanyaan konfirmasi terlebih dahulu sebelum menghapus file crontab
### 2.1 Membuat atau mengubah cron jobs
1. Ketikkan `crontab -e`
2. Ketikkan perintah crontab sesuai aturan parameter crontab
[parameter crontab](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/syntax-crontab.png "parameter crontab")
3. Untuk melihat daftar cron jobs ketikkan `crontab -l`

Contoh perintah yang dijalankan crontab
[contoh crontab](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/contoh-crontab.png "contoh crontab")
Penjelasan :
* setiap jam 00.00 memasukkan hasil `ls /home/tamtama` ke file `/home/tamtama/list_files`
* setiap minggu menjalankan file `script.sh` pada folder `/home/tamtama`

Untuk belajar lebih lanjut perintah-perintah crontab bisa mengakses website [crontab guru](https://crontab.guru/).
[web crontab guru](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/crontab-guru.png "web crontab guru")