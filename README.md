# Ex-5-RECOGNITION-OF-THE-GRAMMAR-anb-where-n-10-USING-YACC
RECOGNITION OF THE GRAMMAR(anb where n>=10) USING YACC
# Date:
05/11/2024
# Aim:
To write a YACC program to recognize the grammar anb where n>=10.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the variables a and b.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ flex lexer.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ bison –d parser.y
7.	Compile these with the C compiler as gcc lex.yy.c parser.tab.c -lfl
8.	Enter a string as input and it is identified as valid or invalid.
# PROGRAM:
lexer.l file
```
%{
/* Definition section */
#include "parser.tab.h"
%}
/* Rule Section */
%%
[aA] { return A; }
[bB] { return B; }
\n { return NL; }
. { return yytext[0]; }
%%
int yywrap() {
return 1;
}
```
parser.y
```
%{
/* Definition section */
#include<stdio.h>
#include<stdlib.h>
extern int yylex(void); // Declaration for yylex
void yyerror(char *msg); // Declaration for yyerror
%}

%token A B NL

/* Rule Section */
%%
stmt: S NL { printf("Valid string\n"); exit(0); }
;

S: A S B
| /* empty string */
;

%%

void yyerror(char *msg) {
    printf("Invalid string\n");
    exit(0);
}

// Driver code
int main() {
    printf("Enter the string\n");
    yyparse();
    return 0;
}
```
# OUTPUT
![WhatsApp Image 2024-11-26 at 17 41 55_d895a805](https://github.com/user-attachments/assets/3f37e3e7-52cc-4ff6-becc-a8f1e828d837)

# RESULT
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
