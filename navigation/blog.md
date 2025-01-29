---
layout: blogs
title: Blogs
search_exclude: true
permalink: /blogs/

Absolutely! Here's a cleaner, sharper, and more concise version of your blog with better formatting and clear divisions to make it easier to present confidently. This version is designed to impress your teacher, Mr. Mortensen, and show that you're prepared and professional:

---

# **CRUD 1/29 Checkpoint**

---

## **Purpose of the Program**
Our group’s program is a **Game History Manager** that allows users to log, update, delete, and retrieve historical game data. It tracks player performance and game outcomes, providing insights into gameplay trends.

- **Group Purpose**: Centralized platform for managing game logs and analyzing player performance.  
- **My Feature**: Backend API implementing CRUD (Create, Read, Update, Delete) operations for seamless communication between the frontend and database.

---

## **Input/Output Demonstration**

### **Frontend API Request and Response**
- **Input**: Users interact with the API via form submissions. Example:
   ```javascript
   fetch('/api/pastgame', {
     method: 'POST',
     headers: { 'Content-Type': 'application/json' },
     body: JSON.stringify({ winner: 'Player1', elo: 1500, uid: 'game123' })
   })
   .then(response => response.json())
   .then(data => console.log(data));
   ```
- **Output**:  
   ```json
   { "message": "Game History logged successfully", "pastGame_log_id": 1 }
   ```

---

### **Postman API Request and Response**
- **POST Request**:
   - **URL**: `/api/pastgame`
   - **Body**:
     ```json
     { "winner": "Player1", "elo": 1500, "uid": "game123" }
     ```
   - **Response**:  
     ```json
     { "message": "Game History logged successfully", "pastGame_log_id": 1 }
     ```
- **Error Example**:  
   ```json
   { "message": "Game winner and elo are required" }
   ```

---

### **Database Operations**
- **`db_init`**: Initializes the database schema.  
- **`db_restore`**: Restores pre-populated test data.  
- **`db_backup`**: Creates a backup of the current database state for recovery.

---

## **Use of Lists, Dictionaries, and Database**

### **Lists and Dictionaries in Backend**
- **List**: Retrieves rows from the database and formats them into a list of dictionaries:
   ```python
   games = pastGame.query.all()
   json_ready = [game.read() for game in games]
   return jsonify(json_ready)
   ```

- **Dictionary Example**:  
   ```json
   { "id": 1, "uid": "game123", "winner": "Player1", "elo": 1500 }
   ```

---

### **Formatting JSON Response for the DOM**
- **Frontend Example**:  
   ```javascript
   fetch('/api/pastgame')
     .then(response => response.json())
     .then(data => {
       data.forEach(game => {
         const row = `<tr><td>${game.id}</td><td>${game.winner}</td><td>${game.elo}</td></tr>`;
         document.querySelector('#gameTable').innerHTML += row;
       });
     });
   ```

---

### **Database Queries**
- **Extracting Python Lists**: Queries like `pastGame.query.all()` return a list of rows.  
- **3rd Party Library**: SQLAlchemy is used for database interactions.

---

## **Methods in Classes**

### **CRUD Methods in `pastGameAPI`**
- **Create**: The `post()` method creates a new game log.  
- **Read**: The `get()` method retrieves all game logs as JSON.  
- **Update**: The `put()` method updates an existing game log by ID.  
- **Delete**: The `delete()` method removes a game log by UID.

---

## **Algorithmic Code**

### **Code to Handle Requests**
- **`post()` Method**: Handles game log creation:
   ```python
   def post(self):
       data = request.get_json()
       if not data or 'winner' not in data or 'elo' not in data:
           return {"message": "Game winner and elo are required"}, 400
       new_pastGame_log = pastGame(winner=data['winner'], elo=data['elo'], uid=data['uid'])
       created_log = new_pastGame_log.create()
       if created_log:
           return {"message": "Game History logged successfully", "pastGame_log_id": created_log.id}, 201
       return {"message": "Failed to create game history"}, 500
   ```

---

### **Sequencing, Selection, and Iteration**
- **Example**: The `put()` method updates fields step-by-step:
   ```python
   if 'uid' in data:
       pastGame_log._uid = data['uid']
   if 'winner' in data:
       pastGame_log._winner = data['winner']
   if 'elo' in data:
       pastGame_log._elo = data['elo']
   ```

---

### **Parameters and Return Types**
- **Parameters**: Request body (`data`) includes `winner`, `elo`, and `uid`.  
- **Return Type**: JSON responses are returned using `jsonify`.

---

## **Calling the Algorithm**

### **Making API Requests**
- **Frontend Example**:  
   ```javascript
   fetch('/api/pastgame', {
     method: 'POST',
     headers: { 'Content-Type': 'application/json' },
     body: JSON.stringify({ winner: 'Player1', elo: 1500, uid: 'game123' })
   });
   ```

---

### **Handling API Responses**
- **Frontend Example**:  
   ```javascript
   fetch('/api/pastgame')
     .then(response => response.json())
     .then(data => console.log(data));
   ```

---

### **Normal vs Error Conditions**
- **Normal**: Valid inputs return success messages.  
   ```json
   { "message": "Game History logged successfully" }
   ```
- **Error**: Missing fields or invalid data return error responses.  
   ```json
   { "message": "Game winner and elo are required" }
   ```

---

## **Conclusion**
This blog demonstrates the collaborative and creative process of building a backend API for managing game history. From CRUD operations to handling API requests and responses, this program highlights how programming can solve real-world problems while enabling innovation and creativity.

---