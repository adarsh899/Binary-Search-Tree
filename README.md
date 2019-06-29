# Binary-Search-Tree 
insertion and traversal
#include <stdio.h>
#include <stdlib.h>
struct node
{
    int data;
    struct node *left,*right;
};
struct node *insert(struct node *head,int n);
void postorder(struct node *root);
int main()
{
    struct node *head = NULL;
int i,d,no;
scanf("%d",&no);
for(i=0;i<no;i++)
{
 scanf("%d",&d);
    head = insert(head,d);
}
postorder(head);
    return 0;
}
struct node *insert(struct node *head,int n)
{
    if(head == NULL)
{
    head=(struct node *)malloc(sizeof(struct node));

    head->data=n;
    head->left=NULL;
    head->right=NULL;
}else
{
if(n < head->data)
{
    head->left = insert(head->left,n);
}
else if(n>head->data)
    {
    head->right = insert(head->right,n);
}
}
return head;
}
void postorder(struct node *root)
{
    if(root)
    {
        postorder(root->left);
        postorder(root->right);
        printf("%d",root->data);
    }
}
