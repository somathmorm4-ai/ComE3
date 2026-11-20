//MY VERSION
This is for working alone with force. In working no more force in workplace
In case it has a bit wrong:

1. Commit one more total2
2. Go base and commit again
   git commit below
   remember base only file in own computer:
   command to back 1 step: // git reset -soft head~1 (1 file)
3. git push origin main -force

//AI VERSION

# Git Workflow: Fixing a Mistake (Solo Projects Only)

# WARNING: Only use --force when working alone. Never force-push in a shared workplace repository.

# Scenario: You made a small mistake on your latest commit (e.g., 2 commits total)

# 1. Undo the last commit locally (keeps your changes staged on your computer)

git reset --soft HEAD~1

# 2. Fix your file, stage it, and create a new commit

git add .
git commit -m "Your updated commit message"

# 3. Force-push the updated commit to the remote repository

git push origin main --force

# Programming Concepts: Recursion, Endless Loops & Safety Tracks

## 1. Recursion (Recursive Functions)

**Definition:** A function that solves a big problem by **calling itself** on a smaller version of that same problem until it reaches a stopping point.

### Two Required Parts

1. **Base Case (The Stop Sign):** The simplest version of the problem that stops the function immediately without calling itself again.
2. **Recursive Case (The Step):** The function calls itself with a smaller or simpler input so it moves closer to the Base Case.

### Example: Countdown

```javascript
function countdown(number) {
  // 1. Base Case: Stop when we reach 0
  if (number <= 0) {
    console.log("Done!");
    return;
  }

  console.log(number);

  // 2. Recursive Case: Call itself with a smaller number
  countdown(number - 1);
}

countdown(3); // Output: 3, 2, 1, Done!
```

- **Real-World Uses:** Searching nested folders inside folders, dropdown sub-menus, and nested comment replies.

---

## 2. Endless Loops (Infinite Loops)

**Definition:** A loop or recursive function that repeats forever because it never reaches a stopping condition.

### Standard Endless Loop (`while` / `for`)

- **Cause:** The loop condition stays `true` forever.
- **Result:** The program or browser tab freezes until you force-stop it (`Ctrl + C` in the terminal).

```javascript
let count = 1;
while (count > 0) {
  console.log(count);
  count++; // Never stops: 1, 2, 3, 4...
}
```

### Recursive Endless Loop (Stack Overflow)

- **Cause:** Missing or unreachable **Base Case**.
- **Result:** Every function call fills up computer memory (the **Call Stack**) until it crashes immediately with a **Stack Overflow** error (`RangeError: Maximum call stack size exceeded`).

```javascript
function brokenCountdown(number) {
  // Missing Base Case!
  console.log(number);
  brokenCountdown(number - 1); // Runs forever: 3, 2, 1, 0, -1, -2...
}
```

---

## 3. Safety Tracks (Guardrails / Fail-Safes)

**Definition:** Deliberate safety checks built into loops and recursive functions to guarantee they stop before freezing or crashing your program.

### Four Common Safety Tracks

1. **Base Case (Stop Condition):** Exit immediately when the target condition is met (`if (n <= 0) return;`).
2. **Input Validation (Boundary Guard):** Check for invalid or negative inputs at the very top of the function before starting the loop.
3. **Maximum Step Counter:** Add a hard limit (e.g., `MAX_ATTEMPTS = 100`) and use `break` if the loop runs too many times.
4. **Timeout Check:** Record `Date.now()` at the start and `break` the loop if too many seconds pass.

### Example with Multiple Safety Tracks

```javascript
function safeFactorial(n) {
  // Safety Track 1: Input Validation (reject negative or non-number inputs)
  if (typeof n !== "number" || n < 0) {
    return "Invalid input";
  }

  // Safety Track 2: Base Case (stop sign)
  if (n === 0) return 1;

  // Recursive Step
  return n * safeFactorial(n - 1);
}
```
