# Lab Report 5
```
# Create your grading script here


rm -rf student-submission

git clone $1 student-submission
declare -i score
cd student-submission/

if [[ -f "ListExamples.java" ]] 
then
    echo "File was found."
    ((score++))
else 
    echo "FAIL"
    echo "File was not found in directory" 
    echo $score
    exit
fi

cd ..
cp TestListExamples.java student-submission/

cd student-submission/
javac -cp ".;C:/Users/anike/list-examples-grader/lib/hamcrest-core-1.3.jar;C:/Users/anike/list-examples-grader/lib/junit-4.13.2.jar" *.java 2> error.txt
if [[ $? -eq 0 ]]
then
    echo "COMPILE SUCCESSFUL"
    ((score++))
else
    echo "COMPILE ERROR"
    echo "$(cat error.txt)"
    echo $score
    exit
fi
java -cp ".;C:/Users/anike/list-examples-grader/lib/hamcrest-core-1.3.jar;C:/Users/anike/list-examples-grader/lib/junit-4.13.2.jar" org.junit.runner.JUnitCore TestListExamples > junit.txt
cat junit.txt
if [ $? -eq 0 ]
then
    echo "All the tests passed"
    ((score=score+2))
else 
    echo "Some tests failed"
    
fi

echo "Final Score = $score"


```
Let us try running the `grade.sh` on different repositories
* Repository 1 : [Repository 1](https://github.com/ucsd-cse15l-f22/list-methods-compile-error) , which has a syntax error of a missing semicolon.

![Image](https://media.discordapp.net/attachments/891952727641456661/1046850419881672704/image.png)

* Repository 2 : [Repository 2](https://github.com/ucsd-cse15l-f22/list-methods-filename) which has a great implementation saved in a file with the wrong name.

![Image](https://media.discordapp.net/attachments/891952727641456661/1046850691953598474/image.png)

* Repository 3 : [Repository 3](https://github.com/ucsd-cse15l-f22/list-methods-nested) which has a great implementation saved in a nested directory called `pa1`.

![Image](https://media.discordapp.net/attachments/891952727641456661/1046850829707133028/image.png)


**Let us analyze how the script runs when we pass in Repository 2**

The first `if` statement is not executed as the name of the file is different. So it goes into the `else` and executes the three echo statements whose standard output can be seen the image for Repository 3. In the else we also have the `exit` statement which changes the return code to 0 as we exit the code due to the absence of the required files!!

```
if [[ -f "ListExamples.java" ]] 
then
    echo "File was found."
    ((score++))

```

This `if` block doesn't run as the name of the file is different.