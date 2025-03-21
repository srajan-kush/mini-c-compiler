# Frontend Phase of a C Compiler

## Using the Compiler

```
lex lexer.l
yacc -d -v parser.y
gcc -w y.tab.c -o parser
./parser < input.c
```


