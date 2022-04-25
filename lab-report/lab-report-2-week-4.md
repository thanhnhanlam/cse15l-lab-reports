# Lab Report 2

## Week 4

In lab 3, the group worked on markdown-parser, a program that gets all the links from a markdown file.
Changes were made to the original code in order to fix bugs. 
This lab report will focus on three of these changes.

### 1. Adding an extra line at the end of the file

![Code Change With Extra Line][Commit Extra Line]

The **failure-inducing** input that prompted me to make that change is 
**adding an extra line at the end of the file**.

Link to the test file for this failure-inducing input.

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

2-3 sentences describing the relationship between 
the bug, the symptom, and the failure-inducing input.

### 2. 

![Code Change With Brackets Without Link][Commit Without Link]

The **failure-inducing** input that prompted me to make that change is 
.

Link to the test file for this failure-inducing input.

The symptom of the failure-inducing input: 
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 37
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:3734)
        at java.base/java.lang.String.substring(String.java:1903)
        at MarkdownParse.getLinks(MarkdownParse.java:20)
        at MarkdownParse.main(MarkdownParse.java:31)
```

### 3. 

![Code Change End With Open Bracket][Commit End Open Bracket]

The **failure-inducing** input that prompted me to make that change is 
.

Link to the test file for this failure-inducing input.

In order to make the symptom visible, a counter for the number of iterations of the loop and 
a corresponding print statement were added. 
The symptom of the failure-inducing input: 
```
Add a counter to MarkdownParse.java to test files
java MarkdownParse test-files/test-file7.md
0
1
2
3
4
5
6
7
8
9
10
11
12
...
```

[Commit Without Link]: ../image/lab-report-2/commit-extra-line.png
[Commit Extra Line]: ../image/lab-report-2/commit-without-link.png
[Commit End Open Bracket]: ../image/lab-report-2/commit-end-open-bracket.png
