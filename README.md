## Modul 1 Sistem Operasi 
# Shell Scripting, Cron, dan AWK
## Prasyarat
#
1. Menginstall OS Linux
2. Memahami CLI (_Command Line Interface_)

## Daftar Isi
#
1. [Shell Scripting](#1-shell-scripting)
    - [1.1 Shell](#1-1-shell)
    - [1.2 Pemrograman Shell](#1.2-pemrograman-shell)
    - [1.3 Perintah Dasar Shell](#1.3-perintah-dasar-shell)
    - [1.4 Simple Shell Script](#1.4-simple-shell-script)
    - [1.5 Variabel](#1.5.1-variable)
        - [1.5.1 Special Variable](#1.5.1-special-variable)
    - [1.6 Input Output](#1.6-input-output)
    - [1.7 Quoting](#1.7-quoting)
    - [1.8 Operator Dasar](#1.8-operator-dasar)
        - [1.8.1 Operator Aritmatika](#1.8.1-operator-aritmatika)
        - [1.8.2 Operator Relasional](#1.8.2-operator-relasional)
    - [1.9 Conditional Statement](#1.9-conditional-statement)
        - [1.9.1 If...Else](#1.9.1-if...else)
        - [1.9.2 Case...Esac](#1.9.2-case...esac)
    - [1.10 Loop](#1.10-loop)
        - [1.10.1 While Loop](#1.10.1-while-loop)
        - [1.10.2 For Loop](#1.10.2-for-loop)
        - [1.10.3 Until Loop](#1.10.3-until-loop)
        - [1.10.4 Select Loop](#1.10.4-select-loop)
        - [1.10.5 Nesting Loop](#1.10.5-nesting-loop)
    - [1.11 Function](#1.11-function)
        - [1.11.1 Nested Function](#1.11.1-nested-function)
2. [Cron](#2-cron)
    - [2.1 Membuat atau mengubah cron jobs](#2.1-membuat-atau-mengubah-cron-jobs)
    - [2.2 Referensi](#2.2-referensi)
3. [AWK](#3-awk)
    - [3.1 Menjalankan Program AWK](#3.1-menjalankan-program-awk)
    - [3.2 Special Rules](#3.2-special-rules)
4. [Referensi](#4-referensi)
5. [Latihan](#5-latihan)


# 1. Shell Scripting
## 1.1 Shell
Sistem operasi dibagi menjadi tiga komponen penting, yaitu Kernel, Shell, dan Program Utility.

![Komponen Sistem Operasi](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/component.png)

- __Kernel__ adalah inti dari komputer. Komponen ini memungkinkan terjadinya komunikasi antara software dan hardware. Jika kernel adalah bagian terdalam dari sebuah sistem operasi, maka __shell__ adalah bagian terluarnya.
- __Shell__ adalah program penerjemah perintah yang menjembatani user dengan kernel. Umumnya, shell menyediakan __prompt__ sebagai user interface tempat user menginputkan perintah-perintah yang diinginkan, baik berupa perintah internal maupun eksternal. Setelah menerima input dari user dan menjalankan program/perintah berdasarkan input tersebut, shell akan mengeluarkan output. Shell dapat diakses melalui __Terminal__.
- __Program Utility__ adalah system software yang menjalankan tugas-tugas maintenance. Program utility ini dibuat secara khsus untuk melakukan fungsi tertentu pada suatu area komputasi secara spesifik, seperti memformat harddisk, atau melakukan pengecekan konektifitas jaringan dll.

` Catatan: Coba buka terminal di Linux, maka kamu akan menemukan prompt shell (biasanya $). Disitu, kamu dapat mengetik input berupa perintah, kemudian mengeksekusinya dengan menekan tombol "Enter". Output akan ditampilkan di terminal. `

Ada 2 tipe shell utama di Unix/Linux, yaitu:

1. Bourne Shell - Prompt untuk shell ini adalah $ 
    - Bourne Shell (sh)
    - POSIX Shell (sh)
    - Korn Shell (ksh)
    - Bourne Again SHell (bash)
2. C Shell - Prompt untuk shell ini adalah %
    - C Shell (csh)
    - TENEX/TOPS C Shell (tcsh)
## 1.2 Pemrograman Shell
## 1.3 Perintah Dasar Shell
## 1.4 Simple Shell Script
## 1.5 Variabel
### 1.5.1 Special Variable
## 1.6 Input Output

# 2. Cron
Cron adalah sebuah service daemon yang memungkinkan user Linux dan Unix untuk menjalankan perintah atau _script_ pada waktu tertentu secara otomatis. Perintah-perintah dan/atau script-script yang dijalankan cron disebut cron jobs.
Syntax crontab :
`crontab [-u user] [-l | -r | -e] [-i]`
Penjelasan :
* `-l` untuk menampilkan isi file crontab
* `-r` untuk menghapus file crontab
* `-e` untuk mengubah atau membuat file crontab jika belum ada
* `-i` untuk memberikan pertanyaan konfirmasi terlebih dahulu sebelum menghapus file crontab
## 2.1 Membuat atau mengubah cron jobs
1. Ketikkan `crontab -e`
2. Ketikkan perintah crontab sesuai aturan parameter crontab   
![parameter crontab](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/syntax-crontab.png "parameter crontab")   
3. Untuk melihat daftar cron jobs ketikkan `crontab -l`

Contoh perintah yang dijalankan crontab   
![contoh crontab](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/contoh-crontab.png "contoh crontab")   
Penjelasan :
* setiap jam 00.00 memasukkan hasil `ls /home/tamtama` ke file `/home/tamtama/list_files`
* setiap minggu menjalankan file `script.sh` pada folder `/home/tamtama`

Untuk belajar lebih lanjut perintah-perintah crontab bisa mengakses website [crontab guru](https://crontab.guru/).   
![web crontab guru](https://github.com/afrchmdi/sisop-modul-1/blob/master/gambar/crontab-guru.png "web crontab guru")

## 2.2 Referensi
* [https://www.computerhope.com/unix/ucrontab.htm](https://www.computerhope.com/unix/ucrontab.htm)
* [https://www.codepolitan.com/memahami-perintah-perintah-crontab-paling-lengkap-59f69445130a0](https://www.codepolitan.com/memahami-perintah-perintah-crontab-paling-lengkap-59f69445130a0)

# 3. AWK
__awk__ merupakan sebuah program yang bisa digunakan untuk mengambil catatan/record tertentu dalam sebuah file dan melakukan sebuah/beberapa operasi terhadap catatan/record tersebut.

Fungsi dasar awk adalah memeriksa sebuah file per barisnya (atau satuan teks lain) yang mengandung pola tertentu. Ketika sebuah baris cocok dengan salah satu pola, awk akan melakukan action tertentu pada baris tersebut. awk melanjutkan proses sampai menemui end of file pada file yang menjadi masukan tadi.

FYI: awk versi baru dinamakan gawk, tapi biasanya tetap disebut awk.

Awk adalah bahasa scripting yang digunakan untuk memanipulasi data dan menghasilkan laporan. Bahasa pemrograman perintah awk tidak memerlukan kompilasi, dan memungkinkan pengguna untuk menggunakan variabel, fungsi numerik, fungsi string, dan operator logika. Awk sebagian besar digunakan untuk pemindaian dan pemrosesan pola.

## 3.1 Menjalankan Program AWK
Syntax:
```
awk options 'selection _criteria {action }' input-file > output-file
```
