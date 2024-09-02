# C-compiler
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

// Token types
typedef enum {
    TOKEN_IDENTIFIER,
    TOKEN_NUMBER,
    TOKEN_PLUS,
    TOKEN_MINUS,
    TOKEN_MUL,
    TOKEN_DIV,
    TOKEN_LPAREN,
    TOKEN_RPAREN,
    TOKEN_LBRACE,
    TOKEN_RBRACE,
    TOKEN_IF,
    TOKEN_ELSE,
    TOKEN_WHILE,
    TOKEN_FUNCTION,
    TOKEN_SEMICOLON,
    TOKEN_ASSIGNMENT,
} token_type;

// Abstract Syntax Tree (AST) node types
typedef enum {
    AST_PROGRAM,
    AST_STATEMENT_LIST,
    AST_STATEMENT,
    AST_EXPRESSION,
    AST_IDENTIFIER,
    AST_NUMBER,
    AST_BINARY_OPERATION,
    AST_IF_STATEMENT,
    AST_WHILE_STATEMENT,
    AST_FUNCTION_DEFINITION,
} ast_node_type;

// AST node structure
typedef struct ast_node {
    ast_node_type type;
    struct ast_node* child1;
    struct ast_node* child2;
    struct ast_node* child3;
    char* identifier;
    int number;
} ast_node_t;

// Time complexity calculation
typedef enum {
    TIME_COMPLEXITY_CONSTANT,
    TIME_COMPLEXITY_LINEAR,
    TIME_COMPLEXITY_QUADRATIC,
    TIME_COMPLEXITY_EXPONENTIAL,
} time_complexity_type;

// Function to calculate time complexity
time_complexity_type calculate_time_complexity(ast_node_t* ast) {
    // Simplified example, not a full implementation
    if (ast->type == AST_WHILE_STATEMENT) {
        return TIME_COMPLEXITY_LINEAR;
    } else if (ast->type == AST_IF_STATEMENT) {
        return TIME_COMPLEXITY_CONSTANT;
    } else {
        return TIME_COMPLEXITY_CONSTANT;
    }
}

// Function to generate machine code
void generate_machine_code(ast_node_t* ast) {
    // Simplified example, not a full implementation
    if (ast->type == AST_EXPRESSION) {
        printf("MOV AX, %d\n", ast->number);
    } else if (ast->type == AST_IDENTIFIER) {
        printf("MOV AX, [%s]\n", ast->identifier);
    }
}

int main() {
    // Example C program
    char* program = "int main() { int x = 5; while (x < 10) { x = x + 1; } return 0; }";

    // Lexical analysis
    token_t* tokens = lex(program);

    // Syntax analysis
    ast_node_t* ast = parse(tokens);

    // Time complexity calculation
    time_complexity_type tc = calculate_time_complexity(ast);

    // Machine code generation
    generate_machine_code(ast);

    printf("Time Complexity: ");
    switch (tc) {
        case TIME_COMPLEXITY_CONSTANT:
            printf("O(1)\n");
            break;
        case TIME_COMPLEXITY_LINEAR:
            printf("O(n)\n");
            break;
        case TIME_COMPLEXITY_QUADRATIC:
            printf("O(n^2)\n");
            break;
        case TIME_COMPLEXITY_EXPONENTIAL:
            printf("O(2^n)\n");
            break;
    }

    return 0;
}



