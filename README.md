# 🚀 Frontend Phase of a C Compiler

## 👨‍💻 Team Members

- **Krishnakant Dinkar**
- **Srajan Kushwaha**

---

## ⚙️ How to Use the Compiler

```bash
lex lexer.l
yacc -d -v parser.y
gcc -w y.tab.c -o parser
./parser < input1.c
```

---

## 🔄 Compilation Flow

1. **Lexical Analysis** → Populate the symbol table using `add()`.
2. **Syntax Analysis** → Build and print the parse tree.
3. **Semantic Analysis** → Detect errors (undeclared variables, type mismatches, etc.).
4. **Intermediate Code Generation** → Generate and print ICG instructions.


---

## 📌 Key Components

### 🔹 Header Section (%{ ... %})

Includes:

- **Standard libraries**: `stdio.h`, `stdlib.h`, `string.h`, `ctype.h`
- **Lexer file** (`lex.yy.c`): Handles tokenization.
- **Core Functions**:
  - `yyerror(const char *s)`: Handles syntax errors.
  - `yylex()`: Calls the lexer for the next token.
  - `yywrap()`: Handles EOF in `lex.yy.c`.
  - `add(char c)`: Adds identifiers, keywords, or functions to the symbol table.
  - `insert_type()`: Assigns data types to identifiers.
  - `search(char *name)`: Checks if an identifier exists.
  - `check_declaration(char *name)`: Ensures variables are declared before use.
  - `check_return_type(char *name)`: Ensures function return types match.
  - `check_types(char *a, char *b)`: Ensures type compatibility.
  - `get_type(char *name)`: Retrieves an identifier’s type.
  - `mknode(struct node *left, struct node *right, char *token)`: Creates syntax tree nodes.

### 🔹 Symbol Table (`symbol_table[40]`)

Stores variable names, data types, and types (function, keyword, variable).

### 🔹 Syntax Tree (`struct node`)

Used for **Abstract Syntax Tree (AST)** generation.

### 🔹 Intermediate Code Generation (ICG)

Stores intermediate code instructions.

---

## 📖 Understanding LEX & YACC

### 📍 What is **LEX**?

LEX is a tool for generating a lexical analyzer. It processes **regular expressions** and outputs `lex.yy.c`, a table-driven scanner.

### 📍 What is **YACC**?

**Yet Another Compiler Compiler (YACC)** generates a parser for **Context-Free Grammar (CFG)**, translating it into a C implementation (`y.tab.c`).

---

## 🎯 Compiler Features

✅ **Symbol Table**
✅ **Parse Tree & AST**
✅ **Semantic Analysis**
✅ **Intermediate Code Generation**

---

## 📜 Supported Syntax

✅ Variable declarations & assignments (`int a;`, `float b = 5.0;`)
✅ `printf`, `scanf`
✅ Arithmetic operations (`+`, `-`, `*`, `/`)
✅ **Simple & Nested** `for` loops
✅ **If-Else** constructs (**No else-if support**)

---

## ⚠️ Assumptions

- **Header files format**: `#include <filename.h>`
- \*\*No function parameters in \*\***`main()`**
- **Numbers format**: `[-]?{digit}+|[-]?{digit}+\.{digit}{1,6}` (No `+123.45` allowed)
- **Supported variable types**: `int`, `float`, `char` (No arrays)
- **Brackets required for single-line ********`if`********, ********`else`********, and ********`for`******** blocks**
- **Flat scope (no re-declaration inside loops or conditionals)**
- **Basic ********`printf`******** and ********`scanf`******** handling (no type checking)**
- \*\*Conditions in ****`if`**** and ****`for`**** must be of form \*\***`value relop value`**

---

## 🛠 Compiler Phases

### 🔹 **Lexical Analysis**

- A **symbol table** (array of structs) stores variable names, data types, and token types.
- Whenever a header, keyword, constant, or variable is encountered, `add()` updates the symbol table.

### 🔹 **Syntax Analysis**

- **Parse tree generation** using `struct node`.
- Nodes are linked based on semantic relationships.

### 🔹 **Semantic Analysis**

- Ensures:
  1. Variables are **declared** before use.
  2. Variables are **not redeclared**.
  3. **Type checking** in expressions.

### 🔹 **Intermediate Code Generation (ICG)**

- **Three-address code representation**.
- Labels & temp variables manage jumps in `if` & `for` loops.

---

## 🖥 Example C Program for Compilation

```c
#include<stdio.h>
#include<string.h>

int main() {
    int a;
    int x = 1, y = 2, z = 3;
    x = 3;
    y = 10;
    z = 5;
    
    if (x > 5) {
        for (int k = 0; k < 10; k++) {
            y = x + 3;
            printf("Hello!");
        }
    } else {
        int idx = 1;
    }
    
    for (int i = 0; i < 10; i++) {
        printf("Hello World!");
        scanf("%d", &x);
        if (x > 5) {
            printf("Hi");
        }
        for (int j = 0; j < z; j++) {
            a = 1;
        }
    }
    
    return 1;
}
```

## 📸 Screenshots  

Enhance your understanding with the following images showcasing compiler outputs:  

### 🖥️ Compiler Output  
<div align="center">  
  <img width="328" alt="icg" src="https://github.com/user-attachments/assets/e071377f-b9d1-43fa-b582-7c69deef81aa" />  
</div>  

---

### 🌳 Inorder Traversal of Tree  
<div align="center">  
  <img width="1110" alt="inorder" src="https://github.com/user-attachments/assets/ea7b77b7-1ad8-4c3c-a8ea-929e2bdb7ae3" />  
</div>  

---

### ⚠️ Checking for Semantic Errors  
<div align="center">  
  <img width="340" alt="semantic" src="https://github.com/user-attachments/assets/3d2a854d-06fe-4755-bb86-c4951e391f40" />  
</div>  

---

### 📊 Symbol Table  
<div align="center">  
  <img width="328" alt="table" src="https://github.com/user-attachments/assets/26a037d4-382b-4ab4-8c43-f6e593cb4e54" />  
</div>  

---

### 🌲 Parse Tree of Input Code  
<div align="center">  
  <img width="600" alt="tree" src="https://github.com/user-attachments/assets/6cc9e07c-55e8-48d3-b28a-eb15ab748539" />  
</div>  

-----





