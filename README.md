# Lab 4a — JavaScript DOM Manipulation

**Course:** BIC21203 — Web Development
**Lab:** #4a (JavaScript)

| Field | Value |
| --- | --- |
| **Name** | `[Your Full Name]` |
| **Student ID** | `[Your Student ID]` |
| **Section / Group** | `[Your Section]` |
| **Lecturer** | `[Lecturer's Name]` |
| **Date Submitted** | `[DD/MM/YYYY]` |

---

## Overview

Lab 4a covers the fundamentals of JavaScript in the browser. All three questions
use clean HTML5 with modern vanilla JavaScript and **zero external libraries**.
Each question lives in its own folder with an external `script.js` linked using
the `defer` attribute, all events are bound with `addEventListener()`, and every
text update uses `textContent` (never `innerHTML`) so user input can never inject
markup into the page.

| Question | Topic | Files |
| --- | --- | --- |
| Q1 | Interactive Text Changer — DOM selection + click events | `q1/index.html`, `q1/script.js` |
| Q2 | Smart Number Validator — `if...else if...else` + input validation | `q2/index.html`, `q2/script.js` |
| Q3 | Dynamic Number Generator — `for` loop + `createElement()` | `q3/index.html`, `q3/script.js` |

---

## Question 1 — Interactive Text Changer

**What it does:** Clicking the *Change Message* button replaces the paragraph text
`Welcome to my website!` with `Hello there!`.

**How it works:**

1. `document.querySelector("#message")` and `document.querySelector("#changeBtn")`
   select the paragraph and the button.
2. The `changeMessage()` function sets `messageElement.textContent = "Hello there!"`.
3. The handler is attached with `changeButton.addEventListener("click", changeMessage)` —
   no inline `onclick` attribute is used.

**To run (step-by-step):**

1. Open `q1/index.html` in any modern browser (double-click the file, or right-click →
   *Open With* your browser).
2. Verify the page shows the heading, the paragraph `Welcome to my website!` and the
   *Change Message* button.
3. Click **Change Message** once. The paragraph must now read `Hello there!`.
4. Reload the page and click again to confirm the behaviour is repeatable.

**Screenshot:**

| # | Screenshot placeholder |
| --- | --- |
| 1 | `[Insert screenshot: q1 before clicking the button]` |
| 2 | `[Insert screenshot: q1 after clicking the button — text reads "Hello there!"]` |

---

## Question 2 — Smart Number Validator

**What it does:** Type a number and press *Check* to compare it against `10`.

**How it works:**

1. The function `checkInput()` reads `#userInput`, calls `.trim()`, and converts the
   result with `Number()`.
2. A single `if...else if...else if...else` chain produces one of four messages in
   `#result` via `textContent`:
   - Invalid or empty → `Please enter a valid number!`
   - `< 10` → `The number is lower than 10`
   - `> 10` → `The number is higher than 10`
   - `= 10` → `The number is equal to 10`
3. Empty strings and non-numeric strings (`abc`) both become `NaN` and are rejected;
   decimals such as `10.5` are accepted.
4. The button uses `checkButton.addEventListener("click", checkInput)`.

**To run (step-by-step):**

1. Open `q2/index.html` in a browser.
2. Leave the field empty and click **Check** → `Please enter a valid number!`
3. Type `abc` and click **Check** → `Please enter a valid number!`
4. Type `5` → `The number is lower than 10`
5. Type `25` → `The number is higher than 10`
6. Type `10` → `The number is equal to 10`
7. Type `10.5` → `The number is higher than 10` (decimal support confirmed).

**Screenshot:**

| # | Screenshot placeholder |
| --- | --- |
| 3 | `[Insert screenshot: q2 with input "5" → "The number is lower than 10"]` |
| 4 | `[Insert screenshot: q2 with input "10" → "The number is equal to 10"]` |
| 5 | `[Insert screenshot: q2 with empty/invalid input → error message]` |

---

## Question 3 — Dynamic Number Generator

**What it does:** Each click on *Generate* builds a numbered list of five items.

**How it works:**

1. `generateNumbers()` first clears `#numberList` by setting its `textContent` to
   `""`, so repeated clicks never duplicate items.
2. A `for` loop runs from `i = 1` to `i <= 5`.
3. Inside the loop, `document.createElement("li")` creates the element, its
   `textContent` is set to `"The number is " + i`, and it is appended with
   `numberList.appendChild(listItem)`.
4. The button uses `generateButton.addEventListener("click", generateNumbers)`.

**To run (step-by-step):**

1. Open `q3/index.html` in a browser.
2. Click **Generate** — the list shows items 1 to 5 (`The number is 1` … `The number is 5`).
3. Click **Generate** several more times — the list still contains exactly five items
   (no duplicates).
4. Open the browser DevTools (F12) → *Elements* panel to inspect the `<ol>` and confirm
   five `<li>` children were created by JavaScript.

**Screenshot:**

| # | Screenshot placeholder |
| --- | --- |
| 6 | `[Insert screenshot: q3 after the first Generate click]` |
| 7 | `[Insert screenshot: q3 after repeated Generate clicks — still exactly 5 items]` |

---

## Project Structure

```
bic21203-lab4a-javascript/
├── README.md
├── PDF_REPORT_NOTES.md
├── q1/
│   ├── index.html
│   └── script.js
├── q2/
│   ├── index.html
│   └── script.js
└── q3/
    ├── index.html
    └── script.js
```

## Compliance Checklist

- [x] Clean HTML5 with external `script.js` files linked using `defer`
- [x] Zero external libraries
- [x] All events bound with `addEventListener()` — no inline `onclick`
- [x] All text updates via `textContent` — no `innerHTML`
- [x] Descriptive labels and visible, accessible output regions (`role="status"`, `aria-live`)
- [x] Q1 `changeMessage()` sets `#message` to `Hello there!`
- [x] Q2 `checkInput()` uses `if...else if...else` with all four exact messages
- [x] Q3 `generateNumbers()` clears the list, loops 1–5, creates and appends `<li>` elements
