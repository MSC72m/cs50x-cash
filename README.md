# Coin Counting Program

## Project Description
This project is a solution to a CS50x problem set that involves implementing a coin counting program. The program calculates the minimum number of coins (quarters, dimes, nickels, and pennies) needed to make a given amount of cents. It prompts the user for the amount in cents and then determines the fewest number of each coin needed to make that amount.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Algorithm Explanation](#algorithm-explanation)
- [Code Explanation](#code-explanation)

## Installation
No special installation is required for this project. Ensure you have a C compiler like `gcc` installed and the CS50 library available.

## Usage
To compile and run the project, use the following commands:
```sh
make coin_counter
./coin_counter
```
You will be prompted to enter the amount of cents, and the program will output the minimum number of coins needed.

## Algorithm Explanation
The coin counting algorithm is designed to minimize the number of coins needed to make change for a given amount of cents. The algorithm works as follows:

Get Cents:
Prompt the user to input a positive number of cents. Repeat the prompt if the input is invalid (negative value).

Calculate Coins:
Calculate Quarters: Determine the number of quarters (25-cent coins) needed.
Calculate Dimes: Determine the number of dimes (10-cent coins) needed after quarters.
Calculate Nickels: Determine the number of nickels (5-cent coins) needed after dimes.
Calculate Pennies: Determine the number of pennies (1-cent coins) needed after nickels.
Output the Result:
Sum the total number of coins and print the result.

Example Walkthrough
Suppose the user inputs 87 cents. The program will:

Calculate the number of quarters: 87 / 25 = 3 quarters (62 cents remaining).
Calculate the number of dimes: 62 / 10 = 1 dime (52 cents remaining).
Calculate the number of nickels: 52 / 5 = 0 nickels (52 cents remaining).
Calculate the number of pennies: 52 / 1 = 2 pennies.
The total number of coins is 3 quarters + 1 dime + 0 nickels + 2 pennies = 6 coins.

## Code Explanation
Constants and Function Prototypes
``` C
#include <cs50.h>
#include <stdio.h>

// Function prototypes
int get_cents(void);
int calculate_quarters(int cents);
int calculate_dimes(int cents);
int calculate_nickels(int cents);
int calculate_pennies(int cents);
```
#include <cs50.h>: Includes the CS50 library for simplified input functions.
#include <stdio.h>: Includes the standard input/output library.
Function prototypes: Declare functions used in the program before their definitions to allow main() to call these functions.
Main Function
```C
int main(void)
{
    int cents; // Declare the 'cents' variable outside the loop to use it after the loop ends

    // Get a positive amount of cents from the user
    do
    {
        cents = get_cents();
    }
    while (cents < 0);

    // Calculate the number of quarters
    int quarters = calculate_quarters(cents);
    cents -= quarters * 25;

    // Calculate the number of dimes
    int dimes = calculate_dimes(cents);
    cents -= dimes * 10;

    // Calculate the number of nickels
    int nickels = calculate_nickels(cents);
    cents -= nickels * 5;

    // Calculate the number of pennies
    int pennies = calculate_pennies(cents);

    // Sum the total number of coins
    int coins = quarters + dimes + nickels + pennies;

    // Print the total number of coins
    printf("%i\n", coins);
}
```
Explanation:
Variable Declaration:

```C
int cents;
```
Declares the cents variable to store user input.

Input Loop:

```C 
do {
    cents = get_cents();
} while (cents < 0);
```
Repeatedly prompts the user for a positive number of cents.

Calculating Coins:

``` C
int quarters = calculate_quarters(cents);
cents -= quarters * 25;

int dimes = calculate_dimes(cents);
cents -= dimes * 10;

int nickels = calculate_nickels(cents);
cents -= nickels * 5;

int pennies = calculate_pennies(cents);
```
Calculates the number of each type of coin needed and subtracts their total value from cents.

Summing Coins:

``` C
int coins = quarters + dimes + nickels + pennies;
```
Sums the total number of coins used.

Output:

``` C
printf("%i\n", coins);
```
Prints the total number of coins.

Get Cents Function
``` C
int get_cents(void)
{
    int cents;
    do
    {
        cents = get_int("How many cents do you owe? ");
    }
    while (cents < 0);
    return cents;
}
```
Purpose: Prompts the user for a positive integer value and returns it.
Loop: Ensures that the user enters a non-negative number.
Calculate Quarters Function
``` C
int calculate_quarters(int cents)
{
    int quarters = 0;
    while (cents >= 25)
    {
        cents -= 25;
        quarters++;
    }
    return quarters;
}
```
Purpose: Calculates the number of quarters (25-cent coins).
Calculate Dimes Function
``` C
int calculate_dimes(int cents)
{
    int dimes = 0;
    while (cents >= 10)
    {
        cents -= 10;
        dimes++;
    }
    return dimes;
}
```
Purpose: Calculates the number of dimes (10-cent coins).
Calculate Nickels Function
``` C
int calculate_nickels(int cents)
{
    int nickels = 0;
    while (cents >= 5)
    {
        cents -= 5;
        nickels++;
    }
    return nickels;
}
```
Purpose: Calculates the number of nickels (5-cent coins).
Calculate Pennies Function
``` C
int calculate_pennies(int cents)
{
    int pennies = 0;
    while (cents >= 1)
    {
        cents -= 1;
        pennies++;
    }
    return pennies;
}
```
Purpose: Calculates the number of pennies (1-cent coins).
