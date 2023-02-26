# **Week 4 Lab Report**
## Setup
### **1. Setup Delete any existing forks of the repository you have on your account**
### **2. Setup Fork the repository**
### **3. The real deal Start the timer!**

## **Challenge Task**
### **4. Log into ieng6**
To login into the ieng6 account, I typed into the terminal `ssh cs15lwi23aad@ieng6.ucsd.edu` and press the `<return>` key.
![]()


### **5. Clone your fork of the repository from your Github account**

**Copying the lab report repository URL:**
Go to the lab report repository. Click on the `<> Code` button, then click on `SSH`, and then click on the `Copy to Clipboard` `❐` button to copy the github repository URL.
![]()

**Cloning the lab report repository:**
 After copying the URL, type in to the terminal, `git clone` then press `<Ctrl> (^)` + `V` to paste the repository URL. After pasting the URL, press `<return>` to clone the repository. 
![]()

### **6. Run the tests, demonstrating that they fail**
Firstly, type in `cd la` then press `<tab>` to autofill to `cd lab7/` and then press `return>` to go into the `lab7` directory. 
![]()

To run the tests, you first must compile and then the test file of the lab report. To compile, press `<Crtl>` + `r` to access my bash history, and type in `javac` which will autofill to `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` and then press `return` to compile the java files. After that, again press `<Ctrl>` + `r` and type in `java ` will it having a space at the end to autofill to `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples` and then press `return` to run the tests.

![]()
### **7. Edit the code file to fix the failing test**

### **8. Run the tests, demonstrating that they now succeed**

### **9. Commit and push the resulting change to your Github account (you can pick any commit message!)**
