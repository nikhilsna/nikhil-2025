---
layout: blogs
title: Blogs
search_exclude: true
permalink: /blogs/


# **Software Deployment Strategy Blog**

---

## **Team Structure and Roles**
Our deployment team is structured to ensure efficient and reliable deployment of our software application:

### **Deployment Administrators**
- **Primary Deployer**: **Nikhil Maturi**
  - Lead deployment coordination
  - Final approval on production deployments
  - Main point of contact for deployment issues
  - AWS EC2 instance management

- **Secondary Deployer**: **Mihir Thaha**
  - Backup for deployment procedures
  - Testing and validation
  - Documentation maintenance
  - Support for configuration management

---

## **Deployment Action Plan**

### **Phase 1: Pre-Deployment Setup**
1. **Local Environment Configuration**
   - Set up Docker environment
   - Configure VSCode with necessary extensions
   - Establish local testing procedures
   - Verify frontend-to-backend connectivity

2. **Port and Domain Planning**
   - Select unique port numbers for our application
   - Document all port configurations
   - Prepare subdomain requirements
   - Update configuration files (`main.py`, `Dockerfile`, `docker-compose.yml`)

---

### **Phase 2: Implementation Strategy**
1. **Docker Configuration**
   - Create and test `Dockerfile` locally
   - Set up `docker-compose.yml` with proper volumes
   - Test container builds on the local machine
   - Document any special requirements

2. **AWS Setup**
   - Configure EC2 instance access
   - Set up Route 53 DNS records
   - Configure Nginx reverse proxy
   - Implement SSL with Certbot

---

### **Phase 3: Deployment Workflow**
1. **Code Deployment Process**
   ```mermaid
   graph TD
       A[Local Development] --> B[Docker Testing]
       B --> C[Git Push]
       C --> D[AWS Pull]
       D --> E[Docker Rebuild]
       E --> F[Nginx Restart]


---
### **Full Stack Check**

---

### **Purpose of Pawnsy (Group Program)**

**Pawnsy** is a **Chess Game History Manager** that allows users to log, update, delete, and retrieve historical game data. The primary purpose of Pawnsy is to provide chess enthusiasts with a centralized platform to manage their game records, analyze player performance, and track trends in gameplay. By organizing game data, Pawnsy enables users to reflect on their strategies, improve their skills, and celebrate their wins.

The program solves the problem of disorganized or inaccessible game records by offering a user-friendly interface and backend system to store and manage this information. It fosters innovation by creating a tool that supports chess players in their learning and development journey.

---

### **Purpose of My Feature (CRUD API)**

My feature is the **backend CRUD API** (Create, Read, Update, Delete), which serves as the backbone of Pawnsy. **The purpose of this feature is to store matches by their winner, as well as their ELO (Chess rating).**

Specifically, my feature provides the following functionalities:

1. **Create**: Allows users to add new chess game logs, including details like the winner, ELO score, and unique identifier.

2. **Read**: Enables users to retrieve all stored game logs and display them in an organized format.

3. **Update**: Provides the ability to edit existing game records, such as updating the winner or ELO score.

4. **Delete**: Lets users remove specific game logs by their unique identifier (UID).

This feature ensures that data is stored, retrieved, and updated efficiently, forming the foundation for all user interactions with the game history. It empowers users to manage their data effectively while maintaining data integrity and providing robust error handling.

---

### **Introduction**

Programming is a collaborative and creative process that allows us to solve problems, express creativity, and innovate. In this project, I contributed to the **Create Performance Task** by designing and implementing a backend API that manages game history data. This feature enables users to interact with game logs dynamically and efficiently.

---

### **Input and Output Requests (User-Centric Demonstration)**

**Program Input:**

Program input is data that are sent to a computer for processing by a program. In our application, the user inputs data through a web form interface.

**User Actions:**

- The user navigates to the "Add Game Log" page.

- The user fills out the form fields:

  - **Winner**: Enters the name of the winning player (e.g., "Player1").

  - **ELO Score**: Enters the ELO rating of the game (e.g., 1500).

  - **Unique Identifier (UID)**: Enters a unique identifier for the game (e.g., "game123").

- The user clicks the "Submit" button to send the information.

**Program's Processing of Input:**

- The application captures the user's inputs and formats them into a JSON object.

- It sends this JSON object as part of an API request to the server.

**Program Output:**

Program output is data that are sent from a program to a device. After processing the input, the server responds with a JSON object.

**User's Reception of Output:**

- The application receives the server's response.

- If the operation is successful, the user sees a confirmation message:

  > "Game History logged successfully. Your game log ID is 1."

- If there's an error (e.g., missing fields), the user sees an error message:

  > "Game winner and ELO are required."

**Example of Program's Output in JSON:**

Success Response:

```json
{
  "message": "Game History logged successfully",
  "pastGame_log_id": 1
}
```

Error Response:

```json
{
  "message": "Game winner and elo are required"
}
```

**Explanation:**

- This demonstrates how the user's input leads to the program's processing, and how the output is presented back to the user.

---

### **Postman Input/Output Demonstration**

**Using Postman to Show Raw API Request and RESTful Response**

- **POST Request**:

  - **Endpoint**: `/api/pastgame`

  - **Headers**:

    ```
    Content-Type: application/json
    ```

  - **Body**:

    ```json
    {
      "winner": "Player1",
      "elo": 1500,
      "uid": "game123"
    }
    ```

  - **Response**:

    ```json
    {
      "message": "Game History logged successfully",
      "pastGame_log_id": 1
    }
    ```

**Explanation:**

- The user tests the API directly using Postman by sending a POST request with the necessary data.

- The server processes the request and returns a JSON response indicating success.

---

### **Database Operations**

- **`db_init`**: Initializes the database schema, creating all necessary tables and structures.

- **`db_restore`**: Restores test data for debugging, allowing developers to work with consistent data sets.

- **`db_backup`**: Backs up the current database state, ensuring data integrity and providing a recovery point.

---

### **Use of Collection Types: Lists and Dictionaries**

In the program, collection types are utilized to aggregate data:

- **List**:

  The variable `games` is a list that holds multiple `pastGame` objects retrieved from the database.

  ```python
  games = pastGame.query.all()  # Retrieves all game records as a list
  ```

  A list comprehension is used to create a new list `json_ready` containing the serialized data:

  ```python
  json_ready = [game.read() for game in games]
  ```

- **Dictionary**:

  Each `game.read()` method returns a dictionary that represents a game log with key-value pairs (e.g., columns in the database), which can be easily converted to JSON.

  Example dictionary:

  ```json
  {
    "id": 1,
    "uid": "game123",
    "winner": "Player1",
    "elo": 1500
  }
  ```

---

### **Formatting JSON Response for the DOM**

The API response is parsed and displayed dynamically in the DOM:

```javascript
fetch('/api/pastgame')
  .then(response => response.json())
  .then(data => {
    data.forEach(game => {
      const row = `<tr><td>${game.id}</td><td>${game.uid}</td><td>${game.winner}</td><td>${game.elo}</td></tr>`;
      document.querySelector('#pastGamesTable tbody').innerHTML += row;
    });
  });
```

**Explanation:**

- The program output (JSON data) is used to update the Document Object Model (DOM), displaying the game logs to the user in a table format.

---

### **Database Queries**

Using SQLAlchemy, queries like `pastGame.query.all()` retrieve rows from the database. These queries simplify database interaction and return Python lists of objects.

---

### **Methods in Class**

The `pastGame` class contains methods for CRUD operations:

- **`create`**: Adds a new record to the database.

- **`read`**: Returns the object's data as a dictionary.

- **`update`**: Updates an existing record in the database.

- **`delete`**: Deletes a record from the database.

---

### **Algorithmic Code Implementation**

The following is an excerpt of the `post` method, which is a **student-developed procedure** designed to handle the creation of a new game entry. This procedure demonstrates the use of **sequencing**, **selection**, and calls to other methods.

```python
def post(self):
    """Create a new game entry."""
    data = request.get_json()
    # **Sequencing**: The steps are executed in order.
    # **Selection**: Conditional checks are performed to validate input.
    if not data or 'winner' not in data or 'elo' not in data:
        return {"message": "Game winner and elo are required"}, 400
    # Create a new game log
    new_pastGame_log = pastGame(
        winner=data['winner'],
        elo=data['elo'],
        uid=data['uid']
    )
    created_log = new_pastGame_log.create()  # **Call to a student-developed procedure**
    if created_log:
        return {"message": "Game History logged successfully", "pastGame_log_id": created_log.id}, 201
    return {"message": "Failed to create game history"}, 500
```

**Explanation:**

- **Sequencing**: The procedure follows a logical sequence of steps: retrieving data, validating input, creating a new game log, and returning a response.

- **Selection**: Conditional statements (`if` statements) are used to check whether required data is present and to handle different outcomes (success or failure).

- **Procedure Call**: The code calls the `create` method (`new_pastGame_log.create()`), which is a **student-developed procedure** that adds the new game log to the database.

---

### **Sequencing, Selection, and Iteration**

The `put` method demonstrates **sequencing**, **selection**, and **iteration**:

```python
def put(self):
    """Update an existing game log."""
    try:
        data = request.get_json()
        if not data:
            return {"message": "No data provided in the request body"}, 400
        if 'id' not in data:
            return {"message": "ID is required in the request body"}, 400

        # Fetch the game log by ID
        pastGame_log = pastGame.query.get(data['id'])
        if not pastGame_log:
            return {"message": "Game Log not found"}, 404

        # **Sequencing**: Updating fields in order
        # **Selection**: Checking for the presence of each field
        if 'uid' in data:
            pastGame_log._uid = data['uid']
        if 'winner' in data:
            pastGame_log._winner = data['winner']
        if 'elo' in data:
            pastGame_log._elo = data['elo']

        # Commit changes to the database
        pastGame_log.update(data)
        return pastGame_log.read(), 200

    except Exception as e:
        return {"message": f"Unexpected error: {str(e)}"}, 500


    def get(self):
      """Retrieve all game logs."""
      # **Sequencing**: Steps are performed in order.
      games = pastGame.query.all()  # Step 1: Retrieve all game records from the database.
      json_ready = []               # Step 2: Initialize an empty list to hold the serialized game data.

      # **Selection**: Check if there are any games to process.
      if not games:
          return jsonify({"message": "No game logs found"}), 404  # Conditional execution based on a condition.

      # **Iteration**: Iterate over each game in the list of games.
      for game in games:
          game_data = game.read()       # **Call to student-developed method**: Serialize the game object.
          json_ready.append(game_data)  # Add the serialized data to the list.

      return jsonify(json_ready)  # Step 4: Return the JSON response to the client.

```

**Explanation:**

- **Sequencing**: Steps are performed in a specific order to ensure proper execution.

- **Selection**: Conditional statements check if there are any chess games on hand to be processed.

- **Iteration**: Iterating over each game in the list of chess games.

---

### **Parameters and Return Values of Procedures**

**Parameters:**

The `post` method accepts **input parameters** in the form of JSON data from the request body. These parameters include:

- `winner` (string): The name of the player who won the game.

- `elo` (integer): The ELO rating associated with the game.

- `uid` (string): A unique identifier for the game.

**Return Values:**

The method returns a JSON response, which includes:

- **Success Message**: A confirmation that the game history was logged successfully.

- **Error Message**: Information about why the request failed, such as missing parameters.

---

### **Call to the Student-Developed Procedure**

**Procedure Call within the Program Code Segment:**

In the `post` method, the student-developed procedure `create` is called to add a new game log to the database.

```python
created_log = new_pastGame_log.create()  # Call to the procedure 'create'
```

**Explanation:**

- **Parameters**: The procedure uses the attributes of `new_pastGame_log`, which have been set with the user-provided data (`winner`, `elo`, `uid`).

- **Return Value**: The `create` method returns the newly created object if successful.

**Handling Different Conditions:**

- **Normal Condition**:

  If the `create` method succeeds, `created_log` is not `None`, and the program returns a success message to the user:

  ```python
  if created_log:
      return {"message": "Game History logged successfully", "pastGame_log_id": created_log.id}, 201
  ```

- **Error Condition**:

  If the `create` method fails, `created_log` is `None`, and the program returns an error message:

  ```python
  return {"message": "Failed to create game history"}, 500
  ```

By changing the input data or encountering errors during execution, different branches of the selection statements are executed, demonstrating how the procedure handles various conditions.

---

### **Normal vs. Error Conditions**

**Normal Condition:**

- When all required data is provided and the database operation is successful, the user receives a confirmation message:

  ```json
  {
    "message": "Game History logged successfully",
    "pastGame_log_id": 1
  }
  ```

- The program follows the standard execution path without any exceptions.

**Error Condition:**

- If required data is missing or an error occurs during processing, the user receives an error message:

  ```json
  {
    "message": "Game winner and elo are required"
  }
  ```

- The program handles exceptions and provides feedback to the user, preventing crashes and maintaining a smooth user experience.

---



