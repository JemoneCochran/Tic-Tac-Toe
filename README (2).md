
# Tic Tac Toe game

 Generating a tic tac toe game and that will allow two players to go against each other in a game of tic tac toe, the winner will have their winning row highlighted in yellow, if the game is a tie, the whole board will be highlighted in red


## Authors

Jemone Cochran II

## Usage/Examples

#imported functions 

#This function allows the user to use selected functions that make game creating easier!

#We specifically used the "*" function as it will give the most commonly used functions for this code

    from tkinter import *

#Another function was added to the program because this function let's the program create random outcomes at whichever limit we choose, it's possible to add more than one function to the program

    import random


#This function defines a functions for each players turn, the boards, the win conditions and rounds or new games to be created

    def next_turn(row, column):

#The primarily used variable, it's set to player to reference player 1
#a "global" variable is a variable that can be used throughout the entire program

    global player

#the if statements (labelled "if") that will declare specific text based on information from the "check_winner" function

    if buttons[row][column]['text'] == "" and check_winner() is False:

    if player == players[0]:

        buttons[row][column]['text'] = player

 #if statements that will display the appropriate text on the tic tac toe board

    if check_winner() is False:
    
        player = players[1]
                label.config(text=(players[1]+" turn"))

            elif check_winner() is True:
                label.config(text=(players[0]+" wins"))

            elif check_winner() == "Tie":
                label.config(text="Tie!")

        else:

            buttons[row][column]['text'] = player

            if check_winner() is False:
                player = players[0]
                label.config(text=(players[0]+" turn"))

            elif check_winner() is True:
                label.config(text=(players[1]+" wins"))

            elif check_winner() == "Tie":
                label.config(text="Tie!")

#A defined function that will see if the winner meets these requirements, this function was used in the beginning
#To show that functions can be used whenever once they are created

    def check_winner():

#The for statements (that are labelled as "for") are created to help show, through the color yellow, that a winner has been declared

    for row in range(3):
    if buttons[row][0]['text'] == buttons[row][1]['text'] == buttons[row][2]['text'] != "":
    buttons[row][0].config(bg="yellow")
    buttons[row][1].config(bg="yellow")
    buttons[row][2].config(bg="yellow")
    return True

#The for statements (that are labelled as "for") are created to help show, through the color yellow, that a winner has been declared

    for column in range(3):
    if buttons[0][column]['text'] == buttons[1][column]['text'] == buttons[2][column]['text'] != "":
    buttons[0][column].config(bg="yellow")
    buttons[1][column].config(bg="yellow")
    buttons[2][column].config(bg="yellow")
    return True

#The for statements (that are labelled as "for") are created to help show, through the color yellow, that a winner has been declared

    if buttons[0][0]['text'] == buttons[1][1]['text'] == buttons[2][2]['text'] != "":
    buttons[0][0].config(bg="yellow")
    buttons[1][1].config(bg="yellow")
    buttons[2][2].config(bg="yellow")
    return True

#The for statements (that are labelled as "for") are created to help show, through the color blue, that a winner has been declared

    elif buttons[0][2]['text'] == buttons[1][1]['text'] == buttons[2][0]['text'] != "":
    buttons[0][2].config(bg="yellow")
    buttons[1][1].config(bg="yellow")
    buttons[2][0].config(bg="yellow")
    return True

    elif empty_spaces() is False:
#The for statements (that are labelled as "for") are created to help show, through the color red, that a tie has been declared
    for row in range(3):
    for column in range(3):
    buttons[row][column].config(bg="red")
    return "It's a Tie"

    else:
    return False

#defined function that will construct the tic tac toe board

    def empty_spaces():

#the space variable is created to give an exact number of spaces needed on the board

    spaces = 9

    for row in range(3):
    for column in range(3):
    if buttons[row][column]['text'] != "":
    spaces -= 1

    if spaces == 0:
    return False
    else:
    return True

#a defined function that will be called once the player(s) decide to call a new game at any point throughout the program

    def new_game():

    global player

    player = random.choice(players)

    label.config(text=player+" turn")

    for row in range(3):
    for column in range(3):
    buttons[row][column].config(text="",bg="#F0F0F0")

#Replaced the imported function "Tk()" with the variable window to keep the continuity of a pop up window of a tic-tac-toe game appearing for this program

    window = Tk()

#The title of the game, it's being set with the function inside of the imported function "Tk()" which was changed to "window" for this program

    window.title("Tic-Tac-Toe")

#designated the symbols that will be used from both players in the tic-tac-toe game

    players = ["x","o"]
    player = random.choice(players)

#Declaring the basic layout for the new board once a new game will begin

    buttons = [[0,0,0],
           [0,0,0],
           [0,0,0]]
#These variables decides the font of the words we will use for the game such as "restart" and "turn"

    label = Label(text=player + " turn", font=('consoles',40))
    label.pack(side="top")

#the function used to create a restart function whenever the user prompts it

    reset_button = Button(text="restart", font=('consoles',20,    command=new_game)
    reset_button.pack(side="top")

    frame = Frame(window)
    frame.pack()

#the for function here is responsible for creating the font and sizing of the text on the board


    for column in range(3):
    buttons[row][column] = Button(frame, text="",font=        ('consoles',40), width=9, height=2,
    command= lambda row=row, column=column: next_turn(row,column))
    buttons[row][column].grid(row=row,column=column)

#display tic-tac-toe board

    window.mainloop()


## Acknowledgements

 - A YouTube Programmer "BroCode" who provided tips, project idea, and basic structure of program 


## 🔗 Links
http://www.youtube.com/@BroCodez 

