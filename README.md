"""Binarno pretrazivanje pokazivaci"""

#include<iostream>
using namespace std;

struct BstNode {
	int d;
	BstNode* levo;
	BstNode* desno;
};


BstNode* Novo_stablo(int d) {
	BstNode* newNode = new BstNode();
	newNode->d = d;
	newNode->levo = newNode->desno = NULL;
	return newNode;
}


BstNode* Unosenje(BstNode* koren,int d) {
	if(koren == NULL) {
		koren = Novo_stablo(d);
	}

	else if(d <= koren->d) {
		koren->levo = Unosenje(koren->levo,d);
	}
	else {
		koren->desno = Unosenje(koren->desno,d);
	}
	return koren;
}
bool Pretraga(BstNode* koren,int d) {
	if(koren == NULL) {
		return false;
	}
	else if(koren->d == d) {
		return true;
	}
	else if(d <= koren->d) {
		return Pretraga(koren->desno,d);
	}
	else {
		return Pretraga(koren->desno,d);
	}
}
int main() {
	BstNode* koren = NULL;

	koren = Unosenje(koren,15);
	koren = Unosenje(koren,10);
	koren = Unosenje(koren,20);
	koren = Unosenje(koren,25);
	koren = Unosenje(koren,8);
	koren = Unosenje(koren,12);

	int n;
	cout<<"Uneti zeljeni broj za pretrazivanje"<<endl;
	cin>>n;

	if(Pretraga(koren,n) == true) cout<<"Broj postoji."<< endl;
	else cout<<"Broj ne postoji." <<endl;
}
  
"""2NZD sa nizom"""
  
#include<iostream>
using namespace std;

// Function to return gcd of a and b
int gcd(int a, int b)
{
	if (a == 0)
		return b;
	cout << a << endl;
	cout << b<<endl;
	return gcd(b%a, a);
}

// Function to find gcd of array of
// numbers
int findGCD(int arr[], int n)
{
	
	int result = arr[0];
	for (int i = 1; i<n; i++)
		result = gcd(arr[i], result);

	return result;
}

// Driven code
int main()
{
	int n;
	cout << "Uneti broj clanova niza: ";
	cin >> n;
	int arr[100];
	int i;
	cout << "Uneti clanove niza: ";
	for (i = 0; i < n; i++)
	{
		cin >> arr[i];
	}

	findGCD(arr, n);
	cout << "nzd je " << findGCD(arr,n);
	return 0;
  }
  
"""Preorder Inorder Postorder"""
  
#include<iostream>
#include<stdio.h>
using namespace std;

struct Node {
	char d;
	struct Node *levo;
	struct Node *desno;
};

void Preorder(struct Node *koren) {

	if(koren == NULL) return;

	printf("%c ",koren->d);
	Preorder(koren->levo);
	Preorder(koren->desno);
}

void Inorder(Node *koren) {
	if(koren == NULL) return;
	Inorder(koren->levo);
	printf("%c ",koren->d);
	Inorder(koren->desno);
}

void Postorder(Node *koren) {
	if(koren == NULL) return;

	Postorder(koren->levo);
	Postorder(koren->desno);
	printf("%c ",koren->d);
}

Node* Insert(Node *koren,char d) {
	if(koren == NULL) {
		koren = new Node();
		koren->d = d;
		koren->levo = koren->desno = NULL;
	}
	else if(d <= koren->d)
		koren->levo = Insert(koren->levo,d);
	else
		koren->desno = Insert(koren->desno,d);
	return koren;
}

int main() {
	/*
                M
			   / \
			  B   Q
			 / \   \
			A   C   Z
    */
	Node* koren = NULL;
	koren = Insert(koren,'C'); koren = Insert(koren,'F');koren = Insert(koren,'E');
	koren = Insert(koren,'B'); koren = Insert(koren,'D');koren = Insert(koren,'G');
	koren = Insert(koren,'A'); koren = Insert(koren,'H');koren = Insert(koren,'J');
	cout<<"Preorder: ";
	Preorder(koren);
	cout<<endl;
	cout<<"Inorder: ";
	Inorder(koren);
	cout<<endl;
	cout<<"Postorder: ";
	Postorder(koren);
	cout<<endl;
}
  
"""Stabla ogledala"""
  
#include <iostream>
#include <stdio.h>
#include <stdlib.h>

struct node
{
	int data;
	struct node* left;
	struct node* right;
};

struct node* newNode(int data)

{
struct node* node = (struct node*)
					malloc(sizeof(struct node));
node->data = data;
node->left = NULL;
node->right = NULL;

return(node);
}

void mirror(struct node* node)
{
if (node==NULL)
	return;
else
{
	struct node* temp;


	mirror(node->left);
	mirror(node->right);


	temp	 = node->left;
	node->left = node->right;
	node->right = temp;
}
}
void inOrder(struct node* node)
{
if (node == NULL)
	return;

inOrder(node->left);
printf("%d ", node->data);

inOrder(node->right);
}



int main()
{
struct node *root = newNode(1);
root->left	 = newNode(2);
root->right	 = newNode(3);
root->left->left = newNode(4);
root->left->right = newNode(5);

printf("\n Stablo je \n");
inOrder(root);


mirror(root);


printf("\n Stablo u ogledalu je \n");
inOrder(root);

getchar();
return 0;
}
  
"""drugi zadatak"""
  
#include<stdio.h>
#include<stdlib.h>
 

struct Node 
{
    int data;
    struct Node* left;
    struct Node* right;
};
 

struct Node* newNode(int data)
 
{
  struct Node* node = (struct Node*)
                       malloc(sizeof(struct Node));
  node->data = data;
  node->left = NULL;
  node->right = NULL;
   
  return(node);
}
 
 

 

void mirror(struct Node* node) 
{
  if (node==NULL) 
    return;  
  else
  {
    struct Node* temp;
     
    
    mirror(node->left);
    mirror(node->right);
 
    
    temp        = node->left;
    node->left  = node->right;
    node->right = temp;
  }
} 
 

void inOrder(struct Node* node) 
{
  if (node == NULL) 
    return;
   
  inOrder(node->left);
  printf("%d ", node->data);
  inOrder(node->right);
}  
 
 

int main()
{
  struct Node *root = newNode(1);
  root->left        = newNode(2);
  root->right       = newNode(3);
  root->left->left  = newNode(4);
  root->left->right = newNode(5); 
   
  
  printf("pocetno binarno stablo je "
           " \n");
  inOrder(root);
   
  
  mirror(root); 
   
  
  printf("\n Binarno stablo u ogledalu je"
         "  \n");  
  inOrder(root);
   
  return 0;  
}
  
"""ino post pre sa slovima"""
  
# include <stdio.h>
# include <conio.h>
# include <stdlib.h>
#include <map>
#include <string>

using namespace std;

typedef struct BST {
	char data;
	struct BST *lchild, *rchild;
} node;

void insert(node *, node *);
void inorder(node *);
void preorder(node *);
void postorder(node *);

map<char, int> mapa;

void main() {

	mapa['A'] = 3;
	mapa['B'] = 2;
	mapa['C'] = 1;
	mapa['D'] = 6;
	mapa['E'] = 4;
	mapa['F'] = 8;
	mapa['G'] = 5;
	mapa['H'] = 7;
	mapa['I'] = 9;


	//printf(" %d", mapa.find("A")->second);

	node *new_node, *root, *tmp, *parent;
	node *get_node();
	root = NULL;

	printf("\n\n_____________________________\n");

	map<char, int>::iterator i;

	for (i = mapa.begin(); i != mapa.end(); i++) {
		new_node = get_node();
		new_node->data = i->first;
		if (root == NULL){
			root = new_node;
		}
		else
		{
			insert(root, new_node);
		}
	}
	printf("Radjeno sa mapom\n\n");

	printf("\n\nSortiranje PREORDER:\n\n");
	preorder(root);

	printf("\n\n\nSortiranje INORDER:\n\n");
	inorder(root);

	printf("\n\n\nSortiranje POSTORDER:\n\n");
	postorder(root);

	printf("\n\n\n");
	system("pause");
}
/*
Kreiranje novog cvora
*/
node *get_node() {
	node *temp;
	temp = (node *)malloc(sizeof(node));
	temp->lchild = NULL;
	temp->rchild = NULL;
	return temp;
}
/*
Ova funkcija ubacuje nove cvorove u stablu
*/
void insert(node *root, node *new_node) {
	if (mapa.find(new_node->data)->second < mapa.find(root->data)->second) {
		if (root->lchild == NULL)
			root->lchild = new_node;
		else
			insert(root->lchild, new_node);
	}

	if (mapa.find(new_node->data)->second > mapa.find(root->data)->second) {
		if (root->rchild == NULL)
			root->rchild = new_node;
		else
			insert(root->rchild, new_node);
	}
}

/*
Ova funkcija obilazi stablo po INORDER principu
*/
void inorder(node *temp) {
	if (temp != NULL) {
		inorder(temp->lchild);
		printf(" %c,", temp->data);
		inorder(temp->rchild);
	}
}
/*
Ova funkcija obilazi stablo po PREORDER principu
*/
void preorder(node *temp) {
	if (temp != NULL) {
		printf(" %c,", temp->data);
		preorder(temp->lchild);
		preorder(temp->rchild);
	}
}

/*
Ova funkcija obilazi stablo po POSTORDER principu
*/
void postorder(node *temp) {
	if (temp != NULL) {
		postorder(temp->lchild);
		postorder(temp->rchild);
		printf(" %c,", temp->data);
	}
}
