# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  
 index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>JavaScript Playground</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <h1>🎮 JavaScript Playground</h1>
  </header>

  <main>
    <!-- Button Interaction -->
    <section>
      <button id="magic-btn">Click Me!</button>
      <p id="magic-text"> Hello World!</p>
    </section>

    <!-- Image Gallery -->
    <section>
      <h2>Image Gallery</h2>
      <img id="gallery-img" src="https://via.placeholder.com/300" alt="Gallery" />
      <button id="next-img">Next</button>
    </section>

    <!-- Tabs -->
    <section class="tabs">
      <div class="tab-buttons">
        <button class="tab-btn" data-tab="1">Tab 1</button>
        <button class="tab-btn" data-tab="2">Tab 2</button>
      </div>
      <div class="tab-content" id="tab-1">This is content for Tab 1</div>
      <div class="tab-content" id="tab-2" style="display:none;">This is content for Tab 2</div>
    </section>

    <!-- Form Validation -->
    <section>
      <h2>Register</h2>
      <form id="signup-form">
        <input type="text" id="name" placeholder="Name" required /><br/>
        <input type="email" id="email" placeholder="Email" required /><br/>
        <input type="password" id="password" placeholder="Password" required /><br/>
        <button type="submit">Submit</button>
        <p id="form-message"></p>
      </form>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>
style.css 

body {
  font-family: 'Segoe UI', sans-serif;
  padding: 20px;
  background-color: #f9f9f9;
}

button {
  padding: 10px 15px;
  margin: 10px 0;
  cursor: pointer;
}

#magic-text {
  font-size: 1.2rem;
  color: #333;
}

.tabs {
  margin-top: 20px;
}

.tab-buttons {
  margin-bottom: 10px;
}

.tab-content {
  padding: 10px;
  background: #e0e0e0;
  border: 1px solid #ccc;
}

 script.js

// Button click event
document.getElementById('magic-btn').addEventListener('click', () => {
  const text = document.getElementById('magic-text');
  text.textContent = " You clicked the button!";
  text.style.color = "green";
});

// Hover event
const btn = document.getElementById('magic-btn');
btn.addEventListener('mouseover', () => btn.style.backgroundColor = "#ffd700");
btn.addEventListener('mouseout', () => btn.style.backgroundColor = "");

// Keypress detection
document.addEventListener('keypress', (e) => {
  console.log(`You pressed: ${e.key}`);
});

// Double-click secret action
btn.addEventListener('dblclick', () => alert(" Secret double-click activated!"));

// Image gallery logic
const images = [
  "https://via.placeholder.com/300/FF5733",
  "https://via.placeholder.com/300/33CFFF",
  "https://via.placeholder.com/300/75FF33"
];
let imgIndex = 0;
document.getElementById('next-img').addEventListener('click', () => {
  imgIndex = (imgIndex + 1) % images.length;
  document.getElementById('gallery-img').src = images[imgIndex];
});

// Tabs
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tab-content').forEach(tab => tab.style.display = 'none');
    document.getElementById(`tab-${btn.dataset.tab}`).style.display = 'block';
  });
});

// Form validation
document.getElementById('signup-form').addEventListener('submit', function(e) {
  e.preventDefault();
  const email = document.getElementById('email').value;
  const password = document.getElementById('password').value;
  const message = document.getElementById('form-message');

  if (!email.includes('@')) {
    message.textContent = "Invalid email!";
    message.style.color = "red";
    return;
  }

  if (password.length < 8) {
    message.textContent = "Password must be at least 8 characters!";
    message.style.color = "red";
    return;
  }

  message.textContent = "Successfully registered!";
  message.style.color = "green";
});
