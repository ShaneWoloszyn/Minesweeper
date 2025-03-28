import java.util.*;

class Main {
  public static void initializeBoard(String[][] board, int size) {
    int num = 0;
    String red = "\u001B[31m";
    String blue = "\u001B[34m";
    for (int i = 0; i < size; i++) {
      for (int p = 0; p < size; p++) {
        if(num % 2 == 0) {
          board[i][p] = red +"X"+"\033[0m";
        } else {
          board[i][p] = blue +"X"+"\033[0m";
        }
        num++;
      }
    }
  }

  public static void printBoard(String[][] board, int size) {
    for (int i = 0; i < size; i++) {
      for (int p = 0; p < size; p++) {
        System.out.print(board[i][p] + " ");
      }
      System.out.print("\n");
    }
  }

  public static int checkMines(int[][] board, int size) {
    int count = 0;
    for (int i = 0; i < size; i++) {
      for (int p = 0; p < size; p++) {
        if (board[i][p] == 1) {
          count++;
        }
      }
    }
    return count;
  }

  public static void initializeMineBoard(int[][] board, int size, int mines) {
    for (int i = 0; i < size; i++) {
      for (int p = 0; p < size; p++) {
        board[i][p] = 0;
      }
    }
    Random rand = new Random();

    int x, y;
    while (checkMines(board, size) < mines) {
      x = rand.nextInt(0, size);
      y = rand.nextInt(0, size);
      board[x][y] = 1;
    }
  }

  public static void printMineBoard(int[][] board, int size) {
    for (int i = 0; i < size; i++) {
      for (int p = 0; p < size; p++) {
        System.out.print(board[i][p] + " ");
      }
      System.out.print("\n");
    }
  }

  public static boolean checkTurn(int[][] mineBoard, String[][] board, int row, int column) {
    if (mineBoard[row][column] == 1) {
      return false;
    } else {
      return true;
    }
  }

  public static int surrounding(int[][] mineBoard, int row, int column, int size) {
    int num = 0;
    if (row == 0 && column == 0) {
      num += mineBoard[row][column];
      num += mineBoard[row + 1][column + 1];
      num += mineBoard[row][column + 1];
      return num;
    }
    if (column == size - 1 && row == size - 1) {
      num += mineBoard[row][column];
      num += mineBoard[row - 1][column];
      num += mineBoard[row - 1][column - 1];
      num += mineBoard[row][column - 1];
      return num;
    }
    if (column == size - 1 && row == 0) {
      num += mineBoard[row][column];
      num += mineBoard[row + 1][column];
      num += mineBoard[row][column - 1];
      num += mineBoard[row + 1][column - 1];
      return num;
    }
    if (row == size - 1 && column == 0) {
      num += mineBoard[row][column];
      num += mineBoard[row][column + 1];
      num += mineBoard[row - 1][column + 1];
      num += mineBoard[row - 1][column];
      return num;
    }
    if (row == size - 1) {
      num += mineBoard[row][column];
      num += mineBoard[row][column + 1];
      num += mineBoard[row - 1][column + 1];
      num += mineBoard[row - 1][column];
      num += mineBoard[row - 1][column - 1];
      num += mineBoard[row][column - 1];
      return num;
    }
    if (column == size - 1) {
      num += mineBoard[row][column];
      num += mineBoard[row + 1][column];
      num += mineBoard[row - 1][column];
      num += mineBoard[row - 1][column - 1];
      num += mineBoard[row][column - 1];
      num += mineBoard[row + 1][column - 1];
      return num;
    }
    if (row == 0) {
      num += mineBoard[row][column];
      num += mineBoard[row + 1][column];
      num += mineBoard[row + 1][column + 1];
      num += mineBoard[row][column + 1];
      num += mineBoard[row][column - 1];
      num += mineBoard[row + 1][column - 1];
      return num;
    }
    if (column == 0) {
      num += mineBoard[row][column];
      num += mineBoard[row + 1][column];
      num += mineBoard[row + 1][column + 1];
      num += mineBoard[row][column + 1];
      num += mineBoard[row - 1][column + 1];
      num += mineBoard[row - 1][column];
      return num;
    }
    num += mineBoard[row][column];
    num += mineBoard[row + 1][column];
    num += mineBoard[row + 1][column + 1];
    num += mineBoard[row][column + 1];
    num += mineBoard[row - 1][column + 1];
    num += mineBoard[row - 1][column];
    num += mineBoard[row - 1][column - 1];
    num += mineBoard[row][column - 1];
    num += mineBoard[row + 1][column - 1];
    return num;
  }
  public static String[][] ifZero(int[][] mineBoard, String[][] board, int row, int column, int size) {
    if(row == 0 && column == 0) { //top left
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row+1][column+1] = Integer.toString(surrounding(mineBoard, row+1, column+1, size));
      board[row][column+1] = Integer.toString(surrounding(mineBoard, row, column+1, size));
      board[row+1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
    } else if(row == 0 && column == (size - 1)) { //top right
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row+1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column-1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row+1][column-1] = Integer.toString(surrounding(mineBoard, row+1, column-1, size));
    } else if(row == (size - 1) && column == (size - 1)) { //bottom right
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row-1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column-1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row-1][column-1] = Integer.toString(surrounding(mineBoard, row+1, column-1, size));
    } else if(row == (size - 1) && column == (size - 1)) { //bottom left
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row-1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column+1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row-1][column+1] = Integer.toString(surrounding(mineBoard, row+1, column-1, size));
    } else if(row == 0) { //first row 
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row+1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column-1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row][column+1] = Integer.toString(surrounding(mineBoard, row, column+1, size));
      board[row+1][column-1] = Integer.toString(surrounding(mineBoard, row+1, column-1, size));
      board[row+1][column+1] = Integer.toString(surrounding(mineBoard, row+1, column+1, size));
    } else if(column == 0) { //first column
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row-1][column] = Integer.toString(surrounding(mineBoard, row-1, column, size));
      board[row+1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column+1] = Integer.toString(surrounding(mineBoard, row, column+1, size));
      board[row-1][column+1] = Integer.toString(surrounding(mineBoard, row-1, column+1, size));
      board[row+1][column+1] = Integer.toString(surrounding(mineBoard, row+1, column+1, size));
    } else if(column == size - 1) { //last column
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row-1][column] = Integer.toString(surrounding(mineBoard, row-1, column, size));
      board[row+1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column-1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row-1][column-1] = Integer.toString(surrounding(mineBoard, row-1, column-1, size));
      board[row+1][column-1] = Integer.toString(surrounding(mineBoard, row+1, column-1, size));
    } else if(row == size -1) { // last row
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row-1][column] = Integer.toString(surrounding(mineBoard, row-1, column, size));
      board[row][column-1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row][column+1] = Integer.toString(surrounding(mineBoard, row, column+1, size));
      board[row-1][column-1] = Integer.toString(surrounding(mineBoard, row-1, column-1, size));
      board[row-1][column+1] = Integer.toString(surrounding(mineBoard, row-1, column+1, size));
    } else {
      board[row][column] = Integer.toString(surrounding(mineBoard, row, column, size));
      board[row-1][column] = Integer.toString(surrounding(mineBoard, row-1, column, size));
      board[row+1][column] = Integer.toString(surrounding(mineBoard, row+1, column, size));
      board[row][column-1] = Integer.toString(surrounding(mineBoard, row, column-1, size));
      board[row][column+1] = Integer.toString(surrounding(mineBoard, row, column+1, size));
      board[row-1][column-1] = Integer.toString(surrounding(mineBoard, row-1, column-1, size));
      board[row-1][column+1] = Integer.toString(surrounding(mineBoard, row-1, column+1, size));
      board[row+1][column-1] = Integer.toString(surrounding(mineBoard, row+1, column-1, size));
      board[row+1][column+1] = Integer.toString(surrounding(mineBoard, row+1, column+1, size));
    }
    return board;
  }
  public static boolean doTurn(int[][] mineBoard, String[][] board, boolean valid, int size) {
    Scanner input = new Scanner(System.in);
    int row = 0, column = 0, surrounding;
    String toSplit;
    try {
        System.out.println("\nEnter row and column where you would like to check (ex. '1 1')?");
        toSplit = input.nextLine();
        String[] splitStr = toSplit.split("\\s+");
        row = Integer.parseInt(splitStr[0]) - 1;
        column = Integer.parseInt(splitStr[1]) - 1;
    } catch(Exception x){
        System.out.println("Improper formatting, reset and follow the correct format -> 'row column' ");
        System.exit(0);
    }
    if (checkTurn(mineBoard, board, row, column) == true) {
      surrounding = surrounding(mineBoard, row, column, size);
      if(surrounding == 0) {
        board = ifZero(mineBoard, board, row, column,size);
      } else {
        board[row][column] = Integer.toString(surrounding);
      }
      return true;
    } else {
      System.out.println("\nBOOM! You lost.");
      return false;
    }
  }

  public static boolean isWon(int[][] mineBoard, String[][] board, int size) {
    int count = 0;
    for (int i = 0; i < size; i++) {
      for (int p = 0; p < size; p++) {
        if (board[i][p].equalsIgnoreCase("X")) {
          count++;
        }
      }
    }
    if (size == 7) {
      if (count == 10) {
        return true;
      }
    } else if (size == 9) {
      if (count == 25) {
        return true;
      }
    } else {
      if (count == 40) {
        return true;
      }
    }
    return false;
  }

  public static void main(String[] args) {

    Scanner input = new Scanner(System.in);
    int size = 0;
    int mines = 0;
    String p;
    System.out.println("Hi, welcome to Minesweeper. Would you like to play:\n\tEasy(7x7)\n\tMedium(9x9)\n\tHard(11x11)");
    p = input.nextLine();
    if (p.equalsIgnoreCase("Easy")) {
      size = 7;
      mines = 10;
    } else if (p.equalsIgnoreCase("Medium")) {
      size = 9;
      mines = 25;
    } else if (p.equalsIgnoreCase("Hard")) {
      size = 11;
      mines = 40;
    }
    boolean valid = true;
    int[][] mineBoard = new int[size][size];
    initializeMineBoard(mineBoard, size, mines);
    String[][] board = new String[size][size];
    initializeBoard(board, size);
    while (valid == true) {
      printBoard(board, size);
      valid = doTurn(mineBoard, board, valid, size);
      if (isWon(mineBoard, board, size) == true) {
        valid = false;
      }
    }
    if (isWon(mineBoard, board, size) == true) {
      System.out.println("Congrats! You Won");
    }

  }
}
