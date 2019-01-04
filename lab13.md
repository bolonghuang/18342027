# snake_eat.c
void snake_eat(int LEN,char x,char map【R0】【 L0】)//snake_eat(int,char)函数 

{
map【R0】【L0】='*';//原蛇头位置变成蛇身‘*’ 
LEN++;

//判断x,重新安置蛇头的位置 
switch(x)

{

case 'A':map[R0][--L0]='H';break; //将蛇头注意到原位置左边
case 'D':map[R0][++L0]='H';break;//将蛇头注意到原位置右边
case 'W':map[--R0][L0]='H';break;//将蛇头注意到原位置上边
case 'S':map[++R0][L0]='H';break;//将蛇头注意到原位置下边
}

}

# snake_move.c

void snake_move()// 蛇移动的算法 

{

char x;//operation 为字符 

int R0=1,C0=4,LEN=5,l,R,L;//蛇头初始在第2row,第4col 

int location【100】={3,3,3,3};//location[]=1,2,3,4分别代表组成蛇的后一个字符在前一个字符的右、下、左、上边 。初始时，所有字符都在前一个字符串的左边 

int step【100】={1,1,1,1};//location[]=1,2,3,4分别表示第n个字符向右、下、左、上移动。初始时，所有字符都向右移动
while(1)//在游戏结束之前，游戏一直进行

{

scanf("%c",&x);//READ opertion;

R=R0;
L=L0;
l=LEN; 
if (x=='A')//x=A,判断蛇头左边是否为‘*’或蛇身

{//蛇头左边是否为‘*’或蛇身 ，游戏结束 

if( map[R][L-1]='*'OR'X'){gameover();break;}//退出游戏 
//蛇头左边是否为‘$

     else if(map[R][L-1]=='$'){snake_eat(LEN,x);location[LEN]=1;}//蛇头左边为‘$’,调用snake_eat(int,char)函数 
else{step[l]=3;map[R][L-1]=map[R][L];}//记录蛇头移动方向，移动蛇头
     
if(x=='D')

{//蛇头右边是否为‘*’或蛇身 ，游戏结束
if(map[R][L+1]='*'OR'X'){gameover();break;}//退出游戏 
else if(map[R][L+1]='$' ) {snake_eat(LEN,x);location[l]=3;}//蛇头右边为‘$’,调用snake_eat(int,char)函数
     
     else{step[l]=1;map[R][L+1]=map[R][L];}//记录蛇头移动方向，移动蛇头  

if(x=='W')

    {
//蛇头上边是否为‘*’或蛇身 ，游戏结束 
     if(map[R-1][L]='*'OR'X'){ gameover();break;}//退出游戏 
else if(map[R-1][L]='$'){snake_eat(LEN,x);location[l]=2;}//蛇头上边为‘$’,调用snake_eat(int,char)函数
else{step[l]=4;map[R-1][L]=map[R][L];}//记录蛇头移动方向，移动蛇头  

    } 

if(x=='S')

    {
//蛇头下边是否为‘*’或蛇身 ，游戏结束 

     if(map[R+1][L]='*'OR'X'){gameover();break;}//退出游戏
else if(map[R+1][L]='$'){snake_eat(LEN,x);location[l]=4;}//蛇头下边为‘$’,调用snake_eat(int,char)函数
     else{step[l]=2;map[R+1][L]=map[R][L];}//记录蛇头移动方向，移动蛇头     

    } 

l--;//对第l个*进行移动
    while(1)//分别判断第l+1个字符移动方向

     {

     if(step[l+1]==3)//第l+1个字符向左移动

     {

     if(location[l]==1)  { map[R][L]=map[R][++L];step[l]=3;} //第l个字符在第l+1个字符右边，往左移动，并下一处理第l-1个字符
     
         if(location[l]==2)  { map[R][L]=map[++R][L];step[l]=4;}  //第l个字符在第l+1个字符下边，往上移动，并下一处理第l-1个字符   
         
if(location[l]==4) { map[R][L]=map[--R][++L];step[l]=2;}//第l个字符在第l+1个字符上边，往下移动，并下一处理第l-1个字符
         
         location[l]=1; //第l个字符在第l+1个字符右边；

        }
         
         if(step[l+1]==1)//第l+1个字符向右移动

     {

     if(location[l]==3)  { map[R][L]=map[R][--L];step[l]=1;} //第l个字符在第l+1个字符右边，往右移动，并下一处理第l-1个字符
     
         if(location[l]==2)  { map[R][L]=map[++R][L];step[l]=4;}//第l个字符在第l+1个字符下边，往上移动，并下一处理第l-1个字符         
         
if(location[l]==4) { map[R][L]=map[--R][++L];step[l]=2;} //第l个字符在第l+1个字符上边，往下移动，并下一处理第l-1个字符
location[l]=3;//第l个字符在第l+1个字符左边；

        }
        
         if(step[l+1]==2)//第l+1个字符向下移动

     {

     if(location[l]==1)  { map[R][L]=map[R][--L];step[l]=3;} //第l个字符在第l+1个字符右边，往左移动，并下一处理第l-1个字符
     
         if(location[l]==3)  { map[R][L]=map[R][++L];step[l]=4;}//第l个字符在第l+1个字符左边，往右移动，并下一处理第l-1个字符         
         
if(location[l]==4) { map[R][L]=map[--R][L];step[l]=2;} //第l个字符在第l+1个字符上边，往下移动，并下一处理第l-1个字符
location[l]=4;//第l个字符在第l+1个字符上边；

        }
        
         if(step[l+1]==4)//第l+1个字符向上移动

     {

     if(location[l]==1)  { map[R][L]=map[R][--L];step[l]=3;} //第l个字符在第l+1个字符右边，往左移动，并下一处理第l-1个字符
     
         if(location[l]==2)  { map[R][L]=map[++R][L];step[l]=4;}  //第l个字符在第l+1个字符下边，往上移动，并下一处理第l-1个字符   
         
if(location[l]==3) { map[R][L]=map[--R][++L];step[l]=2;}//第l个字符在第l+1个字符左边，往右移动，并下一处理第l-1个字符
         
         location[l]=2; //第l个字符在第l+1个字符下边；

        } 
        
     l--;//处理下一个字符
     
        if(l==0) map[R][L]=' '; //将最后一个字符原位置清空
         
}

output(map);//打印移动一步后的情况

}

