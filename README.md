
直接编译运行即可

>**详见：[江服校园导游咨询系统-数据结构课程设计](https://blog.csdn.net/qq_46207024/article/details/127159254?spm=1001.2014.3001.5501)**

#	1 需求分析
## 1.1 问题描述
设计一个校园导游程序，为来访的客人提供各种信息查询服务。

 1.设计江西服装学院的校园平面图。选取若干有代表性的景点抽象成一个无向带权图（无向网），所含景点不少于 6 个。

 2.为来访客人提供图中任意景点相关信息的查询。 

 3.为来访客人提供图中任意景点的问路查询，即查询任意两个景点之间的一条最短的简单路径。

## 1.2 系统简介
1.设计江西服装学院的校园平面图。选取8个有代表性的景点抽象成一个无向带权图（无向网）。以图中顶点表示校内各景点，存放景点名称、编号、简介等信息；以边表示路径，边上的权值表示两景点之间的距离。

2.为用户提供图中任意景点相关信息的查询、图中任意景点的问路查询，即查询任意两个景点之间的一条最短的简单路径。

3.使用C语言，基于《数据结构》中图的相关算法开发了“江西服装学院校园咨询系统”。系统从实际出发，通过对校园平面图的分析，将其转化为数据并保存在系统中，系统提供的路径具有较大的可信性。 
## 1.3 系统模块功能要求介绍
系统分为五大模块功能

1.浏览校园全景：输入即可查看校园全景点名称、编号、简介。

2.查看所有游览路线：用户在选择此功能模块后，按照屏幕上方提示的景点名称及其对应的编号，要求用户输入想要查询的景点的编号，回车后系统将在已存储的景点中进行匹配，若该景点信息尚未存储则将提示错误；若找到对应信息则系统将输出景点信息，显示于幕上方。

3.确定两景点之间最短距离：用户在选择此功能模块后，按照屏幕上方提示的景点名称及其对应的编号，要求用户输入起点和终点的编号,系统将在已存储的景点中进行匹配，若未找到所需查询的景点编号，系统将提示错误并要求用户再次输入。若输入信息合法，则回车后系统将给出最短路径，显示于屏幕上方。

4.查看景点信息：用户在选择此功能模块后，输入景点编号即可查看景点信息。

5.退出导游系统：用户在使用完本系统后，选择此功能模块后按任意键系统将自动退出。 

## 1.4 系统开发环境及开发人员

开发语言: C语言
开发工具：Visual C++6.0
操作系统：Microsoft Windows 10
开发人员：Yeats_Liao

## 1.5 校园平面图

![alt text](/image/image.png)

#	2 概要设计
## 2.1 算法设计及存储结构说明
**2.1.1 主函数概要设计**

调用初始化图函数InitGraph()函数创建一个图，再调用显示主界面函数显示一个可视化主界面，内容景点信息及操作编号的提示信息。当用户成功输入操作编号后，使用switch()函数，判断用户所需操作，匹配成功后，调用相关函数实现用户所需功能。

**2.1.2 初始化图函数InitGraph()** 

InitGraph()函数使用MyGraph结构体声明一个用于存储图中信息的结构体，定义结构体中的景点数量以及路径数量，然后使用循环为景点信息和路径长度赋值。

**2.1.3 显示主界面函数设计void Menu()**

void Menu()函数主要用于显示主界面，界面提示了景点名称及其对应编号。主界面下方以列表方式提示用户系统可进行的操作及其对应编号，最后提示用户进行输入。 


__2.1.4 显示图中信息函数设计void Browser(MGraph *G)__


该函数首先定义了一个变量v(用于接收用户输入的查询编号),而后使用for循环，判断条件为v，以列表方式输出。 


__2.1.5 查询景点信息函数设计void Search(MGraph *G)__


该函数首先定义了一个变量k(用于接收用户输入的查询编号)和一个标记位flag(初始值设为1)，而后使用while()循环，判断条件为flag=1,当输入编号不合法时提示错误，当输入合法时标记位flag置为0，此时跳出循环，调用MyGraph结构体对应编号的景点信息，以列表方式输出。 

**2.1.6 弗洛伊德算法函数设计Floyd()**

Floyd算法首先将两景点间路径长度数据存储于数组 D[v][w]中，然后使用一个三维数组用于存放最短路径所经过的顶点，接下来使用三重循环判断两景点之间直接路径是否大于间接路径，若大于，则将三维数组中存放的顶点信息更改为简介路径所经过的顶点信息。 

以上部分完成后，当用于标记输入数据是否合法的flag=1时，输出错误信息，提示用户重新输入，当输入数据合法时，输出以上程序得到结果。 

## 2.2 系统功能设计
**2.2.1主程序界面**

定义一个I,调用InitGraph()函数初始化图,再调用menu()函数,输入选择,利用switch开关语句,实现用户选择需求。

![alt text](/image/image-1.png)

**2.2.2 浏览景点信息** 

定义v；用for循环for（v=0；i<G.vexnum;v++）当条件成立的时候执行printf语句，直到循环不成立的时候输出结束。

**2.2.3 查找所有游览线路** 

查找路径利用Dijkstra算法，该函数首先定义了一个变量v(用于接收用户输入的查询编号),而后使用for循环，判断条件为v，以列表方式输出。

**2.3.4 确定两景点之间最短距离** 

利用多个for循环嵌套，计算出路径，计算出路径长度，当最外重循环不成立时循环结束.利用for循环输出。

# 3 详细设计
## 3.1 定义符号变量

```c
#define INFINITY 1000//定义一个无穷大数
#define MAX_VERTEX_NUM   40//定义景点数据最大容量 
#define MAX 40 #include<stdlib.h> 
#include<stdio.h> 
#include<conio.h> 
#include<string.h> 
#include<stdlib.h>

typedef struct ArCell //邻接矩阵
{ 
	int adj;//存储路径长度  
}ArCell,AdjMatrix[MAX_VERTEX_NUM][MAX_VERTEX_NUM]; 

typedef struct//图顶点表示主要景点存放景点编号、名称、简介等信息 
{
	int num;
	char name[20]; 
	char introduction[50];//简介
}infotype; 

typedef struct//图中的边表示景点间的道路，存放路径长度等信息。 
{ 
infotype vexs[MAX_VERTEX_NUM];//顶点信息域 
AdjMatrix arcs; 
int vexnum,/*顶点数*/ arcnum;//边个数 
}MGraph; MGraph b;  
```
## 3.2 主程序模块给出函数声明

```c
void cmd(void); 
MGraph InitGraph(void); //初始化图
void Menu(void);//菜单函数 
void Browser(MGraph *G); //浏览函数
void ShortestPath_DIJ(MGraph *G); 
void Floyd(MGraph *G); // 查询图中任意两个景点间的所有路径
void Search(MGraph *G); //查找函数 
int LocateVex(MGraph *G,char*v); // Dijkstra算法 计算起点各顶点间短路径
MGraph * CreatUDN(MGraph *G); //初始化图形，接受用户输入
void print(MGraph *G); //输出函数
```
## 3.3 主程序界面

```c
void cmd(void) 
{  
	int i; 
	b=InitGraph();  //初始化校园地图 
	Menu();			//调用显示主界面函数 
	scanf("%d",&i); 
	
	while(i!=5)  
	{ 
	 switch(i)   
	 { 
	  case 1: system("cls");Browser(&b); Menu();break;//1.浏览校园全景 
	  case 2: ShortestPath_DIJ(&b); Menu();break;//2.查看所有游览路线   
	  case 3: Floyd(&b); Menu(); break;//3.确定两景点之间最短距离     
	  case 4: Search(&b); Menu();break;//4.查看景点信息  
	  case 5:exit(0);break;   
	  default:break;   
	 } 
	scanf("%d",&i);  
	} 
}
```
## 3.4 定义各顶点之间的距离

```c
for(i=0;i<G.vexnum;i++)   
	 for(j=0;j<G.vexnum;j++)    
	 G.arcs[i][j].adj=INFINITY;   
	 G.arcs[0][1].adj=150; 
	 G.arcs[0][2].adj=200;   
	 G.arcs[0][8].adj=600;   
	 G.arcs[1][2].adj=50;  
	 G.arcs[1][4].adj=70;   
	 G.arcs[1][5].adj=100;  
	 G.arcs[2][3].adj=70;  
	 G.arcs[2][5].adj=100;  
	 G.arcs[3][5].adj=250;  
	 G.arcs[3][6].adj=240;   
	 G.arcs[4][5].adj=50;  
	 G.arcs[5][6].adj=50;
	 G.arcs[5][7].adj=200;   
	 G.arcs[5][8].adj=300; 
	 G.arcs[6][7].adj=170;
	 G.arcs[6][8].adj=250;  
	 G.arcs[7][8].adj=200;   
	 for(i=0;i<G.vexnum;i++)   
		 for(j=0;j<G.vexnum;j++) 
   G.arcs[j][i].adj=G.arcs[i][j].adj; //无向图相反方向路径相同  
		 return G; 
}
```


## 3.5 界面菜单设计

```c
void Menu()
{  
 printf("\n                                   江西服装学院导游图\n"); 
 printf("                           ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓\n"); 
 printf("                           ┃   1.浏览校园全景              ┃\n"); 
 printf("                           ┃   2.查看所有游览路线          ┃\n"); 
 printf("                           ┃   3.确定两景点之间最短距离    ┃\n");  
 printf("                           ┃   4.查看景点信息              ┃\n"); 
 printf("                           ┃   5.退出导游系统              ┃\n"); 
 printf("                           ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛\n"); 
 printf("请输入选择编号:"); 
} 
/******************************************************/ 

void Browser(MGraph *G)//介绍景点
{ 
 int v; 
 printf("┏━━━━┳━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓\n"); 
 printf("┃编号┃景点名称            ┃简介																					 \n"); 
 
 for(v=0;v<G->vexnum;v++)  
	 printf("┃%-4d┃%-20s┃%-60s  \n",G->vexs[v].num,G->vexs[v].name,G->vexs[v].introduction); 
 printf("┗━━━━┻━━━━━━━━━━━━━━━━━━━━┻━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛\n"); 
}
```
## 3.6 Dijkstra算法 计算起点各顶点间短路径

```c
void ShortestPath_DIJ(MGraph * G) 
{ 
 int v,w,i,min,t=0,x,flag=1,v0; 
    int final[20], D[20], p[20][20];  
	while(flag)  
	{ 
		printf("请输入景点编号:");   
		scanf("%d",&v0); 
		if(v0<0||v0>G->vexnum)   
		{ 
			printf("景点编号不存在!请重新输入景点编号:");      
			scanf("%d",&v0);   
		} 
		if(v0>=0&&v0<G->vexnum)   
			flag=0;  
	}  
	for(v=0;v<G->vexnum;v++)  
	{   
		final[v]=0;   
		D[v]=G->arcs[v0][v].adj;//存储起始v0-末尾v之间权值 
		for(w=0;w<G->vexnum;w++)   
			p[v][w]=0;  
		if(D[v]<INFINITY) 
		{   
			p[v][v0]=1;p[v][v]=1;   
		}  
	} 
	D[v0]=0;final[v0]=1; 
	for(i=1;i<G->vexnum;i++)  
	{   
		min=INFINITY;   
		for(w=0;w<G->vexnum;w++)    
			if(!final[w])     
				if(D[w]<min){v=w;min=D[w];}     
				final[v]=1;     
				for(w=0;w<G->vexnum;w++)     
					if(!final[w]&&(min+G->arcs[v][w].adj<D[w]))      
					{       D[w]=min+G->arcs[v][w].adj;      
					for(x=0;x<G->vexnum;x++)      
						p[w][x]=p[v][x];      
					p[w][w]=1;      
					}  
 } 
	for(v=0;v<G->vexnum;v++)  
	{   
		if(v0!=v) 
			printf("%s",G->vexs[v0].name);   
		for(w=0;w<G->vexnum;w++)   
		{    
			if(p[v][w]&&w!=v0)     
				printf("-->%s",G->vexs[w].name);    
			t++;   
		}   
		if(t>G->vexnum&&v0!=v)printf(" 总路线%dm\n\n",D[v]);  
	} 
}
```
## 3.7 用floyd算法求两个景点的最短路径

```c
void Floyd(MGraph *G)
{ 
 int v,u,i,w,k,j,flag=1,p[20][20][20],D[20][20];  
	for(v=0;v<G->vexnum;v++)   
		for(w=0;w<G->vexnum;w++)   
		{ 
			D[v][w]=G->arcs[v][w].adj;     
			for(u=0;u<G->vexnum;u++)     
				p[v][w][u]=0; 
			if(D[v][w]<INFINITY)    
			{ 
				p[v][w][v]=1;p[v][w][w]=1;    
			}   
		} 
		for(u=0;u<G->vexnum;u++)   
			for(v=0;v<G->vexnum;v++)   
				for(w=0;w<G->vexnum;w++)     
					if(D[v][u]+D[u][w]<D[v][w])     
					{   D[v][w]=D[v][u]+D[u][w];   
					for(i=0;i<G->vexnum;i++)   
						p[v][w][i]=p[v][u][i]||p[u][w][i];  
}  
		 while(flag)  
		 {   
			 printf("请输入出发地编号:");   
			 scanf("%d",&k);   
			 if(k<0||k>G->vexnum)   
			 {    
				 printf("景点编号不存在!\n请输入出发地编号:");    
				 scanf("%d",&k);   
			 }   

			 printf("请输入目的地编号:");   
			 scanf("%d",&j);   
			 if(j<0||j>G->vexnum)  
			 {    
				 printf("景点编号不存在!\n请输入目的地编号:");    
				 scanf("%d",&j);  
			 }   
			 if(k>=0&&k<G->vexnum&&j>=0&&j<G->vexnum)    
				 flag=0;  
		 } 
		 printf("\n");  
		 printf("%s",G->vexs[k].name);  
		 for(u=0;u<G->vexnum;u++)   
			 if(p[k][j][u]&&k!=u&&j!=u)   
				 printf("-->%s",G->vexs[u].name);  
			 printf("---->%s",G->vexs[j].name);   
			 printf(" 总路线%dm\n",D[k][j]); }
```

## 3.8 查找景点信息

```c
void Search(MGraph *G)
{  
	int k,flag=1;  
	while(flag)  
	{ 
		printf("请输入要查询景点编号:");  
		scanf("%d",&k); 
		if(k<0||k>G->vexnum)   
		{ 
			printf("景点编号不存在! 请重新输入:");      
			scanf("%d",&k);  
		} 
		if(k>=0&&k<G->vexnum)    
			flag=0; 
	} 
	printf("┏━━━━┳━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓\n"); 
	printf("┃编号┃景点名称            ┃简介																					 \n"); 
	printf("┃%-4d┃%-17s   ┃%-60s\n",G->vexs[k].num,G->vexs[k].name,G->vexs[k].introduction); 
	printf("┗━━━━┻━━━━━━━━━━━━━━━━━━━━┻━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛\n"); 
}
```
# 4 测试分析
## 4.1 主程序界面
主程序从void main()开始运行，景点信息的赋值初始化无向邻接图b=InitGraph();  调用menu菜单函数打印菜单，提示用户输入选择功能。 
![alt text](/image/image-2.png)

## 4.2 浏览校园全景
把原景点信息利用for循环输出，int v=0；v小于最多的景点个数输出景点信息，依次输出。

![alt text](/image/image-3.png)

## 4.3 查看所有游览线路

查看所有路线是使用void ShortestPath_DIJ(MGraph * G)// Dijkstra算法 计算起点各顶点间短路径，然后利用for循环输出计算的结果。输入景点不正确时会输出景点不存在重新输入。

![alt text](/image/image-4.png)

## 4.4 确定两景点之间最短距离 
利用void Floyd(MGraph *G)算法以及利用循环嵌套，查询图中存在的任意两个景点间的最短路径再利用循环输出，输入景点不正确时会输出景点不存在重新输入。

![alt text](/image/image-5.png)


## 4.5 查看景点信息 
利用void Search(MGraph *G)函数，查看景点信息和查找景点编号，当输入景点编号不在范围时输出“景点编号不存在请重新输入编号：”输入正确时输出景点信息。 

![alt text](/image/image-6.png)

 
# 5 用户手册

 1.本程序为校园导游程序，为来访的客人提供各种信息查询服务。

 2.进入系统之后，随即显示系统主菜单界面。用户可在该界面下输入各子菜单前对应的数字并按下回车键，执行相应子菜单命令。
  - 操作指令’1’：进入’浏览校园全景’模块。
 - 操作指令’2’：进入’查看所有浏览路线’模块，选择0-8中一个编号输入即可查看。
 - 操作指令’3’：进入’查找两景点之间最短距离’模块，选择0-8中两个个编号输入即可查找。
 - 操作指令’4’：进入’查看景点信息’模块，选择0-8中一个编号输入即可查看。
 - 操作指令’5’：进入’退出系统模块’后，按回车退出系统。

# 6 源程序下载
