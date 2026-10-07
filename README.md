# JOBSHEET-5-SELECTION-STATEMENTS-2

## Identitas Mahasiswa:

* **Nama:** Cantika Putri Fauzan 
* **NIM:** 264107020237
* **Kelas / No. Presensi:** 1I / 05

 ### 1: TUJUAN PRAKTIKUM
  The following are the objectives of this practical session:
1. Students can solve problems and case studies using nested selection statements.
2. Students can apply nested selection statements in Java programs.
3. Students can apply the logical operators (&&, ||, and !) in selection structures.

   ### 2. LAB ACTIVITIES & ANALYSIS

#### 2.1.1 Experiment 1: Nested IF to Check Thesis Exam Requirements

A student wants to register for the thesis exam. The SIMTA system first checks an administrative requirement: the student must have no outstanding penalties. If this requirement is met, the system then checks the guidance log. To register for the exam, the student must have at least 8 guidance sessions with Supervisor 1 and at least 4 guidance sessions with Supervisor 2. If all requirements are met, the student can proceed to register for the thesis exam. If not, the system shows the reason for failure. Based on this case, build the Java program using the steps below.

##### 2.1.2 Java Program Code
'''java
import java.util.Scanner;

public class NestedThesisExam264107020237 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String message;

        System.out.print("Has the student cleared all penalties? yes/no: ");
        String noPenalty = sc.nextLine().trim();
        System.out.print("Enter the number of guidance sessions with Supervisor 1: ");
        int guidanceCount1 = sc.nextInt();
        System.out.print("Enter the number of guidance sessions with Supervisor 2: ");
        int guidanceCount2 = sc.nextInt();

        if (noPenalty.equalsIgnoreCase("Yes")) {
            if (guidanceCount1 >= 8 && guidanceCount2 >= 4) {
                message = "All requirements met. The student may register for the thesis exam";
            } else if (guidanceCount1 < 8 && guidanceCount2 < 4) {
                message = "Failed! Guidance sessions with Supervisor 1 are below 8 and Supervisor 2 are below 4";
            } else if (guidanceCount1 < 8) {
                message = "Failed! Guidance sessions with Supervisor 1 have not reached 8";
            } else {
                message = "Failed! Guidance sessions with Supervisor 2 have not reached 4";
            }
        } else {
            message = "Failed! The student still has an outstanding penalty";
        }

        System.out.println(message);
    }
}
#### 2.1.3 Hasil Running / Screenshot Output
Here is an example of what the output looks like after the program is run:
<img width="338" height="122" alt="hjutr" src="https://github.com/user-attachments/assets/0b4d1613-e73b-4b3e-ae72-cc8f3b902a84" />

#### 2.1.4 Questions
### Questions

1. **What happens if the student answers "No" to the penalty-clearance question? Why?**
   * **Answer:** The program will immediately execute the outer `else` block and output: `"Failed! The student still has an outstanding penalty"`. This happens because the outer `if` condition explicitly requires `noPenalty.equalsIgnoreCase("Yes")` to proceed to the guidance log checks. If the input is anything other than "Yes" (such as "No"), the program skips all the inner nested evaluation logic.

2. **Explain the meaning of the following code snippet:**
   `if (guidanceCount1 >= 8 && guidanceCount2 >= 4) {`
   * **Answer:** This line uses the logical AND (`&&`) operator to check two conditions simultaneously. It ensures that the student has completed at least 8 guidance sessions with Supervisor 1 **AND** at least 4 guidance sessions with Supervisor 2. Both criteria must be completely true at the same time for the program to approve the thesis exam registration.

3. **Describe the full flow of checking the student's requirements from start to finish. Explain step by step for every condition!**
   * **Answer:**
     * **Step 1:** The program evaluates the user's input for `noPenalty`. If it is `"Yes"`, the system grants access to the second level of validation (the nested code block). If it is `"No"`, it goes straight to the final outer `else` and outputs a penalty failure message.
     * **Step 2:** Inside the nested block, it checks if `guidanceCount1 >= 8` and `guidanceCount2 >= 4` are both fulfilled. If true, registration is approved.
     * **Step 3:** If the first condition fails, it evaluates `else if (guidanceCount1 < 8 && guidanceCount2 < 4)`. If true, it means both supervisors' sessions are insufficient.
     * **Step 4:** If that also fails, it checks `else if (guidanceCount1 < 8)`. If true, only Supervisor 1's requirement is lacking.
     * **Step 5:** If none of the conditions above are met, the program falls back to the inner `else` block, which accurately signifies that only Supervisor 2's session requirements have not been reached.
    
       #### 2.2 Experiment 2: Logical Operators to Determine Campus WiFi Access

The campus WiFi can only be used by students or lecturers whose accounts are not blocked. The
program receives information on whether the user is a student, whether the user is a lecturer, and
whether the user's account is currently blocked. Access is granted if the user is a student or a lecturer,
and the account is not blocked. This experiment practices the logical operators && (AND), || (OR), and
! (NOT).

##### 2.2.1 Java Program Code
'''java
import java.util.Scanner;

    public class LogicalOperatorWifi264107020237 {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);

            boolean isStudent;
            boolean isLecturer;
            boolean isBlocked;

            System.out.print("Is the user a student? (true/false): ");
            isStudent = sc.nextBoolean();

            System.out.print("Is the user a lecturer? (true/false): ");
            isLecturer = sc.nextBoolean();

            System.out.print("Is the account currently blocked? (true/false): ");
            isBlocked = sc.nextBoolean();

            if ((isStudent || isLecturer) && !isBlocked) {
             System.out.println("WiFi access granted");
            } else {
            System.out.println("WiFi access denied");
            }
        }
#### 2.2.2 Hasil Running / Screenshot Output
Here is an example of what the output looks like after the program is run:
<img width="372" height="127" alt="you78" src="https://github.com/user-attachments/assets/be1ad723-5f41-4c0c-89ed-199c0cb5d5de" />

#### 2.2.3 Questions
### Questions

**1. Function of the `||`, `&&`, and `!` operators**
    * **Answer:** || (OR) is true if at least one operand is true. Here, isStudent || isLecturer is true if the user is a  student or a lecturer.
&& (AND) is true only if both operands are true. Here, the "student/lecturer" condition and the "account not blocked" condition must both be satisfied.
! (NOT) inverts a boolean value. !isBlocked is true when the account is not blocked (isBlocked = false).

**2. Why can a lecturer still get access when `isStudent = false`?**
Because the two conditions are joined with `||`, only one of them needs to be `true`. In test 2, `false || true` gives `true`. Since the account is not blocked, `!isBlocked` is also `true`, so `true && true` gives `true` and access is granted.

**3. Changing `||` to `&&`**
he condition becomes `(isStudent && isLecturer) && !isBlocked`.

- Test 1: `true && false` = `false`, so the result is **denied**.
- Test 2: `false && true` = `false`, so the result is **denied**.

Users who were previously allowed are now rejected. With `&&`, a user must be a student **and** a lecturer at the same time, which is normally not the case, so almost everyone is denied. This shows that `||` is the correct operator for an "either one" requirement.

**4. When does `isLecturer` not need to be evaluated? (short-circuit)**
When **`isStudent` is `true`**. With `||`, if the left operand is already `true`, the whole expression must be `true` regardless of the right operand, so Java skips evaluating `isLecturer`. Examples are tests 1 and 3.

**5. When does `!isBlocked` not need to be evaluated?**
When **`(isStudent || isLecturer)` is `false`**, meaning both `isStudent` and `isLecturer` are `false` (for example, test 4). With `&&`, if the left operand is already `false`, the whole expression must be `false` regardless of the right operand. Java stops there and skips `!isBlocked`, going straight to the `else` block (**denied**).

 #### 2.3 Experiment 3: Nested IF and Logical Operators to Determine Laboratory Access
 
 A student may use the laboratory outside class hours if their status is active and they are not currently
under sanction. If this requirement is met, the system performs a second check. Laboratory access is
granted if the student has lecturer permission or is a lab assistant. This case combines nested selection
with logical operators.

##### 2.3.1 Java Program Code
import java.util.Scanner;
        
        public class NestedLabAccess264107020237 {
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);
                boolean isActiveStudent;
                boolean isSanctioned;
                boolean hasLecturerPermit;
                boolean isLabAssistant;

                 System.out.print("Is active student (true/false): ");
                 isActiveStudent = sc.nextBoolean();

                 System.out.print("Is sanctioned (true/false): ");
                 isSanctioned = sc.nextBoolean();

                 System.out.print("Has lecturer permit (true/false): ");
                 hasLecturerPermit = sc.nextBoolean();

                System.out.print("Is lab assistant (true/false): ");
                 isLabAssistant = sc.nextBoolean();

                if (isActiveStudent && !isSanctioned) {
                    if (hasLecturerPermit || isLabAssistant) {
                        System.out.println("Laboratory access granted");
                    } else {
                         System.out.println("Access denied: lecturer permission or lab assistant status required");
                    }
                } else {
                    System.out.println("Access denied: student status does not meet the requirement");
                }

                sc.close();
             



            }
    
}

#### 2.3.2 Hasil Running / Screenshot Output
<img width="269" height="149" alt="5432" src="https://github.com/user-attachments/assets/3db9b523-0452-43ee-b750-9e14bf3d6e52" />

#### 2.3.3 Questions
### Questions
**1. Why is the check hasLecturerPermit || isLabAssistant placed inside the first IF?**
The second check is only relevant for users who already meet the basic student requirement (active and not sanctioned). Placing it inside the first if means it runs only after that requirement is satisfied. A user who fails the first check is rejected immediately, and the permission check is never evaluated. This also matches the rule in the problem: "If this requirement is met, the system performs a second check."

**2. Function of the &&, ||, and ! operators in this program**
- && (AND) is true only if both operands are true. In isActiveStudent && !isSanctioned, the user must be an active student and not sanctioned.
- || (OR) is true if at least one operand is true. In hasLecturerPermit || isLabAssistant, having either a lecturer permit or lab assistant status is enough.
- ! (NOT) inverts a boolean value. !isSanctioned is true when the student is not sanctioned (isSanctioned = false).

**3. Can the requirement be written as a single condition?**
Yes. The condition isActiveStudent && !isSanctioned && (hasLecturerPermit || isLabAssistant) is logically equivalent for the access decision. Access is granted only when all three parts are true: the student is active, the student is not sanctioned, and the user has a lecturer permit or is a lab assistant. This is exactly what the nested version checks, so the final decision (granted or denied) stays the same for every input combination.
The difference is that the single condition can only produce two outcomes: granted or denied. It cannot tell the user why access was denied.

**4. What is the advantage of using Nested IF in this case, compared to a single IF, if the system
needs to show different reasons for denial?**
Nested IF separates the checks into levels, and each level has its own else branch with its own message:
- If the first level fails, the system reports that the student status does not meet the requirement.
- If the first level passes but the second fails, the system reports that lecturer permission or lab assistant status is required.

**5.Create one input combination that causes access to be denied at the first level, and one that
causes it to be denied at the second level.**
<img width="301" height="131" alt="656" src="https://github.com/user-attachments/assets/76401e5f-698a-4820-877e-39b928a1b8c7" />

 #### 3. Assignment
 ##### 3.3.1 Java Program Code
import java.util.Scanner;

public class Task2AssistantSelectionAttendanceNo {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.println("=== LAB ASSISTANT CANDIDATE SELECTION ===");
        System.out.print("Student name                                   : ");
        String name = input.nextLine();
        System.out.print("Student status (active/inactive)               : ");
        String status = input.nextLine();
        System.out.print("Currently under academic sanction? (yes/no)    : ");
        String sanction = input.nextLine();

        boolean isActive = status.equalsIgnoreCase("active");
        boolean underSanction = sanction.equalsIgnoreCase("yes");

        System.out.println("\n--- SELECTION RESULT for " + name + " ---");

        // Stage 1: administrative requirement
        if (isActive && !underSanction) {

            System.out.print("Basic Programming grade (0-100)                : ");
            double grade = input.nextDouble();
            input.nextLine(); // clear buffer
            System.out.print("Has programming competency certificate? (yes/no): ");
            boolean hasCertificate = input.nextLine().equalsIgnoreCase("yes");

            // Stage 2: programming competency
            if (grade >= 80 || hasCertificate) {

                System.out.println("Stage 2 passed. The student is called for an interview.");
                System.out.print("Interview score (0-100)                        : ");
                double interviewScore = input.nextDouble();

                // Stage 3: interview
                if (interviewScore >= 75) {
                    System.out.println("RESULT: ACCEPTED as lab assistant. Congratulations!");
                } else {
                    System.out.println("RESULT: NOT ACCEPTED.");
                    System.out.println("Reason: Interview score (" + interviewScore + ") is below the minimum of 75.");
                }

            } else {
                System.out.println("RESULT: NOT ACCEPTED.");
                System.out.println("Reason: Basic Programming grade (" + grade
                        + ") is below 80 and the student has no programming competency certificate.");
            }

        } else {
            System.out.println("RESULT: NOT ELIGIBLE to take part in the selection.");
            if (!isActive && underSanction) {
                System.out.println("Reason: Student is not active and is currently under academic sanction.");
            } else if (!isActive) {
                System.out.println("Reason: Student status is not active.");
            } else {
                System.out.println("Reason: Student is currently under academic sanction.");
            }
        }

        input.close();
    }
}

#### 2.3.2 Hasil Running / Screenshot Output
<img width="542" height="127" alt="657" src="https://github.com/user-attachments/assets/6e05956e-732b-411d-90a1-806bd4d7d3cc" />

#### Conclusion
In this practical session, I learned that nested selection statements let a program check dependent requirements level by level. An inner condition is evaluated only after the outer one is satisfied, and each level has its own else, so the program can show the exact reason for a failure, as in the thesis exam, laboratory access, and lab assistant selection programs. I also learned that the logical operators &&, ||, and ! combine several conditions into one expression, and that choosing the right operator matters because it changes the result (for example, replacing || with && in the WiFi program denied almost every user). Java's short-circuit evaluation skips the right operand when the left one already decides the result. Used together, nested if statements and logical operators make a program's decisions correct, concise, and easy to explain.
