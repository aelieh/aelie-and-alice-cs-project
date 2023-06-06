import java.io.*;
import java.util.*;

public class TicTacToeGame implements Serializable {
    private static final long serialVersioUID = 1L;
    private HashMap<Integer, Character> board;
    private char currentPlayer;
    private boolean gameEnded;

    public TicTacToeGame() {
        board = new Hashmap<>();
        currentPlayer = 'X';
        gameEnded = false;

        for (int i = 1; i<=9; i++) {
            board.put(i, ' ');
        }
    }

    public void playGame() {
        Scanner scanner = new Scanner(System.in);

        while (!gameEnded) {
            drawBoard();
            System.out.println("Player " + currentPlayer + "'s turn. Enter")
        }
    }
}