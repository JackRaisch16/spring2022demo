#Jackson Raisch
#1st year, Graduation: 2025
#Scordle
#spring 2022 demo
import re
import random
"""
preposal = open("preposal.md", "r")
proposal = open("proposal.md", "r")
status = open("status.md", "r")
print(preposal.read())
print(proposal.read())
print(status.read())
"""
#Opens file with all english words
data = open("words.txt", "r")
text = data.readlines()


#Creates a list of five letter words applicable for wordle from list of words
fiveWords = []
for line in text:
    word = line.split()
    if word[0].islower() and len(line)==6:
        word = str(word)[2:7]
        fiveWords.append(word)


#Selects random word from five words list
def gameWord():
    secretWord = random.choice(fiveWords)
    return(secretWord)

    
#Runs wordle game until win or loss
def game():
    secretWord = gameWord()
    #print(secretWord)
    guesses= 0
    remLetters = list("abcdefghijklmnopqrstuvwxyz")
    firstLetter = secretWord[0]
    secondLetter = secretWord[1]
    thirdLetter = secretWord[2]
    fourthLetter = secretWord[3]
    fifthLetter = secretWord[4]
    winorlose = ""
    while guesses<6:    
        gameBoard = ["incorrect","incorrect","incorrect","incorrect","incorrect"]
        playerResponse = input("Enter word: ")
        checker = False
        while not checker:
            if playerResponse in fiveWords:
                checker = True
            else:
                print("Invalid word")
                playerResponse = input("Enter word: ")
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
        if gameBoard[0] == "incorrect":
            if playerResponse[0] in remLetters:
                remLetters.remove(playerResponse[0])
        if gameBoard[1] == "incorrect":
            if playerResponse[1] in remLetters:
                remLetters.remove(playerResponse[1])
        if gameBoard[2] == "incorrect":
            if playerResponse[2] in remLetters:
                remLetters.remove(playerResponse[2])
        if gameBoard[3] == "incorrect":
            if playerResponse[3] in remLetters:
                remLetters.remove(playerResponse[3])
        if gameBoard[4] == "incorrect":
            if playerResponse[4] in remLetters:
                remLetters.remove(playerResponse[4])


        if gameBoard[0]=="correct" and gameBoard[1]=="correct" and gameBoard[2]=="correct" and gameBoard[3]=="correct" and gameBoard[4]=="correct":
            guesses+= 5
            winorlose = "Win!"
        else:
            winorlose = "Lost!"
            print(gameBoard)
            print("Remaining Letters: " ,remLetters)
    print(winorlose, "Correct Word was: ", secretWord)
    return(winorlose)

#Tracks multiple games until user decides to stop playing
def multGames():
    done = False
    wins = 0
    highScore = 0
    while not done:
        outcome = game()
        if outcome == "Win!":
            wins +=1
        elif outcome == "Lost!":
            wins = 0
        if wins>=highScore:
            highScore = wins
        print("Wins in a Row: ", wins)
        response = input("Would you like to play again?(Y/N): ")
        if response == "N" or response == "n":
            done = True


    print("High Score of Session: ", highScore)
    return (highScore)

multGames()
    
        
        
        
