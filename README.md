# Code-decode
# We see here a large number of code which are useful and help to understand the programs
#include<iostream>
using namespace std;
class node
{
 public:
   int data;
   node *next;
};

class linked
{
  private:
      node* start;
  public:
    linked();                            //CONSTRUCTOR
    int coun();
    void traverse();
    void addafter(int,int);
    void addbefore(int,int);
    void addlast(int);
    void addfirst(int);

};

linked::linked()
{
    start=NULL;
}

int linked::coun()
{
    int cnt=0;
    node* ptr=start;
    while(ptr->next!=NULL)
    {
        cnt++;
        ptr=ptr->next;
    }
 return cnt;
}

void linked:: traverse()
{
    node* ptr=start;
    while(ptr!=NULL)
    {
        cout<<ptr->data<<" ";
        ptr=ptr->next;
    }

}

void linked::addafter(int item,int num)
{
    node* newnode;
    node *ptr;
    ptr=start;
    newnode=new node();
    if(newnode==NULL)
    {
        cout<<"overflow";
        return;
    }
    while(ptr!=NULL && ptr->data!=num)
    {
        ptr=ptr->next;
    }
   
    if(ptr==NULL)
    {
        cout<<"number not found";
        return;
    }
    else
    {
      newnode->data=item;
      newnode->next=ptr->next;
      ptr->next=newnode;
      return;
    }
}

void linked:: addbefore(int item,int num)
{
    node* newnode;
    node* ptr;
    node* pre;
    newnode=new node();
    if(newnode==NULL)
    {
        cout<<"OVERFLOW";
        return;
    }
    ptr=start;
    pre=NULL;
    while(ptr!=NULL &&ptr->data!=num)
    {
        pre=ptr;
        ptr=ptr->next;
    }
    newnode->data=item;
    if(ptr==NULL)
    {
        newnode->next=NULL;
        start=newnode;
        return;
    }
   else
   {
    newnode->next=pre->next;
    pre->next=newnode;
   }
 return;
}

void linked::addfirst(int item)
{
    node* newnode;
    newnode=new node();
    if(newnode==NULL)
    {
        cout<<"OVERFLOW";
        return;
    }
    newnode->data=item;
    newnode->next=start;
    start=newnode;
 return;
}

void linked::addlast(int item)
{
    node* newnode;
    node* ptr=start;
    newnode=new node();
    if(newnode==NULL)
    {
        cout<<"OVERFLOW";
        return;
    }
    newnode->data=item;
    newnode->next=NULL;
    if(ptr==NULL)
    {
        start=newnode;
        return;
    }
    else
    {
      while(ptr->next!=NULL)
       {
          ptr=ptr->next;
       }
    
       ptr->next=newnode;
      return;
    }
}
int main()
{
    int item,num,ch;
   linked l1;
   cout<<"\n"<<"Enter your Choice";
   do
   {
       cout<<"press 1:- traverse:"<<endl;
       cout<<"press 2:- addafter:"<<endl;
       cout<<"press 3:- addbefore:"<<endl;
       cout<<"press 4:- addlast:"<<endl;
       cout<<"press 5:- addfirst:"<<endl;
       cout<<"press 6:- count:"<<endl;
       cout<<"Enter your choice:";
       cin>>ch;
       switch(ch)
       {
         case 1:
              l1.traverse();
              break;
         case 2:
              cout<<"enter item and num";
              cin>>item;
              cin>>num;
              l1.addafter(item,num);
              break;
         case 3:
             cout<<"enter item and num";
             cin>>item;
             cin>>num;
            l1.addbefore(item,num);
            break;
         case 4:
            cout<<"enter item";
            cin>>item;
            l1.addlast(item);
            break;
         case 5:
            cout<<"enter item ";
            cin>>item;
            l1.addfirst(item);
            break;
         case 6:
            cout<<l1.coun();
            break;
         case 7:
            break;
         default:
             cout<<"invalid input";
         }
       }while(ch!=7);
return 0;
};
