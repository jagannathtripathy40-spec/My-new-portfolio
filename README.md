
const express = require("express");
const fs = require("fs");
const path = require("path");

const app = express();
const PORT = 3000;
const DB = path.join(__dirname, "matches.json");

app.use(express.json());
app.use(express.static(path.join(__dirname, "public")));

function readMatches() {
  if (!fs.existsSync(DB)) {
    fs.writeFileSync(DB, "[]");
  }
  return JSON.parse(fs.readFileSync(DB, "utf8"));
}

function saveMatches(matches) {
  fs.writeFileSync(DB, JSON.stringify(matches, null, 2));
}

// Get all matches
app.get("/api/matches", (req, res) => {
  res.json(readMatches());
});

// Add new match
app.post("/api/matches", (req, res) => {
  const { team1, team2, venue } = req.body;

  if (!team1 || !team2 || !venue || team1 === team2) {
    return res.status(400).json({ error: "Enter valid match details" });
  }

  const matches = readMatches();

  const match = {
    id: Date.now().toString(),
    team1,
    team2,
    venue,
    status: "Upcoming",
    runs: 0,
    wickets: 0,
    overs: 0
  };

  matches.push(match);
  saveMatches(matches);

  res.status(201).json(match);
});

// Update score
app.patch("/api/matches/:id/score", (req, res) => {
  const matches = readMatches();
  const match = matches.find(m => m.id === req.params.id);

  if (!match) {
    return res.status(404).json({ error: "Match not found" });
  }

  const { runs, wickets, overs, status } = req.body;

  if (runs !== undefined) match.runs = Math.max(0, Number(runs));
  if (wickets !== undefined) match.wickets = Math.min(10, Math.max(0, Number(wickets)));
  if (overs !== undefined) match.overs = Math.max(0, Number(overs));
  if (status !== undefined) match.status = status;

  saveMatches(matches);
  res.json(match);
});

// Delete match
app.delete("/api/matches/:id", (req, res) => {
  const matches = readMatches();
  const updated = matches.filter(m => m.id !== req.params.id);

  if (matches.length === updated.length) {
    return res.status(404).json({ error: "Match not found" });
  }

  saveMatches(updated);
  res.json({ message: "Match deleted successfully" });
});

app.listen(PORT, () => {
  console.log(`CricketLive running at http://localhost:${PORT}`);
});

