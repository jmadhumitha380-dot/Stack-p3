# Stack-p3
Practice program
# Infix to Postfix using Stack
def precedence(op):
    if op in ('+', '-'):
        return 1
    if op in ('*', '/'):
        return 2
    return 0
def infix_to_postfix(expression):
    stack = []
    postfix = ""
    for ch in expression:
        if ch.isalnum():
            postfix += ch
        elif ch == '(':
            stack.append(ch)
        elif ch == ')':
            while stack and stack[-1] != '(':
                postfix += stack.pop()
            stack.pop()
        else:
            while stack and precedence(stack[-1]) >= precedence(ch):
                postfix += stack.pop()
            stack.append(ch)
    while stack:
        postfix += stack.pop()
    return postfix
exp = input("Enter Infix Expression: ")
print("Postfix Expression:", infix_to_postfix(exp))

Output:
Output:

Enter Infix Expression: A+B*C
Postfix Expression: ABC*+
