JAVA CI/CD PRACTICAL 1 - FREESTYLE PROJECT

PROJECT FILES
-------------
src/main/java/App.java       - Java application
src/test/java/AppTest.java   - JUnit test
pom.xml                      - Maven configuration

1. CHECK JAVA AND MAVEN
-----------------------
Open CMD and run:
    java -version
    mvn -version

2. BUILD, TEST AND PACKAGE
--------------------------
Open CMD in the JavaProject folder and run:
    mvn clean package

Expected:
    Tests run: 1
    Failures: 0
    BUILD SUCCESS

The JAR is created in:
    target\JavaProject-1.0.jar

3. RUN THE JAVA PROGRAM
-----------------------
Run:
    java -cp target\classes App

Expected:
    Hello Jenkins

4. UPLOAD TO GITHUB
-------------------
Create an empty GitHub repository named JavaProject.
Open CMD in this folder and run (replace the URL):
    git init
    git add .
    git commit -m "First commit"
    git branch -M main
    git remote add origin YOUR_GITHUB_URL
    git push -u origin main

5. JENKINS FREESTYLE CONFIGURATION
----------------------------------
New Item:
    Java-CI
    Freestyle project

Source Code Management:
    Git
    Repository URL: your GitHub repository URL
    Branch: */main

Build Triggers:
    Poll SCM
    H/1 * * * *

Build Steps:
    Execute Windows batch command
    mvn clean package

Post-build Actions:
    Archive the artifacts
    target/*.jar

Click Save, then Build Now.
Open the build's Console Output.
Expected:
    BUILD SUCCESS
    Finished: SUCCESS

NOTE:
- Maven and Git must be installed and available in PATH.
- Jenkins must be able to run Java, Maven and Git.
- Poll SCM checks for changes approximately every minute.
