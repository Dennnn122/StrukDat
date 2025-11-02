# <h1 align="center">Laporan Praktikum Modul 6 <br> Doubly Linked List (Bagian Pertama)</h1>
<p align="center">DENNA WAHYU SETYOBUDI - 103112430206</p>

## Dasar Teori

Pada materi ini menjelaskan tentang doubly linked list. doubly linked List merupakan struktur data yang lebih kompleks daripada single linked list, tetapi menawarkan beberapa keuntungan. Keuntungan utama dari daftar tertaut ganda adalah memungkinkan traversal daftar yang efisien di kedua arah. Hal ini karena setiap simpul dalam daftar berisi penunjuk ke simpul sebelumnya dan penunjuk ke simpul berikutnya. Hal ini memungkinkan penyisipan dan penghapusan simpul dari daftar dengan cepat dan mudah, serta traversal daftar yang efisien di kedua arah.

## Guided

### soal 1

```go
#include <iostream>
using namespace std;

//struktur node
struct Node {
    int data;
    Node* prev;
    Node* next;
};

//pointer global
Node* head = nullptr;
Node* tail = nullptr;

void insertDepan(int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->prev = nullptr;
    newNode->next = head;

    if(head != nullptr)
        head->prev = newNode;
    else
        tail = newNode; //jika list kosong
    
    head = newNode;
    cout << "data" << data << "berhasil ditambahkan di depan.\n";
}

void insertBelakang(int data){
    Node* newNode = new Node();
    newNode->data = data;
    newNode->next = nullptr;
    newNode->prev = tail;

    if (tail != nullptr)
        tail->next = newNode;
    else 
        head = newNode; //jika list kosong
    
    tail = newNode;
    cout << "data" << data << "berhasil ditambahkan di belakang. \n";
}

void insertSetelah(int target, int data){
Node* current = head;
while (current != nullptr && current->data != target)
    current = current->next;
if (current == nullptr) {
    cout << "data" << target << "tidak ditemukan.\n";
    return;
}

Node* newNode = new Node();
newNode->data = data;
newNode->next = current->next;
newNode->prev = current;

if (current->next !=nullptr)
    current->prev = newNode;
else
    tail = newNode;

current->next = newNode;
cout << "data" << data << "berhasil disisipkan setelah" << target <<".\n";
}

void hapusDepan(){
    if (head == nullptr) {
        cout << "List kosong, tidak ada yang dihapus.\n";
        return;
    }

    Node* temp = head;
    head = head->next;

    if (head != nullptr)
        head->prev = nullptr;
    else
        tail = nullptr;

    cout << "Data " << temp->data << " di depan berhasil dihapus.\n";
    delete temp;
}

void hapusBelakang(){
    if (tail == nullptr) {
        cout << "List Kosong \n";
        return;
    }

    Node* temp =tail;
    tail= tail->prev;

    if(tail != nullptr)
        tail->next = nullptr;
    else
        head = nullptr;
    
    cout << "data" << temp->data <<"dihapus dari belakang.\n";
    delete temp;
}

void hapusData(int target) {
if (head == nullptr) {
        cout << "List kosong, tidak ada yang dihapus.\n";
        return;
    }

    Node* current = head;
    while (current != nullptr && current->data != target)
        current = current->next;

    if (current == nullptr) {
        cout << "Data " << target << " tidak ditemukan.\n";
        return;
    }

    if (current->prev != nullptr)
        current->prev->next = current->next;
    else
        head = current->next;

    if (current->next != nullptr)
        current->next->prev = current->prev;
    else
        tail = current->prev;

    cout << "Data " << target << " berhasil dihapus.\n";
    delete current;
}

void updateData(int oldData, int newData) {
    Node* current = head;
    while (current != nullptr && current->data != oldData)
        current = current->next;

    if (current == nullptr) {
        cout << "Data " << oldData << " tidak ditemukan.\n";
        return;
    }

    current->data = newData;
    cout << "Data " << oldData << " diubah menjadi " << newData<<".\n";
}

void tampilDepan() {
    if (head == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    cout << "Isi list (dari depan): ";
    Node* current = head;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }
    cout << "\n";
}

// ====================================
// Fungsi: Tampilkan dari belakang
// ====================================
void tampilBelakang() {
    if (tail == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    cout << "Isi list (dari belakang): ";
    Node* current = tail;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->prev;
    }
    cout << "\n";
}

// ====================================
// MAIN PROGRAM (MENU INTERAKTIF)
// ====================================
int main() {
    int pilihan, data, target, oldData, newData;

    do {
        cout << "\n===== MENU DOUBLE LINKED LIST =====\n";
        cout << "1. Insert Depan\n";
        cout << "2. Insert Belakang\n";
        cout << "3. Insert Setelah Data\n";
        cout << "4. Hapus Depan\n";
        cout << "5. Hapus Belakang\n";
        cout << "6. Hapus Data Tertentu\n";
        cout << "7. Update Data\n";
        cout << "8. Tampil dari Depan\n";
        cout << "9. Tampil dari Belakang\n";
        cout << "0. Keluar\n";
        cout << "===================================\n";
        cout << "Pilih menu: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1:
                cout << "Masukkan data: ";
                cin >> data;
                insertDepan(data);
                break;
            case 2:
                cout << "Masukkan data: ";
                cin >> data;
                insertBelakang(data);
                break;
            case 3:
                cout << "Masukkan data target: ";
                cin >> target;
                cout << "Masukkan data baru: ";
                cin >> data;
                insertSetelah(target, data);
                break;
            case 4:
                hapusDepan();
                break;
            case 5:
                hapusBelakang();
                break;
            case 6:
                cout << "Masukkan data yang ingin dihapus: ";
                cin >> target;
                hapusData(target);
                break;
            case 7:
                cout << "Masukkan data lama: ";
                cin >> oldData;
                cout << "Masukkan data baru: ";
                cin >> newData;
                updateData(oldData, newData);
                break;
            case 8:
                tampilDepan();
                break;
            case 9:
                tampilBelakang();
                break;
            case 0:
                cout << "👋 Keluar dari program.\n";
                break;
            default:
                cout << "Pilihan tidak valid.\n";
        }

    } while (pilihan != 0);

    return 0;
}
```
> Output
> ![output](output/g1.png)

Pada perogram diatas kita harus membuat sebuah list yang memiliki beberapa fungsi menggunakan doubly linked list, kita membuat sebuah struck berisi data yang kita simpan serta pointer ke node berikutnya dan sebelumnya. Kita membuat fungsi insert depan, belakang dan setelah, insert setelah digunkan untuk memasukan data yang kita mau inputkan ke setelah data yang kita pilih. kita buat fungsi hapusDepan, hapusBelakang, hapusData, updateData, tampilDepan dan tampilBelakang 

Lalu kita buat fungsi main nya kita menggunakan switch case yang berisi 1-9 untuk memilih fungsi yang kita buat serta 0 untuk menghentikan program dan default jika inputan user tidak valid.

## Unguided

### Soal 1

buatlah single linked list untuk Antrian yang menyimpan data pembeli( nama dan pesanan). program memiliki beberapa menu seperti tambah antrian,  layani antrian(hapus), dan tampilkan antrian. \*antrian pertama harus yang pertama dilayani
```go
#include <iostream>
#include <string>
using namespace std;

struct kendaraan {
    string nopol;
    string warna;
    int thnBuat;
};

struct ElmList {
    kendaraan info;
    ElmList* next;
    ElmList* prev;
};

struct List {
    ElmList* first;
    ElmList* last;
};

void createList(List &L) {
    L.first = nullptr;
    L.last = nullptr;
}

ElmList* alokasi(kendaraan x) {
    ElmList* P = new ElmList;
    P->info = x;
    P->next = nullptr;
    P->prev = nullptr;
    return P;
}

void dealokasi(ElmList* P) {
    delete P;
}

void insertLast(List &L, ElmList* P) {
    if (L.first == nullptr) {
        L.first = P;
        L.last = P;
    } else {
        P->prev = L.last;
        L.last->next = P;
        L.last = P;
    }
}

ElmList* findElm(List L, string nopol) {
    ElmList* P = L.first;
    while (P != nullptr) {
        if (P->info.nopol == nopol) {
            return P;
        }
        P = P->next;
    }
    return nullptr;
}

void printInfo(List L) {
    if (L.first == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    ElmList* P = L.last; // tampil dari belakang seperti contoh
    cout << "\nDATA LIST 1\n";
    while (P != nullptr) {
        cout << "Nomor Polisi : " << P->info.nopol << endl;
        cout << "Warna        : " << P->info.warna << endl;
        cout << "Tahun        : " << P->info.thnBuat << endl;
        cout << endl;
        P = P->prev;
    }
}

void deleteFirst(List &L, ElmList* &P) {
    if (L.first == nullptr) {
        P = nullptr;
    } else if (L.first == L.last) {
        P = L.first;
        L.first = nullptr;
        L.last = nullptr;
    } else {
        P = L.first;
        L.first = P->next;
        L.first->prev = nullptr;
        P->next = nullptr;
    }
}

void deleteLast(List &L, ElmList* &P) {
    if (L.first == nullptr) {
        P = nullptr;
    } else if (L.first == L.last) {
        P = L.last;
        L.first = nullptr;
        L.last = nullptr;
    } else {
        P = L.last;
        L.last = P->prev;
        L.last->next = nullptr;
        P->prev = nullptr;
    }
}

void deleteAfter(ElmList* Prec, ElmList* &P) {
    if (Prec != nullptr && Prec->next != nullptr) {
        P = Prec->next;
        Prec->next = P->next;
        if (P->next != nullptr) {
            P->next->prev = Prec;
        }
        P->next = nullptr;
        P->prev = nullptr;
    } else {
        P = nullptr;
    }
}

int main() {
    List L;
    createList(L);
    kendaraan x;
    ElmList* P;
    string cari, hapus;
    int n;

    cout << "Masukkan jumlah kendaraan: ";
    cin >> n;
    cin.ignore();

    for (int i = 0; i < n; i++) {
        cout << "\nMasukkan nomor polisi: ";
        getline(cin, x.nopol);

        // Cek duplikasi nomor polisi
        if (findElm(L, x.nopol) != nullptr) {
            cout << "Nomor polisi sudah terdaftar!\n";
            continue;
        }

        cout << "Masukkan warna kendaraan: ";
        getline(cin, x.warna);
        cout << "Masukkan tahun kendaraan: ";
        cin >> x.thnBuat;
        cin.ignore();

        P = alokasi(x);
        insertLast(L, P);
    }

    printInfo(L);

    cout << "\nMasukkan Nomor Polisi yang dicari: ";
    getline(cin, cari);
    P = findElm(L, cari);
    if (P != nullptr) {
        cout << "\nNomor Polisi : " << P->info.nopol << endl;
        cout << "Warna        : " << P->info.warna << endl;
        cout << "Tahun        : " << P->info.thnBuat << endl;
    } else {
        cout << "Data tidak ditemukan!\n";
    }

    cout << "\nMasukkan Nomor Polisi yang akan dihapus: ";
    getline(cin, hapus);
    P = findElm(L, hapus);
    if (P != nullptr) {
        ElmList* del;
        if (P == L.first) {
            deleteFirst(L, del);
        } else if (P == L.last) {
            deleteLast(L, del);
        } else {
            deleteAfter(P->prev, del);
        }
        dealokasi(del);
        cout << "Data dengan nomor polisi " << hapus << " berhasil dihapus.\n";
    } else {
        cout << "Data tidak ditemukan!\n";
    }

    printInfo(L);
    return 0;
}

```

> Output
> ![output](output/un1.png)

Pada program di atas, kita membuat sebuah struktur data Doubly Linked List untuk menyimpan data kendaraan yang terdiri dari nomor polisi, warna, dan tahun pembuatan. Kita membuat beberapa struct yaitu struct kendaraan,elmlist dan list, kita juga memiliki beberapa fungsi yaitu createList,alokasi,dealokasi,insertlast,findElm,PrintInfo,deleteFirst,deleteLast dan delete after

Lalu pada fungsi main kita membuat list kosoong dengan createList, lalu user memssukan data kendaraan, setelah user mamsukan data kita akan mengecek apakah nopol yang di input sudah ada atau belum menggunakan findElm jika belum maka data akan dimasukan menggunakan insertLast

## Referensi

1.https://www.geeksforgeeks.org/dsa/doubly-linked-list/ (diakses 31/10/2025)
