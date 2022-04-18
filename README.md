#spring 2022 demo
import re
import random


preposal = open("preposal.md", "r")
proposal = open("proposal.md", "r")
status = open("status.md", "r")
#print(preposal.read())
#print(proposal.read())
#print(status.read())


data = open("words.txt", "r")
text = data.readlines()
fiveWords = []
for line in text:
    word = line.split()
    if word[0].islower() and len(line)==6:
        fiveWords.append(word)

def gameWord():
    randomWord = random.choice(fiveWords)
    secretWord= str(randomWord)[2:7]
    return(secretWord)

   


def game():
    secretWord = gameWord()
    guesses= 0
    firstLetter = secretWord[0]
    secondLetter = secretWord[1]
    thirdLetter = secretWord[2]
    fourthLetter = secretWord[3]
    fifthLetter = secretWord[4]
    winorlose = ""
    checker = True
    while guesses<6:
        gameBoard = ["incorrect","incorrect","incorrect","incorrect","incorrect"]
        playerResponse = input("Enter word ")
        guesses+=1
        if playerResponse[0] in secretWord:
            gameBoard[0] = "in word"
            if playerResponse[0] == firstLetter:
                gameBoard[0] = "correct"
        if playerResponse[1] in secretWord:
            gameBoard[1] = "in word"
            if playerResponse[1] == secondLetter:
                gameBoard[1] = "correct"
        if playerResponse[2] in secretWord:
            gameBoard[2] = "in word"
            if playerResponse[2] == thirdLetter:
                gameBoard[2] = "correct"
        if playerResponse[3] in secretWord:
            gameBoard[3] = "in word"
            if playerResponse[3] == fourthLetter:
                gameBoard[3] = "correct"
        if playerResponse[4] in secretWord:
            gameBoard[4] = "in word"
            if playerResponse[4] == fifthLetter:
                gameBoard[4] = "correct"
            

        
        if gameBoard[0]=="correct" and gameBoard[1]=="correct" and gameBoard[2]=="correct" and gameBoard[3]=="correct" and gameBoard[4]=="correct":
            guesses+= 5
            winorlose = "Win!"
        else:
            winorlose = "Lost!"
        print(gameBoard)
        
    return (winorlose,"Correct Word was ", secretWord)
print(game())

def scoreBoard():
    pass
    
        
        
        
