# runestone-2-9-assignment

## Git Config
```
git config user.name "user"
git config user.email "email"
```

## Compiling and Running Java Programs
Note that since the shape classes are separate classes, you will need to compile ALL the files (at least one time).  You can do this by running
```
javac *.java
```
The star means to compile every file that is a Java file type.

Run your code by running
```
java Main.java
```

After you compile the shape classes, you only need to compile and run `Main.java` as usual.

# Instructions

## Preliminaries - Count a Letter
The "counting" algorithm works like this:
1. Create a "count" variable that keeps track of how many elements meet the condition.  Start this count at 0.
2. Loop through your structure (`String`, list, etc.)
3. Check if the current item (could be list element or character from a `String`) meets some condition.
    - Equal to something
    - Greater than something
    - Less than something
    - Some other condition
4. If the element meets the condition, then increment the count.
5. Return the count.

As an example, to count how many letters in a `String` are equal to a `target` character, we can do so like this
```java
String word = "mississippi";

String target = "s";
int count = 0;
for (int i = 0; i < word.length(); i++)
{
    String currentLetter = word.substring(i, i+1);
    if (currentLetter.equals(target))
    {
        count++;
    }
}
System.out.println("The letter " + target + " appears " + count + " times.");
```

## Preliminaries - Count Every Letter
If I wanted to count _every_ letter in a `String`, I could wrap the above counting algorithm in _another_ `for` loop.  See the [example Snap! program](https://snap.berkeley.edu/snap/snap.html#present:Username=ktvu&ProjectName=CSA%20Runestone%202.9%20Letter%20Mode%20Example) for a block visualization of the algorithm.

```java
String word = "mississippi";

for (int i = 0; i < word.length(); i++)
{

    /*********** This here is the "regular" counting algorithm *****/
    String target = word.substring(i, i+1);
    int count = 0;
    for (int j = 0; j < word.length(); j++)
    {
        String currentLetter = word.substring(j, j+1);
        if (currentLetter.equals(target))
        {
            count++;
        }
    }
    System.out.println("The letter " + target + " appears " + count + " times.");
    /***************************************************************/

}
```
      

## Problem 1
Using the counting algorithms above with other algorithms such as the "finding the maximum" algorithm, write a program that finds the letter that appears **most often** in a `String`.  If a word has multiple letters that appear the same number of times, just print out one of the letters.

**Sample Output**
```
Enter a word:
calculator

The letter c appears the most times.

Enter a word:
boom

The letter o appears the most times.
```

## Sample Solutions
```java
Scanner sc = new Scanner(System.in);

System.out.println("Enter a word");
String word = sc.nextLine();

int maxCount = 0;  // I can start at 0 since the number of times a letter can appear is at least 1
String maxLetter = "";

for (int i = 0; i < word.length(); i++)  // loop through to check all the letters
{

    /*********** Count how many times a letter appears in the word *****/
    String target = word.substring(i, i+1);
    int count = 0;
    for (int j = 0; j < word.length(); j++)
    {
        String currentLetter = word.substring(j, j+1);
        if (currentLetter.equals(target))
        {
            count++;
        }
    }
    System.out.println("The letter " + target + " appears " + count + " times.");
    /***************************************************************/
    
    
    // Check if the current count is the maximum count
    // Update maximum values accordingly
    if (count > maxCount)
    {
        maxCount = count;
        maxLetter = target;
    }
}

System.out.println("The letter " + maxLetter + " appears the most times at " + maxCount + " times.");

sc.close();
```
