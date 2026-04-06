## Introduction to C++ and Programming Languages

A **programming language** is a language programmers use to communicate instructions to computers, which only understand binary (0s and 1s). Humans can't write directly in binary, so programming languages like C++ provide a human-readable way to write code (source code), which gets converted to machine-understandable format.     

**C++** is a fast, efficient programming language for high-performance systems. It's used for:
- Game development (e.g., high-speed graphics)
- Real-time systems
- Low-level memory management and system resource access
- Backend development
- Object-oriented programming features (classes, objects—detailed later)

Major companies like Adobe use C++ extensively today.      

## Compilation Process

**Compilation** translates human-readable source code (e.g., C++) into machine code (binary) via a **compiler**. Why? Computers don't understand C++ directly.     
![Compilation Process](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/C%2B%2B%20Compilation%20Process.png)
  

The process creates an **executable file** (.exe on Windows), which runs when double-clicked (e.g., a game like Temple Run compiled from C++ source). Four phases exist (pre-processing, compilation, assembly, linking), but details are advanced.       

## Course Structure and Resources

This 13-hour video covers C++ from basic to advanced in 20 chapters (timestamps in description). Watch at 2x speed for efficiency.   

**Extras provided:**
- 100+ solved questions (in-lecture + homework/practice)
- Article-format notes and all code (links in description)
- Structured version (₹1 access): separate lectures, quizzes, progress tracking, leaderboards, streaks, video solutions          

**Weekly crash course:** Covers C++ intro, basic syntax, STL (Standard Template Library), fundamentals before advanced topics.  

**Homework:** Research—is C++ low-level, high-level, or both? (Comment answer).   

## VS Code Setup for C++ (Mac)

1. Download VS Code from code.visualstudio.com (Mac version).   
2. Drag to Applications folder.  
3. Create folder (e.g., "CPP Crash"), open in VS Code.   
4. Create `main.cpp` file (C++ extension:.cpp).  
5. Install recommended C/C++ extension pack.  
6. Install "C/C++ Compile Run" extension (Extensions tab).   
7. Write/test code (e.g., print "Your name is Babbar"), run via triangle icon.     

VS Code tabs: Explorer (files), Extensions, Run/Debug, Search. Customize themes/folders as needed.     

## VS Code Setup for C++ (Windows)

Requires **MinGW** (GCC compiler collection) first:

| Step | Action | Details |
|------|--------|---------|
| 1. MinGW Install | Download from sourceforge.net (MinGW-w64), run installer | Select basic setup + GNU C++ Compiler, apply changes       |
| 2. Path Config | Copy MinGW/bin path (e.g., C:\MinGW\bin), add to Environment Variables > Path | Verify: Open CMD, run `g++ --version`       |
| 3. VS Code Install | Download from code.visualstudio.com, run installer | Choose theme, create/open folder (e.g., "CPP First Code")      |
| 4. File & Extensions | Create `main.cpp`, install C/C++ pack + "C/C++ Compile Run" | Run code via triangle      |

Test: Code prints input/output (e.g., "Enter age" → "Your age is 25").    

## Your First C++ Program: Namaste Duniya

Assuming setup done, create `main.cpp`:

```
#include <iostream>
using namespace std;
int main() {
    cout << "Namaste Duniya" << endl;
    return 0;
}
```

**Breakdown starts here:** Every program has a **starting point** (`int main()`—function, detailed later). Run it—prints "Namaste Duniya". Empty `main()` compiles but prints nothing. Full explanation (e.g., `#include`, `namespace`, `cout`, `return 0`) follows in next lectures.          



Practice in your setup folder—next lectures detail syntax.   

---

## Program Entry Point: int main()

Every C++ program has a single starting point called `int main()`, where execution begins regardless of program size (e.g., 1000 or 1 million lines). The compiler locates `int main()` and starts running code from there, similar to a race starting from a fixed line.     

The curly braces `{}` after `int main()` define the **scope**—the boundary of code belonging exclusively to `main()`. Code inside belongs to `main()`; code outside does not, like property lines separating your house from a neighbor's. Only code within these braces is considered `main()`'s "property" and executes as part of the entry point.         

```cpp
int main() {
    // All code here belongs to main() and executes sequentially
    return 0;
}
```

## Return Statement: Indicating Execution Status

`return 0;` at the end signals **successful execution** to the operating system (OS). Think of finishing an exam: smiling (success) vs. frowning (failure). `return 0;` is like smiling—program ran perfectly. Any non-zero value (e.g., `return 1001;`, `return -1;`, `return 1;`) indicates **failure** (error, crash, or incomplete execution). The OS calls `main()` and checks this return value to confirm status.         

| Return Value | Meaning                  | Analogy                  |
|--------------|--------------------------|--------------------------|
| 0            | Success                 | Exam went well (smile)    
| Non-zero (1, -1, 1001) | Failure/Error | Exam failed (frown)       

## Printing "Hello World": Basic Output

To print "Namaste Dunia" (Hello World):

1. Include input/output header: `#include <iostream>` —provides input/output facilities and standard namespace definitions.    
2. Use standard namespace: `using namespace std;` —accesses `cout` definition without prefix.   
3. Inside `main()`: `cout << "Namaste Dunia" << endl;` —prints string to output window/terminal.   

Without `#include <iostream>`, compiler errors: "undefined identifier 'cout'"—like using a word without dictionary lookup.    

**Key Components:**
- `cout`: Output stream identifier (keyword for printing).  
- `<<`: Insertion operator (always used with `cout` for output).  
- `"Namaste Dunia"`: **String**—text in double quotes.   
- `endl`: Prints newline (like Enter key in MS Word), moves cursor to next line. Without it, text prints side-by-side.     

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Namaste Dunia" << endl;  // Prints on new line
    cout << "Namaste Dunia";         // Same line if no endl
    return 0;
}
```
**Demo Difference:**

| Without endl          | With endl              |
|-----------------------|------------------------|
| Namaste DuniaNamaste Dunia | Namaste Dunia<br>Namaste Dunia    |

Semicolon `;` terminates every statement (end of line).   

## Variables: Named Memory Storage

Variables are **named memory blocks** for storing data. Memory consists of blocks (e.g., 1 byte = 8 bits). To store 50:

1. Assign name: `marks` (like calling a friend by name).
2. Insert value: Memory block named `marks` holds 50.
3. Access: `cout << marks;` prints 50.          

**Syntax:** `data_type variable_name = value;`
- **Data type**: Specifies type/size (e.g., `int` for integers).
- **Variable name**: Custom label (e.g., `age`, `marks`).
- `=`: Assigns/inserts value.
- `;`: Terminates.     

```cpp
int age = 25;  // int: integer type, age: name, 25: value
cout << age;   // Prints 25, accesses memory block   
age = 32;      // Updates: 25 → 32   
```

Variables enable data storage, access, update—like boxes with labels.  

## Data Types: Type and Size Information

Data types provide two pieces of info:
1. **Type of data** stored (integer, character, etc.).
2. **Size in memory** (e.g., int: ~4 bytes/32 bits on modern systems).     

**Primitive Types (focus here):**

| Type    | Stores                  | Example Syntax          | Size (Typical) | Values Example     |
|---------|-------------------------|-------------------------|----------------|-------------------|
| int     | Integers               | `int count = 5;`       | 4 bytes       | 5, -10   
| float   | Decimal (less precise) | `float pi = 3.14f;`    | 4 bytes       | 3.14  
| double  | Decimal (precise)      | `double weight = 55.6987;` | 8 bytes  | 55.6987   
| char    | Single character       | `char alphabet = 'Z';` | 1 byte        | 'Z' (single quotes!)   
| bool    | True/False             | `bool isMale = true;`  | 1 byte        | true/1, false/0    

**Notes:**
- char: **Single quotes** only (`'Z'`, not `"Z"` or no quotes).  
- bool: true=1, false=0 (interchangeable).   
- void: Later (functions).   
- Sizes **system-dependent**—use `sizeof(variable)` to check.    

**Printing All:**
```cpp
cout << count << pi << alphabet << weight << isMale << endl;
// Output: 5 3.14 Z 55.6987 1   
```

**Ranges:** Derived from bits (e.g., 32-bit int: max ~$$2^{31}-1$$ for signed). Homework: Binary storage, exact ranges.      

## Declaration vs Definition vs Manipulation

- **Declaration**: Create variable, no value (gets **garbage/random value**). `int age;` → Prints garbage (e.g., 4565296, changes per run).     
- **Definition**: Create + assign value. `int age = 21;`   
- **Manipulation/Update**: Change existing value. `age = 1001;` (after creation).   
- **Cannot redeclare** same name twice in same scope: Compiler error "redefinition".    

**Flow Example:**
```cpp
int age = 21;      // Definition: Creates box "age", inserts 21  
cout << age;       // Prints 21  
age = 1001;        // Update: 21 → 1001  
cout << age;       // Prints 1001  
```

## Additional Syntax Elements

- **Comments**: `//` ignores line (notes, disable code).    
- **Preprocessor Directive**: `#include` (processed before compilation).  
- **Homework**:
  | Task | Why/Alternative |
  |------|-----------------|
  | Newline without `endl` | Use `\n`  
  | `cout` without `using namespace std;` | `std::cout`  
  | `return -1;` effect | Signals failure  
  | How data stored in memory (binary) | Integers, float, etc.    

Full "Hello World" enables printing; variables/data types build data handling foundation. Next: Advanced topics like derived/user-defined types.     

---

## Signed vs Unsigned Integers

Integers in C++ come in two forms: **signed integers**, which store both positive and negative numbers (including zero), and **unsigned integers**, which store only non-negative values (zero and positive numbers).    

The range depends on the number of bits $$n$$ (typically 32 bits for `int`):
- **Unsigned**: $$0$$ to $$2^n - 1$$ (e.g., for 32 bits: 0 to 4294967295)   
- **Signed**: $$-(2^{n-1})$$ to $$2^{n-1} - 1$$ (e.g., for 32 bits: -2147483648 to 2147483647)    

**Verification example**:
- $$2^{31} = 2147483648$$
- Signed max: $$2147483648 - 1 = 2147483647$$  

This formula applies to any integer type. Homework: Verify ranges for `int`, `float`, `double`, `char`, `bool` using `sizeof()` and online resources.    

## Memory Allocation for Primitive Data Types

Primitive types have fixed sizes (assuming 32/64-bit systems):
| Type   | Size (bytes) | Notes |
|--------|--------------|-------|
| `int`  | 4            | Signed/unsigned variants   |
| `float`| 4            | Decimal numbers   |
| `double`| 8          | Higher precision decimals   |
| `char` | 1            | Single characters   |
| `bool` | 1            | true/false (despite needing only 1 bit)   |

**Why `bool` takes 1 byte?** Memory's **smallest addressable unit** is 1 byte. Sub-byte addressing isn't possible, so even 1-bit data uses a full byte (e.g., true as 00000001, false as 00000000).     

Variables are **named memory locations**. Data types specify **type** (what kind of data) and **size** (how much memory).   

## Variable Scope and Redeclaration Rules

Variables cannot be **redeclared** in the **same scope** (code block), causing "redefinition" error:
```cpp
int main() {
    int age = 12;      // OK
    int age = 5;       // ERROR: redefinition  
}
```
**Allowed**:
- **Update** value: `age = 5;`  
- **Different scopes** (separate blocks):
  ```cpp
  {
      int a = 12;    // Block 1  
  }
  {
      int a = 5;     // Block 2: OK  
  }
  ```
- **Nested blocks**:
  ```cpp
  {
      int a = 12;
      {              // Nested block
          int a = 5; // OK  
      }
  }
  ```
**Rule**: Same name OK in different scopes; forbidden in same scope.     

## User Input with `cin`

Include `<iostream>` and `using namespace std;` for `cin` (input) and `cout` (output). `cin` uses **extraction operator** `>>` to read into variables, replacing garbage values.      

**Basic syntax**:
```cpp
int marks;
cout << "Enter your marks: ";
cin >> marks;  // Program waits (blocks) until input + Enter   
cout << "Your marks: " << marks << endl;
```
- Blocks execution until input received   
- Works for `int`, `float`, `double`, `char`      

**Boolean special case**: Input 0 (false) or 1 (true); "true"/"false" strings fail     

**Without `using namespace std;`**: Use `std::cin`, `std::cout`     

**Homework**: Study `cin.ignore()`, `cin.fail()`, `getline(cin, str)`   

## Decision Making Statements (if, if-else, etc.)

Control flow uses conditions to execute code selectively. Conditions evaluate to **true** (non-zero) or **false** (zero).     

### Simple `if`
```cpp
if (budget > 2000000) {
    cout << "You can buy Scorpio";  // Only if true   
}
```
- True: Execute block
- False: Skip to next line   



Example output: Budget > 20L prints message; ≤20L skips.   

### if-else
Handles both cases:
```cpp
if (budget > 2000000) {
    cout << "You can buy Scorpio";
} else {
    cout << "You cannot buy Scorpio";  // True: if; False: else   
}
```
True skips else entirely.   

### if-else if (Chain)
Checks sequentially; first true executes, rest skipped:
```cpp
if (marks > 90) cout << "A";
else if (marks > 80) cout << "B";
else if (marks > 70) cout << "C";
else if (marks > 60) cout << "D";
// 65: D (first true); 55: nothing     
```
Order matters: Test strictest first.    

### if-else if-else (with Default)
Adds final `else` for all false cases:
```cpp
//... same chain...
else cout << "You failed";  // 55: "You failed"   
```
First true executes and exits; all false → else.      

### Nested if
if inside if (multiple conditions AND logic):
```cpp
if (height > 5) {
    if (weight > 70) {
        cout << "Good BMI";  // Both true  
    } else {
        cout << "B";         // height>5 true, weight≤70  
    }
} else {
    cout << "C";             // height≤5  
}
```
Outer true required for inner; true if skips its else.     

**Homework**: Practice `::` operator (scope resolution); re-watch for mastery.   

---

## Switch Statement in C++

The **switch statement** is a control flow construct used for multi-way branching based on a single expression's value, making code more readable than long chains of if-else-if statements, especially for multiple discrete cases. It evaluates an expression once and jumps to the matching case, avoiding repeated comparisons.   

### Why Use Switch Over if-else Chains?
Consider determining mark ranges from a grade input ('A', 'B', 'C', 'D', or other). An if-else chain repeats the same comparison (`grade == 'A'`, etc.):

```
if (grade == 'A') {
    cout << "Your marks will be in range of 90 to 100" << endl;
} else if (grade == 'B') {
    cout << "Your marks will be in range of 80 to 90" << endl;
} else if (grade == 'C') {
    cout << "Your marks will be in range of 70 to 80" << endl;
} else if (grade == 'D') {
    cout << "Your marks will be in range of 60 to 70" << endl;
} else {
    cout << "Your marks will revolve in range of 0 to 60" << endl;
}
```

This works but becomes messy for many cases. Switch simplifies it by evaluating `grade` once.       

**Note on `==`**: The double equals (`==`) performs comparison, returning `true` (1) or `false` (0). Single `=` is assignment.   

### Switch Syntax and Execution
```
switch (expression) {
    case constant1:
        // code for constant1
        break;
    case constant2:
        // code for constant2
        break;...
    default:
        // code if no match
        // no break needed
}
```

- **expression**: Evaluated once; must yield unique, constant values (int, char, enum; no float, string, or ranges).
- **case labels**: Match exact constant values from expression.
- **break**: Exits switch after executing the case; without it, execution "falls through" to next cases (intentional for grouped cases, but usually a bug).
- **default**: Optional catch-all (like else).         

Converted grade example:
```
switch (grade) {
    case 'A':
        cout << "Your marks will be in range of 90 to 100" << endl;
        break;
    case 'B':
        cout << "Your marks will be in range of 80 to 90" << endl;
        break;
    case 'C':
        cout << "Your marks will be in range of 70 to 80" << endl;
        break;
    case 'D':
        cout << "Your marks will be in range of 60 to 70" << endl;
        break;
    default:
        cout << "Your marks will revolve in range of 0 to 60" << endl;
}
```

**Execution Flow**:
1. Compute `grade` (e.g., 'A').
2. Sequential check: Match 'A'? Yes → execute code → `break` → exit.
3. Without `break`, it continues to 'B', 'C', etc. (fall-through).        

Example output (with breaks): Input 'A' → "90 to 100"; 'G' → "0 to 60".   
![Switch Execution Flow](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/Switch%20Execution%20Flow.png)
  

Switch checks cases sequentially until match or default.  

### Switch Constraints
| Constraint | Details | Why? |
|------------|---------|------|
| Expression Types | int, char, enum only | No float/string (non-integral).     |
| Case Values | Unique constants | No duplicates (e.g., no two `case 'A':`).    |
| No Ranges | `case age > 8:` invalid | Compiler error: "expression must have constant value". Use if for ranges.     |
| Boolean Hack | Possible but warned (e.g., `switch(age > 10)` → case 1/true). | Unusual; prefer if.     |
| Fall-Through | Without break, executes next cases. | Intentional for multi-cases; else use break.    |
| Default | Optional. | Code runs without it if no match.    |

Day-of-week example: `int day=3;` → `case 3: cout << "Wednesday"; break;` → Output: "Wednesday".   

## Ternary Operator (Conditional Operator)

Not a control flow statement but an operator (`?:`) for concise if-else, useful for simple assignments. Syntax: `condition? true_expression: false_expression`.   

Evaluates condition:
- True → returns value after `?`.
- False → returns value after `:`.     

| if-else | Ternary Equivalent |
|---------|---------------------|
| ```if (age > 18) cout << "Can vote"; else cout << "Cannot vote";``` | ```(age > 18)? cout << "Can vote": cout << "Cannot vote";```    |
| ```int result; if (x > y) result = x; else result = y;``` | ```int result = (x > y)? x: y;```     |

**Output Examples**:
- age=12 (>18? false) → "Cannot vote".
- age=22 → "Can vote".
- x=10, y=20 (>? false) → result=20.      

Use for short logic only; complex → use if-else.

## Loops in C++

Loops repeat code efficiently for repeated tasks (e.g., print "Babbar" 1000 times without 1000 lines). Three types: for, while, do-while.        

### For Loop
**Syntax**: `for (initialization; condition; update) { body }`
- **Initialization**: Run once before loop (e.g., `int i=1`).
- **Condition**: Checked before each iteration (true → enter/continue).
- **Update**: After body, before next condition check.
- All parts optional (just `;;` loops infinitely—homework: verify).     

**Execution Cycle**:
1. Init (once).
2. Check condition (false → exit).
3. Execute body.
4. Update.
5. Repeat 2-4.
![For Loop Execution](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/For%20Loop%20Execution.png)
  

**Examples**:
```
for (int i=1; i<=10; i++) {
    cout << i << " ";  // Prints: 1 2 3 4 5 6 7 8 9 10
}
```
Step-by-step: i=1 (true, print 1), i=2 (true, print 2),..., i=10 (true, print 10), i=11 (false, exit).               

```
for (int i=0; i<5; i++) cout << i << " ";  // 0 1 2 3 4
```
Similar flow.         

Ranges: `for(int i=51; i<=69; i++)` or `i<70` both print 51-69.     

### Break and Continue Keywords
**break**: Exits loop (or switch) immediately.
```
for (int i=1; i<=10; i++) {
    cout << i << " ";
    if (i==5) break;  // Prints: 1 2 3 4 5 (exits before 6)
}
```
Placement matters: Before print → 1 2 3 4; after → 1 2 3 4 5.         

**continue**: Skips rest of current iteration, jumps to update/condition.
- **Iteration**: One full cycle (e.g., i=1 iteration prints/skips for i=1).

```
for (int i=1; i<=5; i++) {
    if (i==4) continue;
    cout << i << " ";  // Prints: 1 2 3 5 (skips i=4 body)
}
```
Skips print for matching i, continues next iteration.           

| Keyword | Effect | Example Output (1-5 loop) |
|---------|--------|---------------------------|
| break (at 3) | Exit entire loop | 1 2 3 |
| continue (at 3) | Skip iteration 3 | 1 2 4 5 |

**Interview Tip**: No mandatory parts in for; `for(;;)` infinite loops. Homework: MCQs on break/continue outputs.     

---

## While Loop in C++

While loops execute a block of code repeatedly as long as a condition remains true. They differ from for loops only in syntax structure, not functionality—both perform initialization, condition checking, logic execution, and updating.

### Converting For Loop to While Loop
A for loop like:
```
for(int i = 1; i <= 5; i = i + 1) {
    cout << i;
}
```
converts to while by moving parts explicitly:
```
int i = 1;  // Initialization outside
while(i <= 5) {  // Condition here
    cout << i;  // Logic inside
    i = i + 1;  // Update inside
}
```
- **Why this works**: For loop's three parts (init; condition; update) map directly—init moves outside, condition becomes while's parameter, logic/update go inside the block.       



This prints 1 2 3 4 5, same as for loop.   

### Dry Run of While Loop
Trace execution step-by-step for `int i = 1; while(i <= 5) { cout << i; i = i + 1; }`:
1. Initialize: i = 1
2. Check: 1 <= 5? **True** → print 1, i = 2
3. Check: 2 <= 5? **True** → print 2, i = 3
4. Check: 3 <= 5? **True** → print 3, i = 4
5. Check: 4 <= 5? **True** → print 4, i = 5
6. Check: 5 <= 5? **True** → print 5, i = 6
7. Check: 6 <= 5? **False** → exit         

**Key mechanism**: Condition checked *before* each iteration (except first entry). Loop body runs only if true; update happens after print but before next check.

## Do-While Loop in C++

Do-while executes the body *at least once*, checking condition *after* the first run. Syntax:
```
int i = 1;
do {
    cout << i;  // Logic first
    i = i + 1;  // Update inside
} while(i <= 5);
```
Converts from for loop similarly: init outside, do {logic; update} while(condition);        

### Dry Run of Do-While Loop
For `int i = 1; do { cout << i; i = i + 1; } while(i <= 5);`:
1. Enter do: print 1, i = 2
2. Check: 2 <= 5? **True** → print 2, i = 3
3. Check: 3 <= 5? **True** → print 3, i = 4
4. Check: 4 <= 5? **True** → print 4, i = 5
5. Check: 5 <= 5? **True** → print 5, i = 6
6. Check: 6 <= 5? **False** → exit           

| Iteration | Action | i Value | Print | Condition Check |
|-----------|--------|---------|-------|-----------------|
| 1         | Do body | 1 → 2  | 1     | 2 <= 5 (True)  |
| 2         | Do body | 2 → 3  | 2     | 3 <= 5 (True)  |
| 3         | Do body | 3 → 4  | 3     | 4 <= 5 (True)  |
| 4         | Do body | 4 → 5  | 4     | 5 <= 5 (True)  |
| 5         | Do body | 5 → 6  | 5     | 6 <= 5 (False) |  

**Critical difference**: First iteration runs *unconditionally* (no pre-check). For `int i = 21; do { cout << i; i++; } while(i <= 5);` prints 21 then exits—body always runs once.      

**Why less preferred**: Unconditional first run can lead to unwanted execution if condition starts false (e.g., invalid inputs).  

## Nested Loops

Loops inside loops: outer loop runs fully for each iteration; inner fully completes before outer updates.

Example (for loop):
```
for(int i = 1; i <= 3; i++) {
    for(int j = 1; j <= 3; j++) {
        cout << i << " " << j;
    }
}
```
**Output**:
```
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3                             
```



**Mechanism**: 
- Outer i fixed during entire inner j cycle (1→3).
- When inner condition false, execution jumps to outer's update/condition.
- Total iterations: outer(3) × inner(3) = 9     

Multiplication example:
```
for(int i=1; i<=2; i++)
    for(int j=1; j<=2; j++)
        cout << i*j;
```
Output: 1 2 2 4 (1*1, 1*2, 2*1, 2*2)                    

Nested works identically in while/do-while—inner completes per outer iteration.  

## Homework Practice Problems
Implement using any loop (for/while/do-while):
- Print 1 to 100
- Print 100 to 1
- Print your name 50 times
- Print 0 to -10
- Print 7's table (7 14... 70)
- Print A-Z (uppercase)
- Print a-z (lowercase)     

For chars: `for(char ch = 'A'; ch <= 'Z'; ch++) cout << ch;`  

## Additional Homework Questions
Predict outputs (common interview traps):
1. `for(int i=1; i<=5; i++); cout << i;` (semicolon after for?)   
2. `if(5 <= 10) cout << "Babbar";`   
3. `int i; if(cin >> i) cout << "Hi";` (cin in if condition?)  
4. `if(cout << "Hi")` (cout in if?)   

## Break and Continue in All Loops
- **break**: Exits innermost loop immediately.
- **continue**: Skips rest of current iteration, proceeds to next (checks condition again).   Applies same to for/while/do-while/nested.

## Unary Operators: Pre vs Post Increment/Decrement

**Definition**: Unary operators (++ or --) act on one operand (variable).

| Type | Position | Rules | Example |
|------|----------|--------|---------|
| Pre-increment (++a) | Before | 1. Increment first<br>2. Then use/access | `int a=5; cout << ++a;` → prints 6 (a now 6)           |
| Post-increment (a++) | After | 1. Use/access first<br>2. Then increment | `int a=5; cout << a++;` → prints 5 (a now 6)     |
| Pre-decrement (--a) | Before | 1. Decrement first<br>2. Then use | `int a=10; cout << --a;` → prints 9      |
| Post-decrement (a--) | After | 1. Use first<br>2. Then decrement | `int a=7; cout << a--;` → prints 7 (a now 6)     |

**In loops**: Replace `i = i + 1` with `i++` or `++i` (same effect); `i = i - 1` with `i--` or `--i`.    

**Why matters**: Order affects value returned/printed—pre changes before use, post after. Practice MCQs for interviews.     

Binary operators (e.g., +, -, *, /) covered next, but focus here on unary for loop efficiency.  

---

## Unary Operators

Unary operators operate on a single operand, modifying its value. The key distinction is **pre** (modify first, then use) vs **post** (use first, then modify). Always remember these rules: pre-increment/decrement changes value before printing/using; post does it after.

Example code demonstrates:
- `int a = 5; cout << a;` → prints 5 (original value)   
- `cout << ++a;` → pre-increment: increments to 6 first, prints 6  
- `cout << a++;` → post-increment: prints 6 first, then increments to 7   
- Verify: `cout << a;` → prints 7  

For decrement:
- `cout << --a;` → pre-decrement: decrements to 6 first, prints 6  
- `cout << a--;` → post-decrement: prints 6 first, then decrements to 5   

| Operator | Pre (e.g., ++a, --a) | Post (e.g., a++, a--) |
|----------|----------------------|-----------------------|
| Increment | Modify first, use new value | Use old value, modify after |
| Decrement | Modify first, use new value | Use old value, modify after |     

## Arithmetic Operators

Perform basic math: `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division), `%` (modulus/remainder).

```cpp
int a = 10, b = 5;
cout << a + b << endl;  // 15
cout << a - b << endl;  // 5
cout << a * b << endl;  // 50
cout << a / b << endl;  // 2 (integer division truncates)
cout << a % b << endl;  // 0 (remainder)    
```

**Integer Division Pitfall**: `5 / 2` → 2 (truncates decimal, discards 0.5). Avoid `%` on floats (resource-heavy, prefer integers).    

**Fix for Floating-Point Results**:
- Use float: `5.0 / 2` → 2.5  
- Cast: `5 * 1.0 / 2` → 2.5 (implicit float conversion)  

Type casting (int-to-float etc.) covered in separate article—converts data types for correct results.    

![Arithmetic Operator Flow](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/Arithmetic%20Operator%20Flow.png)

## Relational Operators

Compare values, return **true** (1) or **false** (0) for conditions.

| Operator | Meaning | 10? 5 | 5? 10 |
|----------|---------|--------|--------|
| `>` | Greater than | true (1) | false (0)   |
| `<` | Less than | false (0) | true (1)   |
| `>=` | Greater/equal | true (1)   | false (0) |
| `<=` | Less/equal | false (0)   | true (1) |
| `==` | Equal | false (0)   | false (0) |
| `!=` | Not equal | true (1)   | true (1) |         

**Mechanism**: Evaluates relation; true if condition holds (e.g., 10 > 5 is true because 10 exceeds 5).

## Logical Operators

Combine multiple conditions into one master condition.

| Operator | Symbol | Rule | Example Output |
|----------|--------|------|---------------|
| AND (`&&`) | All true →

---

## Number Systems Fundamentals

Number systems represent quantities using specific sets of symbols (digits) and a base, which defines the number of unique symbols used. The **decimal system** (base-10) uses 10 symbols (0-9); for example, 15 means 1×10¹ + 5×10⁰ = 15.    The **binary system** (base-2) uses only 2 symbols: 0 and 1. Combinations of these represent any quantity, like 5 as 101 (1×2² + 0×2¹ + 1×2⁰ = 5).   

Binary is essential because computers (CPU and memory) operate exclusively in binary. CPU registers and storage use bits—grids that represent "off" (0, 0 volts) or "on" (1, e.g., 5 volts from DC battery)—to store and compute data.         Decimal is a human-friendly display; internally, even `int n = 5;` stores as binary (e.g., 101 for 5, padded in 4-byte int as 32 bits with leading zeros).    

| Counting Example | Decimal | Binary |
|------------------|---------|--------|
| 0                | 0       | 0      |
| 1                | 1       | 1      |
| 2                | 2       | 10     |
| 3                | 3       | 11     |
| 4                | 4       | 100    |  

![Binary Vs Decimal](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/Binary%20vs%20Decimal.png)

## Decimal to Binary Conversion

**Method 1: Division Method**. Repeatedly divide by 2, record remainders (bits), read from bottom-to-top.

Example: 10 (decimal)  
10 ÷ 2 = 5 rem **0**  
5 ÷ 2 = 2 rem **1**  
2 ÷ 2 = 1 rem **0**  
1 ÷ 2 = 0 rem **1**  
Read remainders bottom-up: **1010** (1×2³ + 0×2² + 1×2¹ + 0×2⁰ = 10).      

**Code Implementation** (C++ skeleton):
```cpp
int decimalToBinary(int n) {
    int binaryNum = 0, i = 0;
    while (n > 0) {
        int bit = n % 2;  // Extract bit
        binaryNum += bit * pow(10, i);  // Build reversed decimal representation
        n /= 2;
        i++;
    }
    return binaryNum;  // Outputs 1010 as integer 1010
}
```
This builds the binary as an integer by multiplying bits by powers of 10 (reverses naturally).     

**Method 2: Bitwise Operations** (faster, interview-preferred). Use `n & 1` for least significant bit (LSB), right-shift (`>> 1`) to move next bit.

Example for 10 (binary 1010):  
- 1010 & 0001 = **0** (LSB), n >> 1 → 0101  
- 0101 & 0001 = **1**, n >> 1 → 0010  
- 0010 & 0001 = **0**, n >> 1 → 0001  
- 0001 & 0001 = **1**, n >> 1 → 0000  
Bits: 0,1,0,1 → reverse to 1010.       

**Code**:
```cpp
int decimalToBinaryBitwise(int n) {
    int binaryNum = 0, i = 0;
    while (n > 0) {
        int bit = n & 1;
        binaryNum += bit * pow(10, i);
        n >>= 1;  // Right shift
        i++;
    }
    return binaryNum;
}
```
Both methods yield same result (e.g., 23→10111, 17→10001). Bitwise is faster as CPU natively handles bits.    

![Decimal Vs Binary](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/Decimal%20to%20Binary%20Process.png)

## Binary to Decimal Conversion

Multiply each bit by its place value (powers of 2, right-to-left starting at 2⁰), sum them.

Example: 10110 (binary) = 0×2⁰ + 1×2¹ + 1×2² + 0×2³ + 1×2⁴ = 0+2+4+0+16 = 22.      
23 (10111) = 1×2⁰ + 1×2¹ + 1×2² + 0×2³ + 1×2⁴ = 1+2+4+0+16 = 23.  

**Code** (division-based, extracts LSB via %10):
```cpp
int binaryToDecimal(int n) {  // n as integer, e.g., 10110
    int decimal = 0, i = 0;
    while (n > 0) {
        int bit = n % 10;  // LSB
        decimal += bit * pow(2, i);
        n /= 10;
        i++;
    }
    return decimal;
}
```
Dry run for 1010: bits 0(×1)+1(×2)+0(×4)+1(×8)=10.      

**Homework**: Implement binaryToDecimal using bitwise (&1, >>1) instead of %10—extract bits without division.    

## Type Casting Introduction

**Type casting** converts a variable's data type (e.g., char to int, int to float). Needed for operations mixing types (e.g., char + int).       Two types: **implicit** (automatic by compiler) and **explicit** (manual).

**Implicit (Automatic)**: Compiler promotes to "larger" type (more precision) to avoid data loss.  
- int (10) + float (5.5) → float (10.0 + 5.5 = 15.5). Storing 15.5 in int truncates to 15 (precision loss).         
- char 'A' (ASCII 65) + int 1 → int 66. Printing int 66 as char → 'B'.        
- int 97 assigned to char → 'a' (ASCII 97).    

| Scenario | Original Types | Promoted To | Result | Notes |
|----------|----------------|-------------|--------|-------|
| int + float | int(10), float(5.5) | float | 15.5 | Precision preserved   |
| char + int | char('A'=65), int(1) | int | 66 | ASCII conversion   |
| int to char | int(97) → char | char | 'a' | ASCII mapping   |    

Compiler prioritizes larger types (float > int > char) for addition/multiplication to maintain precision—no truncation unless storage forces it.   

---

## Explicit Type Conversion (Casting)

Explicit type conversion, also called manual or C-style casting, allows programmers to specify the desired data type during assignment or operations using casting operators (parentheses with type name). Unlike implicit (automatic) conversion where the compiler decides based on precision (e.g., int promotes to float in `int + float`), explicit casting forces a type change, often truncating data and risking loss of precision.     

### Key Mechanism
- Syntax: `(target_type)variable` or `(target_type)expression`.
- Forces the variable/expression into the specified type before operation.
- Common in mixed-type operations to control promotion or truncation.

**Example: int + float → Force float to int**
```cpp
int num1 = 10;
float num2 = 5.5;
float result = num1 + (int)num2;  // (int)num2 truncates 5.5 → 5
```
- `num2` (5.5) casts to 5 (decimal discarded).
- Now `10 + 5 = 15` (int result).
- Stored in float: `15.0` (precision lost forever).           

![Explicit Type Conversion (Casting)](https://github.com/Coddiction-101/cpp-essentials.co/blob/main/Diagrams/Decimal%20to%20Binary%20Process.png)

**Why truncation?** Lower-precision types (int, char) discard decimals; no rounding—always floor toward zero.   

### Examples Across Types

| From Type | To Type | Value | Result | Explanation |
|-----------|---------|-------|--------|-------------|
| double | int | π (3.14159...) | 3 | Decimal precision truncated    |
| float | char | 65.35 | 'A' | Truncate to 65; ASCII 65 = 'A' (chars behave like ints via ASCII)      |
| char | int | 'A' | 65 | ASCII value extracted    |
| int | char | 66 (from 'A'+1) | 'B' | int → ASCII char    |

**ASCII Note:** Chars are integers (e.g., 'A'=65). `char ch = 'A'; int val = ch + 1;` → 66 → stores as 'B' in char. Google "ASCII table" for values.   

## Integer Division Pitfalls and Fixes

**Core Rule:** `int / int` always returns `int` (truncates decimal, e.g., 10/3=3, ignores 0.333). CPU computes full float but discards for int result.      

**Example Issue:**
```cpp
int a = 10, b = 3;
float c = a / b;  // 10/3 → 3 (int), then 3 → float (3.0, not 3.333)
```
- Both operands int → int division → truncate → store in float.         

| Division Type | Returns | Example (10/3) |
|---------------|---------|----------------|
| int / int | int | 3 |
| int / float or float / int | float | 3.333...     |

**Fixes (Without Changing Variable Types):**
1. Cast one operand: `float c = a / (float)b;` → int/float → float (3.333).   
2. Cast numerator: `float c = (float)a / b;` → float/int → float.    

**Warning:** Even with float result, storing in int truncates via implicit conversion.     

## Functions in C++

Functions group multiple lines of code into a reusable entity that takes input (parameters), processes it, and optionally returns output—like an "atta chakki" (wheat mill): wheat in → grinds → flour out.     

**Definition:** Function = named block of code (segment) for repeated tasks, improving:
- **Reusability:** Write once, call many times (avoids copy-paste bloat).
- **Readability:** `printCounting()` clearly signals intent.
- **Maintainability:** Fix bugs in one place.
- **Debugging:** Isolate/modularize code (modular programming).           

**Problem Without Functions:** Copy-pasting counting loop multiple times → bulky, buggy (e.g., missed semicolon propagates), hard to maintain.     

### Function Anatomy
1. **Return Type:** `int`, `float`, `void` (no return). Non-void returns value via `return` keyword.   
2. **Name:** Intuitive (e.g., `printCounting`, `sum`).   
3. **Parameters:** Optional inputs (e.g., `int a, int b`).   
4. **Body:** `{... }` contains logic.   

**Example: Non-Void (Returns int)**
```cpp
int sum(int a, int b) {  // Return int, name sum, params a/b
    int totalSum = a + b;
    return totalSum;
}
// Call: int answer = sum(5, 10);  // 15 stored in answer
```
- Execution: `main` → call → jump to function → compute → return 15 → back to `main`.           

**Example: Void (No Return)**
```cpp
void printMyName() {  // No params, prints "Babbar"
    cout << "Babbar";
}
// Call: printMyName();  // Just call, no storage
```
- Execution: `main` → call → print → end function → back.        



### Declaration vs Definition
- **Declaration (Signature):** Tells compiler "this function exists" (no body). E.g., `int sum(int a, int b);`   
- **Definition:** Full function with body `{... }`.   

**Ordering Rule:** Function call requires declaration **above** the call site (definition counts as declaration). 
- **Way 1:** Define fully before `main`.
- **Way 2:** Declare before `main`, define after.          

**Best Practice:** Always define before use—no reliance on declarations.  

---

## Why Use Functions in C++

Functions encapsulate a segment of code into a single entity that processes inputs (if any) and optionally returns an output, making code reusable, maintainable, readable, and easier to debug. Without functions, code becomes bulky ("bulky"), buggy, and hard to manage—avoiding repetitive variable declarations or logic duplication.   

Functions solve these by:
- **Reusability**: Call the same logic multiple times without rewriting.
- **Modularity**: Isolate bugs to specific functions for easier fixes.
- **Readability**: Intuitive names like `printName10Times` self-document purpose.

**Key Insight**: Every C++ program starts with `int main()`, called by the Operating System (OS). It declares: returns `int` (typically `return 0;` for success), named `main`, takes no parameters initially—OS executes from here.   

## Function Declaration vs Definition

**Declaration** (prototype/signature): Specifies return type, name, and input parameters (types)—tells compiler "this exists" without logic.
```
int getMultiplication(int x, int y, int z);  // Returns int, name: getMultiplication, params: 3 ints
```
**Definition**: Adds body/logic after declaration.
```
int getMultiplication(int x, int y, int z) {
    int result = x * y * z;
    return result;
}
```
**Order Matters**: Declare (or define) **before** calling—compiler checks top-to-bottom. Call after ensures no errors.    

  

Functions use **camelCase** for names (e.g., `getMultiplication`)—search "camel case" for convention.  

## Writing Your First Functions

Demonstrated via examples—**return type** first, then **name**, **parameters** in `()`, **body** in `{}`.

| Function | Return Type | Parameters | Purpose/Logic | Key Learning |
|----------|-------------|------------|---------------|--------------|
| `getMultiplication` | `int` | `int x, int y, int z` | `return x * y * z;` | Multiple params, returns computed int    |
| `printName10Times` | `void` | None | For-loop prints "babbar" 10x: `for(int i=1; i<=10; i++) cout << "babbar";` | No return, intuitive name, no params    |
| `printMultiples` | `void` | `int num` | Prints `num * i` for i=1 to 10 | Single param, uses loop for table    |
| `convertToCelsius` | `int` | `int fahrenheit` | `(fahrenheit - 32) * 5 / 9` (int only, no floats here) | Formula-based conversion     |
| `convertToUpperCase` | `char` | `char c` | `return c - 'a' + 'A';` (lowercase to uppercase trick) | Char param/return    |

**Void Functions**: No return value (`void`)—cannot `return value;` (error), but `return;` exits early (skips remaining code).    

## Function Calling and Arguments vs Parameters

**Calling**: Use **arguments** (actual values) matching parameters (formal placeholders).
```
int answer = getMultiplication(5, 4, 3);  // Arguments: 5,4,3 → stores 60
cout << answer;  // Prints 60   
printName10Times();  // No args/return  
printMultiples(5);  // Arg:5, prints 5's table  
```
- Store non-void returns in matching type variable.
- Avoid poor names like `int m=5;`—use descriptive (e.g., `int number=5;`).  
- **Fahrenheit Example**: `int answer = convertToCelsius(32);` → 0 (verified).   

| Call Type | Example | Store Return? | Args Needed? |
|-----------|---------|---------------|--------------|
| Non-void, multi-param | `getMultiplication(5,4,3)` | Yes (`int ans=`) | Yes (3) |
| Void, no param | `printName10Times()` | No | No |
| Void, single param | `printMultiples(5)` | No | Yes (1) |
| Char return | `char result = convertToUpperCase('k');` | Yes (`char`) | Yes (1)    |

**Arguments** = values passed in call; **Parameters** = variables in definition.   Declaration-before-definition works too.  

## Functions Summary and Benefits Recap

Functions: Code segment taking inputs → processes → outputs (optional). Benefits: Reuse, readable/maintainable, avoids bulk/bugs.   

**Homework** (Practice Creation):
- Print 1-10 counting.
- Simple Interest: Formula (Google: SI = P*R*T/100), params: principal, rate, time → return SI.  
- Print primes 1-100 (loop/check).
- Voting eligibility: Param age → print eligible/not.
- SIP Calculator: Params monthly investment, years, return rate → future value (Google SIP formula).    

## Introduction to Arrays in C++

Arrays store **multiple same-type values** efficiently—instead of 10,000 variables (impractical), declare once: `int arr[10000];`   

**What is an Array?** Data structure for same-type multiples (int, char, float, bool, double) in **contiguous memory blocks** (consecutive addresses).   

**Why Arrays?** Solves variable explosion: 2→3→4→400→1Lakh vars → one array line.   

  

**Declaration**: `int arr[5];`—allocates 5 int blocks (size **must** specify unless initialized).   
**Initialization** (Definition): `int arr[5] = {10,20,30};`—first 3 set, rest garbage. Overflow (6 vals in size-5)? Error.    
- Without size: `int arr[] = {1,2,3};`—infers size 3.  

**Memory Reality**: Contiguous—`int arr[5];` at 104: 104,108,112,116,120 (int=4 bytes). Non-contiguous free space? Allocation fails despite total free (e.g., 10MB fragmented can't fit 6MB array).    

## Accessing Array Elements with Indexes

Arrays indexed **0 to size-1** (n-size: 0..n-1).
```
int multiplesOf2[10] = {2,4,6,8,10,12,14,16,18,20};
cout << multiplesOf2[6];  // 14 (index 6)
```
- Traverse/Print: `for(int i=0; i<10; i++) cout << multiplesOf2[i];`
- Out-of-bounds (e.g., `[33]`)? Warning/error (access invalid memory).     

**Input to Array**:
```
int arr[5];
for(int i=0; i<5; i++) {
    cout << "Enter value for arr[" << i << "]";
    cin >> arr[i];
}
```
Each `arr[i]` acts like a variable—`cin >> arr[3];` inputs to index 3.    

## Array Sum Example (Pre-Function)

Sum array: Initialize `sum=0`, loop `sum += arr[i];`.
```
int arr[] = {10,20,30,40,50};
int sum = 0;
for(int i=0; i<5; i++) sum += arr[i];
cout << sum;  // 150   
```
**Dry Run** (Step-by-step):
- i=0: sum=0+10=10
- i=1: 10+20=30
- i=2: 30+30=60
- i=3: 60+40=100
- i=4: 100+50=150
- i=5: Loop ends, print 150   

This logic sets up passing arrays to functions (next topic).   

---

## Passing Arguments to Functions

Functions in C++ accept parameters to perform operations. Single variables pass directly as arguments.

```cpp
int sum(int a, int b) {
    return a + b;
}
int main() {
    int answer = sum(5, 10);  // 5 goes to a, 10 to b  
}
```

Arrays require special handling: pass the array name and its size explicitly, as size information is lost when passed to a function.   

```cpp
void printArray(int arr[], int n) {  // arr[] receives array, n is size
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
}
int main() {
    int arr[] = {10, 20, 30, 40};
    int size = 4;
    printArray(arr, size);  // Pass array name and size    
}
```

**Why pass size?** Arrays decay to pointers in functions, losing size metadata—must provide it manually to avoid out-of-bounds access.   Loop from `0` to `n-1` for zero-based indexing.  

## Array Initialization with Zeros

Declare and initialize arrays to zero or a value:

```cpp
int arr[5] = {0};  // All elements become 0  
printArray(arr, 5);  // Outputs: 0 0 0 0 0  
```

Partial initialization fills remainder with zeros:
```cpp
int arr[5] = {-1};  // Outputs: -1 0 0 0 0   
```

Pure declaration without values yields garbage:
```cpp
int arr[5];  // Garbage values, e.g., 1, random    
```

**Mechanism:** Compiler auto-fills uninitialized slots with 0 only if at least one value provided; otherwise, memory contains undefined garbage.  

## Storing Multiples in Array (10's Table)

Create function to fill array with multiples:

```cpp
void storeMultiplesOf10(int arr[], int n) {
    int count = 1;
    for(int i = 0; i < n; i++) {
        arr[i] = 10 * count;
        count++;  // Increment multiplier   
    }
}
int main() {
    int arr[10];
    storeMultiplesOf10(arr, 10);
    printArray(arr, 10);  // 10 20 30... 100  
}
```

**Dry run trace (n=10):**
- `i=0`, `count=1`: `arr[0]=10*1=10`, `count=2`
- `i=1`, `count=2`: `arr[1]=10*2=20`, `count=3`
- Continues to `arr[9]=100`            

**Why increment count after store?** Ensures sequential multiples (1→10, 2→20, etc.); count drives the pattern while index fills positions.   

| Iteration | i | count (pre) | arr[i] | count (post) |
|-----------|---|-------------|--------|--------------|
| 0         | 0 | 1           | 10     | 2            |
| 1         | 1 | 2           | 20     | 3            |
| 2         | 2 | 3           | 30     | 4            |
|...       | 9 | 10          | 100    | 11           |  

## Flip 0s and 1s in Array

Invert binary array (0→1, 1→0):

```cpp
void flip01(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        if(arr[i] == 1) arr[i] = 0;
        else arr[i] = 1;  // Or: arr[i] = 1 - arr[i];  
    }
}
int main() {
    int arr[] = {1,1,0,0,1,0,1};
    printArray(arr, 7);  // Before: 1 1 0 0 1 0 1
    flip01(arr, 7);
    printArray(arr, 7);  // After: 0 0 1 1 0 1 0   
}
```

**Logic:** Traverse once; conditional swap based on current value (assumes only 0/1).  

## 2D Arrays (Rows and Columns)

2D arrays represent matrices with rows and columns (like graphs with x/y axes).  

**Declaration:**
```cpp
int arr[3][4];  // 3 rows, 4 columns   
```

**Initialization:**
```cpp
int arr[2][4] = {
    {1,2,3,4},   // Row 0
    {5,6,7,8}    // Row 1   
};
```

**Access:** `arr[row][col]` (zero-based).
- `arr[1][2]` → 7 (row 1, col 2)  
- `arr[3][0]` → row 3, col 0  

**Print with nested loops:**
```cpp
int rows = 3, cols = 4;
for(int i = 0; i < rows; i++) {      // Outer: rows
    for(int j = 0; j < cols; j++) {  // Inner: cols
        cout << arr[i][j] << " ";
    }
    cout << endl;
}      
```

**Input similarly:** Replace `cout` with `cin` in same loops.   

| Equivalent Loop Conditions | Effect |
|----------------------------|--------|
| `i <= rows-1` or `i < rows` | Same: 0 to rows-1    |
| `j <= cols-1` or `j < cols` | Identical range   |

## Passing 2D Arrays to Functions

Pass array, row size, **and column size** (column size required in signature):

```cpp
void print2DArray(int arr[][4], int rowSize, int colSize) {  // cols fixed   
    for(int i = 0; i < rowSize; i++) {
        for(int j = 0; j < colSize; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }
}
int main() {
    int arr[3][4] = {{10,20,30,40},{11,12,13,14},{21,22,23,24}};
    print2DArray(arr, 3, 4);  
}
```

**Why specify columns?** 2D array decays to pointer-to-array; compiler needs column count for memory layout.    Homework: Research why rows optional.  

## Zero-Based Indexing Reminder

Arrays use **zero-based indexing**: size `n` → indices `0` to `n-1`.   

```cpp
int arr[7];  // Valid: arr[0] to arr[6]  
for(int i = 0; i < 7; i++) { /* or i <= 6 */ }   
```

## Character Arrays

Character arrays store chars in contiguous memory (1 byte each vs. int's 4 bytes).    Must end with **null terminator** `\0` (ASCII 0) to mark end.   

**Declaration:**
```cpp
char arr[10];  // Garbage if uninitialized   
cout << arr[3];  // Random char  
```

**Initialization:**
```cpp
char arr[10] = "Babbar";  // Auto-adds \0; "Babbar\0"  
```

**ASCII Values:** Chars map to numbers (e.g., 'a'=97, 'A'=65).    Arithmetic works:
- `'a' + 'b'` → 97+98=195  
- Case convert: `ch = ch - 'a' + 'A';` ('a'→'A')   
- Upper→lower: `ch = ch - 'A' + 'a';`  

**Null terminator printing:** `cout` stops at `\0`.   Homework: Search ASCII table.  

---

## Character Arrays in C++

Character arrays store sequences of characters and differ from integer arrays in initialization and behavior. Unlike integer arrays requiring individual element assignment (e.g., `arr[0] = 1; arr[1] = 2;`), character arrays can be initialized directly with a string literal.  

```cpp
char arr[10] = "babbar";  // Stores 'B','A','B','B','A','R' automatically
```

This creates 6 characters followed by a **null character** (`\0`, ASCII value 0) at index 6, terminating the sequence. Access works like regular arrays: `arr[1]` prints `'A'`, `arr[5]` prints `'R'`.     Null character verification:

```cpp
int s = arr[6];  // s = 0 confirms null terminator
cout << s;  // Prints 0  
```

Manual null insertion is possible: `arr[2] = '\0';`. Without it, `cout << arr;` prints garbage beyond the string.   

**Key Differences from Integer Arrays:**
| Aspect | Integer Array | Character Array |
|--------|---------------|-----------------|
| Initialization | Individual assignments required | Direct string literal allowed   |
| `cout << arr` | Prints base address (e.g., 104)   | Prints characters until `\0` (e.g., "babbar")    |
| Traversal | Manual loop always needed | Direct `cout` or loop   |

Null character (`\0`) marks **string termination**, preventing buffer overflow reads.   

  

Loop traversal mirrors integer arrays: `for(int i=0; i<5; i++) cout << arr[i] << " ";`.  

## Manual Operations on Character Arrays (Two-Pointer Approach)

Common operations use null termination for bounds. Implement using two indices (two-pointer technique).   

### 1. Length Calculation
Count characters until `\0` (excludes null).

```cpp
int getLength(char arr[]) {
    int count = 0, index = 0;
    while(arr[index]!= '\0') {
        count++;
        index++;
    }
    return count;  // Returns 6 for "babbar"  
}
```

**Dry Run Visualization** for `char arr[] = "babbar\0";`:

| Iteration | index | arr[index] | count | Action |
|-----------|-------|------------|-------|--------|
| 0 | 0 | 'B' | 0→1 | ++ |
| 1 | 1 | 'A' | 1→2 | ++ |
| 2 | 2 | 'B' | 2→3 | ++ |
| 3 | 3 | 'B' | 3→4 | ++ |
| 4 | 4 | 'A' | 4→5 | ++ |
| 5 | 5 | 'R' | 5→6 | ++ |
| 6 | 6 | '\0' | 6 | Stop, return 6   |

Space counts as a character.  

### 2. Concatenation
Append `src` to `dest` (modifies `dest`, assumes sufficient size).

```cpp
void concatArrays(char dest[], char src[]) {
    int destIndex = getLength(dest);  // e.g., 4 for "love"
    int srcIndex = 0;
    while(src[srcIndex]!= '\0') {
        dest[destIndex++] = src[srcIndex++];
    }
    dest[destIndex] = '\0';  // Terminate   
}
```

**Step-by-step** for `dest="love"`, `src="babbar"`:
1. `destIndex=4` (after `\0`)
2. Copy `b-a-b-b-a-r`, increment both indices
3. Add `\0` → "lovebabbar"  

### 3. Copying
Copy `source` to `destination`.

```cpp
void copyArray(char source[], char dest[]) {
    int sIndex = 0, dIndex = 0;
    while(source[sIndex]!= '\0') {
        dest[dIndex++] = source[sIndex++];
    }
    dest[dIndex] = '\0';
}
```

Same two-pointer logic as concatenation but starts both at 0.   

### 4. Comparison
Check if identical until shortest null terminator.

```cpp
bool compareArrays(char a[], char b[]) {
    int i = 0, lenA = getLength(a);
    while(i <= lenA && a[i] == b[i]) {  // Handles length diff  
        i++;
    }
    return i > lenA;  // True if all matched  
}
```

**Cases Handled:**
| Case | a | b | Result | Reason |
|------|---|----|--------|--------|
| Equal | "love" | "love" | true | All chars match   |
| Diff char | "kove" | "love" | false | Mismatch at index 0   |
| Diff length | "love" | "lovebabbar" | false | `i <= lenA` exits early   |
| Reverse length | "lovebabbar" | "love" | false | Same   |

## Library Functions (<cstring>)

Include `<cstring>` for built-ins (prefer for production, implement manually for interviews).  

| Function | Purpose | Syntax | Return/Behavior |
|----------|---------|--------|-----------------|
| `strcpy(dest, src)` | Copy | `strcpy(answer, actual);` | Copies until `\0`   |
| `strlen(arr)` | Length | `strlen(actual);` | Chars before `\0` (6 for "babbar")   |
| `strcmp(a, b)` | Compare | `strcmp(actual, answer);` | 0=equal, <0/ >0=not    |
| `strcat(dest, src)` | Concat | `strcat(dest, src);` | Appends to dest   |

**strcmp Dry Run** `strcmp("babbar", "babbar")` → 0 (equal). Non-zero for mismatch.  

**Common Error**: Direct modification like `actual = "love";` fails ("expression must be modifiable"). Use index: `actual[0] = 'l';`.  

## std::string (C++ Strings)

`std::string` (include `<string>`) is a **dynamic class** wrapping character sequences with automatic null handling and resizing.  

**Declaration & Initialization:**
```cpp
#include <string>  // Often auto-included
string name = "babbar";  // Dynamic size, auto \0  
```

**Key Advantages over char arrays:**
| Feature | char[] | std::string |
|---------|--------|-------------|
| Size | Fixed (e.g., 100)   | Dynamic (auto-resizes)   |
| Null handling | Manual   | Automatic   |
| Modification | Index-only, error-prone | Direct: `name = "love";`   |
| Safety | Unsafe (buffer overflow risk) | Bounds-checked   |

**push_back Example** (no manual `\0` needed):
```cpp
string name;
name.push_back('a');  // "a"
name.push_back('b');  // "ab"
name.push_back('c');  // "abc" (auto \0 internally)
cout << name;  // Prints "abc"  
```

Char arrays may print garbage without explicit `\0`, but `std::string` always handles safely.  

**Behavior Consistency**: Traversal, printing identical to char arrays. `.length()` gives size.   Library functions like `.push_back()`, `.pop_back()`, `.find()` available via cppreference.  

---

## Common C++ String Library Functions

C++ strings provide built-in member functions for efficient manipulation, building confidence through hands-on usage. These functions operate on `std::string` objects, which manage dynamic character arrays with null termination.   

### Length Retrieval
- Use `str.length()` or `str.size()` to get the number of characters.
- Example: `string str = "babbar"; cout << str.length();` outputs `6` (B-A-B-B-A-R).   

### Appending Strings
- `str.append(temp)` concatenates `temp` to the end of `str`, modifying `str` in place.
- Mechanism: Appends characters of `temp` sequentially after `str`'s content, updating length.
- Example: `string str = "babbar"; string temp = "love"; str.append(temp);` results in `"babbarlove"`.    

### Inserting Strings
- `str.insert(position, temp)` inserts `temp` at the specified index (0-based), shifting existing characters right.
- Why it works: Strings are resizable; insertion reallocates if needed and copies characters.
- Examples:
  | Position | Original `str` | `temp` | Result          |
  |----------|----------------|--------|-----------------|
  | 0        | "babbar"       | "love" | "lovebabbar"   |
  | 3        | "babbar"       | "love" | "bablovebar"   |       

### Extracting Substrings
- `str.substr(pos, len)` returns a new string starting at `pos` for `len` characters (or to end if `len` omitted).
- Mechanism: Copies specified range without modifying original; efficient for views but creates copy.
- Examples for `string str = "statement";` (indices: s0 t1 a2 t3 e4 m5 e6 n7 t8):
  | pos | len | Result |
  |-----|-----|--------|
  | 3   | 3   | "tem"  |
  | 5   | 4   | "ment" |
  | 0   | 9   | "statement" |       

### Comparing Strings
- `str.compare(other)` returns:
  - 0 if equal.
  - <0 if `str` lexicographically before `other` (ASCII order).
  - >0 otherwise.
- Use: `if (s1.compare(s2) == 0) cout << "Equal";`
- Example: `"love".compare("love")` → 0; `"love".compare("lovf")` → <0 (e before f).         

### Finding Substrings
- `str.find(sub)` returns first occurrence index of `sub` or `string::npos` if not found.
- `string::npos` is a large value (often -1 as `size_t`), signaling "no position."
- Mechanism: Scans sequentially; use to check existence or locate.
- Example:
  ```cpp
  string a = "my name is love babbar not babar";
  string b = "love";
  size_t pos = a.find(b);  // Returns 11
  if (pos == string::npos) cout << "Not found"; else cout << "Found at " << pos;
  ```
  - "lover" → `npos`, prints "Not found."                    

## Strings vs Character Arrays
Both access via indices (`str[0]`, `arr[0]`), but differ in declaration, null handling, and manual operations.

| Aspect          | String (`std::string`)                  | Character Array (`char[]`)             |
|-----------------|-----------------------------------------|----------------------------------------|
| Declaration    | `string s = "hello";`                  | `char arr[] = "hello";`               |
| Initialization | Automatic size/length management       | Fixed size; manual null `\0`          |
| Access         | `s[0]` resizes dynamically             | `arr[0]` fixed; overflows possible    |
| Length         | `s.length()`                           | Manual loop to `\0`                   |
| Comparison     | `s1.compare(s2)`                       | `strcmp(arr1, arr2)`                  |
| Copy/Concat    | Library functions                      | Manual loops (like earlier `mstrlen`, `mstrcmp`)    

Manual functions (length, compare, copy, concat) work identically on both; strings add convenience.  

## Reversing Strings
- `reverse(str.begin(), str.end());` swaps characters from start to end iterators.
- Example: `"love"` → `"evol"`. Use for palindrome checks: compare original to reversed.   

## Practice Problems
Implement manually to build intuition:
- Reverse a string.
- Count vowels/consonants (vowels: a,e,i,o,u; subtract from length).
- Valid anagram (sort/compare frequencies).
- Convert case (upper/lowercase).
- String to integer (e.g., "123" → 123).      

## Reference Variables
Reference variables provide an alias to an existing variable, accessing the **same memory location** with a different name. Declared with `&`.

- Syntax: `int& ref = var;` — `ref` aliases `var`.
- Changes via `ref` or `var` affect the same data.
- Why? Efficiency: No copy; same address.

Example execution trace (`int a = 5; int& temp = a;`):
| Operation     | Value of `a`/`temp` |
|---------------|---------------------|
| Initial       | 5                   |
| `temp++`      | 6                   |
| `temp = 10*10`| 100                 |
| `temp--`      | 99                  |
| `a++`         | 100                 |
| `a -= 5`      | 95                  |                 

**Key Insight**: `Same memory location can be used with different names.`  

## Pass by Value vs Pass by Reference

### Pass by Value (Default)
- **Copies** argument's value into function's local parameter (new memory).
- Changes inside function **do not affect** original.
- Mechanism: Each function has isolated stack frame; copy ensures isolation.

Examples (int/char/string):
| Type  | main print | func entry print | func modify print | main after print |
|-------|------------|------------------|-------------------|------------------|
| int (5)     | 5         | 5                | 6                 | 5                |
| char ('K')  | K         | K                | L                 | K                |
| string ("love") | love  | love             | bov               | love             |                                          

### Pass by Reference (`&`)
- **No copy**: Parameter aliases original (same memory).
- Changes **persist** after function returns.
- Syntax: `void solve(int& a)` or `void solve(int& arr)` (different name ok).

Examples:
| Type  | main print | func entry print | func modify print | main after print |
|-------|------------|------------------|-------------------|------------------|
| int (50)    | 50        | 50               | 51                | 51               |
| char ('K')  | K         | K                | L                 | L                |
| string ("love") | love  | love             | babbar            | babbar           |                                              

**When to Use**:
- **Value**: No changes needed (safe, isolated).
- **Reference**: Sustain changes in caller (efficient for large data like arrays/strings).       

  

**Practical**: For array `arr[] = {1,2,3,4,5}` and `count=0`, pass `count` by reference to `countEvenNumbers` to update caller's `count`.   

---

## Counting Even Numbers in an Array

To count even numbers in an array like `{1, 2, 3, 4, 5}`, initialize a counter to 0 and pass the array, its size (5), and counter to a function. The function traverses the array with a for loop (`for(int i = 0; i < size; i++)`) and checks if `arr[i] % 2 == 0`. If true, increment the counter (`count++`).    

**Key Issue with Pass-by-Value:**  
Printing the counter after the function call shows 0 because `count` is passed by value—a copy is made inside the function. Changes affect only the local copy, not the original.    

```cpp
void countEvenNumbers(int arr[], int size, int count) {
    for(int i = 0; i < size; i++) {
        if(arr[i] % 2 == 0) count++;  // Modifies local copy only
    }
}
```
**Result:** Original `count` remains 0.  

**Solution: Pass-by-Reference**  
Use `int& count` to pass the address of the original variable. Changes directly modify the caller's `count`, yielding 2 (for 2 and 4).  

```cpp
void countEvenNumbers(int arr[], int size, int& count) {  // Reference parameter
    for(int i = 0; i < size; i++) {
        if(arr[i] % 2 == 0) count++;  // Modifies original
    }
}
```

| Parameter | Pass-by-Value | Pass-by-Reference |
|-----------|---------------|-------------------|
| **Array** | Always decays to pointer (starting address); no copy of entire array    | Same as value (pointer) |
| **int size** | Copy made; local changes lost   | Requires `int&` for original modification |
| **Effect** | Function-local changes discarded | Persists to caller   |

**Why Array is Pass-by-Reference:** Arrays decay to pointers (`arr` holds starting address). `sizeof(arr)` inside function gives pointer size (e.g., 8 bytes), not array size (20 bytes). Verify by printing `sizeof(arr)` in main vs. function.    

## Pointer Fundamentals

Pointers are variables that store **memory addresses** (not data values). Like `int a = 5` allocates a 4-byte integer at some address (e.g., 104) holding 5, `int* ptr` declares a pointer variable for integer addresses.   

**Proper Declaration:** Always initialize to null (`int* ptr = nullptr;`) to avoid undefined behavior. Uninitialized pointers cause crashes (null pointer exception).    

**Creation and Initialization:**
1. `int num = 50;` → Allocates `num` at address 104 (stack).
2. `int* ptr = &num;` → `&` (address-of operator) gets 104; `ptr` stores it.   

  

**Key Operators:**
- `&var`: Address of `var`.
- `*ptr`: Dereference—value at address in `ptr` (e.g., `*ptr == 50`).   
- `ptr`: Prints address stored in `ptr`.
- `&ptr`: Address of pointer itself.

| Print Statement | Output (example) | Meaning |
|-----------------|------------------|---------|
| `num` | 50 | Value in `num`   |
| `&num` | 104 | Address of `num`   |
| `ptr` | 104 | Address stored in `ptr`   |
| `&ptr` | 212 | Address of `ptr`   |
| `*ptr` | 50 | Value at `ptr`'s address   |

**Modification via Pointer:** `*ptr++` or `(*ptr)++` increments value at address (50 → 51). Use parentheses to avoid precedence issues (`*` binds tighter than `++`).   

## Dynamic Memory Allocation (Heap vs. Stack)

C++ programs get two memory regions:
- **Stack**: Fixed-size (e.g., few KB-MB), automatic allocation for locals (e.g., `int a = 5`). Fast but limited.   
- **Heap**: Dynamic, grows until virtual memory limit. For runtime-sized data.   

**Why Heap/Pointers?** Stack can't handle variable/large sizes (e.g., `int arr[n]` with `n=1e9` fails). Heap via `new` returns address (stored in pointer).    

**Single Object:**
```cpp
int* ptr = new int;  // Allocates int on heap (uninitialized/garbage)
*ptr = 5;            // Assign value
cout << *ptr;        // 5
delete ptr;          // Free (manual deallocation—no GC in C++)   
```

**Array:**
```cpp
int* ptr = new int[5];       // Heap array of 5 ints, ptr holds start address
ptr[0] = 10;                 // Or *(ptr + 0)
*(ptr + 1) = 20;             // Pointer notation equivalent
for(int i = 0; i < 5; i++) cout << ptr[i];  // Traverses like static array
delete[] ptr;                // [] for arrays    
```

| Allocation | Syntax | Deallocation | Use Case |
|------------|--------|--------------|----------|
| **Single** | `new int` | `delete ptr` | Objects   |
| **Array** | `new int[5]` | `delete[] ptr` | Dynamic arrays   |

**Bad Practice:** `int arr[n]` with runtime `n`—stack overflow risk. Use `int* arr = new int[n];`.   

## Pointer Arithmetic

Pointers support `+`, `-`, `++`, `--` (scaled by type size):
- `*(ptr + 1)`: Address of next element (e.g., int: +4 bytes).  
- Moves by **type size** (int: 4 bytes, char: 1 byte).  

**Example (5-int array at base 104):**
```
ptr     → 104 (ptr[0])
ptr + 1 → 108 (ptr[1])
*(ptr + 1) → Value at 108
```

| Expression | Effect | Example Output (zeros) |
|------------|--------|------------------------|
| `*ptr` | Value at `ptr` (104) | 0   |
| `*ptr + 1` | Value (0) + 1 | 1   |
| `*(ptr + 1)` | Value at next int (108) | 0   |

**Array Access Equivalence:** `ptr[i]` == `*(ptr + i)`. Behind-the-scenes for static arrays too.   

**Uses of Pointers:**
- Dynamic sizing  
- Complex structures (linked lists, trees)  
- Low-level access  
- Arrays always pass as pointers   

References are safer aliases, but pointers enable these advanced features.   

---

## Pointer Arithmetic Operations

Pointer arithmetic adjusts the pointer by the size of the data type it points to, enabling navigation through arrays. For an integer array with `int* ptr` pointing to address 104 (size 4 bytes), `ptr + 1` advances to address 108 because integers occupy 4 bytes—adding 1 moves forward by one integer element. Dereferencing `* (ptr + 1)` accesses the value at 108.       

In contrast, for a character array `char* ctr` (1 byte per char) at address 104 with all 'a' values:
- `* (ctr + 1)` goes to 105, dereferences to 'a' (ASCII 97), but conceptually 'a' + 1 yields 'b' due to char arithmetic treating values as sequential.
- `*(ctr + 3)` reaches 107, still 'a'.    

| Operation | Integer ptr (4 bytes) | Char ctr (1 byte) |
|-----------|-----------------------|-------------------|
| ptr/ctr   | Value at 104 ('a'/5) | Value at 104 ('a') |
| *(ptr/ctr +1) | Value at 108 | Value at 105 ('a') |
| *(ptr/ctr +3) | Value at 116 | Value at 107 ('a') |   

Subtraction works reversely (e.g., `ptr - 1` moves backward). Pointer difference `ptr2 - ptr1` yields the number of elements between them, useful for counting array elements or bounds checking.    

## Void Pointers

`void*` is a generic pointer that can point to any data type but requires explicit casting to dereference (e.g., `*(int*)voidPtr`). Its use cases include flexible memory management like `malloc` returns. **Homework**: Create examples and comment use cases.   

## Double and Multi-Level Pointers

Multi-level pointers point to other pointers, dereferencing level-by-level with successive `*`.

Example setup:
```
int a = 5;      // Address 188, value 5
int* ptr = &a;  // Address 180, value 188
int** ctr = &ptr; // Address 178, value 180
int*** dtr = &ctr; // Address 170, value 178
```
  
Printing verifies: `a` → 5, `&a` → 188, `ptr` → 188, `*ptr` → 5, `ctr` → 180, `*ctr` → 188, `**ctr` → 5, etc. Attempting `*a` errors as `a` is not a pointer. Addresses are illustrative; logic holds regardless.                      

## Classes and Objects Fundamentals

**Class**: User-defined data type or blueprint defining data members (properties like age, weight) and member functions (behaviors like running, studying). Empty class occupies 1 byte.             

**Object**: Actual instance of class (reality from blueprint), e.g., mouse from mouse blueprint.     

Example `Student` class:
```
class Student {
public:
    int age, weight, height;
    string name;
    void running() { cout << "I am running" << endl; }
    void studying() { cout << name << " is studying" << endl; }
};
```
Size ≈12-40 bytes (padding affects; ask in advanced sessions).                   

**Static Object Creation** (stack): `Student s1; s1.age = 50; s1.running();` — uses dot (`.`) operator.         

**Dynamic Object Creation** (heap): `Student* s = new Student();` or `Student* s = new Student(); (*s).age = 50;` or `s->age = 50;` — uses arrow (`->`) or deref+dot. **Homework**: Difference between `new Student()` and `new Student()`.           

## Constructors

Special member function (same name as class, no return type) auto-called on object creation to initialize data members. Replaces manual post-creation setting.       

- **Default/No-Params**: `Student() { cout << "Object initialized"; age=0; }` — called by `Student s;` or `new Student()`.        
- **Parameterized**: `Student(int myAge, int myWeight,...) { age = myAge;... }` — called by `Student s(10,20,...);` or `new Student(10,20,...)`.                

**`this` Pointer**: Resolves ambiguity, points to current object: `this->age = myAge;`.         

**Initializer List** (efficient shorthand): `Student(int myAge,...): age(myAge), weight(myWeight) {}`.         

## Destructors

Special function (`~Student() { cout << "Inside destructor"; }`) auto-called on object deletion (opposite of constructor). Essential for heap objects: `delete s;` triggers it to clean resources. Stack objects auto-clean on scope exit.          

## Homework and Next Steps

- Void pointer examples/use cases.
- `new Student()` vs `new Student()` difference.
- Array of pointers vs pointer to array (StackOverflow/ChatGPT).
- Practice 20-25 pointer problems (reference video).      

Deeper OOP (encapsulation, inheritance, polymorphism, abstraction) and STL covered in follow-up one-shots.
