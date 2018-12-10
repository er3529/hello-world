# hello-world
hello world!

I'm a person on a planet who does this wonderful thing called cellular respiration

Hey guys!!


import java.util.Random;
import java.util.Scanner;

public class Dice 
{
	Scanner scan = new Scanner(System.in);
	private final int MIN_FACES = 4;
	
	private static Random generator = new Random();
	private int numFaces; //number of sides on the die
	private int faceValue; // current value showing on the die
	
	//-----------------------------------------------------------
	// Defaults to a six-sided die. Initial face value is 1.
	//-----------------------------------------------------------
	public Dice ()
	{
		numFaces = 6;
		faceValue = 1;
	}
	
	//-----------------------------------------------------------
	// Explicitly sets the size of the die. Defaults to a size of
	// six if the parameter is invalid. Initial face value is 1.
	//-----------------------------------------------------------
	public Dice (int faces)
	{
		if(faces < MIN_FACES)
			numFaces = 6;
		else
			numFaces = faces;
		
		faceValue = 1;
	}
	
	//-----------------------------------------------------------
	//  Rolls the die and returns the result
	//-----------------------------------------------------------
	public int roll ()
	{
		faceValue = generator.nextInt(numFaces) + 1;
		return faceValue;
	}
	//-----------------------------------------------------------
	//  Returns the current die value
	//-----------------------------------------------------------
	public int getFaceVault ()
	{
		return faceValue;
	}
}






public class SnakeEyes 
{
    public static void main(String[]args) 
    {
    	int boxCars = 0;
    	final int rolls = 1000;
    	Dice dice1 = new Dice();
    	Dice dice2 = new Dice();
		
		for(int roll = 1; roll <= rolls; roll++)
		{
			int num1 = dice1.roll();
			int num2 = dice2.roll();
			
		if (num1 == 6 && num2 == 6)
			boxCars++;
		}
		System.out.println ("Number of rolls: " + rolls);
		System.out.println ("Number of BoxCars in total(two sixes that occured): " + boxCars);
    }
}
