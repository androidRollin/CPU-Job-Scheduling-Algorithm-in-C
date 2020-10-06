#define DRAW_LINE printf("\n********************************************************************************")
#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <string.h>
#include <alloc.h>
#include <dos.h>
#include <graphics.h>
struct node
{
    struct node *prev;
    char name[20];
    int AT,CBT,P,inptnm;
    struct node *next;
}*h,*temp,*temp1,*temp2,*temp4,*gcurr;
struct node* glast=NULL;
struct node* groot=NULL;

struct GC
{
char name[20];
int dAT,burst,endt;
struct GC* link;
}*chart,*tmp1;
struct GC *gnttroot=NULL;

int num();
void PorNP();
void insert2();
void sort();
struct node* stopper();
void FCFS();
void SJF();
struct node* sjfcondi(struct node*);
void NPP();
struct node* nppcondi(struct node*);
void SRTF();
void shortsort(struct node*);
void PP();
void priosort(struct node*);
void RR(int);
void rrsort(struct node*);
void del(struct node*);
void Pins(struct GC*);
void Pmake(struct node*);
void ins(struct node*);
void make(struct node*);
void insIDLE (struct node*);
void IDLE(struct node*);
void gc(struct GC*);
void ttwt(struct GC*);
void Pttwt(struct GC*);
void restartvars();
void cpysrtnodes();

int count = 0;
int timen = 0;
int limi =0 ;
float final=0;
int numero=0;
char Pans=NULL,choice=NULL;

void restartvars(){
count = 0;
timen = 0;
limi =0 ;
final=0;
numero=0;
Pans=NULL;choice=NULL;
gnttroot=NULL;
h=NULL;
temp=NULL;temp1=NULL;temp2=NULL;temp4=NULL;chart=NULL;tmp1=NULL;
}
void HEADING(){
 int gd=DETECT,gm;
 clrscr();
 //PALITAN YUNG DESTINATION FOLDER KAPAG D GUMAGANA SA LAPTOP NIYO-ROLS//
 initgraph(&gd,&gm,"C:\\TURBOC3\\BGI");
 settextstyle(10,0,1);
 setcolor(YELLOW);
 outtextxy(190,200,"JOB SCHEDULING IN C");
 getch();
 closegraph();
}
void title()
{
flushall();
textbackground(BLACK);
textcolor(14);
printf("\n\n\n\n\t\t\t\t     ");
cprintf("CASE STUDY");
printf("\n\t\t\t   ");
textcolor(10+BLINK);
cprintf("JOB SCHEDULING ALGORITHMS IN C");
textcolor(14);
printf("\n\n\t\t\t\t\t ");
cprintf("BY");
printf("\n\t\t\t      ");
cprintf("AGUILAR, ROLINE JOHN  L.");
printf("\n\n\n\n\t\t       ");
textcolor(15+BLINK);
cprintf("*******Press Any Key to Continue******");
printf("\n");
textcolor(14);

}

void main()
{
char ans,rep;
clrscr();
HEADING();
title();
getch();
do
{
restartvars();
fflush(stdin);
clrscr();
printf("\t\t\t\t  ");
printf("JOB SCHEDULING");
errdetect:
printf("\n\nWith Priorities?[Y/N]:");
Pans=getche();
if(Pans!='y' && Pans !='Y' && Pans!='n' && Pans !='N')
 {
   clrscr();
   printf("Error: 'Y','y','n',and 'N' are the only keys available..\n");
   goto errdetect;
 }
 do
  {
  clrscr();
  printf("\t\t\t\t  ");
  printf("JOB SCHEDULING");
  insert2();
  errdetect1:
  printf("\nAnother Job?[y/n]: ");
  ans=getch();
  if(ans!='y' && ans !='Y' && ans!='n' && ans !='N')
  {
   clrscr();
   printf("Error: 'Y','y','n',and 'N' are the only keys available..\n");
   goto errdetect1;
  }
  clrscr();
  }while(ans=='y'||ans=='Y');
sort();
cpysrtnodes();
PorNP();
errdetect2:
printf("\n\nInput Again Another set of Job?[Y/N]:");
rep=getche();
  if(rep!='y' && rep !='Y' && rep!='n' && rep !='N')
  {
   clrscr();
   printf("Error: 'Y','y','n',and 'N' are the only keys available..\n");
   goto errdetect2;
  }
clrscr();
}while(rep=='y'||rep=='Y');
if(rep=='n'||rep=='N')
 {
 abort();
 }
}

void PorNP(){
clrscr();
Pagain:
printf("\nSELECT AN ALGORITHM FOR YOUR JOB\n");
if(Pans=='y'||Pans=='Y')
 {
 printf("\nNon-preemptive\n\n");
 printf("[1] FCFS [2] SJF [3] NPP");
 printf("\n\nPreemptive\n\n");
 printf("[4] PP [5] SRTF [6] RR\n");
 scanf("%d",&choice);
 }
else
 {
 pickL:
 printf("\n[1] FCFS [2] SJF \n[5] SRTF [6] RR\n");
 scanf("%d",&choice);
 if(choice>2&&choice<5||choice>6)
 {
 clrscr();
 printf("\nNot in the choices, please try again");
 goto pickL;
 }
 }
clrscr();
switch(choice){
 case 1:
 printf("First Come First Serve");
 FCFS();
 gc(gnttroot);
 ttwt(gnttroot);
 break;
 case 2:
 printf("Shortest Job First");
 while(h!=NULL)
    {
    SJF();
    if(h==NULL)
    free(h);
    }
 gc(gnttroot);
 ttwt(gnttroot);
 break;
 case 3:
 printf("Non Preemptive Priority");
 while(h!=NULL)
    {
    NPP();
    if(h==NULL)
    free(h);
    }
  gc(gnttroot);
  ttwt(gnttroot);
 break;
 case 4:
 printf("Preemptive Priority");
    PP();
    if(h==NULL)
    free(h);
    gc(gnttroot);
    Pttwt(gnttroot);
 break;
 case 5:
 printf("Shortest Remaining Time First");
    SRTF();
    if(h==NULL)
    free(h);
    gc(gnttroot);
    Pttwt(gnttroot);
 break;
 case 6:
 int quantum=0;
 printf("Round Robin");
 printf("\nEnter Quantum/Time Slice: ");
 scanf("%d",&quantum);
    RR(quantum);
    if(h==NULL)
    free(h);
    gc(gnttroot);
    Pttwt(gnttroot);
 break;
 default:
 clrscr();
 printf("\nError: Not in the choices,please try again");
 goto Pagain;
 }
}
void SJF(){
    struct node *test=NULL;
    test=stopper();
    //printf("\nstopper |%s|",test->name);
    if(h!=NULL)
    {
     if(test==h)
     {
     insIDLE(test);
     }
     else
     {
     struct node *maliit=NULL;
     maliit = sjfcondi(test);
     //printf("\nmaliit |%s|",maliit->name);
     del(maliit);
     }
    }
}
void NPP(){
    struct node *test=NULL;
    test=stopper();
    //printf("\nstopper |%s|",test->name);
    if(h!=NULL)
    {
     if(test==h)
     {
     insIDLE(test);
     }
     else
     {
     struct node *prio=NULL;
     prio = nppcondi(test);
     //printf("\npriority |%s|",prio->name);
     del(prio);
     }
    }
}
struct node* sjfcondi(struct node *stop){
    struct node *sj=h,*shortest=h;
    while(sj!=stop)
    {
    if(sj->CBT <= shortest->CBT)
     {
     if(sj->CBT == shortest->CBT)
     {
      if(sj->AT <= shortest->AT)
      {
      if(sj->AT == shortest->AT)
      {
       if(sj->inptnm < shortest->inptnm)
       shortest = sj;
      }
      else
      shortest = sj;
      }
     }
     else
       shortest=sj;
     }
     sj=sj->next;
    }
    //printf("\nshortest job|%s|",shortest->name);
    ins(shortest);
    return shortest;
}

struct node* nppcondi(struct node *stop){
    struct node *pr=h,*priority=h;
    while(pr!=stop)
    {
    if(pr->P <= priority->P)
     {
     if(pr->P == priority->P)
     {
      if(pr->AT <= priority->AT)
      {
      if(pr->AT == priority->AT)
      {
       if(pr->inptnm < priority->inptnm)
       priority = pr;
      }
      else
      priority = pr;
      }
     }
     else
       priority = pr;
     }
     pr=pr->next;
    }
    //printf("\nshortest job|%s|",shortest->name);
    ins(priority);
    return priority;
}

void make(struct node *f){
chart=(struct GC*)malloc(sizeof(struct GC));
strcpy(chart->name,f->name);
chart->burst=f->CBT;
timen += chart->burst;
chart->endt = timen;
chart->dAT = f->AT;
chart->link=NULL;
}

void IDLE(struct node* after){
int idle=0;
idle= after->AT - timen;
chart=(struct GC*)malloc(sizeof(struct GC));
strcpy(chart->name,"IDLE");
chart->burst = idle;
timen += chart->burst;
chart->endt = timen;
chart->link=NULL;
}

void ins(struct node *box)
{
  if(gnttroot==NULL)
  {
  make(box);
  gnttroot=chart;
  tmp1=chart;
  }
  else
  {
  make(box);
  tmp1->link=chart;
  tmp1=chart;
  }
}

void FCFS(){
struct node *first= h;
int idle=0;
   while(first!=NULL)
   {idle=0;
    if(first->AT>timen)
    {
    idle= first->AT - timen;
    chart=(struct GC*) malloc(sizeof(struct GC));
    strcpy(chart->name,"IDLE");
    chart->burst = idle;
    timen += idle;
    chart->endt = timen;
    if(gnttroot==NULL)
      gnttroot=chart;
    else
      {
      tmp1->link=chart;
	  tmp1=chart;
      }
    }
    ins(first);
    first=first->next;
   }
fflush(stdout);
}

void insIDLE(struct node* stops)
{
  if(gnttroot==NULL)
  {
  IDLE(stops);
  gnttroot=chart;
  tmp1=chart;
  }
  else
  {
  IDLE(stops);
  tmp1->link=chart;
  tmp1=chart;
  }
}
void gc(struct GC *disp)
{struct GC* move;
 long int gtime=0;
 move=disp;
 printf("\nGANTT CHART");
 DRAW_LINE;
 textcolor(10);
 cprintf("|");
 if(move==NULL)
  cprintf("Gannt CHART is EMPTY");
 else{
 while(move->link!=NULL)
  {
  cprintf("%s%d |",move->name,move->burst);
  move=move->link;
  fflush(stdout);
 }
 cprintf("%s%d |",move->name,move->burst);
 printf("\n");
 textcolor(2);
 cprintf("0");
 move=disp;
 while(move!=NULL)
 {
 gtime += move->burst;
 if(strcmp(move->name,"IDLE")==0)
  {
  cprintf("      %ld",gtime);
  fflush(stdout);
  }
 else
  {
  if(move->burst > 9)
  {
  if(gtime > 9)
  {
   if( (gtime+move->burst) > 9 )
    cprintf("  %ld",gtime);
   else
    cprintf("  %ld",gtime);
  }
  else
  {
   if( (gtime+move->burst) > 9 )
    cprintf("  %ld",gtime);
   else
    cprintf("   %ld",gtime);
  }
  }
  else
   {
   if((gtime+move->burst) > 9 )
    cprintf("  %ld",gtime);
   else
    cprintf("   %ld",gtime);
   }
  }
  fflush(stdout);
  move=move->link;
  }
 }
 final=gtime;
 textcolor(14);
}

struct node* stopper(){
struct node *stop=h;
struct node *limit=NULL;
 while(stop->AT<=timen)
 {
 stop=stop->next;
 }
 limit=stop;
 //printf("\n|%s|",limit->name);
 return limit;
}
/* TO create an empty node */
void create()
{   char cname;
    fflush(stdin);
    temp =(struct node *)malloc(1*sizeof(struct node));
    temp->prev = NULL;
    temp->next = NULL;
    fflush(stdout);
    printf("\n\n\t\t\t\t JOB NAME: ");
    scanf("\n");
    scanf("%[^\n]s",&temp->name);
    printf("\n\t\t\t\t ARRIVAL TIME: ");
    scanf("%d",&temp->AT);
    printf("\n\t\t\t\t CPUBURSTTIME: ");
    scanf("%d",&temp->CBT);
    if(temp->CBT != 0)
    {numero++;}
    if(Pans=='y'||Pans=='Y')
    {
    printf("\n\t\t\t\t PRIORITY: ");
    scanf("%d",&temp->P);
    }
    count++;
    temp->inptnm=count;
    fflush(stdin);
}

/* To insert at end */
void insert2()
{
    if (h == NULL)
    {
	create();
	h = temp;
	temp1 = h;
    }
    else
    {
	create();
	temp1->next = temp;
	temp->prev = temp1;
	temp1 = temp;
    }
}
/* To delete an element */
void del(struct node* ete)
{
    if (h == NULL)
    {
	printf("\n Error : Empty list no elements to delete");
	return;
    }
    else
    {
	if (ete == h)
	{
	    if (ete->next == NULL)
	    {
		//printf("Node deleted from list");
		free(ete);
		ete = h = NULL;
		return;
	    }
	}
	if (ete->next == NULL)
	{
	    ete->prev->next = NULL;
	    free(ete);
	    //printf("Node deleted from list");
	    return;
	}
	ete->next->prev = ete->prev;
	if (ete != h)
	    ete->prev->next = ete->next;    /* Might not need this statement if i == 1 check */
	if (ete == h)
	    h = ete->next;
	//printf("\n Node deleted");
	free(ete);
    }
    count--;
}

/* To sort the linked list */
void sort()
{
    int i, j, x, y, z, p;
    char w[20];

    temp2 = h;
    temp4 = h;

    if (temp2 == NULL)
    {
	printf("\n List empty to sort");
	return;
    }

    for (temp2 = h; temp2 != NULL; temp2 = temp2->next)
    {
	for (temp4 = temp2->next; temp4 != NULL; temp4 = temp4->next)
	{
		if(temp2->AT == temp4->AT)
		  {
		  	if(temp2->inptnm > temp4->inptnm)
		       goto sortequalAT;
		  }
	    if (temp2->AT > temp4->AT)
	    {
	    sortequalAT:	
		x = temp2->AT; //ARRIVAL
		temp2->AT = temp4->AT;
		temp4->AT = x;
		y = temp2->CBT;//CBT
		temp2->CBT = temp4->CBT;
		temp4->CBT = y;
		z = temp2->inptnm; //inptnum
		temp2->inptnm = temp4->inptnm;
		temp4->inptnm = z;
		if(Pans=='y'||Pans=='Y')
		{
		p = temp2->P;
		temp2->P = temp4->P;
		temp4->P = p;
	    }
		strcpy(w,temp2->name);
		strcpy(temp2->name,temp4->name);
		strcpy(temp4->name,w);
	    }
	}
    }
    //traversebeg();
}

void ttwt (struct GC* disp)
{
int TT=0,WT=0;
textcolor(13);
float ttave=0,wtave=0,CPUu=0,tb=0;
DRAW_LINE;
printf("\t\t\t\t\t ");
cprintf("TT      WT");
struct GC* move;
move=disp;
 if(move==NULL)
   printf("TABLE IS EMPTY");
 else
  {
   while (move!=NULL)
   {
    if(strcmp(move->name,"IDLE")!=0)
    {
    TT = (move->endt - move->dAT);
    WT = TT - move->burst;
    ttave+=TT;
    wtave+=WT;
    fflush(stdout);
    printf("\n\t\t\t\t");
    if(TT > 9)
    cprintf("%s        %d      %d",move->name,TT,WT);
    else
    cprintf("%s        %d       %d",move->name,TT,WT);
    fflush(stdout);
    tb+=move->burst;
    }
    move=move->link;
   }
   /*******************ROLINEGWAP0*****************/
   ttave=float(ttave/numero);
   wtave=float(wtave/numero);
   fflush(stdout);
   DRAW_LINE;
   cprintf("ttave: %.2f  wtave: %.2f",ttave,wtave);
   fflush(stdout);
   CPUu=float(tb/final); CPUu=float((CPUu)*100);
   cprintf("      CPU utilization: %.2f/%.2f = %.2f%%",tb,final,CPUu);
  }
  textcolor(14);
}
void shortsort(struct node* staph)
{
    int i, j, x, y, z;
    char w[20];

    temp2 = h;
    temp4 = h;
    for (temp2 = h; temp2 != staph; temp2 = temp2->next)
    {
	for (temp4 = temp2->next; temp4 != staph; temp4 = temp4->next)
	{
	    if (temp2->CBT == temp4->CBT)
	     {
	     if(temp2->AT >= temp4->AT) 
	       {
	       	if(temp2->AT == temp4->AT)
	       	{
	          if(temp2->inptnm > temp4->inptnm)	
			    goto sortequalburst;	
			}
	       	else
	         goto sortequalburst;
		   }
	     }
	    if (temp2->CBT > temp4->CBT)
	    {
		sortequalburst:
		x = temp2->AT; //ARRIVAL
		temp2->AT = temp4->AT;
		temp4->AT = x;
		y = temp2->CBT;//CBT
		temp2->CBT = temp4->CBT;
		temp4->CBT = y;
		z = temp2->inptnm; //inptnum
		temp2->inptnm = temp4->inptnm;
		temp4->inptnm = z;
		strcpy(w,temp2->name);
		strcpy(temp2->name,temp4->name);
		strcpy(temp4->name,w);
	    }
	}
    }
    //traversebeg();
}
void cpysrtnodes()
	{ struct node* gtemp=h;
	  while(gtemp!=NULL){
		gcurr=(struct node*)malloc(sizeof(struct node));
		gcurr->AT=gtemp->AT;
		gcurr->CBT=gtemp->CBT;
		gcurr->inptnm=gtemp->inptnm;
		strcpy(gcurr->name,gtemp->name);
		gcurr->prev=NULL;
		gcurr->next=NULL;
		if(groot==NULL)
		{
			groot=gcurr;
			glast=gcurr;
		}
		else
		{
		    glast->next=gcurr;
		    glast=gcurr;
		}
	    gtemp=gtemp->next;
	    }
	}
void Pins(struct GC* chart)
{
  if(gnttroot==NULL)
  {
  gnttroot = chart;
  tmp1 = chart;
  }
  else
  {
  tmp1->link = chart;
  tmp1 = chart;
  }
}
void Pmake(struct node* f){
chart=(struct GC*)malloc(sizeof(struct GC));
strcpy(chart->name,f->name);
chart->burst =NULL;
chart->endt =NULL;
chart->dAT = NULL;
}
void Pttwt (struct GC* disp)
{
int TT=0,WT=0,intburst=0;
float ttave=0,wtave=0,CPUu=0,tb=0;
DRAW_LINE;
textcolor(13);
printf("\t\t\t\t\t");
cprintf(" TT      WT");
struct GC* move;
move=disp;
 if(move==NULL)
   printf("TABLE IS EMPTY");
 else
  {
   while (move!=NULL)
   {
    if(strcmp(move->name,"IDLE")!=0 && move->endt!=0)
      {
	struct node* InitB=groot;
	while(InitB!=NULL)
	{
	if(strcmp(move->name,InitB->name)==0)
	 {
	 intburst=InitB->CBT;
	 move->dAT = InitB->AT;
	 break;
	 }
	 InitB=InitB->next;
	}
		TT = (move->endt - move->dAT);
		WT = TT - intburst;
		ttave+=TT;
		wtave+=WT;
		fflush(stdout);
		printf("\n\t\t\t\t");
		if(TT > 9)
		cprintf("%s        %d      %d",move->name,TT,WT);
		else
		cprintf("%s        %d       %d",move->name,TT,WT);
		fflush(stdout);
      }
    if(strcmp(move->name,"IDLE")!=0)
    tb+=move->burst;
    move=move->link;
   }
   /*******************ROLINEGWAP0*****************/
   ttave=float(ttave/numero);
   wtave=float(wtave/numero);
   fflush(stdout);
   DRAW_LINE;
   cprintf("ttave: %.2f  wtave: %.2f",ttave,wtave);
   fflush(stdout);
   CPUu=float(tb/final); CPUu=float((CPUu)*100);
   cprintf("      CPU utilization: %.2f/%.2f = %.2f%%",tb,final,CPUu);
  }
  textcolor(14);
}
void PP()
{
while(h->next != NULL && h != NULL )
{
 struct node *stop=NULL;
 stop=stopper();
 if(stop==h)
 {
   insIDLE(stop);
 }
 else
 {
  priosort(stop);
  struct node* pp=h;
  Pmake(pp);
  while(timen<stop->AT && h->next!=NULL)
  {
    pp->CBT--;
    chart->burst++;
    timen++;
    if(pp->CBT==0)
    {
     chart->dAT=pp->AT;
     chart->endt=timen;
     Pins(chart);
     del(pp);
      if(timen < stop->AT)
      {
       pp=h;
       Pmake(pp);
      }
    }
    else if(timen==stop->AT)
    {
	 Pins(chart);
    }
  }
 }
}
 if(h->next==NULL)
 {
  FCFS();
  del(h);
  free(h);
  h=NULL;
 }
}
void SRTF()
{
while(h->next != NULL && h != NULL )
{
 struct node *stop=NULL;
 stop=stopper();
 if(stop==h)
 {
   insIDLE(stop);
 }
 else
 {
  shortsort(stop);
  struct node* srtf=h;
  Pmake(srtf);
  while(timen<stop->AT && h->next!=NULL)
  {
    srtf->CBT--;
    chart->burst++;
    timen++;
    if(srtf->CBT==0)
    {
     chart->dAT=srtf->AT;
     chart->endt=timen;
     Pins(chart);
     del(srtf);
      if(timen < stop->AT)
      {
       srtf=h;
       Pmake(srtf);
      }
    }
    else if(timen==stop->AT)
    {
	Pins(chart);
    }
  }
 }
}
 if(h->next==NULL)
 {
  FCFS();
  del(h);
  free(h);
  h=NULL;
 }
}
void priosort(struct node* staph)
{
    int i, j, x, y, z, p;
    char w[20];

    temp2 = h;
    temp4 = h;
    for (temp2 = h; temp2 != staph; temp2 = temp2->next)
    {
	for (temp4 = temp2->next; temp4 != staph; temp4 = temp4->next)
	{
	    if (temp2->P == temp4->P)
	     {
	     if(temp2->AT >= temp4->AT)
	      {
	      if(temp2->AT == temp4->AT)
		  {
			if(temp2->inptnm > temp4->inptnm)
			 goto sortequalpriority;
		  }
	      else
	      goto sortequalpriority;
	      }
	     }
	    if (temp2->P > temp4->P)
	    {
		sortequalpriority:
		x = temp2->AT; //ARRIVAL
		temp2->AT = temp4->AT;
		temp4->AT = x;
		y = temp2->CBT;//CBT
		temp2->CBT = temp4->CBT;
		temp4->CBT = y;
		z = temp2->inptnm; //inptnum
		temp2->inptnm = temp4->inptnm;
		temp4->inptnm = z;
		p= temp2->P;
		temp2->P = temp4->P;
		temp4->P = p;
		strcpy(w,temp2->name);
		strcpy(temp2->name,temp4->name);
		strcpy(temp4->name,w);
	    }
	}
    }
    //traversebeg();
}
void RR(int quantum)
{
while(h->next != NULL && h != NULL )
{
 struct node *stop=NULL;
 stop=stopper();
 if(stop==h)
 {
   insIDLE(stop);
 }
 else
 {
  struct node* rr=h;
    if( ((rr->CBT)-quantum <= 0))
    {
       ins(rr);
       del(rr);
    }
    else
    {
	  Pmake(rr);
	  rr->CBT -= quantum;
	  chart->burst = quantum;
	  timen+=quantum;
	  rr->AT = timen;
	  Pins(chart);
	  rrsort(rr);
	}
 }
}
 if(h->next==NULL)
 {
  FCFS();
  del(h);
  free(h);
  h=NULL;
 }
}
void rrsort(struct node* round)
{
    int i, j, x, y, z, p, flag=0;
    char w[20];
    temp2 = h;
    temp4 = h;

    if (temp2 == NULL)
    {
	printf("\n List empty to sort");
	return;
    }
    for (temp2 = h; temp2 != NULL; temp2 = temp2->next)
    {
    flag=0;
	for (temp4 = temp2->next; temp4 != NULL; temp4 = temp4->next)
	{
	    if(temp2->AT==temp4->AT)
	    {
	    if (temp2==round)
	     {  flag=1;
		goto swapround;
		 }
	    }

	    if (temp2->AT > temp4->AT)
	    {
	    swapround:
		x = temp2->AT; //ARRIVAL
		temp2->AT = temp4->AT;
		temp4->AT = x;
		y = temp2->CBT;//CBT
		temp2->CBT = temp4->CBT;
		temp4->CBT = y;
		z = temp2->inptnm; //inptnum
		temp2->inptnm = temp4->inptnm;
		temp4->inptnm = z;
		p= temp2->P;
		temp2->P = temp4->P;
		temp4->P = p;
		strcpy(w,temp2->name);
		strcpy(temp2->name,temp4->name);
		strcpy(temp4->name,w);
		if(flag==1)
		round=temp4;
	    }
	}
    }
    //traversebeg();
}
