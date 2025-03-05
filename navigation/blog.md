---
layout: blogs
title: Blogs
search_exclude: true
permalink: /blogs/
---
# Final Exam Retrospective: Personal Reflection and Looking Forward

## Introduction

Final Exam retrospective:

As the trimester comes to a close, it's the perfect time to reflect on my journey, assess my accomplishments, and set goals for the future. This retrospective serves as a comprehensive review of my work, highlighting my strengths, areas for improvement, and key lessons learned. It's not just about the technical skills but also about personal growth, collaboration, and planning my next steps in the world of computer science.

This retrospective covers:

- My top five accomplishments over the past 12 weeks.
- An overview of the **Past Game** feature, emphasizing user and login-centric design.
- How the **Past Game** feature meets the College Board CPT requirements, using appropriate terminology.
- A review of the Night at the Museum (N@TM) event, including projects I admired and feedback received.
- Assistance provided to classmates, enhancing collaborative learning.
- Challenges faced and areas for improvement.
- Looking forward to my next steps in computer science, particularly in tech sales.
- Multiple Choice Questions (MCQ) review with a statistical analysis of my improvement.
- Final self-assessment and summary.

---

Over the past 12 weeks, I focused on five major accomplishments:

### 1. Engineered Automated Game Tracking

- **Description**: Developed an automated system that instantly records each win or loss to a SQLite database immediately after match completion.
- **Alignment with Big Idea 2 (Data Abstraction)**: This automation leverages data abstraction to efficiently manage and store game data without manual intervention.

### 2. Implemented Real-Time PUT Requests

- **Description**: Created real-time PUT requests that update player records with zero manual data entry needed.
- **Benefit**: Enhanced data integrity and user experience by ensuring that updates are immediate and accurate.

### 3. Created Direct Database Integration

- **Description**: Established a seamless integration with the database to maintain individual chess match history for each authenticated user.
- **Security**: Ensured that sensitive user data is securely stored and accessible only to authenticated individuals.

### 4. Built User Authentication System

- **Description**: Developed a robust authentication system enabling 100% of players to securely log in and track their chess matches.
- **Impact**: Increased user trust and engagement by providing a secure platform for managing personal game history.

### 5. Leveraged Chrome DevTools for Debugging

- **Description**: Successfully used Chrome DevTools Console to identify and resolve JavaScript runtime errors, debugging the frontend in real-time.
- **Outcome**: Improved application performance and provided a smoother user experience by promptly addressing issues.

---

## Past Game Feature Overview

<img src="{{site.baseurl}}/images/pastGametable.png" alt="pastGame Table Structure">

### User and Login-Centric Design

The **Past Game** feature is designed with a strong emphasis on user experience and security. It's tailored to provide users with an intuitive interface to manage their chess game history.

- **User Authentication**: Ensures that only authenticated users can access and manipulate their game data.
- **Personalized Experience**: Users can view, add, update, and delete their past game records, giving them full control over their data.
- **Secure Data Handling**: Implements secure communication protocols to protect user information.

### The `pastGame` Table Structure

The `pastGame` table is central to this feature, storing all game-related data.

| Field   | Type    | Description                             |
|---------|---------|-----------------------------------------|
| id      | Integer | Primary key, auto-incremented           |
| uid     | String  | Unique identifier for each game         |
| winner  | String  | Name of the winning player              |
| elo     | Integer | ELO rating associated with the game     |
| user_id | Integer | Foreign key linking to the `User` table |

---

## How the Past Game Feature Meets CPT Requirements


### Input and Output from User's Perspective

- **Input**:
  - Users input game details such as winner, ELO rating, and unique game ID.
  - Inputs are provided via a secure, authenticated web interface.
- **Output**:
  - Users receive confirmation messages upon successful operations.
  - The system displays updated game history reflecting recent changes.

### CPT Language and FRQ Terminology

In developing the **Past Game** feature, I incorporated key programming concepts required by the College Board's Create Performance Task (CPT). Below are code snippets from my feature that demonstrate these concepts.

#### **Procedures**: Developed functions that include sequencing, selection, and iteration.

**Sequencing**: The order in which statements are executed in a program.

**Selection**: Making decisions based on conditions (e.g., `if` statements).

**Iteration**: Repeating a sequence of statements (e.g., loops).

**Code Snippet Demonstrating Sequencing, Selection, and Iteration:**

```python
# Function to update a past game record (models.py)

def update(self, winner="", elo=0):
    # Sequencing: steps executed in logical order
    if len(winner) > 0:
        # Selection: condition to check if winner is provided
        self.winner = winner
    if elo > 0:
        # Selection: condition to check if ELO is provided
        self.elo = elo
    try:
        # Attempt to commit changes to the database
        db.session.commit()
        return self
    except Exception as e:
        # Handle exceptions and rollback
        db.session.rollback()
        return None
```

- **Sequencing**: The code executes statements in a specific order to perform the update.
- **Selection**: The `if` statements decide whether to update certain fields based on provided input.
- **Iteration**: While not explicitly shown here, iteration is used when processing multiple records.

#### **Parameters and Return Values**: Functions are designed with clear inputs and outputs to enhance modularity and reuse.

**Code Snippet Demonstrating Parameters and Return Values:**

```python
# Function to create a new past game record (models.py)

def create(self):
    try:
        # Add the new game to the session
        db.session.add(self)
        # Commit the session to save the game
        db.session.commit()
        return self  # Return the created game object
    except IntegrityError:
        # Handle integrity errors (e.g., unique constraints)
        db.session.rollback()
        return None
```

- **Parameters**: The method operates on `self`, which contains attributes like `winner`, `elo`, and `uid`.
- **Return Values**: Returns the `self` object upon successful creation, or `None` if an error occurs. 

#### **Calling Procedures**: Demonstrating how procedures are invoked within the program.

**Code Snippet Showing Procedure Calls:**

```python
# API endpoint to create a new past game (routes.py)

@app.route('/pastgame/create', methods=['POST'])
def create_past_game():
    data = request.get_json()
    # Create a new instance of pastGame
    new_game = pastGame(
        uid=data['uid'],
        winner=data['winner'],
        elo=data['elo'],
        user_id=current_user.id
    )
    # Call the create method
    created_game = new_game.create()
    if created_game:
        return jsonify(created_game.read()), 201
    else:
        return jsonify({"error": "Game could not be created"}), 400
```

- **Procedure Call**: `new_game.create()` invokes the `create` method to save the game.
- **Parameters**: Data from the user is passed to initialize the `pastGame` object.
- **Return Value**: The result of `create()` is used to determine the response.

---

## N@TM Review

### Projects I Liked

During the Night at the Museum (N@TM) event, several projects stood out:

- **TakeaByte**: A customizable cuisine generator, serving as a platform to create and share dishes. However, the lack of user-centric and offline features made all functionalities feel repetitive.
- **Binary**: A collaborative platform where computer science students can learn binary encoding and test their knowledge. However, it lacked originality.

### Feedback and Future Improvements

We received valuable feedback on our project **Pawnsy**, which highlighted both our strengths and areas for enhancement. Here's a summary of the feedback and our planned improvements:

#### **Strengths**

- **Engaging and Fun**: Attendees found the chess features enjoyable and interactive.

  > "It was really fun."

- **Clean Interface with Valuable Features**: The user interface was praised for its cleanliness, and the features were considered impressive.

  > "Very clean looking with nice features."

- **Integration of Stockfish Chess Engine**: The incorporation of the Stockfish engine enhanced the user experience by providing realistic gameplay.

  > "I liked how you guys incorporated the Stockfish chess engine into your website, and the user experience was really simple and easy to use!"

- **Educational Value**: The platform was recognized for helping users improve their chess skills through analysis and feedback.

  > "The chess analyzer looked really cool. As a chess player, being able to analyze your moves, skill rating, ranking, and power bot all helps me to improve my chess skill."

#### **Areas for Improvement**

- **User Interface Enhancements**: Suggestions were made to improve the visual aesthetics and make the UI more engaging.

  > "I would have liked more color in the website but liked the functionality and explanation of how the website works."

- **Feature Expansion**: Attendees recommended adding features such as editing chess moves and providing ratings on user performance.

  > "Add an edit feature for chess moves. Very cool idea to download a file and analyze moves based off of a png file!"

- **Consistency and Theming**: Feedback indicated a desire for a more consistent theme throughout the application to enhance user experience.

  > "One thing I would improve is making the website have a more consistent theme."

- **Scalability and Performance**: As the user base grows, it's critical to ensure the application remains responsive and efficient.

#### **Planned Technical Enhancements**

- **User Interface Redesign**:

  - Implement a more vibrant color scheme to make the UI visually appealing.
  - Enhance the ELO selection interface with interactive elements like sliders or dropdowns.
  - Ensure consistency in fonts, colors, and layouts across all pages.

- **Feature Development**:

  - **Edit Chess Moves**: Allow users to modify and annotate their moves post-game for deeper analysis.
  - **Performance Ratings**: Introduce algorithms to evaluate player moves and provide feedback on strategy and tactics.
  - **Statistical Analysis**: Offer users insights into their gameplay trends over time, including win rates and common move patterns.

- **Scalability Improvements**:

  - Optimize database queries and indexing to handle larger datasets efficiently.
  - Implement caching mechanisms to reduce server load and improve response times.
  - Use load balancing and scalable infrastructure to accommodate increasing traffic.

- **Security Enhancements**:

  - Implement token-based authentication to enhance user data protection.
  - Regularly update dependencies and use security best practices to prevent vulnerabilities.

- **Performance Optimization**:

  - Minimize JavaScript and CSS files to reduce load times.
  - Optimize images and assets for faster rendering.
  - Refactor code to improve efficiency and maintainability.

By focusing on these areas, we aim to improve the scalability, performance, and overall user experience of **Pawnsy**, making it a more robust and valuable tool for chess enthusiasts.

### Visual Highlights

<img src="{{site.baseurl}}/images/natm2.JPG" alt="Presenting at N@TM">

*Caption: Showcasing the Past Game feature at N@TM.*

---

## Assisting Classmates

### Helping Shaurya Singh

- **Contribution**: Assisted Shaurya in organizing his final exam material by creating a blog of key vocabulary points.
- **Impact**: Helped him focus on critical concepts, saving time and enhancing his preparation.

---

## Challenges and Areas for Improvement

No learning journey is without its challenges. Recognizing these obstacles is the first step toward personal and professional growth. Here are the areas I aim to improve:

### Time Management in Large-Scale Projects

- **Underestimation of Time for Debugging and Testing**: Throughout the development process, I occasionally underestimated the time required for thorough debugging and comprehensive testing. This oversight sometimes led to last-minute fixes and added pressure close to deadlines.
- **Future Strategies**:
  - **Structured Sprints**: Implementing structured sprints will allow me to allocate specific time frames for different development stages, including ample time for testing and debugging.
  - **Burndown Charts**: Maintaining a burndown chart will help track progress against time, ensuring that I stay on schedule and identify potential bottlenecks early in the process.

### Developing a Developer's Mindset

- **Challenges with Tools and Workflows**: Adapting to the mindset of a developer involves more than just coding; it requires mastering the tools and workflows that facilitate collaboration and efficient development.
- **Struggles with GitHub**:
  - **Cloning and Sharing**: Initially found it challenging to manage repositories, clone projects, and share code effectively using GitHub.
  - **Version Control**: Faced difficulties in understanding branch management and the nuances of commit histories.
- **Navigating VSCode Operations**:
  - **Merge Conflicts**: Encountered obstacles when working with the merge editor, often leading to merge conflicts that were time-consuming to resolve.
  - **Optimizing Workflow**: Needed to learn how to utilize extensions and features in VSCode to enhance productivity.
- **Implementing CPT Requirements**:
  - **Interpreting Guidelines**: Struggled to interpret and implement the College Board's CPT requirements accurately within my project.
  - **Documentation and Standards**: Found it challenging to adhere to coding standards and properly document code according to CPT expectations.
- **Future Strategies**:
  - **Continuous Learning**: Commit to ongoing education through tutorials, workshops, and collaboration with more experienced developers to enhance my proficiency with development tools.
  - **Practice and Application**: Regularly apply GitHub and VSCode in small projects to build confidence and familiarity.
  - **Seeking Feedback**: Engage with peers and mentors to receive constructive feedback on implementing CPT requirements and improving coding practices.

---

## Looking Forward: Next Steps in Computer Science

### Pursuing a Career in Tech Sales

My goal is to merge my technical expertise with strong communication skills to excel in tech sales.

- **Communication Skills**:
  - **Improvement**: Presenting my feature to Mr. Mortensen honed my ability to convey complex information succinctly.
  - **Application**: These skills are crucial in tech sales for explaining product value to clients.
- **Bridging the Gap**: By understanding both the technical aspects and the client’s needs, I can effectively translate technical features into customer benefits.

### Future Plans

- **Skill Development**:
  - **Technical**: Continue learning about software solutions to stay current.
  - **Sales**: Develop negotiation and relationship-building skills.
- **Networking**:
  - Attend industry events and webinars to connect with professionals in tech sales.
- **Educational Opportunities**:
  - Consider pursuing certifications or courses in sales and marketing to complement my technical background.

---

## MCQ Review

<img src="{{site.baseurl}}/images/practicetest.png" alt="Practice Test Results">

### **AP CSP College Board MCQ Analysis**  

#### **Score Improvement**  
- **First Attempt:** 44/66 (~67%)  
- **Second Attempt:** 55/67 (~82%)  
- **Improvement:** +11 points (+15%)  

---

### **Performance by Topic**

| **Topic**                                   | **Performance** | **Strengths**                          | **Improvements Needed**            |
|---------------------------------------------|-----------------|----------------------------------------|------------------------------------|
| **Collaboration**                           | 100%            | Strong teamwork and collaboration skills. | None.                              |
| **Program Function & Purpose**              | 100%            | Clear understanding of program goals.   | None.                              |
| **Debugging & Error Correction**            | 71%             | Some debugging ability.                 | Improve error identification.       |
| **Binary Numbers**                          | 100%            | Confident with binary operations.       | None.                              |
| **Data Compression**                        | 100%            | Strong understanding of compression.    | None.                              |
| **Extracting Information from Data**        | 71%             | Can handle basic data tasks.            | Practice advanced data analysis.    |
| **Conditionals**                            | 100%            | Mastery of logical statements.          | None.                              |
| **Computing Impacts (Bias, Ethics)**        | 100%            | Strong grasp of societal impacts.       | None.                              |

---

### **Key Insights**  
- **Strengths:** Binary Numbers, Conditionals, Societal Impacts  
- **Weaknesses:** Debugging, Advanced Data Analysis  

---

### **Next Steps**  
1. **Focus on Weak Areas:**  
   - Practice debugging and error correction.  
   - Work on interpreting complex data.  

2. **Take More Timed Tests:**  
   - Build speed and confidence under exam-like conditions.  

---

**Summary:** Improved from **67% to 82%**. Strengths are solid, but I need to refine debugging and data analysis skills for further growth.

---

## Final Self-Assessment and Summary

To summarize my retrospective:

| **Category**                             | **Self-Assessment** | **Reasoning**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Five Things Done Over 12 Weeks**       | **5/5**             | **Successfully completed five detailed accomplishments over the 12 weeks, each with its own burndown list and completion status.** <br><br>**1. Engineered Automated Game Tracking**: Demonstrated all CRUD operations for the `pastGame` table, ensuring that each win/loss is instantly recorded in the SQLite database after match completion. Reloaded pages to prove data persistence and showed entries in the database for reference. <br><br>**2. Implemented Real-Time PUT Requests**: Showed the updating of player records with zero manual data entry needed. Demonstrated how the system enhances data integrity and user experience by providing immediate and accurate updates to player records. <br><br>**3. Created Direct Database Integration**: Established seamless database integration that maintains individual chess match history for each authenticated user. Demonstrated backend connectivity and CRUD operations to prove data is securely stored and correctly associated with each user. <br><br>**4. Built User Authentication System**: Developed robust user authentication enabling 100% of players to securely log in and track their chess matches. Showed the login process, security measures in place, and how authenticated users can access their personalized past game records. <br><br>**5. Leveraged Chrome DevTools for Debugging**: Successfully used Chrome DevTools Console to identify and resolve JavaScript runtime errors. Provided examples of debugging sessions and illustrated how frontend issues were resolved in real-time, improving application performance and user experience. |
| **Full Stack Project Demo**              | **1.2/2**           | **Project demonstrates fully functioning full-stack abilities that meet CPT requirements with positive feedback from N@TM.** <br><br>- **Strengths**: The project integrates frontend and backend components seamlessly. It utilizes secure user authentication and provides full CRUD functionality for game records. Demonstrated a working application that stores user data persistently and allows for real-time updates. <br><br>- **Areas for Improvement**: Could further refine the project's purpose and scope to make it more defined. Incorporating additional features such as statistical analysis or enhanced UI elements, as suggested during N@TM feedback, would provide greater value to users. |
| **Project Feature Blog Writeup**         | **1/1**             | **Created a detailed and thoughtful personal blog that describes how the Past Game feature meets CPT requirements and the College Board Big Ideas, using FRQ language and appropriate terminology.** <br><br>- **Content**: Explained the connection to Big Ideas 1-5, detailed how the feature addresses program requirements, and used CPT language to highlight the use of sequencing, selection, and iteration in code. Provided code examples and explanations for clarity.                                                                                                                                     |
| **MCQ Review and Improvement**           | **1/1**             | **MCQ assessments were completed to the best ability, with personal areas for improvement identified and addressed.** <br><br>- **Actions Taken**: Conducted a thorough analysis of MCQ performance, identifying strengths in areas like Binary Numbers and Conditionals, and weaknesses in Debugging and Advanced Data Analysis. Developed a plan to focus on weak areas through practice and additional timed tests, demonstrating commitment to continuous learning and mastery of subject matter.                                                                                                                                         |
| **Retrospective and Looking Forward**    | **1/1**             | **Developed a clear roadmap for improvement and career growth, articulated in a well-thought-out retrospective blog.** <br><br>- **Reflection**: Highlighted personal achievements over the trimester, including technical skills and personal growth in communication and collaboration. <br><br>- **Career Goals**: Discussed aspirations to pursue a career in tech sales, leveraging technical expertise and improved communication skills. Outlined plans for skill development and networking opportunities to achieve this goal.                                                                                                                           |

**Total Score**: **9.2/10**

---

## Conclusion

This trimester has been incredibly rewarding. I've not only enhanced my technical skills but also grown personally, particularly in communication and collaboration. By focusing on user-centric design and aligning my work with CPT requirements, I've ensured that my project is both functional and meaningful.

Acknowledging the challenges faced, especially in time management and adapting to a developer's mindset, has been instrumental in charting a path forward. Implementing strategies like structured sprints, burndown charts, and continuous learning will address these areas and contribute to future success.

Looking ahead, I'm excited to apply what I've learned to a career in tech sales, bridging the gap between complex technological solutions and the needs of clients. The journey has been both challenging and rewarding, providing invaluable lessons in technical development, problem-solving, and effective communication. I am confident that the skills and experiences gained will serve as a strong foundation as I move forward in my academic and professional endeavors.

---