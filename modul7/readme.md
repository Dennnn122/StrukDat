# <h1 align="center">Laporan Praktikum Modul 7 <br> Queue</h1>
<p align="center">DENNA WAHYU SETYOBUDI - 103112430206</p>

## Dasar Teori

Pada materi ini menjelaskan tentang Queue. Stack adalah struktur data linear yang mengikuti prinsip LIFO (Last In First Out), yaitu elemen terakhir yang dimasukkan akan dikeluarkan pertama kali. Artinya, baik operasi penyisipan maupun penghapusan hanya terjadi di satu sisi.

## Guided

### soal 1

```go
#include <iostream>
using namespace std;

#define MAX 5 // ukuran maksimal queue

//struktur queue
struct Queue {
    int data[MAX];
    int head;
    int tail;
};

//membuat antrean kososng
void createQueue(Queue &Q){
    Q.head = -1;
    Q.tail =-1;
}
//mengecek apakah queue kosong
bool isEmpty(Queue Q) {
    return (Q.head == -1 && Q.tail ==-1);
}
//menegecek apkaah queue penuh
bool isFull(Queue Q) {
    return (Q.tail == MAX - 1);
}
//menapilkan isi antrean
void printQueue(Queue Q) {
    if (isEmpty(Q)) {
        cout << "Queue kososng!" << endl;
    } else {
        cout <<"Queue :";
        for (int i = Q.head; i <= Q.tail; i++) {
            cout << Q.data[i] << "";
        }
        cout << endl;
    }
}

//menambah elemen ke dalam antrian (Enqueue)
void enqueue(Queue &Q, int x) {
    if (isFull(Q)) {
        cout << "Queue penuh! tidak bisa menambah data." << endl;
    } else {
        if (isEmpty(Q)) {
            Q.head = Q.tail = 0;
        } else {
            Q.tail++;
        }
        Q.data[Q.tail] = x;
        cout << "Enqueue:" <<x << endl;
    }
}

//menghapus ekemen dari antrean (Dequeue)
void dequeue(Queue &Q) {
    if (isEmpty(Q)) {
        cout << "Queue kosong! tidak ada data yang dihapus << endl";
    } else {
        cout << "Dequeue:" << Q.data[Q.head]<< endl;
        // jika hanya 1 elemen
        if (Q.head == Q.tail) {
            Q.head = Q.tail =-1;
        } else {
            //geser semua elemen ke kiri
            for (int i = Q.head; i< Q.tail; i++){
                Q.data[i] = Q.data[i+1];}
            }
            Q.tail--;
        } 
    }

//program utama 
int main(){
    Queue Q;
    createQueue(Q);

    enqueue(Q, 5);
    enqueue(Q, 2);
    enqueue(Q, 7);
    printQueue(Q);

    dequeue(Q);
    printQueue(Q);

    enqueue(Q, 4);
    enqueue(Q, 9);
    printQueue(Q);

    dequeue(Q);
    dequeue(Q);
    printQueue(Q);

    return 0;
}
```
> Output
> ![output](output/g1.png)



## Unguided

### Soal 1

buatlah single linked list untuk Antrian yang menyimpan data pembeli( nama dan pesanan). program memiliki beberapa menu seperti tambah antrian,  layani antrian(hapus), dan tampilkan antrian. \*antrian pertama harus yang pertama dilayani
```go


```

> Output
> ![output](output/un1.png)


## Referensi

1.https://www.geeksforgeeks.org/dsa/introduction-to-stack-data-structure-and-algorithm-tutorials/ (diakses 31/10/2025)

