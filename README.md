# JSON Interpreter

A simple yet powerful interpreter that executes JSON files as programs. Write code using familiar JSON syntax and run it with this interpreter!

## Overview

JSON Interpreter is an experimental programming language that uses JSON as its syntax. It allows you to write programs using standard JSON objects, where keys represent commands and values represent their parameters. This project demonstrates how JSON's structured format can be leveraged to create executable code.

## Features

- 🖨️ **Output**: Print text to console with variable interpolation
- 📥 **Input**: Read user input from console
- 🔢 **Variables**: Define and use variables throughout your program
- ⚖️ **Conditionals**: Execute code based on conditions (if statements)
- 🔄 **Loops**: 
  - While loops with condition checking
  - Repeat loops with fixed iterations
- 🔗 **Variable Interpolation**: Reference variables in strings
- 🚪 **Program Control**: Exit program execution

## Prerequisites

- Java Development Kit (JDK) 17 or higher
- Gradle (wrapper included in the project)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/integr-dev/json-compiler.git
cd json-compiler
```

2. Build the project:
```bash
./gradlew build
```

## Usage

### Running a JSON Program

Place your JSON program in the `inputs/` directory and run:

```bash
./gradlew run
```

By default, the interpreter executes `inputs/input.json`.

### Language Syntax

#### Basic Commands

**Print to Console**
```json
{
  "printLn": "Hello, World!"
}
```

**Variables**
```json
{
  "var_name": "value",
  "var_count": "42"
}
```

**Read User Input**
```json
{
  "readLn": "var_name"
}
```

**Exit Program**
```json
{
  "exit": ""
}
```

#### Control Flow

**If Statement**
```json
{
  "if": {
    "condition": "var_x = true",
    "execute": {
      "printLn": "Condition is true!"
    }
  }
}
```

**While Loop**
```json
{
  "while": {
    "condition": "var_count < 10",
    "execute": {
      "printLn": "Looping...",
      "var_count": "11"
    }
  }
}
```

**Repeat Loop**
```json
{
  "repeat": {
    "amount": "5",
    "execute": {
      "printLn": "Iteration: var_i"
    }
  }
}
```

#### Supported Conditions

- `=` - Equality check
- `<` - Less than
- `>` - Greater than
- `<=` - Less than or equal to
- `>=` - Greater than or equal to

### Complete Example

```json
{
  "printLn": "Hello, World!",
  "var_2": "true",
  "if": {
    "condition": "var_2 = true",
    "execute": {
      "if": {
        "condition": "var_1 = true",
        "execute": {
          "var_w": "true",
          "while": {
            "condition": "var_w = true",
            "execute": {
              "printLn": "Hello, People!",
              "var_w": "false",
              "readLn": "var_a",
              "repeat": {
                "amount": "var_a",
                "execute": {
                  "printLn": "Huh? var_i"
                }
              }
            }
          }
        }
      }
    }
  },
  "exit": ""
}
```

This program:
1. Prints "Hello, World!"
2. Sets variable `var_2` to "true"
3. Checks if `var_2` equals "true" and `var_1` equals "true"
4. Enters a while loop that prints "Hello, People!"
5. Reads user input into `var_a`
6. Repeats printing "Huh? var_i" based on the number entered by the user
7. Exits the program

## Project Structure

```
json-compiler/
├── src/
│   └── main/
│       └── kotlin/
│           ├── Main.kt           # Entry point
│           ├── Interpreter.kt    # Core interpreter logic
│           └── InputReader.kt    # JSON file reader
├── inputs/
│   └── input.json               # Sample program
├── build.gradle.kts             # Build configuration
└── README.md                    # This file
```

## Building

Build the project using Gradle:

```bash
./gradlew build
```

Run tests:

```bash
./gradlew test
```

## How It Works

1. The `InputReader` loads and parses the JSON file using Gson
2. The `Interpreter` processes each JSON key as a command
3. Commands are executed sequentially from top to bottom
4. Variables are stored in a mutable map and can be referenced throughout execution
5. Nested objects allow for control flow structures (if, while, repeat)

## Technical Details

- **Language**: Kotlin
- **Build Tool**: Gradle
- **Dependencies**: Gson for JSON parsing
- **JVM Target**: Java 17

## Contributing

This is an experimental project. Feel free to fork and experiment with adding new features!

Potential improvements:
- Functions/procedures
- Arrays and data structures
- More operators and conditions
- File I/O operations
- Error handling and debugging features

## License

This project is available for educational and experimental purposes.
