## profil

| Variable       |    DATA DIRI         |
| ---------------| ----------------     |
| Nama           | Lutpiah Ainus Shiddik|                                     
| NIM            | 312310474            |
| Kelas          | TI.23.A.5            |
| Mata Kuliah    |Basis data            |

## Soal Latihan Praktikum

## Data Model Mapping

```
Mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)
Dosen (kd_ds, nama)
Matakuliah (kd_mk, nama, sks)
JadwalMengajar (kd_ds, kd_mk, hari, jam, ruang)
KRSMahasiswa (nim, kd_mk, kd_ds, semester, nilai)
```

-Buat DDL Script berdasarkan skema ERD tersebut diatas.

-Jalankan script DDL tersebut pada DBMS MySQL.

## *Langkah-langkahnya :*

## *1. Buat dulu script untuk table Mahasiswa :*


```
create table Mahasiswa (
    nim varchar(10) PRIMARY KEY,
    
    nama varchar(25) NOT NULL,
    
    jenis_kelamin ENUM('Laki-Laki', 'Perempuan'),
    
    tgl_lahir DATE,
    
    jalan varchar(15) NOT NULL,
    
    kota varchar(15) NOT NULL,
    
    kodepos varchar(5) NOT NULL,
    
    no_hp varchar(15) NOT NULL,
    
    kd_ds varchar(10) NOT NULL,
    
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
    
    );
```
![ss tgs 1](https://github.com/lutpi9/tugas.pert.7/assets/147919251/3fbefab1-1eda-4d91-81ca-a73e2e626451)

## Tampilkan hasil table :

```
desc Mahasiswa;
```
![ss tgs 1 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/364a1ccc-5c38-4cc2-9015-9f89f19426a2)

## *2. Buat script untuk table Dosen :*
```
create table Dosen (
    kd_ds varchar(10) PRIMARY KEY,
    nama varchar(35) NOT NULL
    );
```
![ss tgs 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/7e8e5914-fe19-46a4-a039-b853eff81aef)
## Tampilkan tabel :
`desc Dosen;`

![ss tgs 2 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/07b5ddeb-ff4b-4411-8238-c8de753f21f1)

## *3. Buat script untuk Mata kuliah :*
```
create table Matakuliah (
    kd_mk varchar(10) PRIMARY KEY,
    nama varchar(30) NOT NULL,
    sks INT NOT NULL
    );
```
![ss tgs 3](https://github.com/lutpi9/tugas.pert.7/assets/147919251/37700698-4674-4329-b842-80e67bb1737c)
## Tampilkan table :
`desc Matakuliah;`

![ss tgs 3 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/bbf180aa-7d8d-4e51-84f7-ceef209a4abc)

## *4. Buat script untuk jadwal mengajar :*
```
create table JadwalMengajar (
    kd_ds varchar(10) NOT NULL,
    kd_mk varchar(10) NOT NULL,
    hari ENUM('Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu', 'Minggu') NOT NULL,
    jam TIME NOT NULL,
    ruang varchar(555) NOT NULL,
    PRIMARY KEY (kd_ds, kd_mk, hari, jam),
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds),
    FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk)
    );

```
![ss tgs 4](https://github.com/lutpi9/tugas.pert.7/assets/147919251/2c726fa0-7056-469b-b51b-1b7befeb81ab)
## Tampilkan table :
`desc JadwalMengajar;`

![ss tgs 4 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/35adb986-ef53-4186-a6ea-c21fbad046a5)

## *5. Buat script untuk KRSMahasiswa :*
```
CREATE TABLE KRSMahasiswa (
    nim varchar(10) NOT NULL,
    kd_mk varchar(10) NOT NULL,
    kd_ds varchar(10) NOT NULL,
    semester varchar(10) NOT NULL,
    nilai FLOAT NOT NULL,
    PRIMARY KEY (nim, kd_mk),
    FOREIGN KEY (nim) REFERENCES Mahasiswa(nim),
    FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk),
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
    );
```
![sss tgs 5](https://github.com/lutpi9/tugas.pert.7/assets/147919251/0098fbb7-72db-48be-ab45-7f3dba5669f9)
## Tampilkan table :
`desc KRSMahasiswa;`

![ss tgs 5 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/9561722c-4e97-4412-a242-12f134f91a78)


## Soal Latihan Praktikum
Berdasarkan table Mahasiswa pada praktikum sebelumnya: (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)

## Isi data pada table tersebut sebanyak minimal 5 record data. Tampilkan semua isi/record tabel!

-Ubah data tanggal lahir Mahasiswa yang bernama Ari menjadi: 1979-08-31!

-Tampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja!

-Hapus Mahasiswa yang bernama Dina!

-Tampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2!

-Tampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan!

-Tampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita!

-Tampilkan data nama dan alamat Mahasiswa saja dari tabel tersebut

-Tampilkan data Mahasiswa terurut berdasarkan nama.

## 1. Mengisi tabel dengan minimal 5 record data :
```
insert into Mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds) values 
-> (11223344,"ari santoso","Laki-laki","1998-10-12","","Bekasi","","",""), 
-> (11223345,"ario talib","Laki-laki","1999-11-16","","Cikarang","","",""), 
-> (11223346,"dina marlina","Perempuan","1997-12-01","","Karawang","","",""), 
-> (11223347,"lisa ayu","perempuan","1996-01-02","","Bekasi","","",""), 
-> (11223348,"tiara wahidah","perempuan","1980-02-05","","Bekasi","","",""), 
-> (11223349,"anton sinaga","laki-laki","1988-03-10","","Cikarang","","","");
```
![ss tgs prktkm 1](https://github.com/lutpi9/tugas.pert.7/assets/147919251/fa270333-97d7-4c64-8137-5ea933a1615d)

## 2. Menampilkan semua isi/record pada tabel bisa menggunakan kode berikut :
`select*from Mahasiswa;`
![ss tgs prktkm 2](https://github.com/lutpi9/tugas.pert.7/assets/147919251/6c782da8-db28-49a7-99b5-c35380434d0d)

## 3. Mengubah data tanggal lahir Mahasiswa yang bernama Ari menjadi : 1979-08-31 menggunakan kode berikut :
`update Mahasiswa set tgl_lahir='1979-08-31' where nim=11223344;`
![ss tgs prktkm 3](https://github.com/lutpi9/tugas.pert.7/assets/147919251/74ed80ec-9d7a-4888-8ae4-3b5ae6ea8726)

## 4. Menampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja dengan cara sebagai berikut :
`select*from Mahasiswa where nim=11223344;`
![ss tgs prktkm 4](https://github.com/lutpi9/tugas.pert.7/assets/147919251/354a6c3d-4528-40f6-84da-77864a78567f)

## 5. Menghapus Mahasiswa yang bernama Dina dengan cara sebagai berikut:
`delete from Mahasiswa where nim=11223346;`
![ss tgs prktkm 5](https://github.com/lutpi9/tugas.pert.7/assets/147919251/d627bacb-2692-437d-91a1-2591ae38ca73)

## 6. Menampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2 dengan cara sebagai berikut :
`select*from Mahasiswa where tgl_lahir<='1996-1-2';`
![ss tgs prktkm 6](https://github.com/lutpi9/tugas.pert.7/assets/147919251/d6f1969e-af47-418e-bbd9-37d4991f001b)

## 7. Menampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan dengan cara sebagai berikut :
`select*from Mahasiswa where kota='bekasi' and jenis_kelamin='Perempuan';`
![ss tgs prktkm 7](https://github.com/lutpi9/tugas.pert.7/assets/147919251/4077dc3f-30b7-4392-a74f-f299728daa87)

## 8. Menampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita dengan cara sebagai berikut :
```
select * from Mahasiswa where kota='Bekasi' and jenis_kelamin='Laki-laki' 
or tgl_lahir<='2002-4-22' 
and jenis_kelamin='Perempuan';
```
![ss tgs prktkm 8](https://github.com/lutpi9/tugas.pert.7/assets/147919251/e0a0b92a-aed6-4cad-9401-fa018beb2084)

## 9. Menampilkan data nama dan jalan Mahasiswa saja dari tabel tersebut dengan cara sebagai berikut :
`select nama, jalan from Mahasiswa;`
![ss tgs prktkm 9](https://github.com/lutpi9/tugas.pert.7/assets/147919251/9520ba9c-9ca4-488a-bab0-8522607918ee)

## 10. Menampilkan data Mahasiswa terurut berdasarkan nama dengan cara sebagai berikut :
`select*from Mahasiswa -> order by nama asc;`
![ss tgs prktkm 10](https://github.com/lutpi9/tugas.pert.7/assets/147919251/357582a9-b3af-4c24-96a6-f6c9ebf810b8)


## Apa bedanya penggunaan BETWEEN dan penggunaan operator >= dan <= ?

(misal: tgl_lahir BETWEEN '1990-10-10' AND '1992-10-11')

(misal: tgl_lahir >= '1990-10-10' AND tgl_lahir <= '1992-10-11')

## Jawaban nya :
Perbedaan utama:

BETWEEN: Hanya memilih data dalam rentang yang ditentukan.
>= dan <=: Memilih data pada atau dalam rentang yang ditentukan.


terimakasih pak





















