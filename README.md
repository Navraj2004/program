#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<math.h>
#define stacksize 70

void push(int item, int*top, int s[])
{
    if(*top == stacksize - 1)
    {
        printf(" stack overflow\n");
        return;

    }
    *top = *top + 1;
    s[*top]= item ;
}
int pop(int *top, int s[])
{
    int item;
    if(*top==-1)
     return -1;
     item = s[*top];
     *top = *top -1 ;
     return item;

}
 int evaluate(char postfix[])
 {
    int i, n, op1, op2, res, op, top, s[stacksize];
    char symbol;
    top = -1;
    n= strlen(postfix);
    for(i=0; i<n ; i++)
    {
        symbol = postfix[i];
        switch(symbol)
        {
            case'+': op2 = pop(&top, s);
                     op1= pop(&top,s);
                     res= op1 + op2;
                     push(res,&top,s);
                     break; 
            case'-': op2 = pop(&top, s);
                     op1= pop(&top,s);
                     res= op1 - op2;
                     push(res,&top,s);
                     break; 
            case'*': op2 = pop(&top, s);
                     op1= pop(&top,s);
                     res= op1 * op2;
                     push(res,&top,s);
                     break; 
            case'/': op2 = pop(&top, s);
                     op1= pop(&top,s);
                     res= op1 / op2;
                     push(res,&top,s);
                     break; 
            case'%': op2 = pop(&top, s);
                     op1= pop(&top,s);
                     res= op1 % op2;
                     push(res,&top,s);
                     break; 
            case'^':
            case'$': op2 = pop(&top, s);
                     op1= pop(&top,s);
                     res= (int)pow((double)op1,(double)op2);
                     push(res,&top,s);
                     break; 
            default: push(symbol-'0',&top, s);
        }
    }
    return(pop(&top,s));
 }
    void main()
    {
        int res;
        char postfix[70];
        
        printf("enter the postfix expression\n");
        scanf("%s",postfix);
        res=evaluate(postfix);
        printf("the value of the postfix exp is %d", res);
        
    }
 
