# React + TypeScript + Vite = Hangman Game for MLB and NBA Teams

This project is an already exisiting project by a Youtube Channel named "Web Dev Simplified", here is the link of the Youtube Video: [This Is A Great Beginner React/TypeScript Project](https://youtu.be/-ONUyenGnWw?list=TLPQMTgwMTIwMjXoEaq1Xe4FLg)

## Changes that I made:

- Instead of English words to use for the users to guess, I replaced it with Major League Baseball(MLB) and National Basketball Association(NBA) team names.
- The normal Hangman rules still applies with the head, body, left arm, right arm, left leg and right leg, accordingly.

### Context of a Hangman Game:

Hangman is a classic word-guessing game where one player thinks of a word, and the other tries to guess it letter by letter. The word's letters are represented by blank spaces, and each incorrect guess adds a part to a "hangman" figure, typically drawn on a gallows. The game ends when the guesser either completes the word or the hangman drawing is finished, symbolizing the player's loss.****

### Features:

- Win and Loss System. Limited to 6 Incorrect Letters, corresponds to the 6 major parts of a Hangman Drawing, that results to a Loss:

```tsx
const incorrectLetters = guessedLetters.filter(
    (letter) => !wordToGuess.includes(letter)
  );

  const isLoser = incorrectLetters.length >= 6;
  const isWinner = wordToGuess
    .split("")
    .filter((letter) => letter !== " ")
    .every((letter) => guessedLetters.includes(letter));
```
