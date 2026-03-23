```java
import java.util.*;

void main() {
    Scanner input = new Scanner(System.in);
   System.out.println("1. Display Aisle ");
    System.out.println("2. Add item ");
    System.out.println("3. Remove item");
    int c = input.nextInt();
    switch(c) {
        case 1:
            break;
        case 2:
            break;
        case 3:
            break;
        default:
            System.out.println("Invalid input");
    }
}
public class Item {
    private String name;
    private String companyName;
    private int quantity;
    public Item(String n, String cn){
        name = n;
        companyName = cn;

    }
    public Item(){

    }

    //Overloaded
    public void updateItem(String n){
        name = n;
    }
    public void updateItem(String n,String cn){
        name = n;
        companyName = cn;

    }
    public void printInfo(){
        System.out.println("Name of product " + name);
        System.out.println("Company Name "+ companyName);
    }


}
public class PainKillers extends Item{
    private String expDate;
    private String ageGroup;

    PainKillers( String a, String b, String  c, String d){
        super(a,b);
        expDate = c;
        ageGroup = d;
    }
    PainKillers(){

    }

    public String  getExpDate(){
        return expDate;
    }
    public String getAgeGroup(){
        return ageGroup;
    }

    public void setExpDate(String s){
        expDate = s;
    }
    public void setAgeGroup(String s){
        ageGroup = s;
    }


    @Override
   public void printInfo() {
        super.printInfo();

        System.out.println("Expiration date: "+ getExpDate());
        System.out.println("Age group: "+ getAgeGroup());
    }
}
public class Bandages extends Item {
    private String expDate;
    private String ageGroup;
    private boolean isWaterproof;
    Bandages( String n, String c, String e, String f, boolean isWaterproof){
        super(n,c);
        expDate = e;
        ageGroup = f;
        this.isWaterproof = isWaterproof;

    }
    Bandages(){

    }

    public String getExpDate(){
        return expDate;
    }
    public String getAgeGroup(){
        return ageGroup;
    }
    public boolean getIsWaterproof(){
        return isWaterproof;
    }


    public void setExpDate(String s){
        expDate = s;
    }
    public void setAgeGroup(String s){
        ageGroup = s;
    }
    //public void setIsWaterproof(boolean s){ isWaterProof = s};

public void printInfo(){
        super.printInfo();
    System.out.println("Expiration date: "+ getExpDate());
    System.out.println("Age group: "+ getAgeGroup());
    System.out.println("Is water proof: " + getIsWaterproof());

}}
public class Equipment extends Item{

    private int itemWeight;
    Equipment( String n, String c, int i){
        super(n,c);

        itemWeight = i;
    }
    Equipment(){

    }


    public void setItemWeight(int n){
        itemWeight = n;
    }

    public int getItemWeight(){
        return itemWeight;
    }

    @Override
    public void printInfo() {
        super.printInfo();
        System.out.println("Item weight: " +getItemWeight()+"lbs");
    }
}


```
