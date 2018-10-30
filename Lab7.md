
```java
import java.util.*;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

/**
 * Task1
 * Create a program where you can enter a big text in console and after that the program should prompt back in console
 * the number of sentences of this text. (Minimum 3 sentences).
 * 
 * Task2
 * Show also in console the number of words from this text.
 * 
 * Task3
 * Show the number of letters from the text.
 * 
 * Task4
 * Show the words that appear mostly in this text (Top 5).
 * 
 * Bonus
 * Show the number of vowels and number of consonants from
 */


public class App {

    private String getText() {
        System.out.println("Input text: ");
        String text = "";
        Scanner sc = new Scanner(System.in);
        text = sc.nextLine();
        sc.close();
        return text;
    }

    private int numberOfSentences(String text) {
        int sentenceCount = 0;
        String terminalSymbol = ".?!";

        for (int i = 0; i < text.length(); i++) {
            if (terminalSymbol.indexOf(text.charAt(i)) != -1) {
                sentenceCount++;
            }
        }
        return sentenceCount;
    }

    private int numberOfWords(String text) {
        int count = 0;
        if (text.length() != 0) {
            count++;
            for (int i = 0; i < text.length(); i++) {
                if (text.charAt(i) == ' ') {
                    count++;
                }
            }
        }
        return count;
    }

    private int numberOfLetters(String text) {
        int result = 0;
        String[] kolichestvoSlov = text.trim().split("\\s+");

        for (int i = 0; i < kolichestvoSlov.length; i++) {
            result = result + kolichestvoSlov[i].length();
        }
        return result;
    }


    private Map<String, Integer> buildWordMap(String text) {
        Map<String, Integer> wordMap = new HashMap();
        Pattern pattern = Pattern.compile("\\s+");

        text = text.toLowerCase();
        String[] words = pattern.split(text);
        for (String word : words) {
            if (wordMap.containsKey(word)) {
                wordMap.put(word, (wordMap.get(word) + 1));
            } else {
                wordMap.put(word, 1);
            }

        }
        return wordMap;
    }

    private static List<Map.Entry<String, Integer>> sortByValueInDecreasingOrder(Map<String, Integer> wordMap) {
        Set<Map.Entry<String, Integer>> entries = wordMap.entrySet();
        List<Map.Entry<String, Integer>> list = new ArrayList(entries);
        Collections.sort(list, new Comparator<Map.Entry<String, Integer>>() {
            @Override
            public int compare(Map.Entry<String, Integer> o1, Map.Entry<String, Integer> o2) {
                return (o2.getValue()).compareTo(o1.getValue());
            }
        });
        return list;
    }

    private void showTopPopularWords(String text){

        Map<String, Integer> wordMap = buildWordMap(text);
        List<Map.Entry<String, Integer>> list = sortByValueInDecreasingOrder(wordMap);
        System.out.println("Repeated words and their number: ");
        for (Map.Entry<String, Integer> entry : list) {
            if (entry.getValue() > 1) {
                System.out.println(entry.getKey() + " => " + entry.getValue());
            }
        }
    }

    private int numOfConsones(String text){
        Pattern vocals = Pattern.compile("(?iu)[eyuioa]"); //RegEx online
        Matcher m = vocals.matcher(text);
        int vocalCounter = 0;
        while (m.find()) {
            vocalCounter++;
        }
        return vocalCounter;
    }

    public static void main(String[] args) {
        App appObj = new App();
        String text = appObj.getText();
        int numOfL = appObj.numberOfLetters(text);
        System.out.println("Number of sentences: " + appObj.numberOfSentences(text));
        System.out.println("Number of words: " + appObj.numberOfWords(text));
        System.out.println("Number of letters: " + numOfL);
        appObj.showTopPopularWords(text);
        int num = appObj.numOfConsones(text);
        System.out.println("Number of consones: " + (numOfL - num));
        System.out.println("Number of vowels: " + (num));
        
}
}
```

![Image 2](https://github.com/AshleyBlair/OOP/blob/images/07_test.png)
