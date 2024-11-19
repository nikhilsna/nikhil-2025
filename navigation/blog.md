---
layout: blogs
title: Blogs
search_exclude: true
permalink: /blogs/
---
Sprint 3 reflection:
**In Sprint 3**, I learned a ton while building the **mini assistant feature**, especially about using **JavaScript** to create interactive and dynamic elements. Making it **draggable** and cycling through responses was a fun challenge that taught me more about **DOM manipulation** and **event handling**. I also focused on improving the design with **cool hover effects** and **smooth transitions**, which made the assistant look more polished. Overall, it was a great mix of **coding and creativity**, and I’m proud of what I built!

Blogs For MCQ wrong questions:

**Score:** 45/66

1. **Q3**:  
   I chose answer **A**, thinking that citizen science could involve everyone working in one location, but the explanation shows that distributed data collection across many locations is key to citizen science, which makes **C** the correct answer.

2. **Q10**:  
   I selected **A**, but the explanation states that the code doesn’t adjust positions correctly to align the circles horizontally. **B** is correct because it properly updates `xPos` while keeping `yPos` constant.

3. **Q11**:  
   I picked **C**, assuming the code accurately simulated the spinner, but the explanation highlights that the probabilities were incorrectly distributed. **D** is correct, as it ensures the spinner matches the intended proportions.

4. **Q12**:  
   I overestimated the growth rate by choosing **C**, but the explanation clarified that **B** is correct because it uses a consistent rate of increase based on the table for a realistic projection for year 12.

5. **Q13**:  
   I selected **A**, believing the app release didn’t affect message activity, but the explanation shows that message frequency increased after the app was introduced. **D** is correct as it reflects the shorter messages trend.

6. **Q22**:  
   I chose **D**, misunderstanding the comparison between hot days and total days. The explanation clarifies that **B** is correct, as it correctly checks if hot days are more than half of the total days.

7. **Q25**:  
   I assumed **D** could not be shortened, but the explanation demonstrates that repeated patterns like "HE" and "RE" allow encoding. **A** is correct as it is a string that cannot be further compressed.

8. **Q26**:  
   I chose **B**, but the explanation pointed out that the robot doesn't move from its position due to an incorrect condition. **C** is correct as it ensures the robot moves toward the gray square.

9. **Q28**:  
   I underestimated the bits needed by choosing **B**, but the explanation states that **D** is correct because 8 bits (\(2^8 = 256\)) are required to represent 200 unique characters.

10. **Q30**:  
    I selected **B**, incorrectly calculating the total time. The explanation confirms that **D** is correct, as the loop iterates through all genres, making the total time 5 hours.
    Here are reflections for the newly uploaded questions based on their question numbers and explanations provided:

11. **Q31**:  
   I chose **A**, thinking that only Program I correctly moves the robot, but the explanation shows that Program II also moves the robot correctly by using a loop that handles the grid logic. The correct answer is **C**.

12. **Q32**:  
   I selected **B**, assuming participants who read more were less likely to be interested, but the explanation clarifies that participants who read more were actually more likely to be interested in the application. The correct answer is **A**.

13. **Q33**:  
   I chose **B**, but I misunderstood how the flowchart logic worked. The explanation shows that **A** is correct because it matches the OR condition, where either one of the conditions being true sets `include` to true.

14. **Q44**:  
   I selected **D**, mistakenly believing all the given operations would result in an overflow error. The explanation clarified that only the operation **7 + 10** causes an overflow. The correct answer is **B**.

15. **Q45**:  
   I chose **A**, incorrectly representing a NAND gate. The explanation explains that **C** is correct because it accurately models a NAND gate, which outputs true unless both inputs are true.

16. **Q46**:  
   I selected **C**, thinking it was possible to solve the problem in unreasonable time, but the explanation confirms that it’s impossible to solve undecidable problems for all inputs. The correct answer is **D**.

17. **Q48**:  
   I selected **B**, but the explanation shows that this caused the experiment to simulate success for 25% of the time instead of 75%. The correct answer is **C**, which correctly represents the intended 75% success rate.

18. **Q52**:  
   I chose **B**, assuming only one sequence of steps worked, but the explanation clarifies that both options **I and III** work correctly for the algorithm. The correct answer is **D**.

19. **Q56**:  
   I selected **C**, assuming the program summed odd integers from 1 to 9, but the explanation clarified the program sums integers up to 19. The correct answer is **D**.

20. **Q62**:  
    I chose **B**, mistakenly thinking content would remain the same each time in an online encyclopedia. The explanation clarified that online encyclopedias are editable and constantly changing. The correct answers are **C** and **D**.
    Here’s the reflection for **Q66**:

21. **Q66**:  
    I chose **A**, but the explanation clarified that the list `[10, 20, 30, 40]` doesn't cause the procedure to fail because there are no values less than the first number, so the smallest value is correctly returned. The correct answers are **C** and **D**, as these lists reveal the flaw in the logic when a smaller value appears later in the list.

Here’s a more in-depth reflection addressing the poor grade and how I plan to improve:

---

## **Where I Went Wrong**

### ⏱ **Timing Issues**  
I rushed through questions that required careful thought and didn’t double-check my work:  
- **Q10**: I didn’t properly track how `xPos` updates in the loop and picked **A**. The correct answer, **B**, adjusts `xPos` while keeping `yPos` constant. I need to slow down when working with positional updates in code.  
- **Q28**: I underestimated the number of bits needed to represent 200 characters, incorrectly choosing **B**. I ignored the formula \(2^n\), where \(n = 8\), meaning 8 bits (\(2^8 = 256\)) are required. The correct answer was **D**.  

To fix this: I’ll allocate more time per question and practice breaking down numerical and logical problems step by step.

---

### 🔄 **Control Flow Struggles**  
I struggled to follow how conditions and loops interact, leading to several incorrect answers:  
- **Q26**: I misunderstood how the robot’s movement logic worked. I picked **B**, but **C** was correct because it properly ensures the robot moves toward the gray square. I didn’t analyze the condition step by step.  
- **Q31**: I assumed only Program I worked, but I missed how Program II’s loop correctly handled grid movement logic. I picked **A**, but **C** was the right answer.  

To fix this: I’ll practice reading and simulating code execution line by line, especially for loops and conditions, to fully understand how they behave.

---

### 📊 **Data and Logic Misinterpretations**  
I made poor assumptions instead of analyzing the data and logic more carefully:  
- **Q3**: I thought citizen science involved one location, so I picked **A**. I missed that it’s about distributed data collection across multiple locations, making **C** correct.  
- **Q13**: I didn’t notice the increase in message frequency after the app launch, which pointed to **D**. I relied on assumptions rather than looking closely at the trend.  
- **Q62**: I incorrectly assumed online encyclopedias are static, choosing **B**. I forgot they’re editable and dynamic, making **C** and **D** correct.  

I also struggled with technical logic:  
- **Q45**: I misrepresented the NAND gate, picking **A** instead of **C**, which accurately models its behavior.  
- **Q66**: I ignored edge cases like lists with smaller values later (e.g., `[5, 10, 3, 8]`), which exposed the flaw in my understanding of the logic.

To fix this:  
1. I’ll **read questions slowly and carefully**, underlining key details like conditions, trends, and keywords.  
2. I’ll **practice edge case scenarios** in coding problems to build better habits for testing logic.

---

### ✏️ **Specific Issues by Question**  
Here’s a breakdown of my major mistakes:  
1. Made a silly error on **control flow**: **Q26, Q31**  
2. Overlooked **data patterns or trends**: **Q3, Q13**  
3. Miscalculated technical problems: **Q28, Q45, Q66**


## **How I Will Improve**

### 🕒 **1. Time Management**
- **Plan**: Spend at least 30-40 seconds reading each question before answering.  
- **Fix**: Practice time management, and analyze key terms first.  

### 🔄 **2. Control Flow Practice**
- **Plan**: Work through 3-5 coding problems daily, focusing on loops and conditions.  
- **Fix**: Write out the steps for each problem to simulate how code executes, especially edge cases.  

### 📊 **3. Analyzing Data and Logic**
- **Plan**: Solve data interpretation problems with graphs, tables, and patterns.  
- **Fix**: Highlight key words like “increase,” “distribution,” or “trend” to slow myself down and focus.  

### 🛠 **4. Technical Practice**
- **Plan**: Use coding platforms like LeetCode or Codecademy to practice topics like logic gates, bit manipulation, and pseudo-code analysis.  
- **Fix**: Review each mistake thoroughly, especially those involving technical logic.  

---

### **Goal**  
With these steps, I’ll improve my problem-solving skills and aim for at least a **60/66** on my next test by focusing on **timing**, **control flow**, and **data analysis**. This way, I can address my weaknesses and learn to approach these problems more systematically.  

