##profil
| Variable       |    DATA DIRI         |
| ---------------| ----------------     |
| Nama           | Lutpiah Ainu Shiddik |                                     
| NIM            | 312310474            |
| Kelas          | TI.23.A.5            |
| Mata Kuliah    |Basis data            |

##Soal Latihan Praktikum

###Data Model Mapping

```
Mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)
Dosen (kd_ds, nama)
Matakuliah (kd_mk, nama, sks)
JadwalMengajar (kd_ds, kd_mk, hari, jam, ruang)
KRSMahasiswa (nim, kd_mk, kd_ds, semester, nilai)
```

-Buat DDL Script berdasarkan skema ERD tersebut diatas.

-Jalankan script DDL tersebut pada DBMS MySQL.

*Langkah-langkahnya :*

*1. Buat dulu script untuk table Mahasiswa :*


'create table Mahasiswa (
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
    
    );'

