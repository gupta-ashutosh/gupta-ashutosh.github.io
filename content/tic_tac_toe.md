title: TicTacToe Game
Slug: tic_tac_toe
Date: 2019-07-11 22:30
Category: python
Tags: python game tictactoe
author: Ashutosh Gupta
Summary: TicTac is a paper-and-pencil game for two players, X and O, who take turns marking the spaces in a 3×3 grid. The player who succeeds in placing three of their marks in a horizontal, vertical, or diagonal row wins the game.


I have written a small program to play command based [TicTacToe]([https://en.wikipedia.org/wiki/Tic-tac-toe]) game in Python.

This is a good programing exercise for beginners.
This small game will help users to start thinking logically and how to proceed and plan when coding.

## Few of concepts that is used in this program
- Dictionary in Python, how to insert value in it and how to iterate it.
- Loops and conditional statements
- Use of continue and break
-  Taking input from user

You can download the source code from [here](https://github.com/gupta-ashutosh/gupta-ashutosh.github.io/blob/master/code_files_and_notebooks/tic_tac_toe.py).

```python

theBoard = {1:' ', 2: ' ', 3: ' ',
			4:' ', 5: ' ', 6: ' ',
			7:' ', 8: ' ', 9: ' ',
}


def printBoard(board):
	print(board[1] + "|" + board[2] + "|" + board[3])
	print("-+-+-")
	print(board[4] + "|" + board[5] + "|" + board[6])
	print("-+-+-")
	print(board[7] + "|" + board[8] + "|" + board[9])


def hasWon(theBoard, move):
	winning_triplets = {
		0: [1,2,3], 1: [4,5,6], 2: [7,8,9],
		3: [1,4,7], 4: [2,5,8], 5: [3,6,9],
		6: [1,5,9], 7: [3,5,7]
	}

	for key, value in winning_triplets.items():
		won = True
		for i in value:
			if theBoard[i] == theBoard[move]:
				won = won and True
			else:
				won = won and False
				break
		if won == True:
			return True
	return False


def boardFull(theBoard):
	for key, value in theBoard.items():
		if theBoard[key] == ' ':
			return False
	else:
		return True

def possibleMove(theBoard, move):
	if theBoard[move] == 'X' or theBoard[move] == '0':
		return False
	return True

def start():
	turn = 'X'
	while(1):
		printBoard(theBoard)
		if boardFull(theBoard):
			print("Match Over, its a tie")
			break

		print("Turn for " +  turn + ". Which place to enter? (Position 1-9 represent the location where you want to enter your turn)")
		
		move = input()

		if possibleMove(theBoard, move) == False:
			print("Move not Possible, please any other move")
			continue

		theBoard[move] = turn

		if hasWon(theBoard, move):
			print("Congratulation " + turn + " you have won the match")
			break

		if turn == 'X':
			turn = '0'
		else:
			turn = 'X'

	printBoard(theBoard)

if __name__ == "__main__":
	start()
```
