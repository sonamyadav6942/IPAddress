// Java program to find class of IP Address and also find Network ID and Host ID of that IP

import java.io.*;
import java.util.Scanner;

class Practice{
    static String findClass(String str){
        int index = str.indexOf('.');
        String ipsub = str.substring(0,index);
        int ip = Integer.parseInt(ipsub);
        if (ip >= 1 && ip <= 126)
            return "A";
        else if (ip >= 128 && ip <= 191)
            return "B";
        else if (ip >= 192 && ip <= 223)
            return "C";
        else if (ip >= 224 && ip <= 239)
            return "D";
        else
            return "E";
    }
    static void findID(String str, String ipClass)
    {
        String network = "", host = "";
        if(ipClass == "A"){
            int index = str.indexOf('.');
            network = str.substring(0,index);
            host = str.substring(index+1,str.length());
        }
        else if(ipClass == "B")
        {
            int index = -1;
            int dot = 2;
            for(int i=0;i<str.length();i++){
                if(str.charAt(i)=='.'){
                    dot -=1;
                    if(dot==0){
                        index = i;
                        break;
                    }
                }
            }
            network = str.substring(0,index);
            host = str.substring(index+1,str.length());
        }
        else if(ipClass == "C"){
            int index = -1;
            int dot = 3;
            for(int i=0; i<str.length(); i++)
            {
                if(str.charAt(i)=='.')
                {
                    dot -=1;
                    if(dot==0){
                        index = i;
                        break;
                    }
                }
            }
            network = str.substring(0,index);
            host = str.substring(index+1,str.length());
        }
        else if(ipClass == "D" || ipClass == "E")
        {
            System.out.println("In this Class, IP address"+
                    " is not divided into Network and Host IDs");
            return;
        }
        System.out.println("Network ID is "+network);
        System.out.println("Host ID is "+host);
    }
    public static void main(String[] args) {
        System.out.println("Enter the IP Address : ");
        Scanner ipAddr = new Scanner(System.in);
        String Str = ipAddr.nextLine();
        String ipClass = findClass(Str);
        System.out.println("Given IP Address belongs to class "+ ipClass);
        findID(Str,ipClass);
    }
}
