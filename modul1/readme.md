
# <h1 align="center">Laporan Praktikum Modul 1 <br> Pengenalan C++</h1>
<p align="center">DENNA WAHYU SETYOBUDI - 103112430206</p>

## Dasar Teori

Bahasa C++ (dibaca ‘Si plus plus’) adalah bahasa pemrograman komputer yang strongly-typed dan fleksibel, serta banyak digunakan untuk pengembangan perangkat lunak dan sistem komputer. Bahasa C++ dikembangkan oleh ilmuwan komputer Denmark, Bjarne Stroustrup dan dirilis pada tahun 1985. Selain itu, C++ juga terkenal dengan performanya yang optimal. Berbeda dengan kebanyakan bahasa pemrograman lain, C++ menawarkan kontrol yang lebih detail terhadap manajemen memori sehingga programmer dapat menulis kode yang berjalan dengan sangat efisien.

## Guided

### soal 1

aritmatika
```go
#include <iostream>
using namespace std;
int main()
{
    int W, X, Y;
    float Z;
    X = 7;
    Y = 3;
    W = 1;
    Z = (X + Y) / (Y + W);
    cout << "Nilai z = " << Z << endl;
    return 0;
}
```
### soal 2

fungsi
```go
#include <iostream>
using namespace std;

// Prosedur: hanya menampilkan hasil, tidak mengembalikan nilai
void tampilkanHasil(double p, double l)
{
    cout << "\n=== Hasil Perhitungan ===" << endl;
    cout << "Panjang : " << p << endl;
    cout << "Lebar   : " << l << endl;
    cout << "Luas    : " << p * l << endl;
    cout << "Keliling: " << 2 * (p + l) << endl;
}

// Fungsi: mengembalikan nilai luas
double hitungLuas(double p, double l)
{
    return p * l;
}

// Fungsi: mengembalikan nilai keliling
double hitungKeliling(double p, double l)
{
    return 2 * (p + l);
}

int main()
{
    double panjang, lebar;

    cout << "Masukkan panjang: ";
    cin >> panjang;
    cout << "Masukkan lebar  : ";
    cin >> lebar;

    // Panggil fungsi
    double luas = hitungLuas(panjang, lebar);
    double keliling = hitungKeliling(panjang, lebar);

    cout << "\nDihitung dengan fungsi:" << endl;
    cout << "Luas      = " << luas << endl;
    cout << "Keliling  = " << keliling << endl;

    // Panggil prosedur
    tampilkanHasil(panjang, lebar);

    return 0;
}
```
### soal 3

kondisi
```go
#include <iostream>
using namespace std;
// int main()
// {
//     double tot_pembelian, diskon;
//     cout << "total pembelian: Rp";
//     cin >> tot_pembelian;
//     diskon = 0;
//     if (tot_pembelian >= 100000)
//         diskon = 0.05 * tot_pembelian;
//     cout << "besar diskon = Rp" << diskon;
// }



// int main()
// {
//     double tot_pembelian, diskon;
//     cout << "total pembelian: Rp";
//     cin >> tot_pembelian;
//     diskon = 0;
//     if (tot_pembelian >= 100000)
//         diskon = 0.05 * tot_pembelian;
//     else
//         diskon = 0;
//     cout << "besar diskon = Rp" << diskon;
// }



int main()
{
    int kode_hari;
    cout << "Menentukan hari kerja/libur\n"<<endl;
    cout << "1=Senin 3=Rabu 5=Jumat 7=Minggu "<<endl;
    cout << "2=Selasa 4=Kamis 6=Sabtu "<<endl;
    cin >> kode_hari;
    switch (kode_hari)
    {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
        cout<<"Hari Kerja";
        break;
    case 6:
    case 7:
        cout<<"Hari Libur";
        break;
    default:
        cout<<"Kode masukan salah!!!";
    }
    return 0;
}
```
### soal 4

struck
```go
#include <iostream>
#include <string>
using namespace std;

// Definisi struct
struct Mahasiswa {
    string nama;
    string nim;
    float ipk;
};

int main() {

    Mahasiswa mhs1;

    cout << "Masukkan Nama Mahasiswa: ";
    getline(cin, mhs1.nama);
    // cin >> mhs1.nama;
    cout << "Masukkan NIM Mahasiswa : ";
    cin >> mhs1.nim;
    cout << "Masukkan IPK Mahasiswa : ";
    cin >> mhs1.ipk;

    cout << "\n=== Data Mahasiswa ===" << endl;
    cout << "Nama : " << mhs1.nama << endl;
    cout << "NIM  : " << mhs1.nim << endl;
    cout << "IPK  : " << mhs1.ipk << endl;

    return 0;
}

```
### soal 5

perulangan
```go
#include <iostream>
using namespace std;
// int main()
// {
//     int jum;
//     cout << "jumlah perulangan: ";
//     cin >> jum;
//     for (int i = 0; i < jum; i++)
//     {
//         cout << "saya sahroni\n";
//     }
//     return 1;
// }


// while
int main()
{
    int i = 1;
    int jum;
    cin >> jum;
    do
    {
        cout << "bahlil ke-" << (i + 1) << endl;
        i++;
    } while (i < jum);
    return 0;
}
```
### soal 6

test
```go
#include <iostream>
using namespace std;
int main()
{
    string ch;
    cout << "Masukkan sebuah karakter: ";
    // cin >> ch;
    ch = getchar();  //Menggunakan getchar() untuk membaca satu karakter
    cout << "Karakter yang Anda masukkan adalah: " << ch << endl;
    return 0;
}

```

## Unguided

### Soal 1

Buatlah program yang menerima input-an dua buah bilangan bertipe float, kemudian memberikan output-an hasil penjumlahan, pengurangan, perkalian, dan pembagian dari dua bilangan tersebut.
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
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Pada program diatas kita menginputkan 2 variabel bertipe data float sebagai inputan, dengan menggunakan rumus aritmatika pada cout kita mendapatkan outputnya yaitu hasil penjumlahan, pengurangan, perkalian dan pembagian dari 2 avriabel tsb. pada pembagian jika y bukan 0 maka akan berjalan, jika y adalah 0 makan outputnya berupa teks.

### Soal 2

Buatlah sebuah program yang menerima masukan angka dan mengeluarkan output nilai angka tersebut dalam bentuk tulisan. Angka yang akan di-input-kan user adalah bilangan bulat positif mulai dari 0 s.d 100.

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
> ![Screenshot bagian x](output/screenshot_soal2A.png)

Pada program diatas kita membuat inputan angka menjadi output teks dari angka yang kita inputkan, dengan menggunakan string array kita membuat sebuah pola untuk bilangan satuan, belasan, puluhan. lalu menggunakan if-else untuk mengecek inputan kita, inputan berupa variabel int angka. output program ini berupa teks dari nilai angka yang kita inputkan

### soal 3

Buatlah program yang dapat memberikan input dan output sebagai berikut:
```go
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Input: ";
    cin >> n;

    for (int i = n; i >= 1; i--) {
        for (int s = 0; s < n - i; s++) cout << "  ";
        for (int j = i; j >= 1; j--) cout << j << " ";
        cout << "* ";
        for (int j = 1; j <= i; j++) cout << j << " ";
        cout << endl;
    }
    for (int s = 0; s < n; s++) cout << "  ";
    cout << "*" << endl;

    return 0;
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2B.png)

Pada program diatas kita harus membuat sebuah pola cermin, inputan program adalah variabel bertipe data int n. lalu mencetak baris demi baris berisi urutan angka menurun di sebelah kiri, tanda * di tengah, dan urutan angka menaik di sebelah kanan. Setelah setiap baris, jumlah angka berkurang satu dan diberi spasi tambahan di depan sehingga membentuk segitiga simetris.

## Referensi

1. https://www.dicoding.com/blog/memahami-esensi-bahasa-pemrograman-c/ (diakses 29/9/2025, 22.23)

