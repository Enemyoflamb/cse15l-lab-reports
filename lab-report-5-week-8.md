# Lab 5

Here is my grade.sh script:
```
set -e
rm -rf student-submission
git clone $1 student-submission
CPATH=.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar
cp -R ./lib ./student-submission
cp *.java ./student-submission
cd student-submission
javac -cp  ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" org.junit.runner.JUnitCore TestListExamples
```
Below are the three screenshots for the GradeServer implementation with different repository URL parameters: 

![Image](/cse15l-lab-reports/w2assets/11.14.1.png)

![Image](/cse15l-lab-reports/w2assets/11.14.1.png)

![Image](/cse15l-lab-reports/w2assets/11.14.1.png)
