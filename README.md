#include<iostream>
#include<vector>
#include<string>
#include<ctime>
#include<cstdlib>
using namespace std;
vector<vector<char>> board(3,vector<char>(3, ' '));
class tic
{
    int t=0;
    public :
 void display()
 {
    cout<< "  1 2 3"<<endl;
    for(int i=0;i<3;++i)
    {
        cout<<i+1<<" ";
        for(int j=0;j<3;++j)
        {
            cout<<board[i][j] <<" ";
        }
        cout<< endl;
    }
 }
 bool gameover()
 {
    for(int i=0;i<3;++i)
    {
        if(board[i][0]!=' '&& board[i][0]==board[i][1]&& board[i][1]==board[i][2])
        {
            return true;
        }
    }
    for(int j=0;j<3;++j)
    {
        if(board[0][j]!= ' ' && board[0][j]==board[1][j]&&board[1][j]==board[2][j])
        {
            return true;
        }
    }
    if(board[0][0]!= ' ' && board[0][0]==board[1][1]&&board[1][1]==board[2][2])
        {
            return true;
        }
        if(board[0][2]!= ' ' && board[0][2]==board[1][1]&&board[1][1]==board[2][0])
        {
            return true;
        }


        for (int i=0; i<3;++i)
        {
            for(int j=0;j<3;++j)
            {
                t++;
                
                if(board[i][j]==' ')
                {
                    return false;
                }

            }
        }
        return false;
 }
 bool validmove(int r,int c)
 {
    if (r<0||r>=3||c<0||c>=3||board[r][c]!= ' ')
    {
        return false;
    }
    return true;
 }
        void makemove(int r ,int c,char player)
        {
            board[r][c]=player;
        }
  };
  int main()
  {
    int R, C, ans, t=0;
    char player='X',comp='O',pname[30], ans1;
    tic t1;
    c:
    cout<<"1. 1 player and computer"<<endl;
    cout<<"2. 2 player"<<endl;
    cin>>ans;
    if(ans==1)
    {
    cout<<"Enter player name"<<endl;
    cin>>pname;
    srand(time(NULL));
    while (!t1.gameover())
    {
        t++;
        cout<<"computer moves :"<<endl;
            b:
         do{
            R= rand()%3+1;
            C=rand()%3+1;

        }while(t1.validmove(R,C));
        if (t1.validmove(R-1,C-1))
    {
        t1.makemove(R-1,C-1,comp);
        t1.display();
        if(t1.gameover())
        {
            cout<<"player "<<comp <<" lose!"<< endl;
            cout<<"computer  won the game"<<endl;
        }
        
    }
     else {
           // cout<<"Invalid move! Try again."<<endl;
            goto b;
        }
         if(t==5)
        {
            cout<<"match is tie"<<endl;
        }
        else {
    a:
    cout<<" player "<<pname<<",Enter your Move (Row and column): ";
    cin>>R>>C;
    if (t1.validmove(R-1,C-1))
    {
        t1.makemove(R-1,C-1,player);
        t1.display();
        if(t1.gameover())
        {
            cout<<"player "<<pname<<" wins!"<< endl;
            cout<<"computer  lose the game"<<endl;
            

        } 
    
    }
  
   else {
            cout<<"Invalid move! Try again."<<endl;
            goto a;
        }
         }
  } 
    }
else{
  cout<<"Welcome to tic - tac toe"<<endl;
t1.display();

//char player= 'X';
//int R , C;
while(!t1.gameover())
{
    t++;
    cout<<" player "<<player<<",Enter your Move (Row and column): ";
    cin>>R>>C;
    if (t1.validmove(R-1,C-1))
    {
        t1.makemove(R-1,C-1,player);
        t1.display();
        if(t1.gameover())
        {
            cout<<"player "<<player <<" wins!"<< endl;    

        } else {
            player =(player=='X')? 'O': 'X';
        }

        }

         else {
            cout<<"Invalid move! Try again."<<endl;
        }
         if(t==8)
        {
            cout<<"match is tie"<<endl;
        }
        else {
    }
}
}
cout<<"Do you want to replay the game(y|n)"<<endl;
cin>>ans1;
if(ans1=='y'||ans=='Y')
{
    goto c;
}

  return 0;
  }
