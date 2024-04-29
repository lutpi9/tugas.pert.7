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









