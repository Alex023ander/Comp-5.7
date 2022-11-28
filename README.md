# Comp-5.7
Rock paper scissors

import java.util.Scanner;
public class Comp57 {

        static Scanner scan = new Scanner(System.in);
        
        static String choices[] = {"rock", "paper", "scissors"};
        
        static int playOneRound(){
            System.out.println("\nEnter 0, 1 or 2:(0)rock,(1)paper,(2)scissors>>");
            int choice = scan.nextInt();
            
            if(choice < 0 || choice > 2){
            System.out.println("Invalid choice");
            return playOneRound();
        }
            //setting user choice using the array and entered number
            String userChoice = choices[choice];
            //generating a number between 0 and 2 for computer
            int num = (int)(Math.random()*3);
            //setting computer choice
            String compChoice = choices[num];
            //displaying choice made
            System.out.println("Computer chose "+ compChoice + ", you chose "
                            + userChoice + ", ");
            //Determining Winners
            if(compChoice.equals("rock") && userChoice.equals("rock")){
                System.out.println("It's a draw!");
                return 0; //draw
            }
            else if(compChoice.equals("rock") && userChoice.equals("paper")){
                System.out.println("Paper beats Rock, you win!");
                return -1; //user
            }
            else if(compChoice.equals("rock") && userChoice.equals("scissors")){
                System.out.println("Rock beats Scissors, computer wins!");
                return 1; //computer
            }
            else if(compChoice.equals("paper") && userChoice.equals("rock")){
                System.out.println("Paper beats Rock, computer wins!");
                return 1;
            }
            else if(compChoice.equals("paper") && userChoice.equals("paper")){
                System.out.println("It's a draw!");
                return 0;
            }
            else if(compChoice.equals("paper") && userChoice.equals("scissors")){
                System.out.println("Scissors beat paper, you win!");
                return -1;
            }
            else if(compChoice.equals("scissors") && userChoice.equals("rock")){
                System.out.println("Rock beats Scissors, you win!");
                return -1;
            }
            else if(compChoice.equals("scissors") && userChoice.equals("paper")){
                System.out.println("Scissors beat Paper, computer wins!");
                return 1;
            }
            else{
                System.out.println("It's a draw!");
                return 0;
            }
            
        }        
    public static void main(String[] args) {
        //initializing counters
        int wins = 0;
        int losses = 0;
        int ties = 0;
        String ch = "y";
                
        while(ch.equalsIgnoreCase("Y")){
            int result = playOneRound();
            
            if(result == -1){
                wins++;
            }
            else if(result == 1){
                losses++;
            }else{
                ties++;
            }
            System.out.println("Another game? (y/n): ");
            ch = scan.next();
        }
        System.out.println("\nNumber of wins: "+ wins);
        System.out.println("\nNumber of losses: "+ losses);
        System.out.println("\nNumber of ties: "+ ties);
        }
}
