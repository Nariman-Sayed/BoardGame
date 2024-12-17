#include "3x3X_O.h"
#include "BoardGame_Classes.h"  
#include "MinMaxPlayer.h"
#include "AiPyramicTicTacToe.h" // 1
#include "FourinArow.h"   //2
// #include "5x5tictactoe" // 3 
#include "aiwordTicTacToe.h"  //4
#include "NumericalTicTacToe.h" //5
//#include "MisereTicTacToe.h" //6
#include "4x4TicTacToe.h" // 7
#include "ultimateTicTacToe.h" // 8
#include <string>
#include <cstdlib>
#include <ctime>
#include <exception>
#include <vector>
#include <iostream>
using namespace std;

int main(){
    int options;
    cout << "Hi welcome to our Menu choose from the below options:" << endl;
    while(options != 9){
    cout << "1)Pyramic Tic Tac Toe" << endl;
    cout << "2)Four in a Row game" << endl;
    cout << "3) 5x5 Tic Tac Toe" << endl;
    cout << "4) Word Tic Tac Toe" << endl;
    cout << "5) Numerical Tic Tac Toe" << endl;
    cout << "6) Misere Tic Tac Toe" << endl;
    cout << "7) 4x4 Tic Tac Toe" << endl;
    cout << "8) Ultimate Tic Tac Toe" << endl;
    cout << "9) exit" << endl;
    cin >> options;

    switch(options){
        case 1:
        {
            Player<char>* players[2];
    Board<char>* Pb = new pyramid_X_O_Board<char>();
    string playerXName, player2Name;
    cout << "Welcome to FCai pyramid X-O Game. :)"<<endl;
    int player;
    cout << "Choose Player X type:"<<endl;
    cout << "1. Human"<<endl;
    cout << "2. Random Computer"<<endl;
    cout << "3. smart ai"<<endl;
    cin >> player;
    switch(player) {
        case 1:
            cout << "Enter Player 1 name: ";
            cin >> playerXName;
            players[0] = new pyramid_X_O_Player<char>(playerXName,'X');
            break;
        case 2:
            players[0] = new pyramid_X_O_Random_Player<char>('X');
            break;
        case 3:
            players[0] = new Pyramid_X_O_MinMax_Player<char>('X');
            players[0]->setBoard(Pb);
            break;
        default:
            cout << "Invalid choice for Player 1. Exiting the game."<<endl;
            return 0;
    }
    cout << "Choose Player 2 type:"<<endl;
    cout << "1. Human"<<endl;
    cout << "2. Random Computer"<<endl;
    cout << "3. smart ai"<<endl;
    cin >> player;
    switch(player) {
        case 1:
            cout << "Enter Player 2 name: ";
            cin >> player2Name;
            players[1] = new pyramid_X_O_Player<char>(player2Name,'O');
            break;
        case 2:
            players[1] = new pyramid_X_O_Random_Player<char>('O');
            break;
        case 3:
            players[1] = new Pyramid_X_O_MinMax_Player<char>('O');
            players[1]->setBoard(Pb);
            break;
        default:
            cout << "Invalid choice for Player 2. Exiting the game."<<endl;
            return 0;
    }
    GameManager<char> pyramid_X_O_Gm(Pb, players);
    pyramid_X_O_Gm.run();
    delete Pb;
    for (int i = 0; i < 2; ++i) {
        delete players[i];
    }
            break;
        }
        case 2:
        {
        srand(static_cast<unsigned int>(time(0)));
    FourInARowBoard board;
    int option;
cout << "You want to play against a player or bot(1 for player 2 for bot): ";
cin >> option;
switch(option){
    case 1:{
    string Player1Name;
    cout << "Enter Player1 name: ";
    cin.ignore();
    getline(cin,Player1Name);
    char player1Symbol;
    cout << "Enter player1 symbol (x or o): ";
    cin >> player1Symbol;
    while(player1Symbol != 'x' && player1Symbol != 'o'){
    cout << "Error: symbol must be either x or o. Try again" << endl;
    cout << "Enter player1 symbol (x or o): ";
    cin >> player1Symbol;
}
HumanPlayer player1(Player1Name,player1Symbol);

string Player2Name;
cout << "Enter player2 name: ";
cin.ignore();
getline(cin,Player2Name);
char player2Symbol;
cout << "Enter player2 symbol: ";
cin >> player2Symbol;
while(player2Symbol == player1Symbol || (player2Symbol != 'x' && player2Symbol != 'o')){
   cout << "Error: symbol must be not like player1 and either x or o. Try again" << endl;
   cout << "Enter player2 symbol: ";
   cin >> player2Symbol;
}
HumanPlayer player2(Player2Name,player2Symbol);
Player<char>* players[2] = {&player1, &player2};
GameManager<char> gameManager(&board, players);
gameManager.run();
break;
    }

    case 2:
    {
    string PlayerName;
    cout << "Enter Player name: ";
    cin.ignore();
    getline(cin,PlayerName);
    char playerSymbol;
    cout << "Enter player symbol (x or o): ";
    cin >> playerSymbol;
    while(playerSymbol != 'x' && playerSymbol != 'o'){
    cout << "Error: symbol must be either x or o. Try again" << endl;
    cout << "Enter player1 symbol (x or o): ";
    cin >> playerSymbol;
    }
    HumanPlayer player(PlayerName,playerSymbol);
    char botSymbol = (playerSymbol == 'x') ? 'o' : 'x';
    RandomAIPlayer bot(botSymbol);
    Player<char>* players[2] = {&player, &bot};
    GameManager<char> gameManager(&board, players);
    gameManager.run();
    break;
}
  default:
   cout << "invalid choice " << endl;
}
        break;
        }

        case 3:
        {
    
         break;
        }

        case 4:
        {
        Player<char>* players[2];
    Board<char>* Pb = new word_X_O_board<char>();
    string playerXName, player2Name;
    cout << "Welcome to FCAI word X-O Game. :)\n";
    int setup;
    // Set up player 1
    cout << "Choose Player X type:\n";
    cout << "1. Human\n";
    cout << "2. Random Computer\n";
    cout << "3. smart AI\n";
    cin >> setup;
    switch(setup) {
        case 1:
            cout << "Enter Player 1 name: ";
            cin >> playerXName;
            players[0] = new word_X_O_player<char>(playerXName);
            break;
        case 2:
            players[0] = new word_X_O_aplayer<char>();
            break;
        case 3:
            players[0] = new word_X_O_AI_player<char>();
            players[0]->setBoard(Pb);
            break;
        default:
            cout << "Invalid choice for Player 1. Exiting the game.\n";
            return 0;
    }
    cout << "Choose Player 2 type:\n";
    cout << "1. Human\n";
    cout << "2. Random Computer\n";
    cout << "3. smart AI\n";
    cin >> setup;
    switch(setup) {
        case 1:
            cout << "Enter Player 2 name: ";
            cin >> player2Name;
            players[1] = new word_X_O_player<char>(player2Name);
            break;
        case 2:
            players[1] = new word_X_O_aplayer<char>();
            break;
        case 3:
            players[1] = new word_X_O_AI_player<char>();
            players[1]->setBoard(Pb);
            break;
        default:
            cout << "Invalid choice for Player 2. Exiting the game.\n";
            return 0;
    }
    GameManager<char> word_X_O_Gm(Pb, players);
    word_X_O_Gm.run();
    delete Pb;
    for (int i = 0; i < 2; ++i) {
        delete players[i];
    }
          break;
        }

        case 5:
        {
         cout << "welcome to our Numerical Tic Tac Toe game " << endl;
FirstNumericalTicTacToe board;
srand(static_cast<unsigned int>(time(0)));
int option;
cout << "you want to play against a player or a bot(1 for player 2 for bot):";
cin >> option;
cin.ignore();
switch(option){
    case 1:
    {
        string Player1Name;
cout << "Enter Player1 name: ";
getline(cin,Player1Name);
char player1Symbol;
cout << "Enter even or odd ('e' for even 'o' for odd) ";
cin >> player1Symbol;
while(player1Symbol != 'e' && player1Symbol != 'o'){
   cout << "Error: symbol must be either even or odd. Try again" << endl;
   cout << "Enter player1 symbol ('e' for even 'o' for odd): ";
   cin >> player1Symbol;
}
SecondNumericalTicTacToe player1(Player1Name,player1Symbol);

string Player2Name;
cout << "Enter player2 name: ";
cin.ignore();
getline(cin,Player2Name);
char player2Symbol;
cout << "Enter even or odd ('e' for even 'o' for odd): ";
cin >> player2Symbol;
while(player2Symbol == player1Symbol || (player2Symbol != 'e' && player2Symbol != 'o')){
   cout << "Error: symbol must be either even or odd. Try again" << endl;
   cout << "Enter player2 symbol: ";
   cin >> player2Symbol;
}
SecondNumericalTicTacToe player2(Player2Name,player2Symbol);
Player<char>* players[2] = {&player1, &player2};
GameManager<char> gameManager(&board, players);
gameManager.run();
break;
    }

    case 2:
    {
string PlayerName;
cout << "Enter Player name: ";
getline(cin,PlayerName);
char playerSymbol;
cout << "Enter even or odd ('e' for even 'o' for odd) ";
cin >> playerSymbol;
while(playerSymbol != 'e' && playerSymbol != 'o'){
   cout << "Error: symbol must be either even or odd. Try again" << endl;
   cout << "Enter player1 symbol ('e' for even 'o' for odd): ";
   cin >> playerSymbol;
    }
    SecondNumericalTicTacToe player(PlayerName,playerSymbol);
    char botSymbol = (playerSymbol == 'o') ? 'e' : 'o';
    RandomNumericalTicTacToe bot(botSymbol);
    Player<char>* players[2] = {&player, &bot};
    GameManager<char> gameManager(&board, players);
    gameManager.run();
    break;
}
default:
cout<< "invalid choice" << endl;
}
         break;
        }
        case 6:
        {
         
          break;
        }
        case 7:
        {
          Player<char>* players[2];
        Board<char>* db = new four_by_four_X_O_board<char>();
        int player;
        cout << "Choose Player X type:\n";
        cout << "1. Human\n";
        cout << "2. Random Computer\n";
        cin >> player;
        string playerXName,player2Name;
        switch(player) {
            case 1:
                cout << "Enter Player 1 name: ";
                cin >> playerXName;
                players[0] = new four_by_four_player<char>(playerXName,'X');
                break;
            case 2:
                players[0] = new four_by_four_randomplayer<char>('X');
                break;
            default:
                cout << "Invalid choice for Player 1. Exiting the game.\n";
                break;
        }
        cout << "Choose Player 2 type:\n";
        cout << "1. Human\n";
        cout << "2. Random Computer\n";
        cin >> player;
        switch(player) {
            case 1:
                cout << "Enter Player 2 name: ";
                cin >> player2Name;
                players[1] = new four_by_four_player<char>(player2Name,'O');
                break;
            case 2:
                players[1] = new four_by_four_randomplayer<char>('O');
                break;
            default:
                cout << "Invalid choice for Player 2. Exiting the game.\n";
                break;
        }
        GameManager<char> four_X_O_Gm(db, players);
        four_X_O_Gm.run();
        delete db;
        for (int i = 0; i < 2; ++i) {
            delete players[i];
        }
        return 0;
        }
        case 8:
        {
         cout << "Welcome to Ultimate Tic Tac Toe!" << endl;
Ultimate<char> board;
   int option;
cout << "You want to play against a player or bot(1 for player 2 for bot): ";
cin >> option;
switch(option){
    case 1:{
    string Player1Name;
    cout << "Enter Player1 name: ";
    cin.ignore();
    getline(cin,Player1Name);
    char player1Symbol;
    cout << "Enter player1 symbol (x or o): ";
    cin >> player1Symbol;
    while(player1Symbol != 'x' && player1Symbol != 'o'){
    cout << "Error: symbol must be either x or o. Try again" << endl;
    cout << "Enter player1 symbol (x or o): ";
    cin >> player1Symbol;
}
Ultimate_Player player1(Player1Name,player1Symbol);

string Player2Name;
cout << "Enter player2 name: ";
cin.ignore();
getline(cin,Player2Name);
char player2Symbol;
cout << "Enter player2 symbol: ";
cin >> player2Symbol;
while(player2Symbol == player1Symbol || (player2Symbol != 'x' && player2Symbol != 'o')){
   cout << "Error: symbol must be not like player1 and either x or o. Try again" << endl;
   cout << "Enter player2 symbol: ";
   cin >> player2Symbol;
}
Ultimate_Player player2(Player2Name,player2Symbol);
Player<char>* players[2] = {&player1, &player2};
GameManager<char> gameManager(&board, players);
gameManager.run();
    break;
        }
        
        case 2:
        {
        string playerName;
    cout << "Enter Player name: ";
    getline(cin, playerName);
    char playerSymbol;
    cout << "Enter Player symbol (x or o): ";
    cin >> playerSymbol;
     Ultimate_Player<char> player(playerName, playerSymbol);
     char symbol = (playerSymbol == 'o') ? 'e':'o';
     Ultimate_Random_Player<char> bot(symbol);
     Player<char>* players[2] = {&player,&bot};
     GameManager game(&board,players);
    game.run();
    break;
        }
     default:
     cout << "invalid choice" << endl;
    }
         break;
        }

        case 9:
        {
            cout << "exiting program" << endl;
            return 0;
        }
        default:
        cout << "invalid choice try again" << endl;
    }
    }
    return 0;
}
#ifndef _3X3X_O_H
#define _3X3X_O_H

#include "BoardGame_Classes.h"

template <typename T>
class X_O_Board:public Board<T> {
public:
    X_O_Board ();
    bool update_board (int x , int y , T symbol);
    void display_board () ;
    bool is_win() ;
    bool is_draw();
    bool game_is_over();

    char get_board_cell(int row, int col) {
        return this->board[row][col];
    }

};

template <typename T>
class X_O_Player : public Player<T> {
public:
    X_O_Player (string name, T symbol);
    void getmove(int& x, int& y) ;

};

template <typename T>
class X_O_Random_Player : public RandomPlayer<T>{
public:
    X_O_Random_Player (T symbol);
    void getmove(int &x, int &y) ;
};





//--------------------------------------- IMPLEMENTATION

#include <iostream>
#include <iomanip>
#include <cctype>  // for toupper()

using namespace std;

// Constructor for X_O_Board
template <typename T>
X_O_Board<T>::X_O_Board() {
    this->rows =3; this->columns = 5;
    this->board = new char*[this->rows];
    for (int i = 0; i < this->rows; i++) {
        this->board[i] = new char[this->columns];
        for (int j = 0; j < this->columns; j++) {
            if (!(i==0 && (j==0 || j==1 || j==3 ||j==4))||
                    !(i==1 && (j==0 || j==4) )) {
                this->board[i][j] = 0;
            }
        }
    }
    this->n_moves = 0;
}

template <typename T>
bool X_O_Board<T>::update_board(int x, int y, T mark) {
    // Only update if move is valid
    if (!(x < 0 || x >= this->rows || y < 0 || y >= this->columns) && (this->board[x][y] == 0|| mark == 0)) {
        if (mark == 0){
            this->n_moves--;
            this->board[x][y] = 0;
        }
        else {
            this->n_moves++;
            this->board[x][y] = toupper(mark);
        }

        return true;
    }
    return false;
}

// Display the board and the pieces on it
template <typename T>
void X_O_Board<T>::display_board() {
    for (int i = 0; i < this->rows; i++) {
        cout << "\n| ";
        for (int j = 0; j < this->columns; j++) {
            if ((i == 0 && (j == 0 || j == 1 || j == 3 || j == 4)) ||
                (i == 1 && (j == 0 || j == 4))) {
                cout << "    ";
                cout << setw(2) << this->board[i][j] << " |";
            }
            else{
                cout << "(" << i << "," << j << ")";
                cout << setw(2) << this->board[i][j] << " |";
            }
        }
        cout << "\n-----------------------------";
    }
    cout << endl;
}

// Returns true if there is any winner
template <typename T>
bool X_O_Board<T>::is_win() {
    // Check rows and columns
    for (int i = 1; i < this->rows; i++) {
        if ((this->board[i][1] == this->board[i][2] && this->board[i][2] == this->board[i][3] && this->board[i][1] != 0) ||
            (this->board[0][2] == this->board[1][2] && this->board[1][2] == this->board[2][2] && this->board[0][2] != 0)) {
            return true;
        }
    }
        if ((this->board[2][0] == this->board[2][1] && this->board[2][1] == this->board[2][2] && this->board[2][0] != 0) ||
            (this->board[2][2] == this->board[2][3] && this->board[2][3] == this->board[2][4] && this->board[2][2] != 0)) {
            return true;
        }

    // Check diagonals
    if ((this->board[0][2] == this->board[1][1] && this->board[1][1] == this->board[2][0] && this->board[0][2] != 0) ||
        (this->board[0][2] == this->board[1][3] && this->board[1][3] == this->board[2][4] && this->board[0][2] != 0)) {
        return true;
    }

    return false;
}

// Return true if 9 moves are done and no winner
template <typename T>
bool X_O_Board<T>::is_draw() {
    return (this->n_moves == 9 && !is_win());
}

template <typename T>
bool X_O_Board<T>::game_is_over() {
    return is_win() || is_draw();
}

//--------------------------------------

// Constructor for X_O_Player
template <typename T>
X_O_Player<T>::X_O_Player(string name, T symbol) : Player<T>(name, symbol) {}

template <typename T>
void X_O_Player<T>::getmove(int& x, int& y) {
    cout << "\nPlease enter your move x and y (0 to 4) separated by spaces: ";
    cin >> x >> y;
   while((x==0 && y==0)|| ( x==0&& y==1)||(x==0&& y==3)||(x==0&& y==4)||(x==1&& y==0)||(x==1&& y==4)) {
       cin >> x >> y;
   }
}

// Constructor for X_O_Random_Player
template <typename T>
X_O_Random_Player<T>::X_O_Random_Player(T symbol) : RandomPlayer<T>(symbol) {
    this->dimension1 = 3;
    this->dimension2 = 5;
    this->num=4;
    this->name = "Random Computer Player";
    srand(static_cast<unsigned int>(time(0)));  // Seed the random number generator
}

template <typename T>
void X_O_Random_Player<T>::getmove(int& x, int& y) {
        x = rand() % this->dimension1;
        y = rand() % this->dimension2;
    while((x==0 && y==0)|| ( x==0&& y==1)||(x==0&& y==3)||(x==0&& y==4)||(x==1&& y==0)||(x==1&& y==4)) {
        x = rand() % this->dimension1;
        y = rand() % this->dimension2;
    }
}
#endif //_3X3X_O_H

#include <iostream>
#include <algorithm>
#include <string>
#include "BoardGame_Classes.h"
#include "3x3X_O.h"   
using namespace std;

int xA,yA;
vector<pair<int,int>>ind = {{0,0},{0,1},{0,2},{0,3},{3,0},{3,1},{3,2},{3,3}};
template <typename T>
class four_by_four_X_O_board : public Board<T>{
public:
    four_by_four_X_O_board(){
        this->rows = this->columns = 4;
        this->board = new char*[this->rows];
        for (int i = 0; i < this->rows; i++) {
            this->board[i] = new char[this->columns];
            for (int j = 0; j < this->columns; j++) {
                if(i == 0){
                   if (j%2 == 0){
                       this->board[i][j] = 'O';
                   } 
                   else{this->board[i][j] = 'X';
                   }
                }
                else if(i == 3){
                    if (j%2 == 0){
                        this->board[i][j] = 'X';
                    }
                    else{this->board[i][j] = 'O';
                    }
                }
                else{
                    this->board[i][j] = 0;
                }
            }
        }
        this->n_moves = 0;
    }
    bool update_board(int x, int y, T mark) {
        if (!(x < 0 || x >= this->rows || y < 0 || y >= this->columns) && (this->board[x][y] == 0|| mark == 0)) {
            if (mark == 0){
                this->n_moves--;
                this->board[x][y] = 0;
            }
            else {
                if(!is_valid(xA,yA,mark)){
                    return false;
                }
                this->n_moves++;
                this->board[x][y] = toupper(mark);
                for(auto i : ind){
                    if(i.first == xA && i.second==yA){
                        i.first = x;
                        i.second = y;
                    }
                }
                remove_cell(xA,yA);
            }
            return true;
        }
        return false;
    }
    bool is_valid(int x, int y , T mark){
        if(this->board[x][y]==mark){
            return true;
        }
        return false;
    }
    void remove_cell(int x , int y){
        this->board[x][y] = 0;
    }
    bool is_win(){
        for (int i = 0; i < this->rows; i++) {
            if ((this->board[i][0] == this->board[i][1] && this->board[i][1] == this->board[i][2] && this->board[i][0] != 0) ||
                (this->board[0][i] == this->board[1][i] && this->board[1][i] == this->board[2][i] && this->board[0][i] != 0) ||
                (this->board[i][1] == this->board[i][2] && this->board[i][1] == this->board[i][3] && this->board[i][1] != 0) ||
                (this->board[1][i] == this->board[2][i] && this->board[1][i] == this->board[3][i] && this->board[1][i] != 0)) {
                return true;
            }
        }
        if ((this->board[0][0] == this->board[1][1] && this->board[1][1] == this->board[2][2] && this->board[0][0] != 0) ||
            (this->board[0][3] == this->board[1][2] && this->board[1][2] == this->board[2][1] && this->board[0][3] != 0) ||
            (this->board[1][1] == this->board[2][2] && this->board[1][1] == this->board[3][3] && this->board[1][1] != 0) ||
            (this->board[1][2] == this->board[2][1] && this->board[1][2] == this->board[3][0] && this->board[1][2] != 0) ||
            (this->board[0][1] == this->board[1][2] && this->board[1][2] == this->board[2][3] && this->board[0][1] != 0) ||
            (this->board[0][2] == this->board[1][1] && this->board[1][1] == this->board[2][0] && this->board[0][2] != 0) ||
            (this->board[1][0] == this->board[2][1] && this->board[1][0] == this->board[3][2] && this->board[1][0] != 0) ||
            (this->board[1][3] == this->board[2][2] && this->board[1][3] == this->board[3][1] && this->board[1][3] != 0)) {
            return true;
        }
        return false;
    }
    bool is_draw(){
        return false;
    }
    bool game_is_over() {
        return is_win();
    }
    void display_board() {
        for (int i = 0; i < this->rows; i++) {
            cout << "\n| ";
            for (int j = 0; j < this->columns; j++) {
                cout << "(" << i << "," << j << ")";
                cout << setw(2) << this->board[i][j] << " |";
            }
            cout << "\n-----------------------------";
        }
        cout << endl;
    }
};
template <typename T>
class four_by_four_player : public Player <T>{
public:
    four_by_four_player(string name, T symbol) : Player<T>(name, symbol){}
    void getmove(int& x, int& y) {
        cout << "enter the ind of the cell you want to move to by space"<<endl;
        cin >> x >> y;
        cout << "enter the ind of the cell you want to use separate by space"<<endl;
        cin >> xA >> yA;
        while(abs(x-xA) + abs(y-yA) != 1){
            cout << "not valid"<<endl;
            cout << "enter the ind of the cell you want to move to by space"<<endl;
            cin >> x >> y;
            cout << "enter the ind of the cell you want to use separate by space"<<endl;
            cin >> xA >> yA;
        }
    }
};
template <typename T>
class four_by_four_randomplayer : public RandomPlayer <T>{
protected:
    vector<pair<int,int>>moves={{0,1},{0,-1},{1,0},{-1,0}};
public:
    four_by_four_randomplayer(T symbol) : RandomPlayer<T>(symbol){
        this->dimension = 4;
        this->name = "Random Computer Player";
        srand(static_cast<unsigned int>(time(0)));  // Seed the random number generator
    }
    void getmove(int& x, int& y) {
        int i,ii ;
        i = rand()%ind.size();
        xA = ind[i].first;
        yA = ind[i].second;
        ii = rand()%moves.size();
        x = moves[ii].first;
        y = moves[ii].second;
        x+=xA;
        y+=yA;
    }
};#include<iostream>
#include <algorithm>
#include <fstream>
#include <string>
#include "BoardGame_Classes.h"
#include "3x3X_O.h"
#include "MinMaxPlayer.h"

using namespace std;
template <typename T>
class pyramid_X_O_Board:public Board<T> {
public:
    pyramid_X_O_Board ();
    bool update_board (int x , int y , T symbol);
    void display_board () ;
    bool is_win() ;
    bool is_draw();
    bool game_is_over();

};

template <typename T>
class pyramid_X_O_Player : public Player<T> {
public:
    pyramid_X_O_Player (string name, T symbol);
    void getmove(int& x, int& y) ;

};

template <typename T>
class pyramid_X_O_Random_Player : public RandomPlayer<T>{
protected:
int dimension1;
int dimension2;
int num;

public:
    pyramid_X_O_Random_Player (T symbol);
    void getmove(int &x, int &y) ;
};





//--------------------------------------- IMPLEMENTATION

#include <iostream>
#include <iomanip>
#include <cctype>  // for toupper()

using namespace std;

// Constructor for pyramid_X_O_Board
template <typename T>
pyramid_X_O_Board<T>::pyramid_X_O_Board() {
    this->rows =3; this->columns = 5;
    this->board = new char*[this->rows];
    for (int i = 0; i < this->rows; i++) {
        this->board[i] = new char[this->columns];
        for (int j = 0; j < this->columns; j++) {
            if (!(i==0 && (j==0 || j==1 || j==3 ||j==4))||
                !(i==1 && (j==0 || j==4) )) {
                this->board[i][j] = 0;
            }
        }
    }
    this->n_moves = 0;
}

template <typename T>
bool pyramid_X_O_Board<T>::update_board(int x, int y, T mark) {
    // Only update if move is valid
    if (!(x < 0 || x >= this->rows || y < 0 || y >= this->columns) && (this->board[x][y] == 0|| mark == 0)) {
        if (mark == 0){
            this->n_moves--;
            this->board[x][y] = 0;
        }
        else {
            this->n_moves++;
            this->board[x][y] = toupper(mark);
        }

        return true;
    }
    return false;
}

// Display the board and the pieces on it
template <typename T>
void pyramid_X_O_Board<T>::display_board() {
    for (int i = 0; i < this->rows; i++) {
        cout << "\n| ";
        for (int j = 0; j < this->columns; j++) {
            if ((i == 0 && (j == 0 || j == 1 || j == 3 || j == 4)) ||
                (i == 1 && (j == 0 || j == 4))) {
                cout << "    ";
                cout << setw(2) << this->board[i][j] << " |";
            }
            else{
                cout << "(" << i << "," << j << ")";
                cout << setw(2) << this->board[i][j] << " |";
            }
        }
        cout << "\n-----------------------------";
    }
    cout << endl;
}

// Returns true if there is any winner
template <typename T>
bool pyramid_X_O_Board<T>::is_win() {
    // Check rows and columns
    for (int i = 1; i < this->rows; i++) {
        if ((this->board[i][1] == this->board[i][2] && this->board[i][2] == this->board[i][3] && this->board[i][1] != 0) ||
            (this->board[0][2] == this->board[1][2] && this->board[1][2] == this->board[2][2] && this->board[0][2] != 0)) {
            return true;
        }
    }
    if ((this->board[2][0] == this->board[2][1] && this->board[2][1] == this->board[2][2] && this->board[2][0] != 0) ||
        (this->board[2][2] == this->board[2][3] && this->board[2][3] == this->board[2][4] && this->board[2][2] != 0)) {
        return true;
    }

    // Check diagonals
    if ((this->board[0][2] == this->board[1][1] && this->board[1][1] == this->board[2][0] && this->board[0][2] != 0) ||
        (this->board[0][2] == this->board[1][3] && this->board[1][3] == this->board[2][4] && this->board[0][2] != 0)) {
        return true;
    }

    return false;
}

// Return true if 9 moves are done and no winner
template <typename T>
bool pyramid_X_O_Board<T>::is_draw() {
    return (this->n_moves == 9 && !is_win());
}

template <typename T>
bool pyramid_X_O_Board<T>::game_is_over() {
    return is_win() || is_draw();
}

//--------------------------------------

// Constructor for pyramid_X_O_Player
template <typename T>
pyramid_X_O_Player<T>::pyramid_X_O_Player(string name, T symbol) : Player<T>(name, symbol) {}

template <typename T>
void pyramid_X_O_Player<T>::getmove(int& x, int& y) {
    cout << "\nPlease enter your move x and y (0 to 4) separated by spaces: ";
    cin >> x >> y;
    while((x==0 && y==0)|| ( x==0&& y==1)||(x==0&& y==3)||(x==0&& y==4)||(x==1&& y==0)||(x==1&& y==4)) {
        cin >> x >> y;
    }
}

// Constructor for pyramid_X_O_Random_Player
template <typename T>
pyramid_X_O_Random_Player<T>::pyramid_X_O_Random_Player(T symbol) : RandomPlayer<T>(symbol) {
    this->dimension1 = 3;
    this->dimension2 = 5;
    this->num=4;
    this->name = "Random Computer Player";
    srand(static_cast<unsigned int>(time(0)));  // Seed the random number generator
}

template <typename T>
void pyramid_X_O_Random_Player<T>::getmove(int& x, int& y) {
    x = rand() % this->dimension1;
    y = rand() % this->dimension2;
    while((x==0 && y==0)|| ( x==0&& y==1)||(x==0&& y==3)||(x==0&& y==4)||(x==1&& y==0)||(x==1&& y==4)) {
        x = rand() % this->dimension1;
        y = rand() % this->dimension2;
    }
}
vector<pair<int,int>> spots = {{0,2},{1,1} , {1,2},{1,3},{2,0},{2,1},{2,2},{2,3},{2,4}};
template <typename T>
class Pyramid_X_O_MinMax_Player : public Player<T> {
public:
    Pyramid_X_O_MinMax_Player(T symbol): Player<T>(symbol) {
        this->name = "ai Player";
        srand(static_cast<unsigned int>(time(0)));
    }
    void getmove(int& x, int& y){
        pair<int, int> bestMove = getBestMove();
        x = bestMove.first;
        y = bestMove.second;
    }
private:
    pair<int, int> getBestMove() {
        if(spots.size() == 1){
            return {spots[0].first,spots[0].second};
        }
        int i , j ;
        pair<int,int> values;
        T opponentSymbol = (this->symbol == 'X') ? 'O' : 'X';
        for(auto k = 0 ; k < spots.size();k++){
            i = spots[k].first ; j = spots[k].second;
            if (this->boardPtr->update_board(i, j, this->symbol)) {
                if (this->boardPtr->is_win()) {
                    this->boardPtr->update_board(i, j, 0); // Undo move
                    for(auto k = 0 ; k < spots.size() ;k++){
                        if(i == spots[k].first && j == spots[k].second){
                            spots.erase(spots.begin()+k);
                        }
                    }
                    return {i, j}; // Winning move found
                }
                this->boardPtr->update_board(i, j, 0);
            }
        }
        for(auto k = 0 ; k < spots.size();k++){
            i = spots[k].first ; j = spots[k].second;
            if (this->boardPtr->update_board(i, j, opponentSymbol)) {
                if (this->boardPtr->is_win()) {
                    this->boardPtr->update_board(i, j, 0); // Undo move
                    for(auto k = 0 ; k < spots.size() ;k++){
                        if(i == spots[k].first && j == spots[k].second){
                            spots.erase(spots.begin()+k);
                        }
                    }
                    return {i, j}; // Block opponent's winning move
                }
                this->boardPtr->update_board(i, j, 0); // Undo move
            }
        }
        int index = rand()%spots.size();
        values = spots[index];
        spots.erase(spots.begin()+index);
        return {values.first,values.second};
    }
};#include <iostream>
#include <algorithm>
#include <fstream>
#include <string>
#include "BoardGame_Classes.h"
#include "3x3X_O.h"
#include "MinMaxPlayer.h"
using namespace std;
string rev(string s){
    string g = s;
    reverse(g.begin(),g.end());
    return g;
}
template <typename T>
class word_X_O_board : public Board<T>{
protected:
    vector<string>words;
public:
    word_X_O_board(){
        this->rows = this->columns = 3;
        this->board = new char*[this->rows];
        for (int i = 0; i < this->rows; i++) {
            this->board[i] = new char[this->columns];
            for (int j = 0; j < this->columns; j++) {
                this->board[i][j] = 0;
            }
        }
        this->n_moves = 0;
        string filename = "dic.txt";
        ifstream file(filename);
        string word;
        while (file >> word) {
            this->words.push_back(word);
        }
        file.close();
    }
    bool update_board(int x, int y, T mark) {
        if (!(x < 0 || x >= this->rows || y < 0 || y >= this->columns) && (this->board[x][y] == 0|| mark == 0)) {
            if (mark == 0){
                this->n_moves--;
                this->board[x][y] = 0;
            }
            else {
                this->n_moves++;
                this->board[x][y] = toupper(mark);
            }
            return true;
        }
        return false;
    }
    bool is_win(){
        for (int i = 0; i < this->rows; i++) {
            for(auto j : this->words){
                if (string(1, this->board[i][0]) + string(1,this->board[i][1]) + string(1,this->board[i][2]) == j ||
                    string(1, this->board[0][i]) + string(1,this->board[1][i]) + string(1,this->board[2][i]) == j ||
                    string(1, this->board[i][0]) + string(1,this->board[i][1]) + string(1,this->board[i][2]) == rev(j) ||
                    string(1, this->board[0][i]) + string(1,this->board[1][i]) + string(1,this->board[2][i]) == rev(j)) {
                    return true;
                }
                if (string(1, this->board[0][0]) + string(1,this->board[1][1]) + string(1,this->board[2][2]) == j ||
                    string(1, this->board[0][2]) + string(1,this->board[1][1]) + string(1,this->board[2][0]) == j ||
                    string(1, this->board[0][0]) + string(1,this->board[1][1]) + string(1,this->board[2][2]) == rev(j) ||
                    string(1, this->board[0][2]) + string(1,this->board[1][1]) + string(1,this->board[2][0]) == rev(j)){
                    return true;
                }
            }
        }
        return false;
    }
    void display_board() {
        for (int i = 0; i < this->rows; i++) {
            cout << "\n| ";
            for (int j = 0; j < this->columns; j++) {
                cout << "(" << i << "," << j << ")";
                cout << setw(2) << this->board[i][j] << " |";
            }
            cout << "\n-----------------------------";
        }
        cout << endl;
    }
    bool is_draw() {
        return (this->n_moves == 9 && !is_win());
    }
    bool game_is_over() {
        return is_win() || is_draw();
    }
};
template <typename T>
class word_X_O_player : public Player<T>{
public:
    word_X_O_player(string name) : Player<T>(name, ' ') {}
    void getmove(int& x, int& y){
        char c;
        cout << "enter char :\n";
        cin >> c;
        this->symbol = toupper(c);
        cout << "\nPlease enter your move x and y (0 to 2) separated by spaces: ";
        cin >> x >> y;
    }
};
template <typename T>
class word_X_O_aplayer : public RandomPlayer<T>{
public:
    word_X_O_aplayer() : RandomPlayer<T>(' ') {
        this->name = "Random Computer Player";
        srand(static_cast<unsigned int>(time(0)));
    }
    void getmove(int& x, int& y) override {
        vector<char>letters = {'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'};
        this->symbol = letters[rand()%letters.size()];
        x = rand() % 3;
        y = rand() % 3;
    }
};
template <typename T>
class word_X_O_AI_player : public RandomPlayer<T>{
protected:
    vector<char>letters = {'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'};
public:
    word_X_O_AI_player() : RandomPlayer<T>(' ') {
        this->name = "AI Computer Player";
        srand(static_cast<unsigned int>(time(0)));
    }
    void getmove(int& x, int& y){
        pair<int, int> bestMove = getBestMove();
        x = bestMove.first;
        y = bestMove.second;
    }
private:
    pair<int, int> getBestMove() {
        for(auto i = 0 ; i < 3 ; i++){
            for(auto j = 0 ; j < 3 ; j++){
                for(auto l : letters) {
                    if (this->boardPtr->update_board(i, j, l)) {
                        if (this->boardPtr->is_win()) {
                            this->boardPtr->update_board(i, j, 0); // Undo move
                            this->symbol = l;
                            return {i, j}; // Winning move found
                        }
                        this->boardPtr->update_board(i, j, 0);
                    }
                }
            }
        }
        int index = rand()%letters.size();
        this->symbol=letters[index];
        return {rand()%3,rand()%3};
    }
};#ifndef _BOARDGAME_CLASSES_H
#define _BOARDGAME_CLASSES_H

#include <string>
#include <vector>
using namespace std;

template <typename T>
class Board {
protected:
    int rows, columns;
    T** board;
    int n_moves = 0;

public:


    /// Return true if move is valid and put it on the board
    /// within board boundaries in an empty cell
    /// Return false otherwise
    virtual bool update_board(int x, int y, T symbol) = 0;

    /// Display the board and the pieces on it
    virtual void display_board() = 0;

    /// Returns true if there is any winner
    virtual bool is_win() = 0;

    /// Return true if all moves are done and no winner
    virtual bool is_draw() = 0;

    /// Return true if the game is over
    virtual bool game_is_over() = 0;
};

template <typename T>
class Player {
protected:
    string name;
    T symbol;
    Board<T>* boardPtr;  // Pointer to the board
public:
    /// Two constructors to initiate players
    /// Give the player a symbol to use in playing
    /// It can be X, O, or others
    /// Optionally, you can give them a name
    Player(string n, T symbol);
    Player(T symbol); // For computer players

    virtual void getmove(int& x, int& y) = 0;
    T getsymbol();
    string getname();
    void setBoard(Board<T>* b);
};

/// This class represents a random computer player
/// that generates random positions x, y
/// If invalid, the game manager asks to regenerate
template <typename T>
class RandomPlayer : public Player<T> {
protected:
    int dimension;
public:
    // Take a symbol and pass it to the parent
    RandomPlayer(T symbol);
    // Generate a random move
    virtual void getmove(int& x, int& y) = 0;
};

template <typename T>
class GameManager {
private:
    Board<T>* boardPtr;
    Player<T>* players[2];
public:
    GameManager(Board<T>*, Player<T>* playerPtr[2]);

    void run();
};


//--------------------------------------- IMPLEMENTATION

#include <iostream>
using namespace std;

template <typename T>
GameManager<T>::GameManager(Board<T>* bPtr, Player<T>* playerPtr[2]) {
    boardPtr = bPtr;
    players[0] = playerPtr[0];
    players[1] = playerPtr[1];
}

template <typename T>
void GameManager<T>::run() {
    int x, y;

    boardPtr->display_board();

    while (!boardPtr->game_is_over()) {
        for (int i : {0, 1}) {
            players[i]->getmove(x, y);
            while (!boardPtr->update_board(x, y, players[i]->getsymbol())) {
                players[i]->getmove(x, y);
            }
            boardPtr->display_board();
            if (boardPtr->is_win()) {
                cout << players[i]->getname() << " wins\n";
                return;
            }
            if (boardPtr->is_draw()) {
                cout << "Draw!\n";
                return;
            }
        }
    }
}


using namespace std;
// Constructor for Player with a name and symbol
template <typename T>
Player<T>::Player(std::string n, T symbol) {
    this->name = n;
    this->symbol = symbol;
}

// Constructor for Player with only a symbol (e.g., for computer players)
template <typename T>
Player<T>::Player(T symbol) {
    this->name = "Computer";
    this->symbol = symbol;
}

// Constructor for RandomPlayer, passing the symbol to the parent Player class
template <typename T>
RandomPlayer<T>::RandomPlayer(T symbol) : Player<T>(symbol) {}

// Getter for player's name
template <typename T>
std::string Player<T>::getname() {
    return this->name;
}

// Getter for player's symbol
template <typename T>
T Player<T>::getsymbol() {
    return this->symbol;
}

// Method to set the board pointer in the Player class
template <typename T>
void Player<T>::setBoard(Board<T>* b) {
    this->boardPtr = b;
}

#endif //_BOARDGAME_CLASSES_H

#include "BoardGame_Classes.h"
#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
using namespace std;

class FourInARowBoard : public Board<char> {
private:
    vector<vector<char>> grid;
    const int winCondition = 4;

public:
    FourInARowBoard() {
        rows = 6;
        columns = 7;
        grid = vector<vector<char>>(rows, vector<char>(columns, ' '));
    }

    bool update_board(int x, int y, char symbol) override {
        if (y < 0 || y >= columns) {
            cout << "Column out of bounds!\n";
            return false;
        }

        for (int i = rows - 1; i >= 0; --i) {
            if (grid[i][y] == ' ') {
                grid[i][y] = symbol;
                ++n_moves;
                return true;
            }
        }
        cout << "Column is full. Choose another column.\n";
        return false;
    }

    void display_board() override {
        for (int i = 0; i < rows; ++i) {
            cout << "|";
            for (int j = 0; j < columns; ++j) {
                cout << " " << grid[i][j] << " |";
            }
            cout << "\n";
            cout << string(columns * 4 + 1, '-') << "\n";
        }
    }

    bool is_win() override {
        // Check horizontal, vertical, and diagonal conditions
        for (int i = 0; i < rows; ++i) {
            for (int j = 0; j <= columns - winCondition; ++j) {
                if (grid[i][j] != ' ' && grid[i][j] == grid[i][j + 1] && grid[i][j] == grid[i][j + 2] && grid[i][j] == grid[i][j + 3])
                    return true;
            }
        }

        for (int i = 0; i <= rows - winCondition; ++i) {
            for (int j = 0; j < columns; ++j) {
                if (grid[i][j] != ' ' && grid[i][j] == grid[i + 1][j] && grid[i][j] == grid[i + 2][j] && grid[i][j] == grid[i + 3][j])
                    return true;
            }
        }

        for (int i = 0; i <= rows - winCondition; ++i) {
            for (int j = 0; j <= columns - winCondition; ++j) {
                if (grid[i][j] != ' ' && grid[i][j] == grid[i + 1][j + 1] && grid[i][j] == grid[i + 2][j + 2] && grid[i][j] == grid[i + 3][j + 3])
                    return true;
            }
        }

        for (int i = 0; i <= rows - winCondition; ++i) {
            for (int j = winCondition - 1; j < columns; ++j) {
                if (grid[i][j] != ' ' && grid[i][j] == grid[i + 1][j - 1] && grid[i][j] == grid[i + 2][j - 2] && grid[i][j] == grid[i + 3][j - 3])
                    return true;
            }
        }

        return false;
    }

    bool is_draw() override {
        return n_moves == rows * columns && !is_win();
    }

    bool game_is_over() override {
        return is_win() || is_draw();
    }
};

class HumanPlayer : public Player<char> {
public:
    HumanPlayer(string name, char symbol) : Player<char>(name, symbol) {}

    void getmove(int& x, int& y) override {
        cout << name << ", enter your move (column 0-6): ";
        cin >> y;
    }
};

class RandomAIPlayer : public RandomPlayer<char> {
public:
    RandomAIPlayer(char symbol) : RandomPlayer<char>(symbol) {}

    void getmove(int& x, int& y) override {
        y = rand() % 7;
        cout << "Computer chooses column " << y << "\n";
    }
};
#ifndef _MINMAXPLAYER_H
#define _MINMAXPLAYER_H

#include "BoardGame_Classes.h"

template <typename T>
class X_O_MinMax_Player : public Player<T> {
public:
    X_O_MinMax_Player(T symbol);

    void getmove(int& x, int& y) override;

private:
    int calculateMinMax(T s, bool isMaximizing);
    std::pair<int, int> getBestMove();
};







//--------------------------------------- IMPLEMENTATION

#include <limits>
#include <algorithm> // For std::max and std::min
using namespace std;
// Constructor for the templated class
template <typename T>
X_O_MinMax_Player<T>::X_O_MinMax_Player(T symbol) : Player<T>(symbol) {
    this->name = "AI Player";
}

// Method to get the best move for the player
template <typename T>
void X_O_MinMax_Player<T>::getmove(int& x, int& y) {
    std::pair<int, int> bestMove = getBestMove();
    x = bestMove.first;
    y = bestMove.second;
}

// Minimax algorithm to evaluate the board
template <typename T>
int X_O_MinMax_Player<T>::calculateMinMax(T s, bool isMaximizing) {
    if (this->boardPtr->is_win()) {
        return isMaximizing ? -1 : 1;
    } else if (this->boardPtr->is_draw()) {
        return 0;
    }

    int bestValue = isMaximizing ? std::numeric_limits<int>::min() : std::numeric_limits<int>::max();
    T opponentSymbol = (s == 'X') ? 'O' : 'X';

    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            if (this->boardPtr->update_board(i, j, s)) {
                int value = calculateMinMax(opponentSymbol, !isMaximizing);
                this->boardPtr->update_board(i, j, 0); // Undo move

                if (isMaximizing) {
                    bestValue = std::max(bestValue, value);
                } else {
                    bestValue = std::min(bestValue, value);
                }
            }
        }
    }

    return bestValue;
}

// Find the best move using the minimax algorithm
template <typename T>
std::pair<int, int> X_O_MinMax_Player<T>::getBestMove() {
    int bestValue = std::numeric_limits<int>::min();
    std::pair<int, int> bestMove = {-1, -1};
    T opponentSymbol = (this->symbol == 'X') ? 'O' : 'X';

    // First, check if we can win in the next move
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            if (this->boardPtr->update_board(i, j, this->symbol)) {
                if (this->boardPtr->is_win()) {
                    this->boardPtr->update_board(i, j, 0); // Undo move
                    return {i, j}; // Winning move found
                }
                this->boardPtr->update_board(i, j, 0); // Undo move
            }
        }
    }

    // Second, check if the opponent can win in their next move and block them
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            if (this->boardPtr->update_board(i, j, opponentSymbol)) {
                if (this->boardPtr->is_win()) {
                    this->boardPtr->update_board(i, j, 0); // Undo move
                    return {i, j}; // Block opponent's winning move
                }
                this->boardPtr->update_board(i, j, 0); // Undo move
            }
        }
    }

    // If no immediate win or block, use MinMax to find the best move
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            if (this->boardPtr->update_board(i, j, this->symbol)) {
                int moveValue = calculateMinMax(this->symbol, false);
                this->boardPtr->update_board(i, j, 0); // Undo move

                if (moveValue > bestValue) {
                    bestMove = {i, j};
                    bestValue = moveValue;
                }
            }
        }
    }

    return bestMove;
}

#endif //_MINMAXPLAYER_H#include <iostream>
#include <string>
#include "BoardGame_Classes.h"  // Header file with class declarations
using namespace std;

// Misere Tic-Tac-Toe Board Class
template <typename T>
class MisereTicTacToeBoard : public Board<T> {
private:
    T board[3][3];  // 3x3 Tic-Tac-Toe board
public:
    MisereTicTacToeBoard();  // Constructor initializes the board
    void display_board() override;  // Display the board
    bool update_board(int x, int y, T symbol) override;  // Update the board
    bool is_win() override;  // Check if a player has won
    bool is_draw() override;  // Check if it's a draw
    bool game_is_over() override;  // Check if the game is over
};

// Constructor for MisereTicTacToeBoard
template <typename T>
MisereTicTacToeBoard<T>::MisereTicTacToeBoard() {
    for (int i = 0; i < 3; ++i)
        for (int j = 0; j < 3; ++j)
            board[i][j] = ' ';  // Initialize all cells to empty
}

// Display the board
template <typename T>
void MisereTicTacToeBoard<T>::display_board() {
    cout << "Board state: \n";
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            cout << board[i][j];
            if (j < 2) cout << " | ";
        }
        cout << endl;
        if (i < 2) cout << "--|---|--" << endl;
    }
}

// Update the board with the player's move
template <typename T>
bool MisereTicTacToeBoard<T>::update_board(int x, int y, T symbol) {
    if (x >= 0 && x < 3 && y >= 0 && y < 3 && board[x][y] == ' ') {
        board[x][y] = symbol;
        return true;
    }
    return false;
}

// Check if there's a winner
template <typename T>
bool MisereTicTacToeBoard<T>::is_win() {
    for (int i = 0; i < 3; ++i) {
        if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][0] != ' ')
            return true;
        if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != ' ')
            return true;
    }

    if ((board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != ' ') ||
        (board[0][2] == board[1][1] && board[1][1] == board[2][0] && board[0][2] != ' '))
        return true;

    return false;
}

// Check if it's a draw
template <typename T>
bool MisereTicTacToeBoard<T>::is_draw() {
    for (int i = 0; i < 3; ++i)
        for (int j = 0; j < 3; ++j)
            if (board[i][j] == ' ') return false;  // Board not full yet
    return !is_win();  // If board is full, check if there's no winner
}

// Check if the game is over (win or draw)
template <typename T>
bool MisereTicTacToeBoard<T>::game_is_over() {
    return is_win() || is_draw();
}

// Human Player Class
template <typename T>
class HumanPlayer : public Player<T> {
public:
    HumanPlayer(string name, T symbol);  // Constructor for human players
    void getmove(int& x, int& y) override;  // Get the player's move
};

// Constructor for Human Player
template <typename T>
HumanPlayer<T>::HumanPlayer(string name, T symbol) : Player<T>(name, symbol) {}

// Get the move from a human player
template <typename T>
void HumanPlayer<T>::getmove(int& x, int& y) {
    cout << this->getname() << "'s turn (" << this->getsymbol() << "):\n";
    cout << "Enter row (0-2): ";
    cin >> x;
    cout << "Enter column (0-2): ";
    cin >> y;
}

int main() {
    MisereTicTacToeBoard<char>* board = new MisereTicTacToeBoard<char>(); // Use the MisereTicTacToeBoard
    HumanPlayer<char>* player1 = new HumanPlayer<char>("Player 1", 'X');
    HumanPlayer<char>* player2 = new HumanPlayer<char>("Player 2", 'O');

    // Set the board for players
    player1->setBoard(board);
    player2->setBoard(board);

    Player<char>* players[2] = { player1, player2 };
    int turn = 0;
    bool gameOver = false;

    // Game loop
    while (!gameOver) {
        int x, y;
        players[turn]->getmove(x, y);

        // Update the board with the player's move
        if (board->update_board(x, y, players[turn]->getsymbol())) {
            board->display_board();

            // Check if the player wins
            if (board->is_win()) {
                // Reversed: the player who loses is actually considered the winner
                cout << players[(turn + 1) % 2]->getname() << " wins!" << endl;
                gameOver = true;
            }
            // Check for a draw
            else if (board->is_draw()) {
                cout << "It's a draw!" << endl;
                gameOver = true;
            }

            // Switch turns
            turn = (turn + 1) % 2;
        }
        else {
            cout << "Invalid move, try again." << endl;
        }
    }

    // Clean up
    delete board;
    delete player1;
    delete player2;

    return 0;
}

 #include "BoardGame_Classes.h"
#include <vector>
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

class FirstNumericalTicTacToe : public Board<char> {
private:
    const int rows = 3;
    const int columns = 3;
    vector<vector<char>> grid;

public:
    FirstNumericalTicTacToe() : grid(rows, vector<char>(columns, ' ')) {}

    void display_board() override {
        for (int i = 0; i < rows; i++) {
            cout << '|';
            for (int j = 0; j < columns; j++) {
                cout << " " << grid[i][j] << " |";
            }
            cout << endl;
            if (i < rows - 1) {
                cout << string(columns * 4 + 1, '-') << endl;
            }
        }
        cout << endl;
    }

    bool update_board(int x, int y, char symbol) override {
        if (x < 0 || x >= rows || y < 0 || y >= columns) {
            cout << "Error: Move is out of bounds." << endl;
            return false;
        }
        if (grid[x][y] != ' ') {
            cout << "Error: Cell is already occupied." << endl;
            return false;
        }

        int number;
        cout << "Enter number from 0 to 9: ";
        cin >> number;

        while (true) {
            bool numberExists = false;
            for (int i = 0; i < rows; i++) {
                for (int j = 0; j < columns; j++) {
                    if (grid[i][j] == ('0' + number)) {
                        numberExists = true;
                        break;
                    }
                }
                if (numberExists)
                    break;
            }
            if (!numberExists)
                break;

            cout << "Error: Number is already entered. Try again: ";
            cin >> number;
        }

        bool isEven = (number % 2 == 0);
        if ((symbol == 'e' && !isEven) || (symbol == 'o' && isEven)) {
            cout << "Error: You must pick an " << (symbol == 'e' ? "even" : "odd") << " number." << endl;
            return false;
        }

        if (number < 0 || number > 9) {
            cout << "Error: Number must be between 0 and 9." << endl;
            return false;
        }

        grid[x][y] = '0' + number;
        return true;
    }

    bool is_win() override {
        const int winCondition = 15;
        for (int i = 0; i < rows; i++) {
            if ((grid[i][0] + grid[i][1] + grid[i][2]) == winCondition) {
                return true;
            }
        }
        for (int j = 0; j < columns; j++) {
            if ((grid[0][j] + grid[1][j] + grid[2][j]) == winCondition) {
                return true;
            }
        }
        if ((grid[0][0] + grid[1][1] + grid[2][2]) == winCondition) {
            return true;
        }
        if ((grid[0][2] + grid[1][1] + grid[2][0]) == winCondition) {
            return true;
        }
        return false;
    }

    bool is_draw() override {
        for (int i = 0; i < rows; ++i) {
            for (int j = 0; j < columns; ++j) {
                if (grid[i][j] == ' ') {
                    return false;
                }
            }
        }
        return !is_win();
    }

    bool game_is_over() override {
        return is_win() || is_draw();
    }
};

class SecondNumericalTicTacToe : public Player<char> {
public:
    SecondNumericalTicTacToe(string playerName, char playerSymbol) : Player<char>(playerName, playerSymbol) {}

    void getmove(int& x, int& y) override {
        cout << name << ", enter your move (Row then Column):\n";
        cout << "Note: Rows and Columns range between 0 and 2.\n";
        cout << "Row: ";
        cin >> x;
        cout << "Column: ";
        cin >> y;
    }
};

class RandomNumericalTicTacToe : public RandomPlayer<char> {
public:
    RandomNumericalTicTacToe(char symbol) : RandomPlayer<char>(symbol) {}

    void getmove(int& x, int& y) override {
        int number;
        bool isEven = (symbol == 'e');
        do {
            x = rand() % 3;
            y = rand() % 3;
            number = rand() % 10;
        } while (!isValidMove(x, y, number, isEven));
        cout << "Computer chooses: Row " << x << " Column " << y << endl;
    }

private:
    bool isValidMove(int x, int y, int number, bool isEven) {
        if ((isEven && number % 2 != 0) || (!isEven && number % 2 == 0)) {
            return false;
        }
        return x >= 0 && x < 3 && y >= 0 && y < 3;
    }
};#ifndef _UltimateTicTacToe
#define _UltimateTicTacToe

#include "BoardGame_Classes.h"
#include <iomanip>

template <typename T>
class Ultimate : public Board<T>
{
private:
    vector<vector<T>> winners;
    pair<bool, char> _is_win(int i, int j);
public:
    Ultimate();
    bool update_board(int x, int y, T symbol);
    void display_board();
    bool is_win();
    bool is_draw();
    bool game_is_over();
};

template <typename T>
Ultimate<T>::Ultimate() : winners(3, vector<T>(3, '\0'))
{
    this->rows = this->columns = 9;
    this->board = new char *[this->rows];
    for (int i = 0; i < this->rows; i++)
    {
        this->board[i] = new char[this->columns];
        for (int j = 0; j < this->columns; j++)
        {
            this->board[i][j] = 0;
        }
    }
    this->n_moves = 0;
}

template <typename T>
bool Ultimate<T>::update_board(int x, int y, T mark)
{
    if (!(x < 0 || x >= this->rows || y < 0 || y >= this->columns) && (this->board[x][y] == 0 || mark == 0) && winners[x / 3][y / 3] == 0)
    {
        if (mark == 0)
        {
            this->n_moves--;
            this->board[x][y] = 0;
        }
        else
        {
            this->n_moves++;
            this->board[x][y] = toupper(mark);
        }
        return true;
    }
    return false;
}

template <typename T>
void Ultimate<T>::display_board()
{
    for (int i = 0; i < this->rows; i++)
    {
        cout << "\n| ";
        for (int j = 0; j < this->columns; j++)
        {
            if (this->board[i][j] == 0)
                cout << "   |";
            else
                cout << setw(2) << this->board[i][j] << " |";
        }
        cout << "\n----------------------------------------";
    }
    cout << endl;
    cout << "minimized version\n";
    for (int i = 0; i < 3; i++)
    {
        cout << "\n| ";
        for (int j = 0; j < 3; j++)
        {
            if (this->winners[i][j] == 0)
                cout << "   |";
            else
                cout << setw(2) << this->winners[i][j] << " |";
        }
        cout << "\n-----------------------------";
    }
    cout << "\n\n";
}

template <typename T>
bool Ultimate<T>::is_win()
{
    for (int i = 0; i < 9; i += 3)
    {
        for (int j = 0; j < 9; j += 3)
        {
            auto it = _is_win(i, j);
            if (it.first  )
            {
                winners[i / 3][j / 3] = it.second;
            }
        }
    }
    for (int i = 0; i < 3; i++)
    {
        if ((winners[i][0] == winners[i][1] && winners[i][1] == winners[i][2] && winners[i][0] != 0) ||
            (winners[0][i] == winners[1][i] && winners[1][i] == winners[2][i] && winners[0][i] != 0))
        {
            this->display_board();
            return true;
        }
    }
    if ((winners[0][0] == winners[1][1] && winners[1][1] == winners[2][2] && winners[0][0] != 0) ||
        (winners[0][2] == winners[1][1] && winners[1][1] == winners[2][0] && winners[0][2] != 0))
    {
        this->display_board();
        return true;
    }
    return false;
}

template <typename T>
pair<bool, char> Ultimate<T>::_is_win(int sr, int sc)
{
    for (int i = 0; i < 3; i++)
    {
        if (this->board[sr + i][sc] == this->board[sr + i][sc + 1] && this->board[sr + i][sc + 1] == this->board[sr + i][sc + 2] && this->board[sr + i][sc] != 0)
        {
            return {true, this->board[sr + i][sc]};
        }
        if (this->board[sr][sc + i] == this->board[sr + 1][sc + i] && this->board[sr + 1][sc + i] == this->board[sr + 2][sc + i] && this->board[sr][sc + i] != 0)
        {
            return {true, this->board[sr][sc + i]};
        }
    }
    if (this->board[sr][sc] == this->board[sr + 1][sc + 1] && this->board[sr + 1][sc + 1] == this->board[sr + 2][sc + 2] && this->board[sr][sc] != 0)
    {
        return {true, this->board[sr][sc]};
    }
    if (this->board[sr][sc + 2] == this->board[sr + 1][sc + 1] && this->board[sr + 1][sc + 1] == this->board[sr + 2][sc] && this->board[sr][sc + 2] != 0)
    {
        return {true, this->board[sr][sc + 2]};
    }
    return {false, '\0'};
}

template <typename T>
bool Ultimate<T>::is_draw()
{
    for(int i = 0;i<9;i+=3)
    {
        for(int j = 0;j<9;j+=3)
        {
            if(winners[i/3][j/3])
            {
                continue;
            }
            for(int k=i;k<i+3;k++)
            {
                for(int l= j;l<j+3;l++)
                {
                    if(this->board[k][l]==0)
                        return false;
                }
            }
        }
    }
    bool ok =!is_win();
    if(ok)
    {
        this->display_board();
    }
    return ok;
}

template <typename T>
bool Ultimate<T>::game_is_over()
{
    return is_win() || is_draw();
}


//player
template <typename T>
class Ultimate_Player : public Player<T> 
{
public:
    Ultimate_Player (string name, T symbol);
    void getmove(int& x, int& y) ;
};
template <typename T>
Ultimate_Player<T>::Ultimate_Player(string name, T symbol) : Player<T>(name, symbol) {}

template <typename T>
void Ultimate_Player<T>::getmove(int& x, int& y) 
{
    cout << "\nPlease enter your move x and y (0 to 8) separated by spaces: ";
    cin >> x >> y;
}

// random player


template <typename T>
class Ultimate_Random_Player : public RandomPlayer<T>
{
public:
    Ultimate_Random_Player (T symbol);
    void getmove(int &x, int &y) ;
};

template <typename T>
Ultimate_Random_Player<T>::Ultimate_Random_Player(T symbol) : RandomPlayer<T>(symbol) {
    this->dimension = 9;
    this->name = "Random Computer Player";
    srand(static_cast<unsigned int>(time(0)));  
}

template <typename T>
void Ultimate_Random_Player<T>::getmove(int& x, int& y) 
{
    x = rand() % this->dimension;  
    y = rand() % this->dimension;
}



#endif
