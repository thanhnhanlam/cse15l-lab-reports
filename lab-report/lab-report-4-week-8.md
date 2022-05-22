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

* #### The implementation I reviewed


## Question

1. Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

2. Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.

3. Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.

[My markdown-parse Repository]: https://github.com/thanhnhanlam/markdown-parser.git
[Reviewed markdown-parse Repository]: https://github.com/NuojinliXu/markdown-parser
