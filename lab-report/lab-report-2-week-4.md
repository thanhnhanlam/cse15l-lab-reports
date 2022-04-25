# Lab Report 2

## Week 4

In lab 3, the group worked on markdown-parser, a program that gets all the links from a markdown file.
Changes were made to the original code in order to fix bugs. 
This lab report will focus on three of these changes.

### 1. Adding an extra line at the end of the file

![Code Change With Extra Line][Commit Extra Line]

Link to the test file for the corresponding failure-inducing input.

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

![Code Change Without Link][Commit Without Link]

### 3. 

![Code Change End With Open Bracket][Commit End Open Bracket]

[Commit Without Link]: ../image/commit-extra-line.png
[Commit Extra Line]: ../image/commit-without-link.png
[Commit End Open Bracket]: ../image/commit-end-open-bracket.png
