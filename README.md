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
