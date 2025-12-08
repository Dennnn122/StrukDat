# <h1 align="center">Laporan Praktikum Modul 10 <br> Tree</h1>
<p align="center">DENNA WAHYU SETYOBUDI - 103112430206</p>

## Dasar Teori

Pada materi ini menjelaskan tentang Tree. Tree adalah struktur data hierarkis yang digunakan untuk mengatur dan merepresentasikan data dalam hubungan induk-anak .
Tree terdiri dari simpul-simpul, dengan simpul teratas disebut akar , dan setiap simpul lainnya dapat memiliki satu atau lebih simpul anak .

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

Pada perogram diatas kita harus mengimplementasikan Abstract Data Type (ADT) Binary Search Tree (BST),Kita membuat sebuah struct Node yang berisi data, pointer kekiri dan kanan. buat fungsi fungsi yaitu membuat_node,insert,search,nilai_terkecil,hapus,update,pre_order,in_order dan post_order

Lalu kita buat fungsi main nya kita buat root kosong lalu kita issert data dummy dan menjalankan semua fungsi yang ada

## Unguided

### Soal 1

```go
#include <iostream>
#include <string>

using namespace std;

typedef int infotype;

struct Node {
    infotype info;
    Node* left;
    Node* right;
};

typedef Node* address;


address alokasi(infotype x) {
    address newNode = new Node;
    newNode->info = x;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

void insertNode(infotype x, address& root) {
    if (root == NULL) {
        root = alokasi(x);
    }
    else if (x < root->info) {
        insertNode(x, root->left);
    }
    else if (x > root->info) {
        insertNode(x, root->right);
    }
}

address findNode(infotype x, address root) {
    if (root == NULL || root->info == x) {
        return root;
    } 
    else if (x < root->info) {
        return findNode(x, root->left);
    } 
    else { 
        return findNode(x, root->right);
    }
}

void printinorder(address root) {
    if (root != NULL) {
        printinorder(root->left);
        cout << root->info << " - ";
        printinorder(root->right);
    }
}

int main()
{
    cout << "Hello World!" << endl;
    
    address root = NULL;

    insertNode(1, root);
    insertNode(2, root);
    insertNode(6, root);
    insertNode(4, root);
    insertNode(5, root);
    insertNode(3, root);
    insertNode(7, root);
    printinorder(root); 
    cout << endl;

    return 0;
}
```

> Output
> ![output](output/un1.png)

Pada program di atas kita disuruh untuk membuat ADT Binary Search Tree menggunakan Linked list, buat struct Node verisi info, pointer ke kiri dan kanan. buat fungsi fungsinnya yaitu alokasi, insertNode,findNode dan printNode

lalu pada fungsi main kita tambahkan output "Hello World!" diawal serta inisiasi root, lalu tambahkan angka dummy agar sesuai dengan output yang diinginkan.

### Soal 2

```go
#include <iostream>
#include <algorithm> // Diperlukan untuk std::max

using namespace std;


typedef int infotype;

struct Node {
    infotype info;
    Node* left;
    Node* right;
};

typedef Node* address;


address alokasi(infotype x) {
    address newNode = new Node;
    newNode->info = x;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

void insertNode(infotype x, address& root) {
    if (root == NULL) {
        root = alokasi(x);
    }
    else if (x < root->info) {
        insertNode(x, root->left);
    }
    else if (x > root->info) {
        insertNode(x, root->right);
    }
}

address findNode(infotype x, address root) {
    if (root == NULL || root->info == x) {
        return root;
    } 
    else if (x < root->info) {
        return findNode(x, root->left);
    } 
    else {
        return findNode(x, root->right);
    }
}

void InOrder(address root) {
    if (root != NULL) {
        InOrder(root->left);
        cout << root->info << " - ";
        InOrder(root->right);
    }
}


// Mengembalikan banyak node yang ada di dalam BST
int hitungNode(address root) {
    if (root == NULL) {
        return 0;
    }
    return hitungNode(root->left) + hitungNode(root->right) + 1;
}

// Mengembalikan jumlah (total) info dari node-node yang ada di dalam BST
int hitungTotalInfo(address root) {
    if (root == NULL) {
        return 0;
    }
    return hitungTotalInfo(root->left) + hitungTotalInfo(root->right) + root->info;
}

// Mengembalikan kedalaman maksimal (tinggi) dari binary tree
int hitungKedalaman(address root) {
    if (root == NULL) {
        return 0;
    }
    
    int kedalamanKiri = hitungKedalaman(root->left);
    int kedalamanKanan = hitungKedalaman(root->right);
    
    // Menggunakan std::max dari <algorithm>
    return max(kedalamanKiri, kedalamanKanan) + 1;
}



int main()
{
    cout << "Hello world!" << endl;
    
    address root = NULL;

    insertNode(1, root);
    insertNode(2, root);
    insertNode(6, root);
    insertNode(4, root);
    insertNode(5, root);
    insertNode(3, root);
    insertNode(6, root); 
    insertNode(7, root);

    InOrder(root); 
    cout << "\n";

    cout << "kedalaman : " << hitungKedalaman(root) << endl; 
    cout << "jumlah node : " << hitungNode(root) << endl;
    cout << "total : " << hitungTotalInfo(root) << endl;


    return 0;
}
```

> Output
> ![output](output/un2.png)

Pada program di atas kita disuruh untuk membuat fungsi untuk menghitung jumlah node, buat struct Node berisi info,pointer kekiri dan kanan.uat fungsi fungsinnya yaitu alokasi, insertNode,findNode, InOrder, hitungNode, hitungTotalInfo, hitungKedalaman

lalu pada fungsi main kita tambahkan output "Hello World!" diawal serta inisiasi root, lalu tambahkan angka dummy agar sesuai dengan output yang diinginkan. Untuk kode ini kita tampilkan juga kedalaman, jumlah node dan total infonya

### Soal 3

```go
#include <iostream>
#include <algorithm> // Diperlukan untuk std::max

using namespace std;


typedef int infotype;

struct Node {
    infotype info;
    Node* left;
    Node* right;
};

typedef Node* address;


address alokasi(infotype x) {
    address newNode = new Node;
    newNode->info = x;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

void insertNode(infotype x, address& root) {
    if (root == NULL) {
        root = alokasi(x);
    }
    else if (x < root->info) {
        insertNode(x, root->left);
    }
    else if (x > root->info) {
        insertNode(x, root->right);
    }
}


// Mengembalikan kedalaman maksimal (tinggi) dari binary tree
int hitungKedalaman(address root) {
    if (root == NULL) {
        return 0;
    }
    int kedalamanKiri = hitungKedalaman(root->left);
    int kedalamanKanan = hitungKedalaman(root->right);
    return max(kedalamanKiri, kedalamanKanan) + 1;
}

// Mengembalikan banyak node yang ada di dalam BST
int hitungNode(address root) {
    if (root == NULL) {
        return 0;
    }
    return hitungNode(root->left) + hitungNode(root->right) + 1;
}

// Mengembalikan total info dari node-node yang ada di dalam BST
int hitungTotalInfo(address root) {
    if (root == NULL) {
        return 0;
    }
    return hitungTotalInfo(root->left) + hitungTotalInfo(root->right) + root->info;
}


// Urutan: Kiri -> Root -> Kanan
void InOrder(address root) {
    if (root != NULL) {
        InOrder(root->left);
        cout << root->info << " - ";
        InOrder(root->right);
    }
}

// Urutan: Root -> Kiri -> Kanan
void PreOrder(address root) {
    if (root != NULL) {
        cout << root->info << " - "; 
        PreOrder(root->left);        
        PreOrder(root->right);       
    }
}

// Urutan: Kiri -> Kanan -> Root
void PostOrder(address root) {
    if (root != NULL) {
        PostOrder(root->left);       
        PostOrder(root->right);      
        cout << root->info << " - "; 
    }
}


int main()
{
    cout << "Hello world!" << endl;
    
    address root = NULL;

    insertNode(1, root);
    insertNode(2, root);
    insertNode(6, root);
    insertNode(4, root);
    insertNode(5, root);
    insertNode(3, root);
    insertNode(7, root); // 6 diabaikan karena duplikat


    cout << "\n--- Traversal ---" << endl;
    
    cout << "InOrder  : ";
    InOrder(root); 
    cout << endl;

    cout << "PreOrder : ";
    PreOrder(root);
    cout << endl;
    
    cout << "PostOrder: ";
    PostOrder(root);
    cout << "\n" << endl;


    cout << "kedalaman : " << hitungKedalaman(root) << endl; 
    cout << "jumlah node : " << hitungNode(root) << endl;
    cout << "total : " << hitungTotalInfo(root) << endl;

    return 0;
}
```

> Output
> ![output](output/un3.png)

Program diatas persis seperti program sebeliumnya hanya kita harus menambahkan print tree secara pre-order dan post-order. Fungsi tambahan yaitu PreOrder dan PostOrder dengan urutan root->kiri->kanan.

fungsi tersebut kita panggil pada fungsi mainnya.

## Referensi

1.https://www.geeksforgeeks.org/dsa/introduction-to-tree-data-structure/ (diakses 8/12/2025)
