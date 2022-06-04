# Lab Report 5

## Repositories Referenced:
1. [My Repository](https://github.com/alicema1202/markdown-parser "Alice Ma")
2. [Shared Repository](https://github.com/nidhidhamnani/markdown-parser.git "Shared")

### To start off, I created two text files that contained all the tests output for each of the repositories.

My Repo Output:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/285048583_593238051953055_7625427372967432467_n.png?_nc_cat=105&ccb=1-7&_nc_sid=aee45a&_nc_ohc=f_uXQqVLaCkAX9BnEJ3&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJmz5dxXh2-WgNKuDynZwXap_DRYP7oTLySpcppdXC7Pw&oe=62BF4788)

Shared Repo Output:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/285102917_562589742096111_3004434806807314000_n.png?_nc_cat=107&ccb=1-7&_nc_sid=aee45a&_nc_ohc=QCUtg30ChcsAX9b6xKA&_nc_oc=AQkGiFCFOl2m573rB8lpzoMnWq0w6ziV71cQ1dlrnSKAjtvdWFuJeclEDxCxRHjEoybGtVLhkGOdNfoloAJG3ity&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVLbqPeCuh7WCh6fRqWo_wqlAk_eqpC8rekJerCw5DA4yw&oe=62C25F55)

### Next, I used vimdiff to find test outputs that differed from each other!

` vimdiff MyRepo.txt SharedRepo.txt`

From this, I could see that many test results differed from each other. Two of which were:

[41.md](41.md) (My Result on Left)
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/285505651_425213659454031_4624966257335054573_n.png?_nc_cat=105&ccb=1-7&_nc_sid=aee45a&_nc_ohc=yVSLKtMQDPAAX-004Yo&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVICUOQzogEouHqhHo6canIjVUJrZ1Zfz28HKqIKnyNuXg&oe=62C1A556)

and
[201.md](201.md) (My Result also on Left)
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/285387258_1875373145990351_2676022377461926965_n.png?_nc_cat=104&ccb=1-7&_nc_sid=aee45a&_nc_ohc=qPNhZcUfr5MAX_rN1NO&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJw8d6ROBC4dKicRhO4WGrxIOCiuIWg0ysuE15ENwuNsg&oe=62BEBD72)

### Investigating further into the test files!
For 41.md, the input is:
```
[a](url &quot;tit&quot;)
```
Based on the markdown preview, the output should be:
[ ]

**The shared repo's output is correct**

The bug: My code recognizes anything in the format ` [](some text) ` as a link, and will always output ` some text ` as the link. There is no location that can be pointed to, where the code causes the bug. Rather, something should be added into the code. There should be an if statement that recognizes if other markdown formatting is within the parentheses, and if this is true, it will stop the code and not recognize it as a link. 

This chunk of code, I would say, should be inserted after the highlighted region:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/286019419_1199506270784348_2867736023516006164_n.png?_nc_cat=106&ccb=1-7&_nc_sid=aee45a&_nc_ohc=v3cz_I4xoxEAX9t1-Fs&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVKG8w_3ds41aVk8QVTDeT4IwtO82d6vHrkLQO9RoqeadQ&oe=62C1784A)
For 201.md, the input is:
```
[foo]: <bar>(baz)

[foo]
```
Based on the markdown preview, the output should be:
[ ]

**My repo's output is correct**

The bug: The shared repo's code for markdown parse recognizes something as a link whenever there are a (pair of parentheses) that come after [a pair of brackets], even if there is something intervening between the brackets and parentheses. The code simply doesn't account for this case. To fix this, there could be an if statement added that makes sure the open parentheses comes directly after the close bracket. 

This chunk of code should be inserted at around this place in the code, before the return statement:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/285003494_1106535316594441_425976853444732081_n.png?_nc_cat=111&ccb=1-7&_nc_sid=aee45a&_nc_ohc=D8ApcWOkavYAX96tc2Y&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVIQ4fxxOGI7g4_3RzL8AwK3p2JMOKkejZCAVGKzOpqmtQ&oe=62BF711D)
