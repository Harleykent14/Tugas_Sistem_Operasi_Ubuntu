# Tugas_Sistem_Operasi_Ubuntu
**Nama: Valentino Harley Kent**\
**NIM: 090112823828087**\
**Kelas: SK3C**
<br>
<br>

<div align="Center">
  
## Praktikum 3

</div>

## Soal 1
**Lihat peralatan I/O, character device, yang ada pada system komputer.**
### Jawab:
- Menampilkan peralatan I/O
  > ls -l /dev


  ![TUGAS 4 (1)](https://github.com/user-attachments/assets/29077cb1-dc34-4529-be6d-81053bd257f3)

<div align="Center">

  ```Pada bagian paling kiri yang ditandai dengan "c" diawal merupakan character device dan yang ditandai dengan "b" meruakan block device```
  
</div>

## Soal 2
**Buatlah subdirektori Januari, Februari dan Maret sekaligus pada direktori latihan5**
### Jawab:
- Terlebih dahulu buat folder **latihan5**
  > mkdir latihan5
- Masuk direktori latihan5
  > cd latihan5
- Buat folder **Januari**, **Februari** dan **Maret** sekaligus
  > mkdir Januari Februari Maret
- Cek folder
  > tree
  

![(2)](https://github.com/user-attachments/assets/fbb9a5d2-82e0-4eaa-96a6-faee4aaea94f)


## Soal 3
**Buatlah file dataku yang berisi Nama, NIM dan Alamat anda pada sub direktori Januari dan copy file tersebt ke sub direktori februari dan maret**
### Jawab:
- Buat file **dataku.txt**
  > nano Januari/dataku.txt
- Isi identitas:


![(3)](https://github.com/user-attachments/assets/f4ebf6d1-df76-434a-848f-480a95408b10)


- keluar dari nano "**CTRL + X**"
- kemudian **Y** dan **enter**
- salin file **dataku.txt** pada **Januari** ke **Februari** dan **Maret**
  > for dest in latihan5/*; do cp latihan5/Januari/dataku.txt "$dest/"; done
  
- lalu cek
  > tree


![(4)](https://github.com/user-attachments/assets/2cf4a148-0288-416b-a406-d5dd03d13410)


## Soal 4
**Ubahlah izin akses file dataku.txt pada sub direktori Januari sehingga group dan others dapat melakukan write**
### Jawab:
- Ubah izin file **dataku.txt** sub direktori **Januari** untuk group dan others
  > chmod g=w,o=w Januari/dataku.txt
- Cek dengan ls -l
  > ls -l Januari/dataku.txt


![(5)](https://github.com/user-attachments/assets/2ad23edc-c995-43d9-abde-9f906316afd2)


## Soal 5
**Ubahlah ijin akses file dataku pada sub direktori Februari sehingga user dapat melakukan read, write dan execute, tetapi group dan other hanya bisa read dan execute.**
### Jawab:
- Ubah izin file **dataku.txt** sub direktori **Februari** untuk user, group dan others
  > chmod u=rwx,g=rx,o=rx Februari/dataku.txt
- Cek dengan ls -l
  > ls -l Februari/dataku.txt


![(6)](https://github.com/user-attachments/assets/75af33a3-5d09-4cc2-9b3a-ff162bf30bf7)


## Soal 6
**Ubahlah ijin akses file dataku pada sub direktori Maret sehingga semua dapat melakukan write, read dan execure**
### Jawab:
- ubah ijin akses file **dataku.txt** sub direktori **Maret** untuk user, group dan others
  > chmod a=rwx Maret/dataku.txt
- Cek dengan ls -l
  > ls -l Maret/dataku.txt
  

![(7)](https://github.com/user-attachments/assets/9a6fd381-3d5b-42dd-a14f-b0e45938ec9f)


## Soal 7
**Hapus direktori maret.**
### Jawab:
- Hapus direktori
  > rm -r Maret


![(8)](https://github.com/user-attachments/assets/8a88882f-130c-499a-8328-ae0a50e778a0)


## Soal 8
**Ubahkan kepemilikan sub direktori Februari sehingga user dan group hanya bisa melakukan read, dan cobalah untuk membuat direktori baru haha pada sub direktori Februari**
### Jawab:
- Ubah kepemilikan
  > sudo chown kentvb:mahasiswa Februari/
- Ubah izin
  > sudo chmod ug=r-- Februari/
- Buat folder **haha**
  > mkdir Februari/haha
  

![(9)](https://github.com/user-attachments/assets/903f8d5e-a7fa-4b94-ace2-29ca7724684d)

 ```Permission Dennied terjadi karna user dan grpup hanya bisa Read```


## Soal 9
**Modifikasi umask dari file dataku pada sub direktori Januari menjadi 027 dan berapakah nilai default-Nya?**
### Jawab:
- cek nilai default umask
  > umask
- umask default adalah **002**
- set nilai umask
  > umask 027


![(10)](https://github.com/user-attachments/assets/9180ff95-4aad-4073-8165-7014d8bb7dba)


- Jika nilai umask adalah 027, maka izin default untuk file baru akan menjadi 750. Berikut adalah perhitungannya:
  - Izin default untuk direktori: 777
  - Umask: 027
  - Izin akhir: 777 - 027 = 750
- ubah izin **dataku.txt** menjadi 750
  > chmod 750 dataku.txt
  

![(11)](https://github.com/user-attachments/assets/5ec43ec4-bc77-4831-a50c-cb18df39369e)


- jadi, izin semula adalah **user** bisa **membaca** dan **menulis**, **group** dan **others** hanya bisa **membaca** atau **622**, setelah diberikan **umask** **027**, mendapatkan perubahan izin menjadi **user** bisa **membaca**, **menulis** dan **eksekusi**, **group** hanya bisa **membaca** dan **mengeksekusi**, sedangkan **others** **tidak memilki izin** apapun atau **750** 

<br>
  

## Soal 10
**Buatlah link dari file dataku.txt ke file dataku.ini dan file dataku.juga dan dengan perintah list perhatikan berapa link yang terjadi?**
### Jawab:
- link **dataku.txt** ke **dataku.ini** dan **dataku.juga**
  > ln -s dataku.txt dataku.ini && ln -s dataku.txt dataku.juga
- tampilkan link dengan list
  > ls -l
  

![(12)](https://github.com/user-attachments/assets/f32a4a69-c794-48b2-9831-63e95f2ae885)












