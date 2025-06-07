# Text Editor with Undo

A simple command-line text editor that allows typing, deleting, and undoing actions using a stack data structure.

## Features
- Type characters
- Delete characters
- Undo last operation (using stack)

## Concepts Used
- Stack
- String Manipulation

## How to Run
1. Compile: `g++ text_editor.cpp -o editor`
2. Run: `./editor`

## Author
[@25jasmeen](https://github.com/25jasmeen)

#include <iostream>
#include <stack>
using namespace std;

int main() {
    string text = "";
    stack<string> history;
    int choice;
    string input;

    while (true) {
        cout << "\n1. Type\n2. Delete\n3. Undo\n4. Show Text\n5. Exit\nEnter choice: ";
        cin >> choice;

        if (choice == 1) {
            cout << "Enter text to add: ";
            cin >> input;
            history.push(text);
            text += input;
        } else if (choice == 2) {
            int n;
            cout << "How many characters to delete? ";
            cin >> n;
            if (n > text.length()) n = text.length();
            history.push(text);
            text.erase(text.length() - n);
        } else if (choice == 3) {
            if (!history.empty()) {
                text = history.top();
                history.pop();
                cout << "Undo successful.\n";
            } else {
                cout << "Nothing to undo.\n";
            }
        } else if (choice == 4) {
            cout << "Current Text: " << text << endl;
        } else if (choice == 5) {
            break;
        } else {
            cout << "Invalid choice.\n";
        }
    }

    return 0;
}
