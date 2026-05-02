# tic-tac-too
import java.util.Scanner;

public class TicTacToe {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        char[][] board = {
            {' ', ' ', ' '},
            {' ', ' ', ' '},
            {' ', ' ', ' '}
        };

        char player = 'X';
        boolean gameOver = false;

        while (!gameOver) {
            System.out.println("\nCurrent Board:");
            for (int i = 0; i < 3; i++) {
                System.out.println(board[i][0] + " | " + board[i][1] + " | " + board[i][2]);
                if (i < 2) System.out.println("--+---+--");
            }

            System.out.print("Player " + player + " enter row and column (0-2): ");
            int row = sc.nextInt();
            int col = sc.nextInt();

            if (row < 0 || row > 2 || col < 0 || col > 2 || board[row][col] != ' ') {
                System.out.println("Invalid move! Try again.");
                continue;
            }

            board[row][col] = player;

            // Check rows, columns, diagonals
            for (int i = 0; i < 3; i++) {
                if (board[i][0] == player && board[i][1] == player && board[i][2] == player)
                    gameOver = true;
                if (board[0][i] == player && board[1][i] == player && board[2][i] == player)
                    gameOver = true;
            }

            if (board[0][0] == player && board[1][1] == player && board[2][2] == player)
                gameOver = true;

            if (board[0][2] == player && board[1][1] == player && board[2][0] == player)
                gameOver = true;

            if (gameOver) {
                System.out.println("Player " + player + " wins!");
                break;
            }

            player = (player == 'X') ? 'O' : 'X';
        }

        sc.close();
    }
}
