#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int tempCount = 1;

char* newTemp() {
    char* temp = (char*)malloc(4);
    sprintf(temp, "t%d", tempCount++);
    return temp;
}

void generateThreeAddressCode(char op, char* arg1, char* arg2, char* result) {
    printf("%s = %s %c %s\n", result, arg1, op, arg2);
}

int main() {
    char expression[100];
    
    printf("Enter an arithmetic expression: ");
    scanf("%s", expression);

    int len = strlen(expression);
    char* stack[len];

    int top = -1;

    for (int i = 0; i < len; i++) {
        if (expression[i] >= 'a' && expression[i] <= 'z') {
            char* temp = newTemp();
            stack[++top] = temp;
            generateThreeAddressCode('=', &expression[i], "", temp);
        } else if (expression[i] == '+' || expression[i] == '-' || expression[i] == '*' || expression[i] == '/') {
            char* temp1 = stack[top--];
            char* temp2 = stack[top--];
            char* temp3 = newTemp();
            stack[++top] = temp3;
            generateThreeAddressCode(expression[i], temp2, temp1, temp3);
        }
    }

    printf("\nThree Address Code:\n");
    for (int i = 0; i <= top; i++) {
        printf("%s\n", stack[i]);
    }

    return 0;
}
