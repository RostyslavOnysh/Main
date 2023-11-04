# Levenshtein distance

In information theory, linguistics, and computer science, the Levenshtein distance is a string metric for measuring the difference between two sequences. Informally, the Levenshtein distance between two words is the minimum number of single-character edits (insertions, deletions or substitutions) required to change one word into the other. It is named after the Soviet mathematician Vladimir Levenshtein, who considered this distance in 1965.[1]

Levenshtein distance may also be referred to as edit distance, although that term may also denote a larger family of distance metrics known collectively as edit distance.[2]: 32  It is closely related to pairwise string alignments.


## Example

Edit distance matrix for two words using cost of substitution as 1 and cost of deletion or insertion as 0.5
For example, the Levenshtein distance between "kitten" and "sitting" is 3, since the following 3 edits change one into the other, and there is no way to do it with fewer than 3 edits:

* kitten → sitten (substitution of "s" for "k"),
* sitten → sittin (substitution of "i" for "e"),
* sittin → sitting (insertion of "g" at the end).


***Алгоритм "Levenshtein distance" (відстань Левенштейна) є метрикою***, яка вимірює різницю між двома рядками. Він визначає мінімальну кількість операцій (вставка, видалення, заміна символів), необхідних для перетворення одного рядка на інший.

Для кожної пари символів (один з першого рядка і один з другого), розглядаються три можливі операції:

* ***Вставка:*** додаємо символ до одного з рядків.
* ***Видалення:*** видаляємо символ з одного з рядків.
* ***Заміна:*** замінюємо один символ на інший.

Алгоритм рекурсивно обчислює відстань Левенштейна шляхом порівняння символів на кожній позиції двох рядків. За допомогою динамічного програмування відстань розраховується поетапно для всіх підрядкових підланок рядків, а потім використовується для обчислення відстані для більшого підланцюжка.

# Основна ідея алгоритму полягає в тому, щоб знайти найменшу кількість операцій, які потрібні для перетворення одного рядка на інший. Це дозволяє виміряти подібність між рядками.

Наприклад, для рядків "kitten" і "sitting" відстань Левенштейна дорівнює 3. Ми можемо досягти цього шляхом видалення "k", заміни "e" на "i" і вставки "g" в кінець. Отже, ці два рядки не є ідентичними, але вони мають відносно невелику відстань Левенштейна, що свідчить про їх подібність.

Алгоритм ***"Levenshtein distance"*** може бути використаний для порівняння двох слів, зокрема для визначення найближчого слова зі словника до заданого терміна.


```java 
public class Dictionary {
    public static void main(String[] args) {
        String[] words = {"java", "python", "php", "ruby"};
        Dictionary dictionary = new Dictionary(words);

        String term = "heaven";
        String closestWord = dictionary.findMostSimilar(term);
        System.out.println("Closest word to \"" + term + "\": " + closestWord);
    }

    private final String[] words;

    public Dictionary(String[] words) {
        this.words = words;
    }

    public String findMostSimilar(String term) {
        int minDistance = Integer.MAX_VALUE;
        String closestWrld = "";
        for (String word : words) {
            int distence = levenshteinDistance(word, term);
            if (distence < minDistance) {
                minDistance = distence;
                closestWrld = word;
            }
        }
        return closestWrld;
    }

    public static int levenshteinDistance(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        int[][] dp = new int[m + 1][n + 1];
        for (int i = 1; i <= m; i++) {
            dp[i][0] = i;
        }
        for (int j = 1; j <= n; j++) {
            dp[0][j] = j;
        }
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (word1.charAt(i - 1) == word2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = 1 + Math.min(dp[i - 1][j - 1],
                            Math.min(dp[i - 1][j], dp[i][j - 1]));
                }
            }
        }
        return dp[m][n];
    }

}
```


У матриці dp, яка використовується для обчислення відстані Левенштейна, розміри її стовпців і рядків більші на одиницю, ніж довжина вихідних слів. Це зроблено для того, щоб врахувати порожній рядок або порожнє слово як базовий випадок.

Коли одне зі слів є порожнім, а інше має довжину n, відстань Левенштейна між ними буде n, оскільки в такому випадку є необхідність вставити n символів, щоб перетворити порожнє слово на слово довжиною n.

Отже, використання m + 1 рядків і n + 1 стовпців дозволяє врахувати всі можливі комбінації порожнього рядка та слів довжиною до m і n відповідно.

Це забезпечує правильне обчислення відстані Левенштейна для всіх можливих випадків, включаючи базовий випадок з порожнім словом.




* The Dictionary class has a constructor that takes an array of words and initializes the words variable.

* The findMostSimilar method takes a term as input and aims to find the word from the dictionary that is most similar to the given term.

* Inside the findMostSimilar method, two variables are initialized: minDistance to keep track of the minimum distance found so far, and closestWrld to store the word with the minimum distance.

* The method then iterates over each word in the dictionary using a for-each loop.

* For each word, the Levenshtein distance between that word and the given term is calculated using the levenshteinDistance method. The distance is stored in the distence variable.

* If the calculated distance is less than the current minimum distance (minDistance), the minimum distance is updated, and the closest word is set to the current word.

* After iterating through all the words in the dictionary, the method returns the closest word found.

* The levenshteinDistance method is a static method that calculates the Levenshtein distance between two strings, word1 and word2, using dynamic programming.

* It initializes a 2D array dp of size (m + 1) x (n + 1), where m is the length of word1 and n is the length of word2. The extra row and column are for the empty string cases.

* It then performs initialization of the base cases: setting the first column to represent deleting characters from word1 (costing i operations) and the first row to represent inserting characters into word1 (costing j operations).

* Next, it iterates through the remaining cells of the dp array and fills them based on the Levenshtein distance formula.

* If the characters at the current positions in word1 and word2 are the same, the cost of the operation is 0, and the value in the dp array is set to the value from the diagonal cell.

* If the characters are different, the cost is 1, and the value in the dp array is set to the minimum of three adjacent cells (left, top, and diagonal) plus 1.

Finally, the Levenshtein distance between the two words is obtained from the bottom-right cell of the dp array (dp[m][n]) and returned.

Overall, this code uses the Levenshtein distance algorithm to calculate the similarity between a given term and the words in the dictionary, and it returns the word with the minimum distance as the most similar word.
