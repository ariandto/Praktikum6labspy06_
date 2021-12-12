# Praktikum6labspy06
#LATIHAN LAMBDA
# Mengubah kode menjadi fungsi menggunakan lambda

```
python
import math
def a(x):
    return x**2
    a = lambda x : x ** 2
print(a(2))

def b(x, y):
    return math.sqrt(x**2 + y**2)
    b = lambda x, y : x ** 2  + y ** 2
print(b(2, 2))

def c(*args):
    return sum(args)/len(args)
    c = lambda *args : sum(args)/len(args)
print(c(5, -1, 8, 19))

def d(s):
    return "".join(set(s))
    d = lambda s: "".join(set(s))
print(d("Budi Ariyanto"))
```
## Praktikum6
source code:
```python
dbm = {} 

def ruler():
    print(73*"=")

def header():
    ruler()
    print("| {0:^2} | {1:^9} | {2:^18} | {3:^5} | {4:^5} | {5:^5} | {6:^7} |".format("NO", "NIM", "NAMA", "TUGAS", "UTS", "UAS", "N.AKHIR"))
    ruler()

def nodata(): 
    header()          
    print("|{0:^72}|".format("Data Not Found!!"))
    ruler()

def tambah():
    print("Tambah Data")
    nama       = input("Nama        : ")
    nim        = input("NIM         : ")
    nilaiTugas = int(input("Nilai Tugas : "))
    nilaiUTS   = int(input("Nilai UTS   : "))
    nilaiUAS   = int(input("Nilai UAS   : "))
    nilaiAkhir = (nilaiTugas * 30/100) + (nilaiUTS * 35/100) + (nilaiUAS * 35/100)
    dbm[nama] = [nim, nilaiTugas, nilaiUTS, nilaiUAS, nilaiAkhir]
    print(f"Berhasil menambahkan data '{nama}' dengan NIM : {nim}!")

def Tampilkan():
    print("============================Daftar Mahasiswa============================")
    if len(dbm) <= 0:  
        nodata()
    else:
        no = 0
        header()
        for data in dbm.items():
            no += 1 
            print(f"| {no:>2} | {data[1][0]:<9} | {data[0]:<18} | {data[1][1]:>5} | {data[1][2]:>5} | {data[1][3]:>5} | {data[1][4]:>7.2f} |")               
        ruler() 

def ubah():
    print("Ubah Data Mahasiswa berdasarkan Nama")
    if len(dbm) <= 0:  
        nodata()

    else:
        nama = input("Masukan Nama : ") 
        if nama in dbm.keys():
            print(f"Data ditemukan!")
            print(25*"=")
            print(f"Nama        : {nama}")
            print(f"NIM         : {dbm[nama][0]}")
            print(f"Nilai Tugas : {dbm[nama][1]}")
            print(f"Nilai UTS   : {dbm[nama][2]}")
            print(f"Nilai UAS   : {dbm[nama][3]}")
            print(25*"=")
            print("1. Nama\n2. NIM\n3. Nilai\n0. Kembali")
            tanya = int(input("Apa yang ingin diubah? [1-3] : "))
            if tanya == 1:
                _nama = input("Masukan Nama Baru : ")
                dbm[_nama] = dbm.pop(nama)
                print("Berhasil merubah Nama! ")

            elif tanya == 2:
                _nim = input("Masukan Nim Baru : ")
                dbm[nama][0] = _nim
                print("Berhasil merubah NIM!")

            elif tanya == 3:
                _nilaiTugas = int(input("Masukan Nilai Tugas Baru : "))
                _nilaiUTS = int(input("Masukan Nilai UTS Baru : "))
                _nilaiUAS = int(input("Masukan Nilai UAS Baru : "))
                _nilaiAkhir = _nilaiTugas * 30/100 + _nilaiUTS * 35/100 + _nilaiUAS * 35/100
                dbm[nama][1:4] = _nilaiTugas, _nilaiUTS, _nilaiUAS, _nilaiAkhir
                print("Berhasil merubah data nilai!")
            elif tanya == 0:
                pass
            
            else:
                print(f"Pilihan {tanya} tidak ada! Silahkan masukan [1-3]")

        else:
            print(f"Data {nama} tidak ditemukan!") 

def hapus():
    print("Hapus Data Mahasiswa berdasarkan Nama")
    if len(dbm) <= 0:  
        nodata()

    else:
        nama = input("Masukan nama : ")
        if(nama in dbm):
            del dbm[nama]
            print(f"Data {nama} berhasil dihapus!")
        else:
            print(f"Data {nama} tidak ditemukan!")

while True:
    print()
    print(25*"-", "Program Input Nilai", 25*"-")
    print("1. Tambah Data \n2. Tampilkan Data \n3. Ubah Data \n4. Hapus Data \n0. Keluar")
    print(73*"-")
    menu = int(input("Pilih menu : "))
    print(73*"-")
    print()

    if menu == 1:
        tambah()       

    elif menu == 2:
        Tampilkan()

    elif menu == 3:
        ubah() 

    elif menu == 4:
        hapus()

    elif menu == 0:
        print("End Program")
        loop = False 

    else:
        print(f"Menu '{menu}' tidak ada! Silahkan masukan [0-4]")

```
Keterangan:
 
 1. Deklarasi Dictionary sebagai database
 ```python
dbm = {} 
 ```
 
 2. Membuat Function tambahan agar bisa dipanggil saat dibutuhkan
 ```python
def ruler():
    print(73*"=")

def header():
    ruler()
    print("| {0:^2} | {1:^9} | {2:^18} | {3:^5} | {4:^5} | {5:^5} | {6:^7} |".format("NO", "NIM", "NAMA", "TUGAS", "UTS", "UAS", "N.AKHIR"))
    ruler()

def nodata(): 
    header()          
    print("|{0:^72}|".format("Data Not Found!!"))
    ruler()

```
 3. Membuat Function Program
#### Tambah()
- Memasukan data
- Jika sudah, maka data akan dimasukkan kedalam Dict `dbm`
- Dimana Nama sebagai key dan sisanya values yang dimasukkan kedalam list
- Jika berhasil maka akan menampilkan "Berhasil menambahkan data 'nama' dengan NIM : nim"
 ```python
 def tambah():
    print("Tambah Data")
    nama       = input("Nama        : ")
    nim        = input("NIM         : ")
    nilaiTugas = int(input("Nilai Tugas : "))
    nilaiUTS   = int(input("Nilai UTS   : "))
    nilaiUAS   = int(input("Nilai UAS   : "))
    nilaiAkhir = (nilaiTugas * 30/100) + (nilaiUTS * 35/100) + (nilaiUAS * 35/100)
    dbm[nama] = [nim, nilaiTugas, nilaiUTS, nilaiUAS, nilaiAkhir]
    print(f"Berhasil menambahkan data '{nama}' dengan NIM : {nim}!") 
 ```

Output Tambah Data

![Tambah Data](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc1.png)

 #### Lihat()
 1) Apabila Dict `dbm` masih kosong maka akan memanggil function `nodata`
 ```python
 def Tampilkan():
    print("============================Daftar Mahasiswa============================")
    if len(dbm) <= 0:  
        nodata()
  ```
 
Output Tidak Ada Data

![nodata](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc0.png)

2) Program Lihat Data Dijalankan
- Menggunakan looping untuk mengeluarkan data
- Dan menggunakan f-string agar tidak terlalu panjang dan format.string agar tampilan terlihat rapih
```python
else:
        no = 0
        header()
        for data in dbm.items():
            no += 1 
            print(f"| {no:>2} | {data[1][0]:<9} | {data[0]:<18} | {data[1][1]:>5} | {data[1][2]:>5} | {data[1][3]:>5} | {data[1][4]:>7.2f} |")               
        ruler() 
```

Output Jika Data Diinputkan

![tampil](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc2.png)

#### Ubah()
1) Apabila Dict `dbm` masih kosong maka akan memanggil function `nodata`
 ```python
 def ubah():
    print("Ubah Data Mahasiswa berdasarkan Nama")
    if len(dbm) <= 0:  
        nodata()
 ```
 ![no](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc0.png)

2) Function **ubah()** dijalankan berdasarkan nama
- Memasukan nama sebagai key dan akan memunculkan isi data dari key tersebut
- Jika salah memasukkan nama, maka akan mengeluarkan "data nama tidak ditemukan!"
- Selanjutnya akan diberi pilihan apa yang ingin diubah, jika ingin membatalkan maka ketik 0
- Jika salah memasukkan pilihan maka mengeluarkan "Pilihan input tidak ada! Silahkan masukan [1-3]"
 ```python
else:
   nama = input("Masukan nama : ")
   if nama in dbm.keys():
      print(f"Nama        = {nama}")
      print(f"NIM         = {dbm[nama][0]}")
      print(f"Nilai Tugas = {dbm[nama][1]}")
      print(f"Nilai UTS   = {dbm[nama][2]}")
      print(f"Nilai UAS   = {dbm[nama][3]}")
      print(25*"=")
      print("1. Nama\n2. NIM\n3. Nilai\n0. Kembali")
      tanya = int(input("Apa yang ingin diubah? [1-3] : "))
      ...      
      elif tanya == 0:
          pass
          
      else:
          print(f"Pilihan {tanya} tidak ada! Silahkan masukan [1-3]")
   else:
      print(f"Data {nama} tidak ditemukan!") 
 ```
 
 ##### Ubah Nama
 Memasukan nama baru, nama akan berubah, maka akan mengeluarkan "Berhasil merubah Nama!"
 ```python
 if tanya == 1:
    _nama = input("Masukan Nama Baru : ")
    dbm[_nama] = dbm.pop(nama)
    print("Berhasil merubah Nama! ")
 ```

Output Ubah Nama

![ubah](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc5.png)
![ubah1](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc6.png)

##### Ubah NIM
Memasukan NIM baru, NIM akan berubah, maka akan mengeluarkan "Berhasil merubah NIM!"
```python
elif tanya == 2:
    _nim = input("Masukan Nim Baru : ")
    dbm[nama][0] = _nim
    print("Berhasil merubah NIM!")
```

Output Ubah NIM

![ubah2](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc7.png)

##### Ubah Nilai
Memasukan nilai baru, nilai akan berubah, maka akan mengeluarkan "Berhasil merubah data nilai!"
```python
elif tanya == 3:
    _nilaiTugas = int(input("Masukan Nilai Tugas Baru : "))
    _nilaiUTS = int(input("Masukan Nilai UTS Baru : "))
    _nilaiUAS = int(input("Masukan Nilai UAS Baru : "))
    _nilaiAkhir = _nilaiTugas * 30/100 + _nilaiUTS * 35/100 + _nilaiUAS * 35/100
    dbm[nama][1:4] = _nilaiTugas, _nilaiUTS, _nilaiUAS, _nilaiAkhir
    print("Berhasil merubah data nilai!")
```

Output Ubah Nilai

![ubah3](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc8.png)

#### Hapus()
1) Apabila Dict `dbm` masih kosong maka akan memanggil function `nodata`
```python
def hapus():
    print("Hapus Data Mahasiswa berdasarkan Nama")
    if len(dbm) <= 0:  
        nodata()
```

2) Program Hapus Data Dijalankan
- Memasukan nama sebagai key data yang ingin dihapus
- Jika salah memasukan nama ,maka akan mengeluarkan "data nama tidak ditemukan!"
```python
else:
     nama = str(input("Masukan nama : "))
     if(nama in dbm):
         del dbm[nama]
         print(f"Data {nama} berhasil dihapus!")
     else:
         print(f"Data {nama} tidak ditemukan!") 
```

Output Hapus Data

![ubah3](https://github.com/ariandto/Praktikum6labspy06_/blob/main/sc/sc9.png)

#### Menu
- Menggunakan infinite loop while True
- Apabila salah memasukkkan inputan maka akan muncul "Menu 'menu' tidak ada!"
- Jika benar maka function yang sudah dibuat akan dijalankan
```python
while True:
    print()
    print(25*"-", "Program Input Nilai", 25*"-")
    print("1. Tambah Data \n2. Tampilkan Data \n3. Ubah Data \n4. Hapus Data \n0. Keluar")
    print(73*"-")
    menu = int(input("Pilih menu : "))
    print(73*"-")
    print()

    if menu == 1:
        tambah()       

    elif menu == 2:
        Tampilkan()

    elif menu == 3:
        ubah() 

    elif menu == 4:
        hapus()

    elif menu == 0:
        print("End Program")
        loop = False 

    else:
        print(f"Menu '{menu}' tidak ada! Silahkan masukan [0-4]")

```
