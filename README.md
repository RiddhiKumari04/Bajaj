# Quiz Leaderboard System

Java-based solution for the SRM Internship Assignment.

## Features
- Polls validator API 10 times
- Maintains 5-second delay between polls
- Removes duplicate events using `roundId + participant`
- Aggregates total scores per participant
- Generates leaderboard sorted by score
- Submits final leaderboard once

## How to Test

Follow these steps to run and test the application locally:

### 1. Prerequisites
Make sure you have the following installed on your machine:
- **Java 17** (or higher)
- **Maven** (to build and run the project)

### 2. Configure Registration Number
Before running the application, you need to set your registration number.
1. Open `src/main/java/com/riddhi/quiz/Main.java`.
2. Find the `REG_NO` constant on line 8.
3. Replace the placeholder value with your actual registration number.
```java
private static final String REG_NO = "RA2311003030302";
```

### 3. Build the Project
Open your terminal/command prompt in the root of the project directory and compile the code using Maven:
```bash
mvn clean compile
```

### 4. Run the Application
Execute the compiled Java code using the following Maven command:

**For Windows (PowerShell / Command Prompt):**
```bash
mvn exec:java -D"exec.mainClass=com.riddhi.quiz.Main"
```

**For Linux / macOS (or Git Bash):**
```bash
mvn exec:java -Dexec.mainClass="com.riddhi.quiz.Main"
```

### 5. What to Expect During Execution
When you run the application, it will perform the following steps:
1. **Polling:** It will silently call the `fetchMessages` API 10 times to collect event data.
2. **Delay:** It intentionally pauses for **5 seconds** between each poll (as per API requirements). The script will appear to hang for about 45-50 seconds—this is normal behavior.
3. **Leaderboard Generation:** After polling is complete, it aggregates the scores, removes duplicate entries, and sorts the leaderboard in descending order.
4. **Submission:** It prints the final leaderboard to the console, calculates the total score, and submits the data.
5. **Output:** You should finally see a console output similar to this:
```text
Final Leaderboard:
Bob -> 295
Alice -> 280
Charlie -> 260
Total Score: 835
Submission Response: {"regNo":"RA2311003030302","totalPollsMade":...,"submittedTotal":835,"attemptCount":...}
```
