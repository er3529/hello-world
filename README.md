# hello-world
hello world!

import java.util.*;
public class FracCalc_Egg {

   public static String f1;
   public static String op;
   public static String f2;
   public static int w1;
   public static int w2;
   public static int n1;
   public static int n2;
   public static int d1;
   public static int d2;

   public static void main(String[] args) {
      System.out.println("Welcome to the Fraction calculator!");
      Scanner console = new Scanner(System.in);
       System.out.print("Enter an expression (or \"quit\"): ");
      //get the first fraction, or quit
  f1 = console.next();
  //test fraction1 to see if the user types "quit"
  if(f1.equalsIgnoreCase("quit")){
     System.out.println("Goodbye!");
  }
  while(!f1.equalsIgnoreCase("quit")){
     op = console.next();
     f2 = console.next();
     processFractions(f1, op, f2);
     System.out.print("Enter an expression (or \"quit\"): ");
     f1 = console.next();
     if(f1.equalsIgnoreCase("quit")){
     System.out.println("Goodbye!");
     }
  }//end while loop
  //while loop continues the calc until the user types "quit"
   }//end of main


  public static void processFractions(String f1, String op, String f2){
  //get int variables from fractions

  //testing fraction 1 to get int values
    if(f1.contains("_")){ //testing for mixed number
     w1=Integer.parseInt(f1.substring(0,f1.indexOf("_")));
     n1=Integer.parseInt(f1.substring(f1.indexOf("_")+1,f1.indexOf("/")));
     d1=Integer.parseInt(f1.substring(f1.indexOf("/")+1));
     n1=(w1*d1)+n1; //making mixed number improper
  } else if(f1.contains("/")) { //testing for fraction
     n1=Integer.parseInt(f1.substring(0,f1.indexOf("/")));
     d1=Integer.parseInt(f1.substring(f1.indexOf("/")+1));
  } else {//testing for whole number
     w1=Integer.parseInt(f1.substring(0));
     n1=w1;
     d1=1;
  }//end if, else if, else method

  //testing fraction 2 to get int values 
  if(f2.contains("_")){ //mixed fraction
     w2=Integer.parseInt(f2.substring(0,f2.indexOf("_")));
     n2=Integer.parseInt(f2.substring(f2.indexOf("_")+1,f2.indexOf("/")));
     d2=Integer.parseInt(f2.substring(f2.indexOf("/")+1));
     n2=w2*d2+n2;  
  } else if(f2.contains("/")) { //fraction 
     n2=Integer.parseInt(f2.substring(0,f2.indexOf("/")));
     d2=Integer.parseInt(f2.substring(f2.indexOf("/")+1));
  } else { //whole number 
     w2=Integer.parseInt(f2.substring(0));
     n2=w2;
     d2=1;
  }//end if, else if, else method


  dotheMath(n1, n2, d1, d2, op);

   }//end processFraction method    

//dotheMath detmerines the operator 
 public static void dotheMath(int n1, int n2, int d1, int d2, String op) {
   if(op.equals("+")){
       System.out.println(add(n1, n2, d1, d2));     
    } else if(op.equals("-")) { 
       n2=-1*n2;
       System.out.println(add(n1, n2, d1, d2)); 
    } else if(op.equals("*")) {
       System.out.println(multiply(n1, n2, d1, d2));
    } else { 
       int x = n2;
       int y = d2;
       d2=x;
       n2=y;
       System.out.println(multiply(n1, n2, d1, d2));
    } //end the if, else if, else statement

 }//end dotheMath method


 public static String add(int n1, int n2, int d1, int d2) {
    int newn = (n1*d2) + (n2*d1);
    int newd = d1*d2;
    int divisor = reduce(newn,newd);
    newn/=divisor;
    newd/=divisor;
    String answer = reduce(newn, newd);

    return answer;
 }//end add method


 public static String multiply(int n1, int n2, int d1, int d2) {
    int newn = n1*n2;
    int newd = d1*d2;
    int divisor = reduce(newn,newd);
    newn/=divisor;
    newd/=divisor;

    String answer = reduce(newn, newd);
    return answer;
 }//end multiply method  


 public static int lcd(int n1,int d1, int n2, int d2){
   int dividend=(d1*n2)+(n1*d2); 
   int divisor = d1*d2;
   int rem = dividend % divisor;
   while (rem != 0){
     dividend = divisor;
     divisor = rem;
     rem = dividend % divisor;
  }  

 return divisor;
   } //end lcd   


public static int reduce (int newn, int newd) { //
int newn_abs = Math.abs (newn);
int newd_abs = Math.abs (newd); //

 int min_num = Math.min (newn_abs, newd_abs);

int divisor = 1;

for (int i = 1; i <= min_num; i++) {
 if (newn%i == 0 && newd%i == 0){

 divisor = 1;
 }//end if 
   }//end for
   return divisor;

}//end reduce


}//end of class 
