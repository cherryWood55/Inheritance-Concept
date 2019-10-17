# Abstract Data Type in C++
## Stack, Queues and Lists

## Data Abstraction & ADT
When you start your car, you don't need to know the intricate workings of the starter motor. All you need to do is turn the key to initiate the sequence. If successful, the engine will turn over. This real-world example highlights the programming concept of data abstraction, which allows a programmer to protect/hide the implementation of a process and only gives the keys to other functions or users. You only need to know enough about a given function to run it but don't need to know (or care) about how the internal code works.

To take this a step further, we can create entire data types. An abstract data type (or ADT) is a class that has a defined set of operations and values. In other words, you can create the starter motor as an entire abstract data type, protecting all of the inner code from the user. When the user wants to start the car, they can just execute the start() function. In programming, an ADT has the following features:

An ADT doesn't state how data is organized, and
It provides only what's needed to execute its operations
An ADT is a prime example of how you can make full use of data abstraction and data hiding. This means that an abstract data type is a huge component of object-oriented programming methodologies: enforcing abstraction, allowing data hiding (protecting information from other parts of the program), and encapsulation (combining elements into a single unit, such as a class).

One of the most common ADTs is the stack. Let's take a look at it in action.

## Stack Data Type Example
In this example, we're creating an object-oriented C++ program that creates an abstract data type in the form of a stack, in which items can be pushed onto the top and popped off the top. The program simulates your browsing history. Each page you visit is stored in a stack. As you click 'back' on the browser, you are removing/viewing the top element of the stack. As you go forward you are pushing them back onto the stack.

This example also shows a little different method for declaring functions from a class. Notice how they're declared inside the class but created outside of it. Stacks are very common, so let's see how they can work for us.



#include <iostream>
using namespace std;
//limit size of browser stack to 100
#define MAX_SIZE 100
class Stack {
 public:
  int top;
  int size[MAX_SIZE];
  
  //constructor
  Stack() {
   //no top yet
   top = -1;
  }
  //function declarations
  bool push(int page);
  int pop();
  bool is_empty();
};
//Functions created below
//are we empty?
bool Stack::is_empty() {
 return (top < 0);
}
//pop from stack (back button)
int Stack::pop() {
 if(top < 0) {
  cout << "Nothing here...";
  return 0;
 } else {
  int page = size[top--];
  return page;
 }
}
//push onto stack
bool Stack::push(int page) {
 if(top >= MAX_SIZE) {
  cout << "Can't anymore, Jim";
  return false;
 } else {
  size[++top] = page;
  return true;
 }
}
// Finally, create the main function to create a new instance of the stack, which you can see appearing here:

int main( ) {
 //new stack
 Stack pages;
 pages.push(5);
 pages.push(10);
 pages.push(15);
 pages.push(20);
 
 cout << " Page " << pages.pop() << " popped from stack " << endl;
 cout << " Page " << pages.pop() << " popped from stack " << endl;
 return 0; }
 
 
