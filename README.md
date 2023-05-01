package javaapplication2;
import java.time.LocalDate;
import java.util.Scanner;

public class JavaApplication2 {
    private static boolean[] roomAvailability = new boolean[4];
    static {
        for (int i = 0; i < 4; i++) {
            roomAvailability[i] = true;
        }
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        String name ="arlane";
        String pass = "123";
        
        System.out.println("-------------------------------------------------------------");
        System.out.println("*                    RENTING SYSTEM                     *");
        System.out.println("-------------------------------------------------------------");
        
        for (int i = 0; i < 100; i++) {
        System.out.print("Username: ");
        String name2 = input.nextLine();
        System.out.print("Password: ");
        String pass2 = input.nextLine();
        
        if(name2.equalsIgnoreCase(name) && pass2.equalsIgnoreCase(pass)) {
            System.out.println("-------------------------------------------------------------");
            System.out.println(">>>  You can now select an option Maam " + name2 + "  <<<");
            System.out.println("-------------------------------------------------------------");
            break;
        }else{
            System.out.println("-------------------------------------------------------------");
            System.out.println("The password youve entered is incorrect. Please try again");
            System.out.println("-------------------------------------------------------------");
        }
        }

        while (true) {
            try {
            System.out.println("[1] Check room availability & Prices");
            System.out.println("[2] Rent a room");
            System.out.println("[3] Free up a room");
            System.out.println("[4] Exit");
            System.out.print("Please select an option: ");
            int choice = input.nextInt();

            switch (choice) {
                case 1:
                    checkAvailability();
                    break;
                case 2:
                    occupyRoom();
                    break;
                case 3:
                    freeUpRoom();
                    break;
                case 4:
                    System.out.println("");
                    System.out.println("-------------------------------------------------------------");
                    System.out.println(">>>  Thank youu! PROGRAMM EXIT  <<<");
                    input.close();
                    System.out.println("-------------------------------------------------------------");
                    System.out.println("");
                    return;
                default:
                    System.out.println("");
                    System.out.println("-------------------------------------------------------------");
                    System.out.println(">>>  Invalid option. Please choose a number from the following list.  <<<");
                    System.out.println("-------------------------------------------------------------");
                    System.out.println("");
            }
            }catch (Exception e) {
                System.out.println("");
                System.out.println("-------------------------------------------------------------");
                System.out.println(">>>  Invalid room number. Please choose a number from the following list.  <<<");
                input.next();
                System.out.println("-------------------------------------------------------------");
                System.out.println("");
            }
        }
        
    }

        private static void checkAvailability() {
            System.out.println("-------------------------------------------------------------");
            System.out.println(">>>  Room availability  <<<");
            System.out.println("-------------------------------------------------------------");
            for (int i = 0; i < 4; i++) {
                System.out.println("Room " + (i+1) + " has a price of 1500. " + ": " + (roomAvailability[i] ? "available" : "occupied"));
                System.out.println("-------------------------------------------------------------");
        }
    }

    private static void occupyRoom() {
        Scanner input = new Scanner(System.in);
        LocalDate today = LocalDate.now();
        LocalDate expirationDate = today.plusMonths(1);
        
        System.out.println("");
        System.out.println("-------------------------------------------------------------");
        System.out.println(">>>ALL ROOM HAS A DISCOUNT OF 10%<<<");
        System.out.println(" ROOM 1 PRICE: 1500");
        System.out.println(" ROOM 2 PRICE: 1500");
        System.out.println(" ROOM 3 PRICE: 1500");
        System.out.println(" ROOM 4 PRICE: 1500");
        
        System.out.println("-------------------------------------------------------------");
        System.out.print("Name: ");
        String Name = input.next();
        System.out.print("LastName: ");
        String LastName = input.next();
        System.out.print("MiddleName: ");
        String MiddleName = input.next();
        System.out.print("Address: ");
        String Address = input.next();
        System.out.print("Contact number: ");
        int Contact = input.nextInt();
        System.out.println("-------------------------------------------------------------");
        
        System.out.print("Enter amount of cash: ");
        int cash = input.nextInt();
        double TotalChange;
        int cost = 1500;
        double discountPercentage = 0.1;
        double money, change, balance, percentage;
        System.out.print("Please select a room from 1 to 4:");
        int roomNumber = input.nextInt();
        System.out.println("-------------------------------------------------------------");
        
        if (roomAvailability[roomNumber - 1]) {
            roomAvailability[roomNumber - 1] = false;
            
        } else {
            System.out.println("Room " + roomNumber + " is  already occupied right now.");
            System.out.println("-------------------------------------------------------------");
            return;
            
        }
        
        if (cash > cost) {
            change = cash - cost;
            discountPercentage = change * discountPercentage;
            TotalChange = discountPercentage + change;
            System.out.println("Room " + roomNumber + " has been occupied for " + LastName + "," + Name + " " + MiddleName);
            System.out.println("Change: " + change);
            System.out.println("Discount: " + discountPercentage);
            System.out.println("TotalChange: " + TotalChange);
            System.out.println("Address: " + Address );
            System.out.println("Contact: " + Contact);
            System.out.println("Rent at: " + today );
            System.out.println("Date until: " + expirationDate);
            System.out.println("-------------------------------------------------------------");
            
        }else if (cash < cost){
            balance = cash - cost;
            System.out.println("Not enough money! but can rent with a balance of ");
            System.out.println("Balance: " + balance);
            System.out.println("Date rent today: " + today);
            System.out.println("Date until: " + expirationDate);
            System.out.println("Room 1 has been occupied for " + LastName + "," + Name + " with a balance of: " + balance);
            System.out.println("Address: " + Address );
            System.out.println("Contact: " + Contact);
            System.out.println("-------------------------------------------------------------");
        }
        

        if (roomNumber < 1 || roomNumber > 4) {
            System.out.println(">>>  Invalid option . Please choose a number from (1 to 4) only.  <<<");
            return;
        }
    }

    private static void freeUpRoom() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("-------------------------------------------------------------");
        System.out.print("Please select an occupied room to free up (1 to 4): ");
        int roomNumber = scanner.nextInt();
        
        if (roomNumber < 1 || roomNumber > 4) {
            System.out.println(">>>  Invalid room number. Please choose a number from (1 to 4) only.  <<<");
            System.out.println("-------------------------------------------------------------");
            return;
        } else if (!roomAvailability[roomNumber - 1]) {
            roomAvailability[roomNumber - 1] = true;
            System.out.println("-------------------------------------------------------------");
            System.out.println("Room " + roomNumber + " is now available.");
            System.out.println("-------------------------------------------------------------");
        } else {
            System.out.println("-------------------------------------------------------------");
            System.out.println("Room " + roomNumber + " is available.");
            System.out.println("-------------------------------------------------------------");
        }
    } 
        
}
