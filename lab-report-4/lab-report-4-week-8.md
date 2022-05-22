# Lab Report 4

### markdown-parse repositories

[Link to my markdown-parse repository][My markdown-parse Repository]

[Link to the markdown-parse repository I reviewed][Reviewed markdown-parse Repository]

---

### Expected Output

The tests for the three markdown snippets should produce the following output: 

##### 1. Code Snippet 1
```
[`google.com, google.com, ucsd.edu]
```

##### 2. Code Snippet 2
```
[a.com, a.com(()), example.com]
```

##### 3. Code Snippet 3
```
[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]
```

### Code in MarkdownParseTest.java
```
@Test
public void testSnippet1() throws IOException {
    List<String> testFileLinks = List.of("`google.com", "google.com", "ucsd.edu");
    Path testFile = Path.of(LAB4_FOLDER + "snippet1.md");
    String testFileContent = Files.readString(testFile);
    assertEquals(testFileLinks, MarkdownParse.getLinks(testFileContent));
}

@Test
public void testSnippet2() throws IOException {
    List<String> testFileLinks = List.of("a.com", "a.com(())", "example.com");
    Path testFile = Path.of(LAB4_FOLDER + "snippet2.md");
    String testFileContent = Files.readString(testFile);
    assertEquals(testFileLinks, MarkdownParse.getLinks(testFileContent));
}

@Test
public void testSnippet3() throws IOException {
    List<String> testFileLinks = List.of("https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule");
    Path testFile = Path.of(LAB4_FOLDER + "snippet3.md");
    String testFileContent = Files.readString(testFile);
    assertEquals(testFileLinks, MarkdownParse.getLinks(testFileContent));
}
```

### Output

* #### My implementation

None of the tests passed for my implementation.

![The JUnit output that shows the test failure for my implementation][My Output]

* #### The implementation I reviewed

None of the tests passed for the implementation I reviewed.
![The JUnit output that shows the test failure for the implementation I reviewed][Reviewed Output]

## Questions

1. Do you think there is a small (<10 lines) code change that will make your program work 
for snippet 1 and all related cases that use inline code with backticks? 
If yes, describe the code change. If not, describe why it would be a more involved change.

    I don't think there is a small code change that will make my program work for snippet 1 and all related cases that use inline code with backticks. 
    I think it would be a more involved change because I would have to keep track of the number of backticks. 
    Then, I would have to find whether each link's brackets are inside a pair of backticks or between two pairs of backticks.

2. Do you think there is a small (<10 lines) code change that will make your program work 
for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? 
If yes, describe the code change. If not, describe why it would be a more involved change.

    I think there is a small code change that will make my program work for snippet 2 and all related cases 
    that nest parentheses, brackets, and escaped brackets because I only have to check 
    whether each bracket before the opening parenthesis are escaped. 
    If they are not escaped, then I end the search for the current link and search for another one (starting with an opening bracket). 
    If they are escaped, then I can continue my current search for the link as if there was not bracket.

3. Do you think there is a small (<10 lines) code change that will make your program work 
for snippet 3 and all related cases that have newlines in brackets and parentheses? 
If yes, describe the code change. If not, describe why it would be a more involved change.

    I think there is a small code change that will make my program work 
    for snippet 3 and all related cases that have newlines in brackets and parentheses. 

    I would have to: 
    * check whether the opening parenthesis is followed by a new line, 
    * check whether the closing parenthesis is preceded by a new line, and
    * ensure that there is non space inside the link.



[My markdown-parse Repository]: https://github.com/thanhnhanlam/markdown-parser.git
[Reviewed markdown-parse Repository]: https://github.com/NuojinliXu/markdown-parser
[My Output]: images/my-output.png
[Reviewed Output]: images/reviewed-output.png
