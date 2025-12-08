# <h1 align="center">Laporan Praktikum Modul 13 <br> Multi Linked List</h1>
<p align="center">DENNA WAHYU SETYOBUDI - 103112430206</p>

## Dasar Teori

Pada materi ini menjelaskan tentang Multi Linked List. Multi Linked List adalah Multi linked list adalah jenis list khusus yang berisi dua atau lebih rangkaian kunci logis. Dalam daftar multi-link, setiap simpul dapat memiliki N pointer ke simpul lain. Daftar multi-link umumnya digunakan untuk mengatur beberapa urutan elemen dalam satu set.
## Guided

### soal 1

```go
#include <iostream>
#include <string>
using namespace std;

struct ChildNode
{
    string info;
    ChildNode *next;
};

struct ParentNode
{
    string info;
    ChildNode *childHead;
    ParentNode *next;
};

ParentNode *createParent(string info)
{
    ParentNode *newNode = new ParentNode;
    newNode->info = info;
    newNode->childHead = NULL;
    newNode->next = NULL;
    return newNode;
}

ChildNode *createChild(string info)
{
    ChildNode *newNode = new ChildNode;
    newNode->info = info;
    newNode->next = NULL;
    return newNode;
}

void insertParent(ParentNode *&head, string info)
{
    ParentNode *newNode = createParent(info);
    if (head == NULL)
    {
        head = newNode;
    }
    else
    {
        ParentNode *temp = head;
        while (temp->next != NULL)
        {
            temp = temp->next;
        }
        temp->next = newNode;
    }
}

void insertChild(ParentNode *head, string parentInfo, string childInfo)
{
    ParentNode *p = head;
    while (p != NULL && p->info != parentInfo)
    {
        p = p->next;
    }

    if (p != NULL)
    {
        ChildNode *newChild = createChild(childInfo);
        if (p->childHead == NULL)
        {
            p->childHead = newChild;
        }
        else 
        {
            ChildNode *c = p->childHead;
            while (c->next != NULL)
            {
                c = c->next;
            }
            c->next = newChild;
        }
    }
}

void printAll(ParentNode *head)
{
    ParentNode *p = head;
    while (p != NULL)
    {
        cout << p->info;
        ChildNode *c = p->childHead;
        if (c != NULL)
        {
            while (c != NULL)
            {
                cout << " -> " << c->info;
                c = c->next;
            }
        }
        cout << endl;
        p = p->next;
    }
}

int main()
{
    ParentNode *list = NULL;

    insertParent(list, "Parent Node 1");
    insertParent(list, "Parent Node 2");

    insertChild(list, "Parent Node 1", "Child Node A");
    insertChild(list, "Parent Node 1", "Child Node B");
    insertChild(list, "Parent Node 2", "Child Node C");

    printAll(list);

    return 0;
}
```
> Output
> ![output](output/g1.png)

Pada perogram diatas kita membuat sebuah implementasi Multi Linked List, buat struct ChildNode berisi string info dan pointer next, serta buat struct ParentNode berisi string info, pointer ke childHead sebagai anak pertama dan pointer next. Kita buat fungsi fungsinya yaitu createParent, createChild, insertParent,insertChild, printAll

Lalu kita buat fungsi main nya kita buat list kososng setelahnya kita masukan data dummy 

## Unguided

### Soal 1

```go

```

> Output
> ![output](output/un1.png)



## Referensi

1.https://www.geeksforgeeks.org/dsa/introduction-to-multi-linked-list/ (diakses 8/12/2025)
