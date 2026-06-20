# Rust Basics: Variables, Data Types, and Control Flow

I  was studying rust and primary looking at high level syntax and these were my deductions/learnings.

## 1. Printing and Macros

In Rust, `println!` and `print!` are macros (they behave similarly to functions).

* `println!()` inserts a new line at the end of the output.
* `print!()` prints on the same line.

```rust
fn main() {
    println!("hello world..i am surya.");
    print!("Hello World! ");
    print!("I will print on the same line.\n");

    let name = "Suryansh";
    // Rust uses formatted strings(not exactly as it seems just like using format specifier like how  we do in c). Order matters when inserting variables!
    print!("My good name is: {}", name);
}
```

## 2. Variables and Mutability

Variables in Rust are initialized with the `let` keyword and are **immutable** by default. It is not always necessary to define the data type as Rust can automatically infer it, but you can explicitly declare it if needed.

```rust
// Variables are immutable by default
let x = 5;
// x = 10; // This would give an error 
```

## 3. Data Types

The general syntax for explicit typing is:
`let variable_name: variable_type = actual_value;`

### Basic Data Type Groups

* **Numbers (`i32`, `f64`):** Whole numbers and decimal numbers.
* **Characters (`char`):** Single letters or symbols (must be surrounded by single quotes, e.g., `'A'`).
* **Strings (`&str`):** Text, a sequence of characters (must be surrounded by double quotes).
* **Booleans (`bool`):** `true` or `false` values.

```rust
let my_num: i32 = 5;          // Integer (whole numbers, positive or negative)
let my_double: f64 = 5.99;    // Float (contains decimals)
let my_letter: char = 'D';    // Character
let my_bool: bool = true;     // Boolean
let my_text: &str = "Hello";  // String
```

## 4. Constants

Constants store values that *never* change. Unlike regular variables, constants **must** be defined with a type (e.g., `i32`). Use the `const` keyword, followed by the name, type, and value.

```rust
const BIRTHYEAR: i32 = 1980;
const MINUTES_PER_HOUR: i32 = 60;
```

## 5. Operators and Comparisons

Arithmetic operators work similarly to C. Operations must be done on the same data types, and the result will match that type. Comparisons yield boolean values, which can be assigned directly to variables.

```rust
let age = 20;
let can_vote = age >= 18; // Assigns the boolean result of the comparison
println!("Can vote? {}", can_vote);
```

## 6. Control Flow: If-Else

Conditional statements are identical to Python, except that the `elif` block is written as `else if`.

One feature in Rust is the ability to assign an `if-else` block directly to a variable. Note: The return values from all branches must be of the same type. Ensure you include both `if` and `else` blocks so the variable always receives a value.

```rust
let time = 20;

// Multi-line syntax
let greeting = if time < 18 {
    "Good day."
} else {
    "Good evening."
};
println!("{}", greeting);

// Short, one-line syntax
let quick_greeting = if time < 18 { "Good day." } else { "Good evening." };
```

## 7. Control Flow: Match

When handling many choices, `match` is much cleaner than multiple `if...else` statements. The `match` variable is evaluated once and checked against the value of each branch (`=>`).

```rust
let day = 4;

match day {
    1 => println!("Monday"),
    2 => println!("Tuesday"),
    3 => println!("Wednesday"),
    4 => println!("Thursday"),
    5 => println!("Friday"),
    6 => println!("Saturday"),
    7 => println!("Sunday"),
    _ => println!("Invalid day."), // '_' acts as a default catch-all 
}
```

### Multiple Matches

Use the `|` (OR) operator to define multiple matching values in a single branch.

```rust
let day = 6;
match day {
    1 | 2 | 3 | 4 | 5 => println!("Weekday"),
    6 | 7 => println!("Weekend"),
    _ => println!("Invalid day"),
}
```

### Assigning Match to a Variable

Just like `if`, `match` expressions return a value, so the output can be safely stored in another variable.

```rust
let day = 4;
let result = match day {
    1 => "Monday",
    2 => "Tuesday",
    3 => "Wednesday",
    4 => "Thursday",
    5 => "Friday",
    6 => "Saturday",
    7 => "Sunday",
    _ => "Invalid day.",
};

println!("{}", result);
```

## 8. Comments in Rust

* `//` represents a single-line comment.
* `/* ... */` represents a multi-line comment.
