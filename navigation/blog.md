---
layout: blogs
title: Blogs
search_exclude: true
permalink: /blogs/
---
CRUD checkpoint 1/28

---

# 🧩 CRUD Integration Checkpoint (01/28/2025)  

## **📜 Executive Summary:**  
- Developed a feature to log, retrieve, and edit past chess games.  
- REST API supports **POST**, **GET**, and **PUT** methods for managing game data.  
- Frontend allows users to view and edit logged games directly.  

---

## **🎯 Team Purpose:**  
Our project is a chess platform where users can log, analyze, and track their progress. My feature enables users to not only view but also edit their game logs, ensuring data remains accurate and up-to-date.  

---

## **🛠️ Individual Features:**  
The purpose of my feature is to allow users to:  
1. **Log games** (POST).  
2. **View games** in a table (GET).  
3. **Edit games** (PUT).  

This ensures users can correct mistakes or update details like `elo`, `winner`, or `game result`.  

---

## **📥 Input/Output Requests:**  

### **Frontend Workflow:**  
1. **GET**: Fetches all logged games and populates a table.  
2. **PUT**: Triggered when the user edits a game and submits the changes.  

### **Postman Testing:**  
- **POST Request:**  
  ```json
  {
    "uid": "12345",
    "elo": 1500,
    "winner": "Player A",
    "result": "Win"
  }
  ```
  **Response:**  
  ```json
  {
    "message": "Game Log created successfully",
    "id": "12345"
  }
  ```

- **PUT Request:**  
  ```json
  {
    "uid": "12345",
    "elo": 1600,
    "winner": "Player B"
  }
  ```
  **Response:**  
  ```json
  {
    "message": "Game Log updated successfully"
  }
  ```

### **Database Tools:**  
- `db_init`: Initializes the schema.  
- `db_restore`: Resets test data.  
- `db_backup`: Saves the current state for recovery.  

---

## **📊 Requests & Data Flow:**  

### **Data Representation:**  
- **Backend:** Game entries are stored as rows in the database. Each row is represented as a dictionary:  
  ```python
  {
      "uid": "12345",
      "elo": 1500,
      "winner": "Player A",
      "result": "Win"
  }
  ```
- **Frontend:** API responses are in JSON format, which is looped through to dynamically populate the DOM (e.g., a table).  

### **Database Queries:**  
- **Retrieve All Games (GET):**  
  ```python
  games = Game.query.all()  # Returns a list of all game logs
  ```
- **Update a Game (PUT):**  
  ```python
  game = Game.query.filter_by(uid=uid).first()
  if game:
      game.elo = updated_elo
      game.winner = updated_winner
      db.session.commit()
  ```

---

## **🤖 Algorithmic Request:**  

### **API Class (Flask):**  
The API class handles the following methods:  
- **POST**: Logs a new game.  
- **GET**: Retrieves all games.  
- **PUT**: Updates an existing game.  

### **PUT Method (Code Example):**  
```python
@app.route('/api/game', methods=['PUT'])
def update_game():
    data = request.get_json()  # Parse JSON input
    uid = data.get('uid')  # Unique ID of the game to update
    updated_elo = data.get('elo')
    updated_winner = data.get('winner')

    # Locate the game in the database
    game = Game.query.filter_by(uid=uid).first()

    if not game:
        return jsonify({"message": "Game Log not found"}), 404

    # Update fields
    if updated_elo:
        game.elo = updated_elo
    if updated_winner:
        game.winner = updated_winner

    # Commit changes
    db.session.commit()

    return jsonify({"message": "Game Log updated successfully"}), 200
```

### **Sequencing, Selection, and Iteration:**  
1. **Sequencing:** The PUT method follows these steps:  
   - Parse input JSON → Locate the game → Update fields → Commit changes → Return response.  
2. **Selection:** Checks if the game exists (`if not game:`).  
3. **Iteration:** Loops through the input fields to selectively update them.  

---

## **🔗 Call to Algorithm:**  

### **Frontend (JavaScript):**  
When a user edits a game and clicks "Save," a PUT request is sent to the backend.  

```javascript
async function updateGame(uid, updatedData) {
    const response = await fetch('/api/game', {
        method: 'PUT',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            uid: uid,
            ...updatedData,
        }),
    });

    const result = await response.json();
    if (response.ok) {
        alert(result.message); // "Game Log updated successfully"
    } else {
        alert(result.message); // "Game Log not found"
    }
}
```

### **Backend Response:**  
- **Normal:**  
  ```json
  {
    "message": "Game Log updated successfully"
  }
  ```
- **Error:**  
  ```json
  {
    "message": "Game Log not found"
  }
  ```

---

## **Frontend Example Table:**  
The frontend dynamically displays data fetched from the backend. Users can edit game details directly in the table.  

```html
<table>
  <thead>
    <tr>
      <th>UID</th>
      <th>ELO</th>
      <th>Winner</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody id="gameTable"></tbody>
</table>

<script>
  async function fetchGames() {
    const response = await fetch('/api/game');
    const games = await response.json();

    const tableBody = document.getElementById('gameTable');
    tableBody.innerHTML = ''; // Clear table before populating

    games.forEach((game) => {
      const row = document.createElement('tr');
      row.innerHTML = `
        <td>${game.uid}</td>
        <td contenteditable="true">${game.elo}</td>
        <td contenteditable="true">${game.winner}</td>
        <td><button onclick="saveChanges('${game.uid}', this)">Save</button></td>
      `;
      tableBody.appendChild(row);
    });
  }

  async function saveChanges(uid, button) {
    const row = button.parentElement.parentElement;
    const updatedElo = row.children[1].innerText;
    const updatedWinner = row.children[2].innerText;

    await updateGame(uid, { elo: updatedElo, winner: updatedWinner });
    fetchGames(); // Refresh table
  }

  fetchGames(); // Populate table on page load
</script>
```

---

## **Normal vs. Error Scenarios:**  
- **Normal:**  
  - User edits a game → PUT request sent → Backend updates DB → Success message returned.  
- **Error:**  
  - User edits a non-existent game → PUT request sent → Backend returns `404` with error message.  

---
