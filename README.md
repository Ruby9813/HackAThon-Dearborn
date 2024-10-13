# HackAThon-Dearborn
Hackathon Dearborn Project:

Here's the code: 


#include <iostream>
using namespace std;

void drawBoard(char board[3][3])
{
    cout << "-------------" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "| ";
        for (int j = 0; j < 3; j++) {
            cout << board[i][j] << " | ";
        }
        cout << endl << "-------------" << endl;
    }
}

// to check for a win
bool checkWin(char board[3][3], char player)
{
    // Check rows, columns, and diagonals
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == player && board[i][1] == player
            && board[i][2] == player)
            return true;
        if (board[0][i] == player && board[1][i] == player
            && board[2][i] == player)
            return true;
    }
    if (board[0][0] == player && board[1][1] == player
        && board[2][2] == player)
        return true;
    if (board[0][2] == player && board[1][1] == player
        && board[2][0] == player)
        return true;
    return false;
}

int main()
{
    char playerX; 
    char playerO; 
    // Board
    char board[3][3] = { { ' ', ' ', ' ' },
                         { ' ', ' ', ' ' },
                         { ' ', ' ', ' ' } };
    char player = 'X';
    int row, col;
    int turn;

    cout << "Welcome to Tic-Tac-Toe!" << endl;

 
    for (turn = 0; turn < 9; turn++) {
      
        drawBoard(board);

        while (true) {
            cout << "Player " << player
                << ", enter row (0-2) and column (0-2): ";
            cin >> row >> col;

            if (board[row][col] != ' ' || row < 0 || row > 2
                || col < 0 || col > 2) {
                cout << "Invalid move. Try again." << endl;
            }
            else {
                break; 
            }
        }

        //Moves
        board[row][col] = player;

        if (checkWin(board, player)) {
            drawBoard(board);
            cout << "Player " << player << " wins!" << endl;
            return 0; 
        }
        
       //Players X and O
        player = (player == 'X') ? 'O' : 'X';
    }

    drawBoard(board);

    if (turn == 9 && !checkWin(board, 'X')
        && !checkWin(board, 'O')) {
        cout << "It's a draw!" << endl;
    }
    return 0;
}
