# Ticketmachine
package sample;
import java.util.Scanner;
public class Controller {
    private int price;
    private int balance;
    private int total;
    Scanner scanner = new Scanner(System.in);

    public void setPrice() {
        System.out.println("请输入票价:");
        int ticketCost = scanner.nextInt();
        balance = 0;
        total = 0;
        if (ticketCost > 0) {
            price = ticketCost;
        } else {
            System.out.println("ticket must be positive!");
        }

    }

    public void insertMoney() {
        System.out.println("请投钱:");
        int amount = scanner.nextInt();
        if (amount < 0) {
            System.out.println("You must use a positive value!");
        } else {
            balance += amount;
        }

    }

    void print(){
        System.out.println("请输入打印票数:");
        while(true){
            int sum = scanner.nextInt();
            if(balance >=price*sum){
                for (int i = 0; i < sum; ++i) {
                    System.out.println("===================");
                    System.out.println("票价" + price);
                    System.out.println("谢谢惠顾");
                    System.out.println("===================");
                    balance-=price;
                    total+=price;}
                break;
            }
            else {
                System.out.println("余额不足，请重新输入");
            }
        }
    }

    public int refundBalance() {
        int amountRefunded = balance;
        System.out.println("您的余额剩余:"+balance);
        balance=0;
        return amountRefunded;
    }

    public int getPrice() {
        return price;
    }



     int getBalance() {
        return balance;


    }

     int getTotal() {

        return total;

    }


    public static void main (String[] args){
        Controller test1 = new Controller();
        test1.setPrice();
        test1.insertMoney();
        test1.print();
        test1.refundBalance();
        test1.getBalance();
        test1.getTotal();

    }
}
