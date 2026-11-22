# Roam Local — Complete Full-Stack Website (Evaluation 2 & 3)

A Delhi & Gurugram regional travel guide built with HTML5, CSS3, Vanilla JavaScript, Node.js, Express, local JSON file persistence, MongoDB (Mongoose), and the Open-Meteo External Weather API.

---

## How to Run the Website (3 Steps)

1. **Open the project folder** (`Roam-Local`) in VS Code or a terminal.
2. **Install dependencies** (only needed once):
   ```bash
   npm install
   ```
3. **Start the server:**
   ```bash
   npm start
   ```
4. Open **`http://localhost:4000`** in your browser.

---

## Where Each Rubric Requirement Lives

### Evaluation 2 Requirements
1. **Multi-page navigation:** `public/index.html`, `explore.html`, `destination.html`, `saved.html`, `community.html`, `about.html`, `contact.html`.
2. **JavaScript interactions & form validation:** `public/script.js` handles live search, region filtering, sorting, dynamic URL parameters (`?id=`), character counters, and real-time field validation.
3. **Form submissions:** Contact Us (`public/contact.html`) and Community Tips (`public/community.html`).
4. **Saving submitted form data to local JSON files:** `src/controllers/jsonStorage.controller.js` uses Node's `fs/promises` to write contact form submissions to `data/messages.json` and saved favorites to `data/favorites.json`.

### Evaluation 3 Requirements
1. **External API integration:** `public/script.js` calls the public **Open-Meteo Weather API** on `destination.html` to display live temperature, weather status, and wind speed for Delhi/Gurugram spots.
2. **Node & Express setup:** `package.json`, `src/index.js`, `src/app.js`, and `src/config/database.js`.
3. **Express APIs for local JSON files:** `src/routes/jsonStorage.route.js` (`GET` & `POST` `/api/v1/json/messages`, `GET` & `DELETE` `/api/v1/json/favorites`, `POST /api/v1/json/favorites/toggle`).
4. **CRUD operations in MongoDB via Express APIs:** `src/models/tip.model.js`, `src/controllers/tip.controller.js`, and `src/routes/tip.route.js`:
   - **Create:** `POST /api/v1/tips` (Post a new community tip)
   - **Read:** `GET /api/v1/tips` (Load all community tips from MongoDB)
   - **Update:** `PUT /api/v1/tips/:id` (Edit tip title/text or upvote a tip)
   - **Delete:** `DELETE /api/v1/tips/:id` (Remove a tip from MongoDB)

---

## Plain-English Viva Cheat Sheet

- **Why do we have BOTH local JSON files and MongoDB?**
  - Local JSON files (`data/messages.json` and `data/favorites.json`) satisfy the server-side file storage requirement using Node's `fs` module, while MongoDB (`tips` collection via Mongoose) handles full database CRUD operations for dynamic community posts.
- **`var` vs `let` vs `const`:**
  - `const` is block-scoped and cannot be reassigned (used for `DESTINATIONS`, DOM references, and Express routers). `let` is block-scoped and can be reassigned (used for counters and filtered arrays). `var` is function-scoped and hoisted, which we avoid to prevent accidental bugs.
- **Synchronous vs Asynchronous JS, Promises, and `async/await`:**
  - JavaScript runs on a single thread. Network requests (`fetch`) and file/database operations take time, so they return a **Promise** instead of freezing the page. `async/await` lets us write asynchronous Promise code cleanly step-by-step.
- **Callbacks, Higher-Order Functions, and First-Class Functions:**
  - Functions in JS are **first-class** (can be stored in variables or passed as arguments). Functions like `.map()`, `.filter()`, `.sort()`, and `addEventListener()` are **higher-order functions** because they accept another function (**callback**) as an argument.
- **DOM Manipulation & Event Delegation:**
  - Instead of attaching separate click listeners to every heart, edit, or delete button, we attach one listener on the parent container (`document` or `#communityGrid`) and check `e.target.closest(...)`—this is called **event delegation**.
