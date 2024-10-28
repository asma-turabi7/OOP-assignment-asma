# OOP-assignment-asma

package ajavaapplication33;

import java.util.ArrayList;
import java.util.GregorianCalendar;

class AContact {
    private String aFName, aLName;
    private String[] aPhoneNum;
    private String aAffiliation;
    private String aOccupation;
    private String aNote = "";
    private GregorianCalendar aDob;
    private boolean aBlocked = false;

    // Default constructor
    public AContact() {
    }

    // Parameterized constructor
    public AContact(String aFName, String aLName, String[] aPhoneNum, String aAffiliation, String aOccupation, String aNote, GregorianCalendar aDob) {
        this.aFName = aFName;
        this.aLName = aLName;
        this.aPhoneNum = aPhoneNum;
        this.aAffiliation = aAffiliation;
        this.aOccupation = aOccupation;
        this.aNote = aNote;
        this.aDob = aDob;
    }

    // Setters and Getters
    public void setaFName(String aFName) {
        this.aFName = aFName;
    }

    public String getaFName() {
        return aFName;
    }

    public void setaLName(String aLName) {
        this.aLName = aLName;
    }

    public String getaLName() {
        return aLName;
    }

    public void setaPhoneNum(String[] aPhoneNum) {
        this.aPhoneNum = aPhoneNum;
    }

    public String[] getaPhoneNum() {
        return aPhoneNum;
    }

    public void setaAffiliation(String aAffiliation) {
        this.aAffiliation = aAffiliation;
    }

    public String getaAffiliation() {
        return aAffiliation;
    }

    public void setaOccupation(String aOccupation) {
        this.aOccupation = aOccupation;
    }

    public String getaOccupation() {
        return aOccupation;
    }

    public void setaNote(String aNote) {
        this.aNote = aNote;
    }

    public String getaNote() {
        return aNote;
    }

    public void setaDob(GregorianCalendar aDob) {
        this.aDob = aDob;
    }

    public GregorianCalendar getaDob() {
        return aDob;
    }

    public void setaBlocked(boolean aBlocked) {
        this.aBlocked = aBlocked;
    }

    public boolean isaBlocked() {
        return aBlocked;
    }

    // Replace number
    public void areplaceNumber(String oldNumber, String newNumber) {
        for (int i = 0; i < aPhoneNum.length; i++) {
            if (aPhoneNum[i].equals(oldNumber)) {
                aPhoneNum[i] = newNumber;
                break;
            }
        }
    }

    // toString method
    @Override
    public String toString() {
        return "Contact [First Name=" + aFName + ", Last Name=" + aLName + ", Phone Numbers=" + String.join(",", aPhoneNum)
                + ", Affiliation=" + aAffiliation + ", Occupation=" + aOccupation + ", Note=" + aNote + ", DOB="
                + aDob.getTime() + ", Blocked=" + aBlocked + "]";
    }
}

package ajavaapplication33;

import java.util.ArrayList;

class ADirectory {
    private ArrayList<AContact> aDirectory;
    private int aNum;

   
    public ADirectory() {
        aDirectory = new ArrayList<>();
        aNum = 0;
    }

    public ADirectory(ArrayList<AContact> aDirectory) {
        this.aDirectory = aDirectory;
        this.aNum = aDirectory.size();
    }

   
    public void setaDirectory(ArrayList<AContact> aDirectory) {
        this.aDirectory = aDirectory;
        this.aNum = aDirectory.size();
    }

    public ArrayList<AContact> getaDirectory() {
        return aDirectory;
    }

    public void setaNum(int aNum) {
        this.aNum = aNum;
    }

    public int getaNum() {
        return aNum;
    }

  
    public void aaddContact(AContact aContact) {
        aDirectory.add(aContact);
        aNum++;
    }

   
    public void aaddContact(String aFName, String aLName, String[] aPhoneNum, String aAffiliation, String aOccupation, String aNote, GregorianCalendar aDob) {
        AContact aContact = new AContact(aFName, aLName, aPhoneNum, aAffiliation, aOccupation, aNote, aDob);
        aaddContact(aContact);
    }

   
    public AContact aSearchContact(String aFName) {
        for (AContact aContact : aDirectory) {
            if (aContact.getaFName().equalsIgnoreCase(aFName)) {
                return aContact;
            }
        }
        return null;
    }

    
    public void aDeleteContact(String aFName) {
        AContact toRemove = aSearchContact(aFName);
        if (toRemove != null) {
            aDirectory.remove(toRemove);
            aNum--;
        }
    }

    
    @Override
    public String toString() {
        return "Directory [Number of Contacts=" + aNum + ", Contacts=" + aDirectory + "]";
    }
}

package ajavaapplication33;
import java.util.Scanner;

public class AJavaApplication33 {

    public static void main(String[] args) {
        ADirectory aDirectory = new ADirectory();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Menu:-");
            System.out.println("1. Add  a Contact");
            System.out.println("2. Search Contact");
            System.out.println("3. Delete Contact");
            System.out.println("4. Replace the Number");
            System.out.println("5. Display All Contacts");
            System.out.println("6. Block a Number");
            System.out.println("7. Exit");
            System.out.print("Choose an option form above : ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    
                    System.out.print("Enter the First Name: ");
                    String aFName = scanner.next();
                    System.out.print("Enter the Last Name: ");
                    String aLName = scanner.next();
                    String[] aPhoneNum = new String[1]; 
                    System.out.print("Enter Phone Number: ");
                    aPhoneNum[0] = scanner.next();
                    System.out.print("Enter Affiliation: ");
                    String aAffiliation = scanner.next();
                    System.out.print("Enter your Occupation: ");
                    String aOccupation = scanner.next();
                    System.out.print("Enter any Note: ");
                    String aNote = scanner.next();
                    GregorianCalendar aDob = new GregorianCalendar(); 
                    aDirectory.aaddContact(aFName, aLName, aPhoneNum, aAffiliation, aOccupation, aNote, aDob);
                    break;
                case 2:
                    
                    System.out.print("Enter the First Name to search: ");
                    String searchName = scanner.next();
                    AContact searched = aDirectory.aSearchContact(searchName);
                    if (searched != null) {
                        System.out.println("Contact Found: " + searched);
                    } else {
                        System.out.println("Contact Not Found");
                    }
                    break;
                case 3:
                    
                    System.out.print("Enter First Name to delete: ");
                    String deleteName = scanner.next();
                    aDirectory.aDeleteContact(deleteName);
                    System.out.println("Contact  is deleted");
                    break;
                case 4:
                    
                    System.out.print("Enter First Name to find: ");
                    String replaceName = scanner.next();
                    AContact contactToReplace = aDirectory.aSearchContact(replaceName);
                    if (contactToReplace != null) {
                        System.out.print("Enter Old Number: ");
                        String oldNumber = scanner.next();
                        System.out.print("Enter New Number: ");
                        String newNumber = scanner.next();
                        contactToReplace.areplaceNumber(oldNumber, newNumber);
                        System.out.println("Number is replaced");
                    } else {
                        System.out.println(" The Contact is Not Found");
                    }
                    break;
                case 5:
                    
                    System.out.println(aDirectory);
                    break;
                case 6:
                   
                    System.out.print("Enter First Name to block: ");
                    String blockName = scanner.next();
                    AContact contactToBlock = aDirectory.aSearchContact(blockName);
                    if (contactToBlock != null) {
                        contactToBlock.setaBlocked(true);
                        System.out.println("Contact is blocked");
                    } else {
                        System.out.println("Contact Not Found");
                    }
                    break;
                case 7:
                    
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid Option . Please Try again.");
            }
        }
    }
}
