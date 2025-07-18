#ifndef STACK_H
#define STACK_H

#include <iostream>

// Node structure for stack
struct StackNode {
    int data;
    StackNode* next;

    StackNode(int val) {
        data = val;
        next = NULL;  // changed from nullptr to NULL
    }
};

// Stack class using linked list
class Stack {
private:
    StackNode* top;

public:
    // Constructor
    Stack() {
        top = NULL;  // changed from nullptr to NULL
    }

    // Push an element onto the stack
    void push(int val) {
        StackNode* newNode = new StackNode(val);
        newNode->next = top;
        top = newNode;
    }

    // Pop an element from the stack
    int pop() {
        if (isEmpty()) {
            std::cout << "Stack Underflow!" << std::endl;
            return -1;
        }
        StackNode* temp = top;
        int popped = temp->data;
        top = top->next;
        delete temp;
        return popped;
    }

    // Peek at the top element
    int peek() const {
        if (isEmpty()) {
            std::cout << "Stack is empty!" << std::endl;
            return -1;
        }
        return top->data;
    }

    // Check if the stack is empty
    bool isEmpty() const {
        return top == NULL;  // changed from nullptr to NULL
    }

    // Display the stack elements
    void display() const {
        StackNode* current = top;
        std::cout << "Stack (top to bottom): ";
        while (current != NULL) {
            std::cout << current->data << " ";
            current = current->next;
        }
        std::cout << std::endl;
    }

    // Destructor to clean up memory
    ~Stack() {
        while (!isEmpty()) {
            pop();
        }
    }
};

#endif // STACK_H
