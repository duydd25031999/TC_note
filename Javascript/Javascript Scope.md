# Scope in Javascript

Category: Javascript
First Refrence: How%20many%20types%20of%20scope%203a883fd1ae984e8f80db17fd29a2fa50.md, What%20is%20scope%20in%20javascript%20cd45923415ae417db8ad384854775c6f.md, What%20is%20Hoisting%20390228e6047740bd8ab6cb922667670e.md, %5BExample%5D%20hoisting%20e2ab9358ca944b639013351cfc7623d5.md
Tags: Common, Concept

**Recall**

1. Lexing sẽ phát hiện Var được access ở token nào
2. Lập bản đồ code = dạng tree
3. Thu thập variables + accessable của các variables đó
4. Từ thu thập của Scope ⇒ AST
5. Excute dựa trên AST
- Semantic: ngữ nghĩa
- Scope look-up tìm accessable của 1 biến trong scope
- Shadowing là layer của 1 var trùng tên với var ở parent scope
- Mỗi function = 1 scope riêng ⇒ var trùng tên với parent scope = var mới nếu được identify lại
- Hoisting là việc khi var khi báo ở scope thì có thể access ở bất kì đâu
    - Kể cả trước khi identify
- Sẽ ưu tiên khai báo function bình thường nhất

## Basic S****cope****

### Global

- Defined in outer document

### Functional

- When call function ⇒ create new scope for function.
- When call function ⇒ Re-declare local var
    - Local var is only accessed inside scope of function.
- When function finished the execution
    - When return
    - destroy scope
        - garbage collection = automatically clean like java

## Concept

- Scope is the `accessibility` of `variables`, `functions`, and `objects` in some particular part of code `during runtime`.
- Scope is the set of rules that determines where and how a variable (identifier) can be looked up.
- Store values and pull values out of variables is what gives a program state.

### Compiler Theory

3 steps before it is executed

1. Tokenizing/Lexing
    
    `var a = 2;` ⇒ var, a, =, 2 and ; 
    
    - Breaking up a string of characters into meaningful chunks (chunk = token).
    - Lexing = tokenizer were to invoke stateful parsing rules to figure out whether should be considered a distinct token or just part of another token.
        - Lexing is tokenizer that checks token is independence or belong to other token.
    - The difference between tokenizing and lexing is subtle and academic
2. Parsing
    - Taking a stream (array) of tokens and turning it into abstract syntax tree (AST).
        - A tree of nested elements
        - Collectively represent the grammatical structure of the program
        - Top-level node = VariableDeclaration
            - Child node hold variable name = Identifier
            - Child node = AssignmentExpression
                - Child of child called NumericLiteral
3. Code-Generation
    - The process of taking an AST and turning it into executable code.
    - This part varies greatly depending on the language, the platform it’s targeting, and so on.
- The JavaScript engine is vastly more complex than just those three steps, as are most other language compilers.

## Understanding Scope

### The Cast

1. Scope
    - One of Engine’s friends
    - Collects and maintains a look-up list of all the declared identifiers (variables), and enforces a strict set of rules as to how these are accessible to currently executing code.
2. Compiler
    - Another friend of Engine
    - Handles all the dirty work of parsing and code-generation (see previous section).
    - Perform lexing to break it down into tokens, which it will then parse into a tree.
    1. Compiler asks Scope to see if a variable already exists for that particular scope collection.
        - True ⇒ Compiler ignores this declaration and moves on.
        - Compiler asks Scope to declare a new variable called a for that scope collection.
    2. Compiler then produces code for Engine to later execute.
        1. Ask Scope if there is a variable called a accessible in the current scope col‐
        lection.
        2. True ⇒ Engine uses that variable. 
        3. False ⇒ Engine looks else‐where
        4. If Engine eventually finds a variable
3. Engine
    - Responsible for start-to-finish compilation and execution of our JavaScript program.

## Lexical scope

- lexical scope = dynamic scope
- Lexing process = examines ⇒  string of source code characters ⇒ semantic meaning to the tokens = result of some stateful parsing.
- Scope look-up stops once it finds the first match.
- shadowing = multiple layers of nested scope ⇒ same identifier name can be specified

### eval

- Function that compile string into JS code while running.

## Function Scope

### Hoisting

- Hoisting is a JavaScript mechanism where variables, function declarations and classes are moved to the top of their scope before code execution.
- `var` appears inside a scope
    - Belong to the entire scope and accessible everywhere throughout.
    - When 1 variable is declared in 1 scope (functional or global), it can be used in everywhere in that scope ⇒ dynamic.
    - `var` keyword to declare a variable that will belong to the current function scope.
    - This the global scope if at the top level outside of any function.

### Nested scopes

- When you declare a variable, it is available anywhere in that scope, as well as any lower/inner scopes.
- hiding variables = use variable declared from another scope (parent scope) ⇒ Can't create a variable like that.

### Blocks as Scopes

- When var is declared in if | for, it is still belong to parent block.

### Functions First

```jsx
foo(); // 3

function foo() {
	console.log( 1 );
}

var foo = function() {
	console.log( 2 );
};

function foo() {
	console.log( 3 );
}
```