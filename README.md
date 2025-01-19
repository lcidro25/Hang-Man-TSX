# React + TypeScript + Vite = Hangman Game for MLB and NBA Teams

This project is an already exisiting project by a Youtube Channel named "Web Dev Simplified", here is the link of the Youtube Video: [This Is A Great Beginner React/TypeScript Project](https://youtu.be/-ONUyenGnWw?list=TLPQMTgwMTIwMjXoEaq1Xe4FLg)

## Changes that I made:

- Instead of English words to use for the users to guess, I replaced it with Major League Baseball(MLB) and National Basketball Association(NBA) team names.
- The normal Hangman rules still applies with the head, body, left arm, right arm, left leg and right leg, accordingly.

### Context of a Hangman Game:

Hangman is a classic word-guessing game where one player thinks of a word, and the other tries to guess it letter by letter. The word's letters are represented by blank spaces, and each incorrect guess adds a part to a "hangman" figure, typically drawn on a gallows. The game ends when the guesser either completes the word or the hangman drawing is finished, symbolizing the player's loss.****

### Features:

- Win and Loss System. Limited to 6 Incorrect Letters, corresponds to the 6 major parts of a Hangman Drawing, that results to a Loss. Otherwise, the player will Win:

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

- Flexibiility. Both the system's keyboard and the physical keyboard of the user cna be used on playing:

```tsx
useEffect(() => {
    const handler = (e: KeyboardEvent) => {
      const key = e.key;
      if (!key.match(/^[a-z]$/)) return;

      e.preventDefault();
      addGuessedLetter(key);
    };

    document.addEventListener("keypress", handler);

    return () => {
      document.removeEventListener("keypress", handler);
    };
  }, [guessedLetters]);
```

- Hint System. I provided a hint button on whether the current word is a MLB or a NBA team name, for users who are not familiar to the sports team names.
```tsx
const showHint = () => {
    if (mlbTeams.includes(wordToGuess)) {
      setHint("MLB Team");
    } else if (nbaTeams.includes(wordToGuess)) {
      setHint("NBA Team");
    }
  };
```
