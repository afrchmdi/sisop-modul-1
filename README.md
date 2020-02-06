## Modul 1 Sistem Operasi 
# Shell Scripting, Cron, dan AWK
## Prasyarat

1. Menginstall OS Linux
2. Memahami CLI (_Command Line Interface_)

## Daftar Isi

1. [Shell Scripting](#1-shell-scripting)
    - [1.1 Shell](#-1.1-shell)
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

## 1.7 Quoting
Shell Unix/Linux memiliki beberapa karakter spesial yang disebut dengan **metakarakter**. Karakter tersebut punya makna khusus jika digunakan di dalam shell script. Beberapa macam metakarakter:
```bash
* ? [ ] ' " \ $ ; & ( ) | ^ < > new-line space tab
```

Ada 4 jenis **quoting**, yaitu:   
| No | Quoting | Deskripsi|
|---|---|---|
| 1 | Single Quote (') | Semua metakarakter di antara single quote akan kehilangan makna khusus |
| 2 | Double Quote (") | Sebagian besar metakarakter di antara double quote akan kehilangan makna khusus, kecuali `$, backquote, \$, \', \", \\` |
| 3 | Backslash (\\) | Karakter apa pun setelah backslash akan kehilangan makna khusus |
| 4 | Backquote (`) | Apa pun di antara back quote akan diperlakukan sebagai perintah dan akan dieksekusi |

Contoh:   
```bash
#!/bin/bash

single=3

#Single quote
echo '$single'

#Double quote
echo "$single"

#Backslash
echo \<-\$1500.\*\*\>\; \(update\?\) \[y\|n\]

#Backquote
dmn=`pws`
echo "Dimana kita? " $dmn
```

Output:   
![hasil-quote](/gambar/hasil-quote.png)

Lebih banyak dapat dilihat sendiri di `man bash`

## 1.8 Operator Dasar
Ada beberapa jenis operator yang didukung oleh shell, yaitu:
  1. Operator Aritmatika
  2. Operator Relasional
  3. Operator Boolean
  4. Operator String
  5. Operator File Test

Namun yang akan dibahas lebih jauh hanyalah operator **aritmatika** dan **relasional**.

### 1.8.1 Operator Aritmatika

| No | Operator | Deskripsi |
|---|---|---|
| 1 | + | Penjumlahan |
| 2 | - | Pengurangan |
| 3 | * | Perkalian |
| 4 | / | Pembagian |
| 5 | % | Modulus (sisa pembagian) |
| 6 | = | Menempatkan nilai di sisi kanan ke variabel di sisi kiri |
| 7 | == | Membandingkan 2 nilai yang sama |
| 8 | != | Membandingkan 2 nilai yang tidak sama |

Ada 3 cara yang dapat digunakan untuk melakukan operasi matematika, yaitu:
1. Menggunakan perintah built-in **let**
2. Menggunakan perintah eksternal **expr** atau **awk** 
3. Menggunakan perintah subtitusi ` $((ekspresi))`

Contoh:   
```bash
#!/bin/bash

a=15
b=7

#memakai let
let jumlah=$a+$b
let kurang=$a-$b
let kali=$a*$b

#memakai expr
bagi=`expr $a / $b`

#memakai perintah subtitusi $((ekspresi))
mod=$(($a % $b)) 

echo "a + b = $jumlah"
echo "a - b = $kurang"
echo "a * b = $kali"
echo "a / b = $bagi"
echo "a % b = $mod"

b=$a

echo "a = $a"
echo "b = $b"
```

Output:

![hasil-181](/gambar/hasil-181.png)

### 1.8.2 Operator Relasional

| No | Operator | Deskripsi | 
|---|---|---|
| 1 | -eq | Memeriksa apakah nilai kedua operan sama (==) |
| 2 | -ne | Memeriksa apakah nilai kedua operan tidak sama (!=) |
| 3 | -gt | Memeriksa apakah nilai operan kiri lebih besar daripada operan kanan (>) |
| 4 | -lt | Memeriksa apakah nilai operan kiri lebih kecil daripada operan kanan (<)  |
| 5 | -ge | Memeriksa apakah nilai operan kiri lebih besar atau sama dengan operan kanan (>=) |
| 6 | -le | Memeriksa apakah nilai operan kiri lebih kecil atau sama dengan operan kanan (<=) |

Operator relasional biasanya digunakan bersama dengan conditional statements, contoh:   
```bash
#!/bin/bash

a=15
b=7

if [ $a -eq $b ]
then
  echo "$a -eq $b: a sama dengan b"
else
  echo "$a -eq $b: a tidak sama dengan b"
fi
```
Output:   
```bash
15 -eq 7: a tidak sama dengan b
```

## 1.9 Conditional Statements
**Conditional statements** digunakan untuk memungkinkan program dapat membuat keputusan yang benar dengan memilih tindakan tertentu berdasarkan syarat/kondisi tertentu.
Ada 2 jenis conditional statements dalam Unix shell, yaitu:
1. **if...else**
2. **case**
  
### 1.9.1 If...Else
Syntax:
```bash
if [ kondisi1 ]
then 
  perintah1 
elif [ kondisi2 ]
then
  perintah2 
else
  alternatif_perintah
fi
```
Contoh:
```bash
#!/bin/bash

cintaku=100
cintanya=88

if [ $cintaku == $cintanya ]
then
  echo "cintaku sama dengan cintanya"
elif [ $cintaku -gt $cintanya ]
then
  echo "cintaku lebih besar dari cintanya"
elif [ $a -lt $cintanya ]
then
  echo "cintaku lebih kecil dari cintanya"
else
  echo "Tidak ada kondisi yang memenuhi"
fi
```
Output:
```bash
cintaku lebih besar dari cintanya
```

### 1.9.2 Case
Syntax:
```bash
case var in
  pola1)
    perintah1 
    ;;
  pola2)
    perintah2 
    ;;
  *)
    alternatif_perintah
    ;;
esac
```
Contoh:
```bash
#!/bin/bash

echo "Aku udah suka sama kamu dari lama, kamu mau ga jadi pacar aku?"
echo "1. Ya"
echo "2. Tidak"
echo "3. Aku gak bisa jawab sekarang"
echo -n "jawab: "
read jawaban

case "$jawaban" in
  "1")
    echo "Ga ada hal yang lebih aku tunggu dari ini, terimakasih!!!"
    ;;
  "2")
    echo "Oke, maaf ya udah ganggu waktu kamu"
    ;;
  "3")
    echo "Gantung aja aku, gantung aja!!!"
    ;;
  *)
    echo "Apa apa? Gimana??"
    ;;
esac
```
Output:   
![hasil-case](/gambar/hasil-case.png)

## 1.10 Loop
**Loop** digunakan untuk mengeksekusi serangkaian perintah berulang kali. Ada beberapa macam shell loops:
  1. While loop
  2. For loop
  3. Until loop
  4. Select loop

### 1.10.1 While loop
**While loop** digunakan untuk mengeksekusi serangkaian perintah berulang kali **selama** suatu kondisi terpenuhi. While digunakan jika kita ingin memanipulasi suatu variabel secara berulang-ulang.
Syntax:
```bash
while kondisi
do
  perintah 
done
```
Contoh:
```bash
#!/bin/bash

a=0

while [ $a -lt 10 ]
do
echo $a
  a=$((a + 2))
done
```
Output:
```bash
0
2
4
6
8
```
### 1.10.2 For loop
**For loop** digunakan untuk mengulang serangkaian perintah untuk setiap item pada daftar.
Syntax:
```bash
for var in daftar_item
do
  perintah 
done
```
Contoh:
```bash
#!/bin/bash

for num in 1 2 3 4 5
do
  echo $num
done
```
Selain itu, bisa ditulis seperti ini:
```bash
#!/bin/bash

for ((num=1; num<=5; num=num+1))
do
  echo $num
done
```
Output:
```bash
1
2
3
4
5
```

### 1.10.3 Until loop
Berbeda dengan while, **until loop** digunakan untuk mengeksekusi serangkaian perintah berulang kali **sampai** suatu kondisi terpenuhi.
Syntax:
```bash
until kondisi
do
  perintah
done
```
Contoh:
```bash
#!/bin/bash

a=0

until [ ! $a -lt 10 ]
do
  echo $a
  a=$((a + 2))
done
```
Output:
```bash
0
2
4
6
8
```

### 1.10.4 Select loop
**Select loop** digunakan ketika kita ingin membuat sebuah program dengan beberapa daftar pilihan yang bisa dipilih oleh user, misalnya daftar menu.
Syntax:
```bash
select var in daftar_item
do
  perintah
done
```
Contoh:
```bash
#!/bin/bash

select minuman in teh kopi air jus susu semua gaada
do
  case $minuman in
    teh|kopi|air|semua)
      echo "Maaf, habis"
      ;;
    jus|susu)
      echo "Tersedia"
    ;;
    gaada)
      break
    ;;
    *) echo "Tidak ada di daftar menu"
    ;;
  esac
done
```
Output:   
![hasil-select-loop](/gambar/hasil-select-loop.png)

### 1.10.5 Nesting Loops
Semua jenis loop di atas mendukung konsep nesting, artinya kita dapat menempatkan satu loop ke dalam loop lain, baik loop yang sejenis maupun berbeda jenis
Contoh:
```bash
#!/bin/sh

a=0

while [ "$a" -lt 10 ]  #loop1
do
  b="$a"
  while [ "$b" -ge 0 ]  #loop2
  do
    echo -n "$b "
    b=`expr $b - 1`
  done
  echo ""
  a=`expr $a + 1`
done
```
Output:
```bash
0
1 0
2 1 0
3 2 1 0
4 3 2 1 0
5 4 3 2 1 0
6 5 4 3 2 1 0
7 6 5 4 3 2 1 0
8 7 6 5 4 3 2 1 0
9 8 7 6 5 4 3 2 1 0
```
## 1.11 Function
**Fungsi** digunakan untuk memecah fungsionalitas keseluruhan script menjadi sub-bagian yang lebih kecil. Sub-bagian itu dapat dipanggil untuk melakukan tugas masing-masing apabila diperlukan.
Syntax:
```bash
nama_fungsi () { 
  perintah1
  perintah2
  ...
  perintahN
}
```
Contoh:
```bash
#!/bin/bash
#define functions
ask_name() {
  echo "Siapa namamu?"
}
reply() {
  read nama
  echo "Hai $nama, selamat datang di praktikum sistem operasi!"  
}

#call functions
ask_name
reply
```
Output:   
![hasil-fungsi](/gambar/hasil-fungsi.png)

### 1.11.1 Nested Functions
Sama halnya dengan loop, function juga bisa menerapkan konsep nested. Dimana kita bisa memanggil sebuah fungsi di dalam fungsi.
```bash
#!/bin/bash

#define functions
ask_name() {
  echo "Siapa namamu?"
  reply   #call reply function inside ask_name function
}
reply() {
  read nama
  echo "Hai $nama, selamat datang di praktikum sistem operasi!"
}

#call functions
ask_name
```
Output:   
![hasil-fungsi](/gambar/hasil-fungsi.png)

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
