#include<iostream>
using namespace std;
struct node
{
    int data;
    struct node *next;
};
void insert_node(struct node ** head,int val,int pos)
{
    struct node* curr = *head,*newNode = NULL;
    
    newNode = (struct node*)malloc(sizeof(node));
      if (newNode == NULL) {
        printf("Memory allocation is failed:");
        return;
    }
    
    int count=1;
    newNode->data = val;
    newNode->next = NULL;
    //count+=1;
      
    if(*head==NULL)
    {
        *head=newNode;
        return;
    }
    if(pos==1)
    {
        newNode->next=*head;
        *head=newNode;
        //count+=1;
        return;
    }
        while(curr && count<pos-1)
        {
            curr = curr->next;
            count=count+1;
        }
        if (count + 1 == pos && curr->next == NULL) {
        // Inseting node at the end of the list
        curr->next = newNode;
        return;
    }
        newNode->next = curr->next;
        curr->next = newNode;
    
    
}
void print(struct node*head)
{
    if(head==NULL)
    return;
    struct node*temp=head;
    while(temp!=NULL)
    {
        printf("%d ",temp->data);
        temp=temp->next;
    }
}
int main()
{
   struct node *head = NULL;
   int n,pos,val;
   printf("Enter the number of elements you want to insert");
   scanf("%d",&n);
   for(int i=1;i<=n;i++)
   {
       printf("insert the element at %d position",i);
       scanf("%d",&val);
       insert_node(&head,val,i);
   }
   print(head);
}
