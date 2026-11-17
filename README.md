
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CricketLive - Match Management</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
  <h1>🏏 CricketLive</h1>
  <p>Cricket Match Management System</p>
</header>

<nav>
  <a href="#dashboard">Dashboard</a>
  <a href="#matches">Matches</a>
  <a href="#add">Add Match</a>
</nav>

<main>
  <section id="dashboard">
    <h2>Match Dashboard</h2>
    <div class="stats">
      <div class="stat">
        <h3 id="total">0</h3>
        <p>Total Matches</p>
      </div>
      <div class="stat">
        <h3 id="live">0</h3>
        <p>Live Matches</p>
      </div>
      <div class="stat">
        <h3 id="upcoming">0</h3>
        <p>Upcoming</p>
      </div>
    </div>
  </section>

  <section id="matches">
    <h2>🏆 All Cricket Matches</h2>
    <div id="matchList" class="match-list"></div>
  </section>

  <section id="add">
    <h2>➕ Add New Match</h2>
    <form id="matchForm">
      <input id="team1" placeholder="Team 1 Name" required>
      <input id="team2" placeholder="Team 2 Name" required>
      <input id="venue" placeholder="Match Venue" required>
      <button type="submit">Add Match</button>
    </form>
    <p id="message"></p>
  </section>
</main>

<footer>
  <p>© 2026 CricketLive | Developed by Jagannath</p>
</footer>

<script src="app.js"></script>
</body>
</html>
