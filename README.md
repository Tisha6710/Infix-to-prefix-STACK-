# Infix-to-prefix-STACK-
package Stacks;
import java.util.*;
public class Infixtoprefix {
    public static void main(String[] args) {
        String infix="7-1+7*5/3";
        System.out.println(infix);
        Stack<String>val=new Stack<>();
        Stack<Character> op=new Stack<>();
        for(int i=0;i<infix.length();i++){
            char ch= infix.charAt(i);
            int ascii =(int) ch;
            // numbers as charcters
            // like 0 ki ascii value hoti h 48 and 9 ki hoti h 57 means 48 to 57
            if(ascii>=48 && ascii<=57){
                String s="" +ch;
                val.push(s);
            }
                 // if char is 5 means ascii val is
                // 53
            else if(op.size()==0 || ch=='(' || op.peek()=='(')
                op.push(ch);
            else if(ch==')'){
                while(op.peek()!='(') {
                    // work
                    String v2 = val.pop();
                    String v1 = val.pop();
                    char o = op.pop();
                    String t=o+v1+v2;
                    val.push(t);
                }
                    op.pop(); // '(' hata diya

                }
            else{
                if(ch=='+' || ch=='-'){
                    // work
                    String v2 = val.pop();
                    String v1 = val.pop();
                    char o = op.pop();
                    String t=o+v1+v2;
                    val.push(t);
                    // push
                        op.push(ch);
                    }

                if (ch == '*' || ch == '/') {
                    if(op.peek()=='*' || op.peek()=='/'){
                        String v2 = val.pop();
                        String v1 = val.pop();
                        char o = op.pop();
                        String t=o+v1+v2;
                        val.push(t);
                        // push
                        op.push(ch);


                }
                    else op.push(ch);
                }
            }
        }
        // val wale ko stack ko 1 banana h
        while(val.size()>1){
            String v2 = val.pop();
            String v1 = val.pop();
            char o = op.pop();
            String t=o+v1+v2;
            val.push(t);
        }
        String prefix=val.pop();
        System.out.println(prefix);
    }

}

