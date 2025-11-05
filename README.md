#include <stdio.h>
#include<stdlib.h>
void insertbeg();
void display();
void insertrandom();
struct Node{
    int data;
    struct Node *next;
};
struct Node *start = NULL;
int main()
{
    int choice,value;
    while(1){
        printf("\n Linked List Operation:\n");
        printf("1. Insert Beg\n");
        printf("2. Insert random\n");
        printf("3. Insert last\n");
        printf("4. Delete beg\n");
        printf("5. Delete random\n");
        printf("6. Delete last\n");
        printf("7. Search \n");
        printf("8. Display\n");
        printf("9. Exit\n");
        printf("Enter your choice\n");
        scanf("%d",&choice);
        switch(choice){
            case 1:
                // printf("Enter the value ");
                // scanf("%d",&value);
                insertbeg();
                break;
            case 2:
                insertrandom();
                break;
            case 3:
                //insertlast();
                break;
            case 4:
                //deletebeg();
                break;
            case 5:
                //deleterandom();
                break;
            case 6:
                //deletelast();
                break;
            case 7:
                //search();
                break;
            case 8:
                display();
                break;
            case 9:
                exit(0);
                break;
                
            default:
                printf("invalid choice , try again\n");
        }
    }
    return 0;
}
void insertbeg(){
    int item;
    struct Node *ptr;
ptr = (struct Node *)malloc(sizeof(struct Node));
    if(ptr==NULL){
        printf("Memory overflow\n");
        return;
    }
    printf("Enter valur to insert at beginning:");
    scanf("%d",&item);
    ptr->data = item;
    ptr->next = start;
    start = ptr;
    printf("Node inserted at beginning.\n");
}
void display(){
    struct Node *temp = start;
    if(start==NULL){
        printf("List is empty.\n");
        return;
    }
    printf("Linked List:");
    while(temp!=NULL){
        printf("%d -> ",temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}
void insertrandom(){
    int item,pos;
    printf("Enter value to insert:");
    scanf("%d",&item);
    printf("Enter position to insert (starting from 1):");
    scanf("%d",&pos);
    
    struct Node *ptr;
    ptr = (struct Node *)malloc(sizeof(struct Node));
    ptr->data = item;
    
    if(pos==1){
        ptr->next = start;
        start = ptr;
    }else{
        struct Node *temp = start;
        for(int i=1;i<pos-1 && temp!=NULL;i++){
            temp = temp->next;
        }
        
        if(temp==NULL){
            printf("position out of bounds\n");
            free(ptr);
            return;
        }
        ptr->next = temp->next;
        temp->next = ptr;
    }
    printf("Node inseted at position%d.\n",pos);
}
