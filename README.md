# OIBSIP
#Number Guessing Game
#The fun and easy project “Guess the Number” is a short Java project that allows the user to guess the number generated by the computer & involves the following steps:
#The system generates a random number from a given range, say 1 to 100.
#The user is prompted to enter their given number in a displayed dialogue box.
#The computer then tells if the entered number matches the guesses number or it is higher/lower than the generated number.
#The game continues under the user guessing the number.
#You can also incorporate further details as:
#Limiting the number of attempts.
#Adding more rounds.
#Displaying score.
#Giving points based on the number of attempts.

#Code:-

import java.util.Random;
import java.util.Scanner;

public class task2 {
    private static final int MIN_RANGE = 1;
    private static final int MAX_RANGE = 100;
    private static final int MAX_ATTEMPTS = 10;
    private static final int MIN_ROUNDS = 3;

    public static void main(String[] args) {
        Random random = new Random();
        Scanner sc = new Scanner(System.in);
        int totalScore = 0;

        System.out.println("NUMBER GUESSING GAME");
        System.out.println("Total number of Rounds: 3");
        System.out.println("Attempts to Guess Number in each round: 10\n");

        for (int i = 1; i <= MIN_ROUNDS; i++) {
            int number = random.nextInt(MAX_RANGE) + MIN_RANGE;
            int attempts = 0;

            System.out.printf("Round %d: Guess the number between %d and %d in %d attempts.\n", 
            		i, MIN_RANGE, MAX_RANGE, MAX_ATTEMPTS);
            while (attempts < MAX_ATTEMPTS) {
                System.out.print("Enter your guess: ");
                int guess_number = sc.nextInt();
                attempts++;

                if (guess_number == number) {
                    int score = MAX_ATTEMPTS - attempts;
                    totalScore += score;
                    System.out.printf("Hurray! Number Guessed Successfully. Attempts = %d."
                    		+ " Round Score = %d\n", attempts, score);
                    break;
                } else if (guess_number < number) {
                    System.out.printf("The number is greater than %d.\n Attempts Left = %d.\n",
                    		guess_number, MAX_ATTEMPTS - attempts);
                } else if (guess_number > number) {
                    System.out.printf("The number is less than %d. Attempts Left = %d.\n",
                    		guess_number, MAX_ATTEMPTS - attempts);
                }
            }

            if (attempts == MAX_ATTEMPTS) {
                System.out.printf("\nRound = %d\n", i);
                System.out.println("\nAttempts = 0\n");
                System.out.printf("\nThe Random Number was: %d\n\n", number);
            }
        }

        System.out.printf("\nGame Over. Total Score = %d\n", totalScore);
        sc.close();
    }
}
