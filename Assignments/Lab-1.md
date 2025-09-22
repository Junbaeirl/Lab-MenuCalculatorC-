# Code
```c++
 // These help with stopping bad inputs with <limits> and shortening names with the use of using namespace std
#include <iostream>
#include <limits>
#include <string>

using namespace std;
// Creates a class named Menu that gives choices of 1 through 5 for each category assigned.
enum class Menu { Add = 1, Subtract, Multiply, Divide, Quit };
// Prints the menu and asks the user to choose an option between 1-5
Menu readMenuChoice() {
    for (;;) {
        cout << "\nCalculator Menu Options\n"
             << "1. Add\n"
             << "2. Subtract\n"
             << "3. Multiply\n"
             << "4. Divide\n"
             << "5. Quit\n"
             << "Choose an option: ";
        // reads numeric input
        int choiceInput;
        // Returns an invalid option and tries to get the user to input a valid option, if an invalid input is detected.
        if (!(cin >> choiceInput)) {
            cout << "Invalid option. Enter a numerical value between 1 and 5.\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            continue;
        }
        // Enforces the range of 1-5 for inputs
        if (choiceInput >= 1 && choiceInput <= 5)
            // converts typed enumeration for switch
            return static_cast<Menu>(choiceInput);
        cout << "Invalid option. Enter a numerical value between 1 and 5.\n";
    }
}
// Numeric input reader that will keep prompting the user until a double is inputted.
double readDouble(const string& prompt) {
    double value;
// for loop to keep prompting the user
    for (;;) {
        cout << prompt;
        if (cin >> value) return value;
        cout << "Invalid input. Enter a numeric value.\n";
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }
}
// Main, starting point of the program.
int main() {
    bool running = true;
    // Keeps the program running until the user selects "Quit"
    while (running) {
        Menu choice = readMenuChoice();

        switch (choice) {
            case Menu::Add: {
                // Takes the input of first number and second number and uses the following operator, based on what was chosen in the previous menu. And then print the output of the math problem.
                double a = readDouble("Enter first number: ");
                double b = readDouble("Enter second number: ");
                cout << "Results: " << a + b << "\n";
                break;
            }
            case Menu::Subtract: {
                double a = readDouble("Enter first number: ");
                double b = readDouble("Enter second number: ");
                cout << "Results: " << a - b << "\n";
                break;
            }
            case Menu::Multiply: {
                double a = readDouble("Enter first number: ");
                double b = readDouble("Enter second number: ");
                cout << "Results: " << a * b << "\n";
                break;
            }
            case Menu::Divide: {
                double a = readDouble("Enter first number: ");
                double b;
                for (;;) {
                    b = readDouble("Enter second number: ");
                    // Prevents "b" from being equal to 0 to avoid division by 0, followed by an output showing an error on division by zero.
                    if (b == 0.0) {
                        cout << "Error: Division by zero is not allowed.\n";
                        continue;
                    }
                    break;
                }
                cout << "Results: " << a / b << "\n";
                break;
            }
                // Exits the program
            case Menu::Quit:
                cout << "Exiting Calculator. Thanks for using my Calculator :)\n";
                running = false;
                break;
        }
    }
    // Indicates a successful input and output. Instead of an error, which would be any non numerical value.
    return 0;
```
## My Video link explaining the code.
https://youtu.be/2OcTAv2HXYI
