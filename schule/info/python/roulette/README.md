# Roulette by Johannes Olzem - Documentation
## Introduction
Roulette is a casino Game that appeared first in 1720 in the form of the Italian game Biribi.

## Installation
1. Download Python 3.9 [here](https://www.python.org/downloads/).
2. Download the Source Code
3. Insert the path to your roulette.py file in Line 24 inside the apostrophes
4. If it is not already there, create a balance.txt file with the value 10.0

## Usage
Have fun gambling **without** real money.

## Code Explanation
***
### Imports and Lists
```python
import random
import time
import os
```
Importing built-in python modules for later use.
***
```python
r = str([1, 3, ...])
... = str([...])
```
Lists defining the Roulette Fields for betting and payout, also being converted to strings.
***
### Introduction to the Game
```python
print("Roulette by Johannes Olzem\nDocumentation at https://johannesolzem.gq/schule/info/python/roulette/README.md")
time.sleep(0.5)
for i in range(3):
    print(".\n")
```
The title section. This prints the text in the Quotation marks, then waits 0.5 seconds (with help of the time module). Afterwards it prints a dot and a line break 3 times with help of a for loop.
***
```python
startGame = input("Would you like to play roulette? (yes/no)\n")
```
The Variable startGame asks the user for an input, whether he would like to start the game or not.
***
```python
if startGame == 'no':
    exit()
```
If the user input of the Variable startGame is "no", the program exits.
***
```python
elif startGame == 'yes':
    ...
else:
    exit()
```
Else, if the user input of the Variable startGame is "yes", the code inside the tab spacing gets executed.
If the input is anything else, the program exits.
***
```python
os.chdir(r'C:\Users\Johannes\Documents\py\roulette')
```
The program gets directed to the path given, with help of the os module.
***
```python
with open('balance.txt', 'r') as balance:
    coinbal = float(balance.read())
```
Opens the file balance.txt with read access as a variable "balance". Inside that, the Variable coinbal gets defined. It's supposed to read the file balance(.txt) and convert it into a float (also called floating number).
***
```python
print("\nreview payout here")
print("https://johannesolzem.gq/schule/info/python/roulette/werte.png \n")
```
A Link to the payout table.
***
### Betting
```python
betcoi = float(input("How many coins would you like to bet\n"))
```
The Variable betcoi asks the user for an input and converts it into a float.
***
```python
if betcoi > coinbal:
    print("You don't have enough coins!")
    exit()
```
If the amount the user is trying to bet is bigger than his balance, the program prints "You don't have enough coins!" and then exits.
***
```python
with open('balance.txt', 'w') as useCoins:
    useCoins.write(str(coinbal - betcoi))
```
The file balance.txt gets opened again (now with write access), as the Variable useCoins. Inside this, the file gets overwritten with the subtraction of the balance (coinbal) and the bet (betcoi). The solution of that gets converted into a string.
***
```python
coinbal = coinbal - betcoi
```
The variable coinbal is now the subtraction of the users balance and the bet.
***
```python
betnum = input("\nWhat would you like to bet on?\n\n0-36\neven/odd\nred/black\n1st/2nd/3rd\nhalf1/half2\n\n")
```
The Variable betnum asks the user for an input. This input decides whether the user wins or not after the "wheel" has landed. It also prints out the possible bets.
***
### Wheel
```python
def wheel(spinTimes):
```
The function wheel with the parameter spinTimes gets defined.
```python
winnum = 0
for i in range(spinTimes):
    winnum = winnum + 1
    print(winnum)
    time.sleep(0.1)
    if winnum == 36:
    winnum = 0
```
First the winning number gets set to 0. Then the for loop adds 1 every repeat, prints it and waits 0.1 seconds. If the Winning number goes above 36 it gets reset to 0
```Python
    time.sleep(0.3)
    winnum = winnum + 1
    print(winnum)
    time.sleep(0.4)
    winnum = winnum + 1
    print(winnum)
    time.sleep(0.7)
    winnum = winnum + 1
    print(winnum)
```
This scheme continues, but with increasing time between the printing, to show that the wheel is slowing down.
```Python
return(winnum)
```
The winning number gets returned for later use.
***
```Python
winnum = float(wheel(random.randrange(26,74)))
```
The Variable winnum gets defined outside the "wheel". The function wheel gets executed with a spinTimes value of random.randrange(26,74), which returns a number between 26 and 74.
***
### Payout
```Python
if betnum == winnum:
    print("Congratulations! You won 5x your Coins!")
    win = betcoi * 5
```
If the bet is equal to the winning number, the variable win equals the bet times 5.
```Python
elif betnum == "even" and (winnum % 2 == 0):
    print("Congratulations! You won 2x your Coins!")
    win = betcoi * 2

elif betnum == "odd" and (winnum % 2 != 0):
    print("Congratulations! You won 2x your Coins!")
    win = betcoi * 2
```
If the bet is even/odd and the winning number divided by 2 does/doesnt equal 0, the user wins his bet times 2.
```Python
elif betnum == "red" and winnum in r:
    print("Congratulations! You won 2x your Coins!")
    win = betcoi * 2
```
If the bet is "red" and the winning number can be found in the list "r" (line 5), the user wins his bet times 2.\
This is the same for the other elif statements.
```Python
else:
    print("Oh no, you lost!")
    win = 0
```
If none of the above apply, the user wins nothing.
***
```Python
with open('balance.txt', 'w') as payout:
    payout.write(str(coinbal + win))
```
The file balance.txt gets opened once again, with write access. It overwrites the data of the file with the sum of the users balance and win, which gets converted into a string.
***
### End
```Python
time.sleep(1)
exit()
```
The program waits for 1 second before closing, to show the winnings to the user
