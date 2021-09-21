# removing-duplicate-element-from-linked-list-by-brute-force-method-in-C

#include <stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node *next;
};// 1 2 3 2 1 6

struct node* duplicate(struct node *head)
{
    struct node *ptr1 , *ptr2 , *dup;
    ptr1=head;
    
    while(ptr1->next!=NULL ){
        ptr2=ptr1;
        
        while(ptr2->next!=NULL){
            if(ptr1->data == ptr2->next->data){
                dup=ptr2->next;
                ptr2->next=ptr2->next->next;
                free(dup);
                
                
            }
            else
            ptr2=ptr2->next;
            
        }
        ptr1=ptr1->next;
    }
    
}





void disp(struct node *ptr){
        while(ptr!=NULL){
        printf("%d",ptr->data);
        ptr=ptr->next;
        
    }
}



int main()
{
    struct node *head , *first , *second , *third , *fourth , *fifth;
    head = (struct node*) malloc(sizeof(struct node));
    first = (struct node*) malloc(sizeof(struct node));
    second = (struct node*) malloc(sizeof(struct node));
    third = (struct node*) malloc(sizeof(struct node));
    fourth = (struct node*) malloc(sizeof(struct node));
    fifth = (struct node*) malloc(sizeof(struct node));
    
    head->data=1;
    head->next=first;
    
    first->data=2;
    first->next=second;
    
    second->data=3;
    second->next=third;
    
    third->data=2;
    third->next=fourth;
    
    fourth->data=1;
    fourth->next=fifth;
    
    fifth->data=6;
    fifth->next=NULL;
    
    duplicate(head);
    disp(head);
    

    

    return 0;
}
