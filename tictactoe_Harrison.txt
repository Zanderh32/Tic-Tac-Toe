// Online C# Editor for free
// Write, Edit and Run your C# code using C# Online Compiler

using System;

public class GuessingGame
{
    public static void Main(string[] args)
    {
        
        Console.WriteLine("Who goes first X or O");
        string[,] board = {{" "," "," "},{" "," "," "},{" "," "," "}};
        bool XorO = false; 
        bool playing = true;
        string user = Console.ReadLine();

        if(user.Equals("x")){
            XorO = false;
        } else if(user.Equals("o")){
            XorO = true;
        }
        while(playing){
            Console.WriteLine(printBoard(board));
            if(checkWinner(board, "X")){
                Console.WriteLine("X's Win!");
                break;
            } else if(checkWinner(board, "O")){
                Console.WriteLine("O's Win!");
                break;
            } else if(checkWinner(board, "O") == false && checkWinner(board, "X") == false && checkFull(board) == true){
                Console.WriteLine("Tie!");
                break;
            }
            if(XorO == false){
                Console.WriteLine("Where do you want to place your X");
                Console.Write("please use index's (0,0) being top left");
                int r = Convert.ToInt32(Console.ReadLine());
                int c = Convert.ToInt32(Console.ReadLine());
                makeMove(r,c,board,"X");
                if(checkWinner(board, "X") == false){
                    XorO = true;
                } else {
                    Console.Write("X has won!");
                }

            } else if(XorO == true){
                Console.WriteLine("Where do you want to place your Y");
                Console.Write("please use index's (0,0) being top left");
                int r = Convert.ToInt32(Console.ReadLine());
                int c = Convert.ToInt32(Console.ReadLine());
                makeMove(r,c,board,"O");
                if(checkWinner(board, "O") == false){
                    XorO = false;
                } else {
                    Console.Write("O has won!");
                }
            }

        }
        Console.WriteLine();
        playing = false;
        
        Console.WriteLine("Would you like to play again!  Y/N");
        string s = Console.ReadLine();
        if(s.Equals("y")){
            Main(args);
        } else if(s.Equals("n")){
            Environment.Exit(0);
        }

        
    }
    public static string printBoard(string[,] arr){
        int up1 = arr.GetUpperBound(0);
        int up2 = arr.GetUpperBound(1);
        for(int r = 0; r < up1; r++){
            if(r > 0 && r < up1){
                Console.WriteLine(" ");
                Console.WriteLine("-----");
            }
            for(int c = 0; c < up2; c++){
                Console.Write(arr[r,c]);
                if(c < up2){
                    Console.Write("|");
                }
            }
        }

        return "";
    }

    public static void makeMove(int r, int c, string[,] arr, string XorY){
        bool hehe = true;
        while(hehe){
            if(arr[r,c] == " "){
                arr[r,c] = XorY;
                hehe = false;
            } else if(arr[r,c] != " "){
                Console.WriteLine("Someone has already picked this spot");
                break;
            }
        }
    }

    public static bool checkWinner(string[,] b, string s) {
        if(b[0,0].Equals(s) && b[0,1].Equals(s) && b[0,2].Equals(s) ||
        b[1,0].Equals(s) && b[1,1].Equals(s) && b[1,2].Equals(s) ||
        b[2,0].Equals(s) && b[2,1].Equals(s) && b[2,2].Equals(s) ||
        b[0,0].Equals(s) && b[1,0].Equals(s) && b[2,0].Equals(s) ||
        b[0,1].Equals(s) && b[1,1].Equals(s) && b[2,1].Equals(s) ||
        b[0,2].Equals(s) && b[1,2].Equals(s) && b[2,2].Equals(s) ||
        b[0,0].Equals(s) && b[1,1].Equals(s) && b[2,2].Equals(s) ||
        b[0,2].Equals(s) && b[1,1].Equals(s) && b[2,0].Equals(s)) {
            return true;
        }
        else {
            return false;
        }
    }

    public static bool checkFull(string[,] arr){
        int up1 = arr.GetUpperBound(0);
        int up2 = arr.GetUpperBound(1);
        for(int i = 0; i < up1; i ++){
            for(int j = 0;  j < up2; j++){
                if(arr[i,j].Equals(" ")){
                    return false;
                }
            }
        }
        return true;
    }
}