# Lab Report 3
### Implementing all Group Choice Options from Lab 5.

## Streamlining ssh Configuration

My .ssh/config file and how I edited it:

I opened my config file in the notepad and edited it in there. I set my alias to be "alice"

>I later modified it to be "ieng6" just so I could copy the commands from the lab easily, so some screenshots will show me doing `ssh ieng6` instead of `ssh alice`

![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280076811_1180703666097699_1235992140166893346_n.png?_nc_cat=106&ccb=1-6&_nc_sid=aee45a&_nc_ohc=cBHK3BRvpW8AX8QYeE9&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVINgLVIz3eIDGeJkotsp7z1S4soB4J3moO4MxzetrcYiw&oe=629FD39B)

The ssh command logging me into my account with my alias:

In the terminal, I typed `ssh alice` to log into my ieng6 account

![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280122006_1051182129137777_7908281862068135903_n.png?_nc_cat=108&ccb=1-6&_nc_sid=aee45a&_nc_ohc=rGd7TROQpbAAX8j-5mQ&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVLPq5xF1i67c1g582QkWrKhLyieS7rMJsCNQKH-jMPV2Q&oe=629E3DDA)

An scp command copying a file to my account using just my alias; I will copy over index.md in this case

![](https://scontent.xx.fbcdn.net/v/t1.15752-9/279244065_800450520935355_4640089459631946226_n.png?_nc_cat=111&ccb=1-6&_nc_sid=aee45a&_nc_ohc=W1fkgzXTcp4AX-vJKf6&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVLLvcDiRz7b7v1UN3Pow4-67Eob_wxKXhlpy9vORbGudQ&oe=629DC769)

Using the ls command, we can see that the file, index.md, has been copied over to my account using my alias.

## Setup Github Access from ieng6
The public key that is made is stored here on Github...
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280120381_308068234681186_3905321658330235621_n.png?_nc_cat=104&ccb=1-6&_nc_sid=aee45a&_nc_ohc=mwVmAL4NZsgAX89bNoA&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVIFPSYz_1hSBs3DpkHze3KzUHzVNkK6zp9NLA6m9Q2Bew&oe=629F82E7)

and here in my user account:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/279802389_328276499250969_704356715956388360_n.png?_nc_cat=103&ccb=1-6&_nc_sid=aee45a&_nc_ohc=SbV1Ukj-DQIAX-AMeh1&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVITFtRw0BnB2zNz1wfyLszas4fMMQAaWc-QKJVeYyipjA&oe=629C3B67)

The private key I made is stored in the id_rsa file in the ssh folder:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280390101_317092743836534_2117228152023734444_n.png?_nc_cat=108&ccb=1-6&_nc_sid=aee45a&_nc_ohc=Ot0z9Y8KWgsAX-Cqku1&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJ14MpsHo9jtsYngHN9quRKSGyolt43vxgB8YgaDIl1AQ&oe=629FA2C7)

Let's run some git commads and push the changes to Github while on my ieng6 account! 
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280240914_547138916775576_2575191255221803961_n.png?_nc_cat=108&ccb=1-6&_nc_sid=aee45a&_nc_ohc=JI54ALsOTqAAX8W-B4T&_nc_oc=AQkhXrw5UdZ6FqoK5jgeIx5-rw1mnuHLPWKUnEj8VU5p8qmZSIUGhomsESypA7sQ1yF8RO-HJzaxQ_eE_mPDjsAz&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJH6Yn0H0ytbhru-8rwMzb5AAdftI9brYoDTcYHbJtlvw&oe=629FAACF)

Here's the [link](https://github.com/alicema1202/markdown-parser/commit/fc9782f8939a4788185cab67135f28162b1e298b "markdown-parser repository") for the resulting commit:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280192101_5415016561864778_2347696041906020515_n.png?_nc_cat=103&ccb=1-6&_nc_sid=aee45a&_nc_ohc=gApz04CKrk4AX_a-FOZ&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVKQSi4WNdOuHwzrcg-Mjyk_MOdNU0rHsBvqMcQ2Xcpwgg&oe=629EEA05)

## Copy whole directories with scp -r

The picture below shows my entire markdown-parse directory being copied into my ieng6 account using the following command:
```
scp -r *.java *.md lib/ ieng6:markdown-parse
```
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280180437_753130449191179_1327177585582640984_n.png?_nc_cat=102&ccb=1-6&_nc_sid=aee45a&_nc_ohc=yx2Oll_owEEAX8dMGRD&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJnX0h-trSForlGwbLsguENpDE1CGfI0hVqzEnoZzVOJg&oe=629CB726)

Now, if I log into my ieng6 account and compile the tests for my repository, it will show the JUnit tests running:
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/279815557_4969395779763785_5412307686231111366_n.png?_nc_cat=108&ccb=1-6&_nc_sid=aee45a&_nc_ohc=cY8WEdG1VTMAX_9AY-V&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVKlL3Ku-MM5bQF0XWnvb7d33spV6cxLHy46GajwzdvVqQ&oe=62A0120F)

Combining `scp`, `;`, and `ssh`, I am able to copy the entire directory to my ieng6 account and run the JUnit tests all in one command line with the following command:
```java
scp -r *.java *.md lib/ ieng6:markdown-parser; ssh ieng6 "cd markdown-parser; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"  
```
![](https://scontent.xx.fbcdn.net/v/t1.15752-9/280279700_1457206708051544_2968601044265201778_n.png?_nc_cat=106&ccb=1-6&_nc_sid=aee45a&_nc_ohc=c4M7MMnG644AX-fgquV&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AVJBHm6rt0Xf0Xqagr2V87-IMx_xCZqv-6hHxTWspBO3ug&oe=629EF2D0)
