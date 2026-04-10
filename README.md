# NCStateDiningHall
NC State Dining Hall website for allergies recommendations
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>NC State Dining Guide</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

<header>
  <h1>NC State Dining Guide</h1>
  <p>Find where to eat based on your dietary restrictions</p>
</header>

<main id="container"></main>

<script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  background-color: #f5f5f5;
}

header {
  background-color: #CC0000;
  color: white;
  text-align: center;
  padding: 20px;
}

h1 {
  margin: 0;
}

.dropdown {
  background-color: white;
  margin: 15px;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
}

.dropdown-header {
  background-color: #990000;
  color: white;
  padding: 15px;
  cursor: pointer;
  font-size: 18px;
}

.dropdown-content {
  display: none;
  padding: 20px;
}

.columns {
  display: flex;
  gap: 20px;
}

.column {
  flex: 1;
}

.column h3 {
  border-bottom: 2px solid #CC0000;
  padding-bottom: 5px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 6px 0;
}
const data = [
  {
    title: "Soy",
    go: [
      "Char Grill",
      "Taverna Agora",
      "Lobera Tacos & Tequila",
      "Meat & Bite",
      "Guasaca South American Grill",
      "The Players Retreat",
      "Coco Bongo Mexican Cantina"
    ],
    avoid: ["Fun DipPot"]
  },
  {
    title: "Dairy",
    go: [
      "Char Grill",
      "Kabab and Curry",
      "Lobera Tacos & Tequila",
      "Guasaca South American Grill",
      "Taverna Agora"
    ],
    avoid: [
      "Mitch’s Tavern",
      "Alpaca Chicken",
      "The Players Retreat",
      "Fun DipPot"
    ]
  },
  {
    title: "Sesame",
    go: [
      "Taverna Agora",
      "Guasaca South American Grill",
      "Meat & Bite",
      "Kabab & Curry",
      "Jasmin & Olivz Mediterranean"
    ],
    avoid: [
      "Hibachi & Company",
      "Kabab and Curry",
      "Fun DipPot"
    ]
  },
  {
    title: "Nuts",
    go: [
      "Taverna Agora",
      "Guasaca South American Grill",
      "Meat & Bite",
      "Kabab & Curry",
      "Jasmin & Olivz Mediterranean"
    ],
    avoid: [
      "Alpaca Chicken",
      "Fun DipPot",
      "Coco Bongo Mexican Cantina",
      "Hibachi & Company"
    ]
  },
  {
    title: "Fish & Shellfish",
    go: [
      "Taverna Agora",
      "Meat & Bite",
      "Guasaca South American Grill",
      "Jasmin & Olivz Mediterranean",
      "Kabab & Curry"
    ],
    avoid: [
      "The Players Retreat",
      "Coco Bongo Mexican Cantina",
      "Fun DipPot",
      "Alpaca Chicken",
      "Hibachi & Company"
    ]
  },
  {
    title: "Eggs",
    go: [
      "Taverna Agora",
      "Lobera Tacos & Tequila",
      "Meat & Bite",
      "Guasaca South American Grill",
      "Jasmin & Olivz Mediterranean"
    ],
    avoid: [
      "The Players Retreat",
      "Coco Bongo Mexican Cantina",
      "Fun DipPot",
      "Alpaca Chicken",
      "Mitch’s Tavern"
    ]
  },
  {
    title: "Gluten",
    go: [
      "Kabab and Curry - Raleigh",
      "Char Grill",
      "Meat & Bite",
      "Guasaca South American Grill",
      "Lobera Tacos & Tequila"
    ],
    avoid: [
      "The Players Retreat",
      "Coco Bongo Mexican Cantina",
      "Fun DipPot",
      "Alpaca Chicken"
    ]
  }
];

const container = document.getElementById("container");

data.forEach(item => {
  const dropdown = document.createElement("div");
  dropdown.className = "dropdown";

  const header = document.createElement("div");
  header.className = "dropdown-header";
  header.textContent = item.title;

  const content = document.createElement("div");
  content.className = "dropdown-content";

  const columns = document.createElement("div");
  columns.className = "columns";

  const left = document.createElement("div");
  left.className = "column";
  left.innerHTML = "<h3>Where to go</h3>";

  const right = document.createElement("div");
  right.className = "column";
  right.innerHTML = "<h3>Where to avoid</h3>";

  const ulGo = document.createElement("ul");
  item.go.forEach(place => {
    const li = document.createElement("li");
    li.textContent = place;
    ulGo.appendChild(li);
  });

  const ulAvoid = document.createElement("ul");
  item.avoid.forEach(place => {
    const li = document.createElement("li");
    li.textContent = place;
    ulAvoid.appendChild(li);
  });

  left.appendChild(ulGo);
  right.appendChild(ulAvoid);

  columns.appendChild(left);
  columns.appendChild(right);
  content.appendChild(columns);

  header.addEventListener("click", () => {
    content.style.display =
      content.style.display === "block" ? "none" : "block";
  });

  dropdown.appendChild(header);
  dropdown.appendChild(content);
  container.appendChild(dropdown);
});
