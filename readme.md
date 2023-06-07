import java.io.*;
import java.util.*;

public class TicTacToeGame implements Serializable {
    private static final long serialVersionUID = 1L;
    private HashMap<Integer, Character> board;
    private char currentPlayer;
    private boolean gameEnded;

    public TicTacToeGame() {
        board = new HashMap<>();
        currentPlayer = 'X';
        gameEnded = false;

        for (int i = 1; i <= 9; i++) {
            board.put(i, ' ');
        }
    }

    public void playGame() {
        Scanner scanner = new Scanner(System.in);

        while (!gameEnded) {
            drawBoard();
            System.out.println("Player " + currentPlayer + "'s turn. Enter a position (1-9):");

            try {
                int position = scanner.nextInt();
                makeMove(position);
            } catch (InputMismatchException e) {
                System.out.println("Invalid input! Please enter a number between 1 and 9.");
                scanner.nextLine(); // Clear input buffer
            } catch (IllegalArgumentException e) {
                System.out.println(e.getMessage());
            }
        }

        drawBoard();
        scanner.close();
    }

    public void makeMove(int position) {
        if (position < 1 || position > 9) {
            throw new IllegalArgumentException("Invalid position! Please enter a number between 1 and 9.");
        }

        if (board.get(position) != ' ') {
            throw new IllegalArgumentException("Position already occupied! Choose another position.");
        }

        board.put(position, currentPlayer);
        if (checkWin()) {
            gameEnded = true;
            System.out.println("Player " + currentPlayer + " wins!");
        } else if (isBoardFull()) {
            gameEnded = true;
            System.out.println("It's a draw!");
        } else {
            currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
        }
    }