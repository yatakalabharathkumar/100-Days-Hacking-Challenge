## 🗓️ Day 21/100 – PHP Functions Complete Guide

**Focus:** Server-side code organization and reusability.

### 1️⃣ Function Declaration Syntax
```php
function functionName($parameter1, $parameter2) {
    // Function body - code to execute
    return $result; // Optional return value
}
Explanation: function keyword declares, parameters accept input, {} contains logic.
2️⃣ Function Calling
function greet($name) {
    echo "Hello $name!";
}
// Calling the function
greet("Ethical Hacker"); // Output: Hello Ethical Hacker!

3️⃣ Function Types
A. Echo Function:
echo "Direct output to browser";

B. Predefined (Built-in) Functions:
echo strlen("Hello");     // 5
echo date("Y-m-d");       // 2026-01-17
echo md5("password");     // Hashed value

C. User-defined Functions:function calculateAge($birthYear) {
    return date("Y") - $birthYear;
}
echo calculateAge(1995); // 31
4️⃣ Series of Interaction Flow1. Declare function → Stored in memory
2. Call function → Executes code block
3. Process parameters → Perform logic
4. Return result → Continue program flow
5️⃣ Key Benefits Explained-  Avoid Repetitive Code: Write once, use many times
-  Controlled Execution: Call only when needed
-  Parameter Flexibility: Dynamic input processing
-  Modular Design: Organized, maintainable code

🔍 Security Relevance// BAD - Direct user input
echo $_POST['username'];

// GOOD - Sanitized via function
function sanitize($input) {
    return htmlspecialchars(trim($input));
}
echo sanitize($_POST['username']);Day 21 Summary: Functions transform scattered code into organized, reusable modules – essential for secure backend development.
