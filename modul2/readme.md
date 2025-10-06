# <h1 align="center">Laporan Praktikum Modul 2 <br> Pengenalan C++ (Bagian Kedua)</h1>
<p align="center">DENNA WAHYU SETYOBUDI - 103112430206</p>

## Dasar Teori

Pada materi ini menjelaskan tentang array,pointer,fungsi dan prosedur dalam c++. Array merupakan struktur data yang digunakan untuk menyimpan sekumpulan data dalam satu tempat, setiap data dalam Array memiliki indeks sehingga kita akan mudah memprosesnya. Lalu Dalam C++, Pointer adalah variabel yang menyimpan alamat variabel lain. Pointer tidak hanya dapat menyimpan alamat satu variabel, tetapi juga dapat menyimpan alamat sel array. Lalu Fungsi adalah sub-program yang bisa digunakan kembali baik di dalam program itu sendiri, maupun di program yang lain.Fungsi dapat menerima input dan menghasilkan output. Contoh fungsi yang sering kita buat adalah fungsi main(). Fungsi yang tidak menerima input, kadang juga disebut dengan prosedur.

## Guided

### soal 1

call by pointer
```go
#include <iostream>
using namespace std;

void tukar(int*, int*);

int main()
{
    int a = 10, b = 20;
    cout << "Sebelum ditukar: a = " << a << ", b = " << b << endl;
    tukar(&a, &b);
    cout << "Setelah ditukar: a = " << a << ", b = " << b << endl;
    return 0;
}

void tukar(int *px, int *py)
{
    int temp = *px;
    *px = *py;
    *py = temp;
}
```
> Output
> ![output](output/g1.png)

Pada perogram diatas kita harus melakukan pemanggilan dengan pointer untuk melewatkan parameter, dengan mendeklarasikan sebuah fungsi berisi parameter *px dan *py yang berupa variabel pointer. *px berarti nilai yang ada di alamat px, yaitu nilai a,*py berarti nilai yang ada di alamat py, yaitu nilai b dan temp digunakan sebagai penyimpanan sementara saat menukar.

Pada int main kita memiliki 2 angka a=10 dan b=20 lalu Kita memanggil tukar(&a, &b); supaya fungsi tukar bisa mengubah nilai aslinya langsung, bukan hanya salinannya. dengan langkah pada fungsi tukar kita mendapat outputnya setelah ditukar
### soal 2

call by reference
```go
#include <iostream>
using namespace std;

void tukar(int &x, int &y);

int main()
{
    int a = 10, b = 20;
    cout << "Sebelum ditukar: a = " << a << ", b = " << b << endl;
    tukar(a, b);
    cout << "Setelah ditukar: a = " << a << ", b = " << b << endl;
    return 0;
}

void tukar(int &x, int &y)
{
    int temp = x;
    x = y;
    y = temp;
}
```
> Output
> ![output](output/g2.png)

Untuk program diatas kurang lebih sama hanya kita harus memanggil menggunakan reference, terdepat beberapa perbedaan pada soal 1 yaitu parameter pada fungsi tukar ditulis dengan int &x dan int &y bukan dengan *px dan *py yang dimana tanda & di parameter fungsi artinya: variabel ini adalah referensi ke variabel asli, jadi tidak membuat salinan. semua perubahan langsung mengubah nilai aslinya, yang membuat pemanggilan ini lebih sederhana.
## Unguided

### Soal 1

Buatlah sebuah program untuk melakukan transpose pada sebuah matriks persegi berukuran 3x3. Operasi transpose adalah mengubah baris menjadi kolom dan sebaliknya. Inisialisasi matriks awal di dalam kode, kemudian buat logika untuk melakukan transpose dan simpan hasilnya ke dalam matriks baru. Terakhir, tampilkan matriks awal dan matriks hasil transpose.
```go
#include <iostream>
using namespace std;
int main(){
    float x, y;
    cout << "masukan 2 angka :";
    cin >> x >> y;

    cout << "hasil penjumlahan :"<< x + y << endl;
    cout << "hasil pengurangan :"<< x - y << endl;
    cout << "Hasil Perkalian : " << x * y << endl;
    if (y != 0)
        cout << "Hasil Pembagian : " << x / y << endl;
    else
        cout << "Pembagian tidak bisa dilakukan (y = 0)" << endl;

    return 0;

}
```

> Output
> ![output](output/un1.png)

Pada program diatas kita menginputkan 2 variabel bertipe data float sebagai inputan, dengan menggunakan rumus aritmatika pada cout kita mendapatkan outputnya yaitu hasil penjumlahan, pengurangan, perkalian dan pembagian dari 2 avriabel tsb. pada pembagian jika y bukan 0 maka akan berjalan, jika y adalah 0 makan outputnya berupa teks.

### Soal 2

Buatlah program yang menunjukkan penggunaan call by reference. Buat sebuah prosedur bernama kuadratkan yang menerima satu parameter integer secara referensi (&). Prosedur ini akan mengubah nilai asli variabel yang dilewatkan dengan nilai kuadratnya. Tampilkan nilai variabel di main() sebelum dan sesudah memanggil prosedur untuk membuktikan perubahannya.
```go
#include <iostream>
using namespace std;

string numberToWords(int n) {
    string satuan[10] = {"nol","satu","dua","tiga","empat","lima",
                        "enam","tujuh","delapan","sembilan"};
    string belasan[10] = {"sepuluh","sebelas","dua belas","tiga belas",
                        "empat belas","lima belas","enam belas",
                        "tujuh belas","delapan belas","sembilan belas"};
    string puluhan[10] = {"","", "dua puluh","tiga puluh","empat puluh",
                        "lima puluh","enam puluh","tujuh puluh",
                        "delapan puluh","sembilan puluh"};

    if (n < 10) return satuan[n];
    else if (n < 20) return belasan[n - 10];
    else if (n < 100) {
        int p = n / 10;   
        int s = n % 10;   
        if (s == 0) return puluhan[p];
        else return puluhan[p] + " " + satuan[s];
    } else if (n == 100) {
        return "seratus";
    }
    return "tidak valid";
}

int main() {
    int angka;
    cout << "Masukkan angka (0 - 100): ";
    cin >> angka;

    if (angka < 0 || angka > 100) {
        cout << "Angka di luar jangkauan" << endl;
    } else {
        cout << angka << " : " << numberToWords(angka) << endl;
    }

    return 0;
}
```

> Output
> ![output](output/un2.png)

Pada program diatas kita membuat inputan angka menjadi output teks dari angka yang kita inputkan, dengan menggunakan string array kita membuat sebuah pola untuk bilangan satuan, belasan, puluhan. lalu menggunakan if-else untuk mengecek inputan kita, inputan berupa variabel int angka. output program ini berupa teks dari nilai angka yang kita inputkan

## Referensi

1.https://www.programiz.com/cpp-programming/pointers-arrays (diakses 6/10/2025)
2.https://www.petanikode.com/cpp-array/ (diakses 6/10/2025)
3.https://www.petanikode.com/cpp-fungsi/ (diakses 6/10/2025)
