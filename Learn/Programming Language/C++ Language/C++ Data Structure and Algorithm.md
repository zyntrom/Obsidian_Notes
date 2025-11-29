- Linked List:

```cpp
#include<iostream> 
using namespace std;
struct Node{
	int data;
	Node* next=nullptr;
};
void insertData(Node*& head,int value){
	Node* newNode= new Node();
	newNode->data=value;
	newNode->next=nullptr;
	if(head==nullptr){
		head=newNode;
	}
	else{
		Node* curr=head;
		while(curr->next!=nullptr){
			curr=curr->next;
		}
		curr->next=newNode;
	}
}
void print(Node*& head){
	Node* curr=head;
	while(curr!=nullptr){
		cout<<curr->data<<" ";
	}
	cout<<endl;
}

int main(){
	Node* list=NULL;
	insertData(list, 20);
	insertData(list, 2);
	insertData(list, 67);
	insertData(list, 98);
	print(list);
	return 0;
}
```

- Doubly LinkedList:

```cpp
#include <iostream>
using namespace std;

struct Node{
	int data;
	Node* next;
	Node* prev;
};
void add(Node*& head,int value){
	Node* newNode  =new Node();
	newNode->next=NULL;
	newNode->prev=NULL;
	newNode->data=value;	
	if(head==NULL){
		head=newNode;
	}
	else{
		Node* curr=head;
		while(curr->next!=NULL){
			curr=curr->next;
		}
		curr->next=newNode;
		newNode->prev=curr;
	}
}
void printFr(Node* head){
	Node* curr=head;
	while(curr!=NULL){
		cout<<curr->data<<" ";
		curr=curr->next
	}
	cout<<endl;
}
void printBa(Node* head){
	Node* curr=head;
	if(head==NULL){return;}
	while(curr->next!=NULL){
		curr=curr->next;
	}
	while(curr!=NULL){
		cout<<curr->data<<" ";
		curr=curr->prev;
	}
	cout<<endl;
}

int main(){
	Node* list=NULL;
	add(list,30);
	add(list,87);
	add(list,8967);
	add(list,9876);
	add(list,234);
	printFr(list);
	printBa(list);
	return 0;
}
```