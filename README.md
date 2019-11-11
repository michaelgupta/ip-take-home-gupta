# IP Address Management System
 
Create a simple IP Address Management System using your prefered language/framework on top of any data store. It will include the ability to add IP Addresses by CIDR block and then either acquire or release IP addresses individually. Each IP address will have a status associated with it that is either “available” or “acquired”. 
 
The System must support four operations:
  * **Create IP addresses** - take in a CIDR block (e.g. 10.0.0.1/24) and add all IP addresses within that block to the data store with status “available”
  * **List IP addresses** - return all IP addresses in the system with their current status
  * **Acquire an IP** - set the status of a specified IP to “acquired”
  * **Release an IP** - set the status of a specified IP to “available”

## Bonus

The System will check if a suppied CIDR block is in conflict with an already registered CIDR block.



import java.util.Scanner;
import java.util.*; 
import java.lang.Math; 

public class takeHome {
   public static void main(String[] args) {
      Scanner inputCidrBlock = new Scanner(System.in);
      //asks for user input in the format needed.
      System.out.println("Enter your CIDR BLOCK HERE (eg. 10.0.0.1/24: ");
      String cidrBlock = inputCidrBlock.nextLine();
      String lastTwoDigitsString = "";
      
      // gets the last two digits to determine the number of ips in the block.
      lastTwoDigitsString = cidrBlock.substring(cidrBlock.length() - 2);
      
      //conversts the string to an int value.
      int lastTwoDigitsInt = Integer.parseInt(lastTwoDigitsString);
      
      //does the calc for number of ips for the block.
      double numberOfIps=Math.pow(2, 32-lastTwoDigitsInt)-2;
      
      //removes "n/nn" from the block
      String stringAfterRemovalOf4=cidrBlock.substring(0, cidrBlock.length() - 4);
     
      //prints the ip addresses for the block and increments the counter untill the number of ips are met
      int counter=0;
      while(counter < numberOfIps){
         if(counter == 0){
            System.out.println(stringAfterRemovalOf4+counter);
            counter++;
         }
         else{
            counter++;
            System.out.println(stringAfterRemovalOf4+counter);
         }
      }   
   }
}
 
