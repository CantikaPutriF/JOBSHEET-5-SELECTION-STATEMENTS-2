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
#### 2.1.2 Hasil Running / Screenshot Output
Here is an example of what the output looks like after the program is run:
<img width="338" height="122" alt="hjutr" src="https://github.com/user-attachments/assets/0b4d1613-e73b-4b3e-ae72-cc8f3b902a84" />

#### 2.1.3 Questions
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

##### 2.1.2 Java Program Code
'''java
