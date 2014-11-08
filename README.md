ScannerFun
==========
import java.io.File;
import java.io.FileNotFoundException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Scanner;


public class ScannerFun {

	public static void main(String[] args) throws FileNotFoundException {
		//Make a file named "book"
		File book = new File("Book.txt");
		//Make a scanner named reader
		Scanner reader = new Scanner(book);
		ArrayList <String> allWords = new ArrayList <String> ();

		HashMap<String, Integer> wordCount = new HashMap<String, Integer>();
		wordCount.put("meow", 5);

		System.out.println(wordCount);
		int total = 0;

		while(reader.hasNextLine()) {
			String line = reader.nextLine();
			line = line.replaceAll("\\.", "");
			line = line.replaceAll("\\?", "");
			line = line.replaceAll("\\!", "");
			line = line.replaceAll("\\*", "");
			line = line.replaceAll("\\_", "");
			line = line.replaceAll("\\\"", "");
			line = line.replaceAll("reg'lar", "regular");
			line = line.replaceAll("'bout", "about");
			line = line.replaceAll("\\--", "");


			String[] words = line.split(" ");

			for (int i = 0 ; i < words.length ; i++) {
				allWords.add(words[i]);
			}
			total = total + words.length;

		}
		int totalThe = 0;
		int totalTom = 0;
		String longestWord = allWords.get(0);

		for (int i = 0 ; i <allWords.size(); i++) {
			String word = allWords.get(i);
			int lengthOfWord = word.length();
			if (word.equals("the")) {
				totalThe++;
			}


		}

		for (int j = 0 ; j < allWords.size() ; j++) {
			String word2 = allWords.get(j);
			int lengthOfWord2 = word2.length();
			if (word2.equals("Tom")) {
				totalTom++;
			}
		}

		for (int i = 0 ; i < allWords.size(); i ++) {
			String word = allWords.get(i);

			if (word.length() > longestWord.length()) {
				longestWord = word;
			}
		}

		System.out.println("The word the appears " + totalThe + " times");
		System.out.println("Word count: " + total);
		System.out.println("The word Tom appears " + totalTom + " times");
		System.out.println("The longest word is " + longestWord + " .");
		System.out.println("Unique words: " + wordCount.size());
	}

}
