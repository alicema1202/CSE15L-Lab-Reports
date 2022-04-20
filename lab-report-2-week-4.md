# Lab Report 2
> Three code changes that contributed to bug-fixing.

## Code Change 1
> Issue: When there is an extra line at the end, the code runs into an infinite loop and stops working. 

The issue can be seen when the original code is run with [this](test-file-1.txt) test file.

When the above file was run at the command line, it outputted a message like this:
```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space at java.base/java.
util.Arrays.copyOfRange(Arrays.java:3822) at java.base/java.lang.StringLatin1.newString
(StringLatin1.java:769) at java.base/java.lang.String.substring(String.java:2709) at 
MarkdownParse.getLinks(MarkdownParse.java:19) at MarkdownParse.main(MarkdownException in 
thread "main" java.lang.OutOfMemoryError: Java heap space at java.base/java.util.Arrays.
copyOfRange(Arrays.java:3822) at java.base/java.lang.StringLatin1.newString(StringLatin1.
java:769) at java.base/java.lang.String.substring(String.java:2709) at MarkdownParse.
getLinks(MarkdownParse.java:19) at MarkdownParse.main(MarkdownParse.java:30)Parse.java:30)
main
```
Relationship between the bug, the symptom, and the failure inducing input:

In the code, there is a while loop that causes the bug: 

```
while(currentIndex < markdown.length())
```

The failure-inducing input has extra lines at the end, which cause `markdown.length()` to be incremented by two each extra line. Thus, `currentIndex` is never larger than or equal to `markdown.length()`, creating an infinite loop that causes the `java.lang.OutOfMemoryError`.


## Code Change 2
> Issue: The code recognizes images as links as well

## Code Change 3
>Issue: 