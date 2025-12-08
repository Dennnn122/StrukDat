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
#include <iostream>
using namespace std;

const int MAX = 20;

struct Stack {
    int info[MAX];
    int top;
};

void createStack(Stack &S) {
    S.top = -1;
}

bool isFull(Stack S) {
    return S.top == MAX - 1;
}

bool isEmpty(Stack S) {
    return S.top == -1;
}

void push(Stack &S, int x) {
    if (isFull(S)) {
        cout << "Stack penuh!\n";
    } else {
        S.top++;
        S.info[S.top] = x;
    }
}

int pop(Stack &S) {
    if (isEmpty(S)) {
        cout << "Stack kosong!\n";
        return -1;
    } else {
        int x = S.info[S.top];
        S.top--;
        return x;
    }
}

void printInfo(Stack S) {
    if (isEmpty(S)) {
        cout << "Stack kosong.\n";
    } else {
        cout << "[TOP] ";
        for (int i = S.top; i >= 0; i--) {
            cout << S.info[i] << " ";
        }
        cout << endl;
    }
}

void balikStack(Stack &S) {
    Stack temp;
    createStack(temp);

    while (!isEmpty(S)) {
        int x = pop(S);
        push(temp, x);
    }
    S = temp;
}

void pushAscending(Stack &S, int x) {
    if (isFull(S)) {
        cout << "Stack penuh!\n";
        return;
    }

    Stack temp;
    createStack(temp);

    // Pindahkan elemen lebih kecil dari x ke stack sementara
    while (!isEmpty(S) && S.info[S.top] < x) {
        push(temp, pop(S));
    }

    // Masukkan elemen baru
    push(S, x);

    // Kembalikan elemen dari stack sementara
    while (!isEmpty(temp)) {
        push(S, pop(temp));
    }
}

// Membaca karakter satu per satu hingga user menekan Enter
void getInputStream(Stack &S) {
    cout << "Masukkan karakter (tekan ENTER untuk berhenti): ";
    char c;
    while (true) {
        c = cin.get();  // baca 1 karakter
        if (c == '\n') break; // berhenti jika enter
        if (!isFull(S))
            push(S, c - '0'); // ubah char ke angka
    }
}


int main() {
    cout << "Hello world!\n";

    Stack S;
    createStack(S);

    push(S, 3);
    push(S, 4);
    push(S, 8);
    pop(S);
    push(S, 2);
    push(S, 3);
    pop(S);
    push(S, 9);

    printInfo(S);

    cout << "balik stack\n";
    balikStack(S);
    printInfo(S);

    cout << "\n\n=== PUSH ASCENDING ===\n";
    createStack(S);
    pushAscending(S, 3);
    pushAscending(S, 4);
    pushAscending(S, 8);
    pushAscending(S, 2);
    pushAscending(S, 3);
    pushAscending(S, 9);
    printInfo(S);
    cout << "balik stack\n";
    balikStack(S);
    printInfo(S);

    cout << "\n\n=== INPUT STREAM ===\n";
    createStack(S);
    cin.ignore(); 
    getInputStream(S);
    printInfo(S);
    cout << "balik stack\n";
    balikStack(S);
    printInfo(S);

    return 0;
}

```

> Output
> ![output](output/un1.png)

Pada program di atas, kita membuat sebuah adt stack, kita membuat serbuah struck berisi info[max] untuk menyimpan array dan top untuk menunjuk posisi data paling atas. kita juga memiliki beberapa fungsi yaitu kita membuat sebuah fungsi untuk menginisialisasi stack tsb, lalu kita mengecek kondisi stack menggunakan variabel boolean, lalu membuat sebuah fungsi untuk menambahkan dan mennghapus data, serta menampilkan isi,reverse, push ascending dan get input

## Referensi

1.https://www.geeksforgeeks.org/dsa/introduction-to-stack-data-structure-and-algorithm-tutorials/ (diakses 31/10/2025)

