
Lab4.java:

```java


package University;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.io.IOException;

/**
 * Write a program which would find if a mathematical expression is
 * correct from the point of view of the parentheses within it.
 */
 
public class Lab4 {

    private static boolean countParentheses(String text) {
        int counter = 0;
        for (char ch : text.toCharArray()) {
            if (ch == '(') counter++;
            else if (ch == ')') counter--;

            if (counter < 0) break;
        }
        if (counter != 0) return false;
        return true;
    }

    public static void main(String[] args) throws IOException {
        File file = new File("C:\\Users\\Anastasia\\IdeaProjects\\University\\expressions.txt");

        BufferedReader br = new BufferedReader(new FileReader(file));

        String st;
        while ((st = br.readLine()) != null) {
            System.out.println("Expression: " + st);
            System.out.println("Parentheses are put correct in this expression: " + countParentheses(st));
        }
    }

}

```

Lab4.cpp:

```cpp


#include <iostream>
#include <stack>
#include <string>
#include <fstream>

/**
 * Write a program which would find if a mathematical expression is
 * correct from the point of view of the parentheses within it.
 */
 
using namespace std;

bool Parantheses(char opening,char closing){
    if(opening == '(' && closing == ')') return true;
    return false;
}
bool AreParanthesesBalanced(string exp){
    stack<char> S;
    
    for(int i = 0; i < exp.length(); i++){
        if(exp[i] == '(')
            S.push(exp[i]);
        else if(exp[i] == ')'){
            if(S.empty() || !Parantheses(S.top(),exp[i]))
                return false;
            else
                S.pop();
        }
    }
    return S.empty() ? true:false;
}

int main(){
    std::string line_;
    ifstream file_("expressions.txt");
    
    if(file_.is_open()){
        while (getline(file_, line_))
        {
            std::cout<<line_<< '\n';
            if(AreParanthesesBalanced(line_))
                cout<<"Balanced \n";
            else
                cout<<"Not balanced \n";
        }
        file_.close();
    }
    else
        std::cout<<"The file could not be opened due to an error."<<'\n';
    std::cin.get();
    return 0;
}

```

expressions.txt:

```
2 * 4 + (3 +6 * 9 -    12 * (2*9 - 15))  + 2 +(-4)*((2 - 15))
2x - 3y + 25 / (2+5)*12 - ((29*4-2) + 32) -14
2x - 3y + 25 / (-((29*4-2) + 32) -14 - (2+5)*12
((((((((((((((((((((2x-4y * 98 )))))))))))))))))))))
```
