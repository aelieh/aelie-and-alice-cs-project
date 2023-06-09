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

    