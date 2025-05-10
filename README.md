# Unolingo
A bad Duolingo tribute for class.

# Overview

It's a multiplayer application where clients can:

* **Register** and **Login** to their accounts.
* Play a Hiragana game where they type the Romaji for each character.
* **Upload** their scores to a centralized leaderboard
* **View** the leaderboard in **realtime**

# Architecture

```bash
├── Server.java               --> Main server application
├── Client.java               --> Main client GUI and communication
├── ClientHandler.java        --> Handles client requests in separate threads
├── DatabaseManager.java      --> Manages database operations with SQLite
├── HiraganaGame.java         --> The game logic and UI
└── LeaderboardFrame.java     --> Displays the leaderboard with real-time updates
```

# Classes

**Server**

* Initializes the server on the specified port (`5150`)
* Uses `ThreadPoolExecutor` to manage multiple clients
* Accepts new clients and hands them off to `ClientHandler`

**Client**

* The main GUI for the user
* Buttons to Login, Register, Play, View Leaderboard


**Client Handler**

* Handles communication between client and server

**DatabaseManager**

* Manages the SQLite database (`users.db`)

**HiraganaGame**

* Launches a new game where players are tested on Hiragana characters
* Asks 10 random questions
* Updates the user's total score after the game

**LeaderboardFrame**

* Displays the leaderboard in real-time.

# Database

To view the database go into the directory it's located in and:

```bash
sqlite3 users.db
SELECT * FROM users
```

# Running the Project

Navigate to where you saved the project:

```
cd your-project-directory-goes-here
```

Compile everything:

```
javac -cp ".:sqlite-jdbc-3.49.1.0.jar" *.java
```

*SIDE NOTE: make sure sqlite-jdbc-3.49.1.0.jar is inside the same folder*

Start the server:

```
java -cp ".:sqlite-jdbc-3.49.1.0.jar" Server
```

You'll see something like:

```
Server is listening on port 5150
```

Start the client in a new terminal:

```
java -cp ".:sqlite-jdbc-3.49.1.0.jar" Client
```

Enjoy!
