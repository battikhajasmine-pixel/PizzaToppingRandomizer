# PizzaToppingRandomizer
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Pizza Topping Randomizer</title>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; padding: 40px; }
    h1 { color: #d35400; }
    button { padding: 10px 20px; font-size: 16px; margin-top: 20px; }
    ul { list-style-type: none; padding: 0; }
    li { font-size: 18px; margin: 5px 0; }
  </style>
</head>
<body>
  <h1>🍕 Pizza Topping Randomizer</h1>
  <p>Click the button to generate a random pizza topping combination!</p>
  <button onclick="generateToppings()">Randomize Toppings</button>
  <ul id="toppingList"></ul>

  <script>
    const toppings = ["Mushrooms", "Broccoli", "Tomatoes", "Pepperoni", "Onions", "Olives"];

    function generateToppings() {
      const totalToppings = Math.floor(Math.random() * 3) + 3; // 3 to 5 toppings
      const toppingCounts = {};

      toppings.forEach(t => toppingCounts[t] = 0);

      let count = 0;
      while (count < totalToppings) {
        const topping = toppings[Math.floor(Math.random() * toppings.length)];
        if (toppingCounts[topping] < 3) {
          toppingCounts[topping]++;
          count++;
        }
      }

      const list = document.getElementById("toppingList");
      list.innerHTML = "";
      for (const [topping, qty] of Object.entries(toppingCounts)) {
        if (qty > 0) {
          const li = document.createElement("li");
          li.textContent = `${qty} × ${topping}`;
          list.appendChild(li);
        }
      }
    }
  </script>
</body>
</html>
