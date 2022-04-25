# Lab Report 2
> Three code changes that contributed to bug-fixing.

## Code Change 1
> Issue: When there is an extra line at the end, the code runs into an infinite loop and stops working. 

Code change difference:

![](https://scontent.xx.fbcdn.net/v/t1.15752-9/278501479_468417601704718_8389449468913125687_n.png?_nc_cat=106&ccb=1-5&_nc_sid=aee45a&_nc_ohc=7zkC7KQvGBUAX9cWZtw&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVLjzgT9FYL0GnY9Ah3FhJjG59mBLTolAzjzDGMWJZklmA&oe=628B0A49)

The issue can be seen when the original code is run with [this](test-file-1.txt "Test File 1") test file.

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
>Issue: The code recognizes any text file with [a pair of brackets] that comes before (a set of parentheses) as a link.

Code change difference:

![](https://scontent.xx.fbcdn.net/v/t1.15752-9/278958125_525245492345403_1016325706361200936_n.png?_nc_cat=108&ccb=1-5&_nc_sid=aee45a&_nc_ohc=_qVS9cWo-EoAX9A9X-P&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVL9WhFxFcRAJGhtB-1qtuXVlNJmPWLgJTa9lv4pk10jtA&oe=62891872)

The issue can be recognized when the code is run through [this](test-file-3.txt "Test File 3") test file. 

When this file is run at the command line, it outputs the following:

```
[page.com]
```
Relationship between the bug, the symptom, and the failure inducing input:

The code looks for a [pair of brackets] and (a set of parentheses) that follow. It will recognize anything which follow that set of rules as a link.

This means that even if it was in this format: `[something] intervening text (wontBeALink.com)`

It would output `wontBeALink.com`. This is the reason why page.com was outputted in our test file, despite how there was no proper markdown-format link in the file.


## Code Change 3
> Issue: The code recognizes images as links as well

Code change difference:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/278936196_590958952462949_8542918747941334661_n.png?_nc_cat=104&ccb=1-5&_nc_sid=aee45a&_nc_ohc=jldoniEFGZYAX8LSsxf&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVI0MUuF6MMQvIXkTEkJinU-p-jDMmuO2SR3p4UTcgJSdA&oe=62881A0D)

The issue can be recognized when the code is run through [this](test-file-2.txt "Test File 2") test file.

When this file is run at the command line, it outputs the following:

```
[https://something.com, some-thing.html, some-image.jpg]
```
Relationship between the bug, the symptom, and the failure inducing input:

We can see that the code recognizes `some-image.jpg` as a link because an image in markdown follows a similar format as a link. 

Links in markdown follow this format: `[title](link.com)`

Images in markdown follow this format: `![image](image.png)`

When we feed the code a file which has both links and images, it will recognize images as links as well because it does not know that the exclamation mark signifies that it is not a link.

This is why we can see `some-image.jpg` get returned in the command line, even though it is not a link.

