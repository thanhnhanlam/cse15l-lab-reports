# Lab Report 5

### Finding the Tests with Different Results

I ran `vimdiff` on the results of running a bash for loop for each implementation of MarkdownParse and compared their output. 
I then selected two test files among the tests resulting in different outputs.

![Vimdiff][Vimdiff]

The first test file is [487.md][Test File 1]. 

The second test file is [496.md][Test File 2].

#### 1. Test File: [487.md][Test File 1]

According to the [the CommonMark demo site][CommonMark Demo Site], 
the Markdown file [487.md][Test File 1] contains no link, so the correct output should be 
```
[]
```

Therefore, the output of the provided implementation is **correct**.
![Provided Implementations's Output 1][Provided Output 1]

The output of my implementation was **wrong**.
![My Implementation's Output Test 1][My Output 1]

There is a bug in my implementation because it accepts spaces inside the link while it should not. 
To fix it, I can add an if-statement in the `getLinks` method that checks whether there is a space 
between the opening parenthesis at index `openParen` and the closing parenthesis at index `closeParen` 
for each potential link (thus inside the while loop). 
I highlighted the lines between which the fix should be added.
![Code Change Location]

#### 2. Test File: [496.md][Test File 2]

According to [the CommonMark demo site][CommonMark Demo Site], 
the Markdown file [496.md][Test File 2] contains no link, so the correct output should be 
```
[]
```

Therefore, the output of the provided implementation is **correct**.
![Provided Implentation's Output 2][Provided Output 2]

The output of my implementation was **wrong**.
![My Implementation's Output Test 2][My Output 2]

There is a bug in my implementation because it accepts opening parentheses without matching closing parentheses while it should not. 
To fix it, I can create a method that recursively checks whether each opening parenthesis has a matching closing parenthesis inside the link. 
I can add this method to the `getLinks` method at the location that I highlighted in the image below so that only links 
with matching opening and closing parentheses are added.
![Code Change Location]


[Test File 1]: https://github.com/thanhnhanlam/markdown-parser/blob/a3e7910dbc708af9b9e02cdea4bb4e9ed90bf7cd/test-files/487.md
[Test File 2]: https://github.com/thanhnhanlam/markdown-parser/blob/a3e7910dbc708af9b9e02cdea4bb4e9ed90bf7cd/test-files/496.md
[CommonMark Demo Site]: https://spec.commonmark.org/dingus/

[Vimdiff]: ./images/vimdiff.png
[My Output 1]: ./images/my-output-1.png
[Provided Output 1]: ./images/provided-output-1.png
[My Output 2]: ./images/my-output-2.png
[Provided Output 2]: ./images/provided-output-2.png
[Code Change Location]: ./images/code-change-location.png
