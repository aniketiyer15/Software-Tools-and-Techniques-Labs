# Linux Commands
## grep Commands
* **grep -i**

This command line is used to return the line in which the input string is present irrespective of the case.

For example :

```
technical:232$ grep -i "hello" 911report/chapter-1.txt
    At 10:39, the Vice President updated the Secretary on the air threat conference: Vice President: There's been at least three instances here where we've had reports of aircraft approaching Washington-a couple were confirmed hijack. And, pursuant to the President's instructions I gave authorization for them to be taken out. Hello? 

```

This checks for the occurences of the word *"hello"*. And as we can see it prints out the line which has **Hello**. This shows that it is case insensitive while searching

This is useful as we can find the lines in which the particular word occurs irrespective of the case.

Few more usages of **grep -i** on the files in the technical directory are as follows:

```
[cs15lfa22dp@ieng6-201]:technical:235$ grep -i "LEGAL" government/Media/A_Perk_of_Age.txt
A Perk of Age: Free Legal Advice
Free Legal advice is only a phone call away - and the hot lines
states, Washington D.C., and Puerto Rico operate legal-assistance
caregivers as well. Volunteers offer advice on legal questions,
provide self-help materials, and make referrals to legal aid
legal-services network. Anyone who meets the age requirement can
call the hot line, but hands-on legal counsel goes first to people
numbers and hours, go to www.aoa.gov/legal/hotline.html, or call
state without a hot line, the locator can point you to local legal
Legal Services Network is now available in 46 states and expects to
legal counseling, either face-to-face or by phone, at no cost.

```
As we can see, although I entered **"LEGAL"** as my input, I got multiple occurences of legal as `grep -i` is case insensitive. This is a really helpful feature of grep as we can find the occurences irrespective of whatever case the user inputs the word as.

```
[cs15lfa22dp@ieng6-201]:technical:236$ grep -i "rElaTiVes" plos/pmed.0010069.txt 
        distant relatives also having that cancer, or another kind of cancer. Of the 27 cancers, 16
        third- to fifth-degree) relatives. The seven cancers with the highest increased familial
        occurrence both in close and distant relatives were breast, prostate, stomach, lung, colon,
        cancers, for example, relatives of individuals with stomach, colon, rectal, or endometrial

```
As you can see, purposely I entered my input in a weird way. But still, `grep -i` manages to find all the occurences of "relatives" in the file, hence proving that the case insensitive feature of the grep search is really useful

* **grep -n**

This command line helps return the line where the input string occurs along with the line number.

For example:

```
[cs15lfa22dp@ieng6-201]:technical:237$ grep -n "trials" biomed/1468-6708-3-4.txt
7:        common problem in clinical trials is the missing data
289:          explanatory trials' [ 6 ] . It is often concerned with
297:          If we can design trials that will allow patients to be
301:          trials' [ 7 ] . Prevention studies with all-cause
309:          design of (b) is highly recommended for all trials if at
321:          in clinical trials. For clinical trials conducted for
370:          Its popularity has recently gainied in clinical trials
428:        trials include the Wilcoxon signed-rank test, Mann-Whitney
468:        Association's draft guidance on diabetes trials
504:        dropouts in clinical trials is a research topic that is

```
As we can see, it prints out the line number and the line where the input string occurs. It is really useful as it prints out the line number too which makes it much easier for the users to find the exact line where the string occurs.

We could also combine the usage of `grep -i` and `grep -n` to find the occurences of the string irrespective of the case in which is entered.

For example:


`[cs15lfa22dp@ieng6-201]:technical:239$ grep -n "TRIALS" biomed/1468-6708-3-4.txt`

As we can see the above command doesn't print anything. But if we include the `grep -i` command, it produces a different output

```
[cs15lfa22dp@ieng6-201]:technical:238$ grep -i -n "TRIALS" biomed/1468-6708-3-4.txt
7:        common problem in clinical trials is the missing data
289:          explanatory trials' [ 6 ] . It is often concerned with
297:          If we can design trials that will allow patients to be
301:          trials' [ 7 ] . Prevention studies with all-cause
309:          design of (b) is highly recommended for all trials if at
321:          in clinical trials. For clinical trials conducted for
370:          Its popularity has recently gainied in clinical trials
428:        trials include the Wilcoxon signed-rank test, Mann-Whitney
468:        Association's draft guidance on diabetes trials
504:        dropouts in clinical trials is a research topic that is

```
As we can see, this command prints the desired output. Hence, the combination of `grep -i` and `grep -n` can be really useful as it searches for the input string irrespective of the case

One last usage of the `grep -n` command is as follows:

```
[cs15lfa22dp@ieng6-201]:technical:240$ grep -n "planes" 911report/chapter-3.txt
1104:                Force planes carrying Delta Force commandos and fresh fuel. Mild sandstorms disabled
1159:                operation was not cost free: the United States lost two planes. Evidence accumulated

```
As we can see **chapter-3.txt** is a large file and it could be tough to search for the lines in which *planes* occur. `grep -n` makes our task a lot easier and is hence quite useful.

* **grep -l**

This command line helps us find the files in which a particular string appears.

For example: In the directory 911report, there are multiple files which contain the string **planes**. The following command line helps us print the files containing the string **planes**

```
[cs15lfa22dp@ieng6-201]:technical:245$ cd 911report
[cs15lfa22dp@ieng6-201]:911report:246$ grep -l planes *
chapter-1.txt
chapter-11.txt
chapter-12.txt
chapter-13.1.txt
chapter-13.2.txt
chapter-13.3.txt
chapter-13.4.txt
chapter-13.5.txt
chapter-3.txt
chapter-5.txt
chapter-6.txt
chapter-7.txt
chapter-8.txt
chapter-9.txt

```
As we can see it prints out all the files containing the word planes
```

[cs15lfa22dp@ieng6-201]:Alcohol_Problems:264$ grep -l alcohol *
DraftRecom-PDF.txt
Session2-PDF.txt
Session3-PDF.txt
Session4-PDF.txt

```
The above command line prints out all the files containing the word alcohol.

One last example of the usage of `grep -l` would be:
```
[cs15lfa22dp@ieng6-201]:biomed:268$ grep -l melatonin *
1471-213X-1-9.txt
1472-6793-2-11.txt
```
As we can see `grep -l` could be helpful in many ways. Let's say we have three files. One file contains the names of students who got an A on the first midterm. The second file contains the names of students who got an A on the second midterm and the third file contains the name of students who scored an A in the final. We could search for the name of the students who have done extraordinarily well in all the exams using the `grep -l` command.

