# Lab Report 2

## Week 4

In lab 3, the group worked on markdown-parser, a program that gets all the links from a markdown file.
Changes were made to the original code in order to fix bugs. 
This lab report will focus on three of these changes. 
Each change to the code is prompted by a **failure-inducing input**.

### 1. Adding an extra line at the end of the file

The **failure-inducing** input that prompted me to make the change is 
**adding an extra line at the end of the file**.

The code change diff: 
![Code Change With Extra Line][Commit Extra Line]

Link to the test file for this failure-inducing input: 
[test-extra-line.md](https://github.com/thanhnhanlam/markdown-parser/blob/main/test-extra-line.md)

The symptom of the failure-inducing input: 
```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.util.Arrays.copyOf(Arrays.java:3511)
        at java.base/java.util.Arrays.copyOf(Arrays.java:3480)
        at java.base/java.util.ArrayList.grow(ArrayList.java:237)
        at java.base/java.util.ArrayList.grow(ArrayList.java:244)
        at java.base/java.util.ArrayList.add(ArrayList.java:454)
        at java.base/java.util.ArrayList.add(ArrayList.java:467)
        at MarkdownParse.getLinks(MarkdownParse.java:17)
        at MarkdownParse.main(MarkdownParse.java:25)
```

The program only stopped when the closing parenthesis of the last link was the last character. 
Therefore, **adding an extra line at the end of the file** created an **infinite loop** that led to an `OutOfMemoryError`.
**The condition of the loop remained true even when there was no link left to retrieve**, 
so another condition was added so that the program would stop when there was no opening bracket after the last link. 

### 2. Using brackets without link

The **failure-inducing** input that prompted me to make that change is 
**using a pair of brackets without a link**.

The code change diff: 
![Code Change With Brackets Without Link][Commit Without Link]

Link to the test file for this failure-inducing input: 
[test-brackets.md](https://github.com/thanhnhanlam/markdown-parser/blob/main/test-brackets.md)

The symptom of the failure-inducing input: 
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 37
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:3734)
        at java.base/java.lang.String.substring(String.java:1903)
        at MarkdownParse.getLinks(MarkdownParse.java:20)
        at MarkdownParse.main(MarkdownParse.java:31)
```

**When using brackets that are not followed by a link (between parentheses)**, 
the program still tries to find a link, so it looks for parentheses. 
However, since there are no parenthesis, the index returned by the search is -1. 
Then, when **the program tries to add a new link to its list of links using this invalid negative index**, 
**an IndexOutOfBoundsException is thrown**.

### 3. Ending the file with an open bracket

The **failure-inducing** input that prompted me to make that change is 
**ending the file with an open bracket**.

The code change diff: 
![Code Change End With Open Bracket][Commit End Open Bracket]

Link to the test file for this failure-inducing input: 
[test-file8.md](https://github.com/thanhnhanlam/markdown-parser/blob/main/test-files/test-file8.md)

The symptom of the failure-inducing input: 
```
Exception in the thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:764)
        at java.base/java.lang.String.substring(String.java:1908)
        at MarkdownParse.getLinks(MarkdownParse.java:20)
        at MarkdownParse.main(MarkdownParse.java:34)
```

After the last link, the program checked for the existence of an opening bracket but not for that of a closing bracket. 
Therefore, in **a file that contained an opening bracket without a closing bracket**, 
the loop of **the program kept searching for a link from the same index**, created an **infinite loop**, which led to an `OutOfMemoryError`.


[Commit Without Link]: images/commit-extra-line.png
[Commit Extra Line]: images/commit-without-link.png
[Commit End Open Bracket]: images/commit-end-open-bracket.png
