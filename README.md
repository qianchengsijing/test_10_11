# test_10_11
#include <stdio.h>
//线索二叉树
//中序线索二叉树
typedef struct BiTNode{
	int data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;

BiTNode* Pre = NULL;
BiTNode* p;
BiTNode* final = NULL;

void PreOrder(BiTree T){
	if(T != NULL){
		PreOrder(T->lchild);
		visit(T);
		PreOrder(T->rchild);
	}
}
void visit(BiTNode* q){
	if(q == p)
		final = Pre;
	else
		Pre = q;
}

typedef struct ThreadNode{
	int data;
	struct ThreadNode *lchild,*rchild;
	int ltag,rtag;
}ThreadNode,*ThreadTree;

void CreatInTread(ThreadTree T){
	Pre = NULL;
	if(T != NULL){
		InThread(T);
		if(Pre->rchild == NULL){
			Pre->rtag = 1;
		}
	}
}

void InThread(ThreadTree T){
	if(T != NULL){
		InThread(T->lchild);
		visit(T);
		InThread(T->rchild);
	}
}

void visit(ThreadNode *q){
	if(q->lchild == NULL){
		q->lchild = Pre;
		q->ltag = 1;
	}
	if(Pre != NULL && Pre->rchild == NULL){
		Pre->rchild = q;
		Pre->rtag = 1;
	}
	Pre = q;
}
//王道书教材版
void InThread(ThreadTree p,ThreadTree &Pre){
	if(p != NULL){
		InThread(p->lchild,Pre);
		if(q->lchild == NULL){
		q->lchild = Pre;
		q->ltag = 1;
	}
	    if(Pre != NULL && Pre->rchild == NULL){
		Pre->rchild = q;
		Pre->rtag = 1;
	}
	Pre = q;
	InThread(p->rchild,Pre);
	}
}
