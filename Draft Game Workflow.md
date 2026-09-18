# hangman
hangman game

Hangman — Game Flow

Start game

Initialize game state
    pick a random word from the word list
    set guessed letters to empty
    set lives to 6
    set game over to False

Loop — repeat while game is not over:
    Display current information
        word progress with blanks
        letters already guessed
        lives remaining
        
Ask player for a letter

Validate input — if invalid, ask again without costing a life
    must be exactly one character
    must be a letter
    must not already be guessed
    
Add letter to guessed letters

Check the letter
    in the word → reveal it, lives unchanged
    not in the word → lose one life
    
Check win condition — all letters revealed → game over, player wins
Check lose condition — lives reach zero → game over, player loses

End game
    show win or lose message
    reveal the secret word



    game_state = {
    "score": 0,
    "lives": 3,
    "game_over": False
}y^