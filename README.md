# Setter Getter Generator (Java)

SetterGetterGenerator is a runtime code generation utility that uses the Java Reflection API to automatically generate:

- Default constructor
- Setter methods
- Getter methods

Instead of manually writing boilerplate code, this tool dynamically generates the code and copies it directly to the system clipboard.

## Features

- Uses Java Reflection API
- Automatically assigns default values
- Copies generated code to clipboard
- Works for any compiled class

## How to Run

Compile:
javac SetterGetterGenerator.java

Run:
java SetterGetterGenerator ClassName

Example:
java SetterGetterGenerator bbb