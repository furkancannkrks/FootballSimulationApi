# Football Analytics & Match Simulation Dashboard

This project is a modern football data analytics and match simulation application. Initially prototyped with Python, it was migrated to **ASP.NET Core 10** architecture to meet high scalability and performance requirements.

## 🚀 Key Features

* **Advanced Scouting System:** Ability to filter thousands of players in the database using more than 30 parameters such as position, age (optional), shooting, passing, and defensive metrics.
* **Server-Side Rating (Weighted Rating):** A performance-oriented architecture that offloads the player performance calculation from the application layer to the database, utilizing PostgreSQL `PERCENT_RANK()` window functions.
* **Interactive Match Simulation:**
    * **Drag & Drop** supported football pitch interface for squad selection.
    * Dynamic formation selection (4-3-3, 4-4-2, etc.).
    * Probabilistic simulation algorithm based on **xG (Expected Goals)**, key passes, and defensive actions.
* **Responsive Design:** A modern user interface with a dark mode theme and mobile compatibility.

## 🛠️ Technology Stack

### Backend
* **Framework:** ASP.NET Core 10 (Web API)
* **ORM:** Entity Framework Core (Database-First approach)
* **Database:** PostgreSQL
* **Architecture:** N-Tier Architecture (Repository, Service, Controller, DTO)
* **Asynchronous Programming:** All I/O operations are designed to be thread-safe using the `async/await` pattern.

### Frontend
* **Language:** Pure JavaScript (Vanilla JS), HTML5, CSS3
* **UI Logic:** DOM Manipulation, Fetch API, HTML5 Drag and Drop API
* **Design:** Dynamic pitch layout using CSS Grid and Absolute Positioning.

## 📊 Algorithm Details

### Player Rating System
Ratings are calculated by weighting and normalizing the player's overall season statistics:
`raw_score = (xg * 2.5) + (key_passes * 0.8) + (defensive_actions * 0.15)`
This value is processed at the database level using PostgreSQL `PERCENT_RANK()` and scaled between 1.0 and 10.0.

### Simulation Engine
By proportioning the total offensive and defensive strengths of the selected starting 11s, the engine calculates:
* Win / Draw / Loss probabilities,
* Over / Under 2.5 goal thresholds,
* **BTTS** (Both Teams to Score) status.

## ⚙️ Installation and Setup

1.  **Database Preparation:**
    * Ensure that the required tables (`player_season_stats`, `team_match_stats`) are ready in your PostgreSQL server.
2.  **Configuration:**
    * Update the `ConnectionStrings` section in the `appsettings.json` file with your PostgreSQL credentials.
3.  **Execution:**
    ```bash
    dotnet restore
    dotnet run
    ```
4.  **Access:**
    * Navigate to `http://localhost:5000` (or the designated port) in your browser.
