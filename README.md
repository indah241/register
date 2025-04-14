# Organisasi Arsitektur Komputer
## Register
Register adalah memori kecil berkecepatan tinggi yang terdapat di dalam CPU. Register digunakan untuk menyimpan data sementara selama proses eksekusi instruksi. Karena berada di dalam prosesor, register memungkinkan akses data yang sangat cepat dibandingkan dengan memori utama (RAM).

## Fungsi Register:
Menyimpan data sementara selama eksekusi.

Menyimpan alamat memori atau instruksi.

Mendukung operasi perhitungan dan logika.

## Hasil running:
![Screenshot 2025-04-14 141931](https://github.com/user-attachments/assets/3eaddbce-8aaf-4f1c-894f-430075d37ca8)

## Penjelasan kode codingan
## Baris 1-2
![Screenshot 2025-04-14 150832](https://github.com/user-attachments/assets/bb6cd540-1e16-4a4b-af21-2cf4126429fc)

section .text: Menandai bagian program yang berisi instruksi eksekusi.

global _start: Menentukan titik masuk program dengan label _start, sehingga sistem operasi tahu dari mana memulai.
## Baris 4: Label _start
![Screenshot 2025-04-14 150843](https://github.com/user-attachments/assets/f5b21b86-fe09-4121-9b0a-f7daa4b5c433)

Label _start adalah titik awal eksekusi program.
## Blok Pertama: Menampilkan pesan pertama
![Screenshot 2025-04-14 150855](https://github.com/user-attachments/assets/365e3b1b-c56d-4ef0-b5cb-e1b0205179ee)

mov edx, len: Menyalin panjang pesan (len) ke register edx (sistem memerlukan panjang data yang akan ditulis).

mov ecx, msg: Menyalin alamat pesan (msg) ke register ecx (berisi data yang akan ditampilkan).

mov ebx, 1: Menyalin nilai 1 ke ebx, yang berarti stdout (output layar).

mov eax, 4: Menyalin nilai 4 ke eax untuk memilih syscall sys_write.

int 0x80: Memanggil interrupt untuk eksekusi syscall sys_write.

Fungsi: Menampilkan pesan pertama (msg) ke layar.

## Blok Kedua: Menampilkan lima simbol '?'
![Screenshot 2025-04-14 150908](https://github.com/user-attachments/assets/0978eccc-b48c-4001-9d43-a511568f063d)

mov edx, 9: Menyalin nilai 9 (panjang data s2) ke register edx.

mov ecx, s2: Menyalin alamat pesan kedua (s2) ke register ecx.

mov ebx, 1: Menyalin nilai 1 ke ebx (stdout).

mov eax, 4: Menyalin nilai 4 ke eax untuk memilih syscall sys_write.

int 0x80: Memanggil interrupt untuk menulis simbol ?.

Fungsi: Menampilkan 5 simbol ? secara berurutan di layar.

## Blok Ketiga: Keluar dari program
![Screenshot 2025-04-14 150921](https://github.com/user-attachments/assets/fe789881-45f2-45ec-ab05-071151f20a6d)

mov eax, 1: Menyalin nilai 1 ke register eax untuk memilih syscall sys_exit.

int 0x80: Memanggil interrupt untuk mengakhiri program.

Fungsi: Program selesai dan keluar.

## Section .data
![Screenshot 2025-04-14 150928](https://github.com/user-attachments/assets/eae2ef58-0ed3-4ae3-ade5-5f74190ebc97)

Berisi data statis (konstan) yang digunakan dalam program.
msg db 'menampilkan 5 simbol ?', 0xa:

msg adalah pesan teks pertama ('menampilkan 5 simbol ?') diakhiri dengan karakter newline (0xa).

len equ $ - msg:

len adalah panjang data msg, dihitung secara otomatis dari alamat saat ini ($) dikurangi alamat awal msg.

s2 times 5 db '?':

s2 adalah data yang terdiri dari 5 simbol ?.
## Output Program
![Screenshot 2025-04-14 150943](https://github.com/user-attachments/assets/6d4dfd0c-a939-4831-86b4-909ef5733fd5)

Jika kode dijalankan, output yang dihasilkan adalah:
menampilkan 5 simbol ?
?????






