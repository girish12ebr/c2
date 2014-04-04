#include<stdio.h>
struct node
{
	int data;
	struct node *next;
};
typedef struct node node;
node *start;
node *getnode();
void add();
void add_beg(node *);
void add_end(node *);
void add_bet(node *);
void del();
void del_beg();
void del_end();
void del_bet();
void rev();
void linsearch();
void disp();
main()
{
	start=NULL;
	int ch;
	while(1)
	{
		printf("1.add 2.del 3.disp 4.rev 5.linsearch 6.exit\n");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:add();break;
			case 2:del();break;
			case 3:disp();break;
			case 4:rev();break;
			case 5:linsearch();break;
			case 6:exit(0);
		}
	}
}
void add()
{
	node *newnode;
	int ch;
	while(1)
	{
		printf("1.add_beg 2.add_end 3.add_bet 4.return\n");
		scanf("%d",&ch);
		if(ch==1||ch==2||ch==3)
		{
			newnode=getnode();
		}
		switch(ch)
		{
			case 1:add_beg(newnode);break;
			case 2:add_end(newnode);break;
			case 3:add_bet(newnode);break;
			case 4:return;
		}
	}
}
node *getnode()
{
	node *temp;
	temp=(node *)malloc(sizeof(node));
	if(temp==NULL)
	{
		printf("DMA is failed\n");
		exit(1);
	}
	printf("enter the data\n");
	scanf("%d",&temp->data);
	temp->next=NULL;
	return temp;
}
void add_beg(node *nn)
{
	if(start==NULL)
	{
		start=nn;
		return;
	}
	nn->next=start;
	start=nn;
}
void add_end(node *nn)
{
	node *temp=start;
	if(start==NULL)
	{
		start=nn;
		return;
	}
	while(temp->next!=NULL)
	{
		temp=temp->next;
	}
	temp->next=nn;
}

void add_bet(node *nn)
{
	int i,pos;
	node *temp1=start,*temp2;
	if(start==NULL)
	{
		start=nn;
		return;
	}
	printf("enter the pos\n");
	scanf("%d",&pos);
	for(i=0;i<pos;i++)
	{
		temp2=temp1;
		temp1=temp1->next;
	}
	temp2->next=nn;
	nn->next=temp1;
}	
void del()
{
	int ch;
	while(1)
	{
		printf("1.del_beg 2.del_end 3.del_bet 4.return\n");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:del_beg();break;
			case 2:del_end();break;
			case 3:del_bet();break;
			case 4:return;
		}
	}
}
void del_beg()
{
	node *temp=start;
	if(start==NULL)
	{
		printf("linked list is empty\n");
		return;
	}
	start=start->next;
	free(temp);
}
void del_end()
{
	node *temp1=start;
	node *temp2;
	if(start==NULL)
	{
		printf("linked list is empty\n");
		return;
	}
	while(temp1->next!=NULL)
	{
		temp2=temp1;
		temp1=temp1->next;
	}
	temp2->next=NULL;
	free(temp1);
}

void del_bet()
{
	int pos,i;
	node *temp1=start,*temp2;
	if(start==NULL)
	{
		printf("linked list is empty\n");
		return;
	}
	printf("enter the pos\n");
	scanf("%d",&pos);
	for(i=0;i<pos;i++)
	{
		temp2=temp1;
		temp1=temp1->next;
	}
	temp2->next=temp1->next;
	free(temp1);
	
}
void rev()
{
	node *temp1=start,*temp2=NULL;
	while(temp1!=NULL)
	{
		start=start->next;
		temp1->next=temp2;
		temp2=temp1;
		temp1=start;
	}
	start=temp2;
		
	
}
void linsearch()
{
	node *temp;
	int i=0,srch,flag=0;
	printf("enter the element 2 b searched\n");
	scanf("%d",&srch);
	 for(temp=start;temp!=NULL;temp=temp->next,i++)
	 {
		 if(temp->data==srch)
		 {
			 flag=1;
			 printf("%d is found at %d position\n",srch,i);
			 break;
		 }
	 }

	 if(flag==0)
	 {
		 printf("%d is not found\n",srch);
	 }
	 
	 
}

		 
	

	
void disp()
{
	node *temp=start;
	if(start==NULL)
	{
		printf("empty\n");
		return;
	}
	while(temp!=NULL)
	{
		printf("%d\n",temp->data);
		temp=temp->next;
	}
}









