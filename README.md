# my-scratch-projects
# 🎓 School Navigator: MCQ Adventure Game

A Scratch-based educational game where players navigate through a virtual school environment while answering multiple-choice questions to progress through different locations.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Game Mechanics](#game-mechanics)
- [How to Play](#how-to-play)
- [Game Development](#game-development)

---

## 🎮 Overview

School Navigator is an interactive educational game built in Scratch that combines exploration with learning. Players move through various school locations (classrooms, library, cafeteria, etc.) and must correctly answer MCQ (Multiple Choice Questions) to unlock new areas and progress through the game.

**Genre:** Educational Adventure  
**Platform:** Scratch 3.0  
**Target Audience:** Students, educators, and anyone who enjoys educational games  
**Difficulty:** Beginner to Intermediate

---

## ✨ Features

- **Interactive School Map**: Navigate through multiple school locations with backdrop changes
- **MCQ Challenge System**: Answer questions by clicking option buttons (A, B, C, D)
- **Progressive Difficulty**: Questions get harder as you advance through locations
- **Multiple Subjects**: Questions span various academic topics
- **Sound Effects**: Audio feedback for answers and navigation
- **Animated Character**: Player sprite moves between locations

---

## 🎯 Game Mechanics

### Navigation System
- Players start at the **School Entrance** backdrop
- Click on arrows/doors to move between connected locations
- Locations are unlocked after answering questions correctly

### Question System
- Multiple-choice questions displayed as text on screen
- Four clickable buttons (A, B, C, D) for answer options
- Questions stored in lists (Question, OptionA, OptionB, OptionC, OptionD, CorrectAnswer)
- Correct answers trigger:
  - Unlock next location
- Wrong answers trigger:
  - a Gameover Screen
  - They have to Retry

### Broadcasts (Messages)
- `Start Game` - Initialize game from title screen
- `Correct Answer` - Handle point award and unlock
- `Wrong Answer` - Handle penalty and retry
- `Game Over` - End game and show final score
- `Reset Game` - Return to start screen

---

## 🕹️ How to Play

### Starting the Game
1. Click the **Green Flag** 🏳️ to start
2. Click "Start Game" button on title screen
3. Read the introduction and game rules

### Playing the Game
1. **Read the question** displayed on screen
2. **Click your answer** (Button A, B, C, or D)
3. **Navigate** by clicking arrows/doors to move to new locations
4. **Complete all locations** to finish the game

### Controls
- **Mouse Click** - Select answers
- **Arrow Keys** - Navigating the map
- **Green Flag 🏳️** - Start/Restart game
- **Red Stop Sign 🛑** - Stop game

### Example Gameplay Flow
```
Title Screen → Click "Start Game"
  ↓
School Entrance → Question appears
  ↓
Click Answer "B" → Correct!
  ↓
Move to "SAS" → Get Star
  ↓
New Question appears → Click Answer
  ↓
Continue until all locations visited
  ↓
Final Score Screen → Click "Play Again" or "Home Screen"
```

---

## 👨‍💻 Game Development

### Project Structure in Scratch

```
School Navigator Game
│
├── Sprites
│   ├── Player (Main character)
│   ├── QuestionBox (Text display)
│   ├── ButtonA (Answer option)
│   ├── ButtonB (Answer option)
│   ├── ButtonC (Answer option)
│   ├── ButtonD (Answer option)
│   ├── CorrectSprite (Feedback)
│   ├── WrongSprite (Feedback)
│   ├── ScoreCounter
│   ├── NavigationArrows
│   └── StartButton
│
├── Backdrops
│   ├── TitleScreen
│   ├── SchoolEntrance
│   ├── Hallway
│   ├── ClassroomA
│   ├── ClassroomB
│   ├── Library
│   ├── Cafeteria
│   ├── ScienceLab
│   ├── PrincipalsOffice
│   └── GameOverScreen
│
└── Lists & Variables
    ├── Variables
    │   ├── Score
    │   ├── CurrentLocation
    │   ├── QuestionNumber
    │   └── LocationsUnlocked
    │
    └── Lists
        ├── Questions
        ├── OptionA
        ├── OptionB
        ├── OptionC
        ├── OptionD
        └── CorrectAnswers
```

### Key Code Blocks

#### Initializing the Game (Stage or Player Sprite)
```scratch
when green flag clicked
switch backdrop to [TitleScreen v]
set [Score v] to [0]
set [QuestionNumber v] to [1]
set [LocationsUnlocked v] to [1]
hide all question sprites
show [Start Button v]
```

#### Loading Questions (Question Display Sprite)
```scratch
when I receive [Load Question v]
set [CurrentQuestion v] to (item (QuestionNumber) of [Questions v])
set [OptionAText v] to (item (QuestionNumber) of [OptionA v])
set [OptionBText v] to (item (QuestionNumber) of [OptionB v])
set [OptionCText v] to (item (QuestionNumber) of [OptionC v])
set [OptionDText v] to (item (QuestionNumber) of [OptionD v])
show
```

#### Checking Answer (Button Sprites)
```scratch
when this sprite clicked
if <(MyAnswer) = (item (QuestionNumber) of [CorrectAnswers v])> then
    broadcast [Correct Answer v]
    change [Score v] by (10)
    play sound [Ding v]
else
    broadcast [Wrong Answer v]
    change [Score v] by (-5)
    play sound [Buzz v]
end
```

#### Moving Between Locations (Navigation Arrows)
```scratch
when this sprite clicked
if <(LocationsUnlocked) > [2]> then
    switch backdrop to [Hallway v]
    broadcast [Load Question v]
    change [QuestionNumber v] by (1)
else
    say [Locked! Answer the question first.] for (2) seconds
end
```

### Lists Setup Example

**Questions List:**
1. "What is 2 + 2?"
2. "What is the capital of France?"
3. "Who wrote Romeo and Juliet?"
4. "What is H2O?"

**OptionA, B, C, D Lists:**
(Each list has 4 items corresponding to each question)

**CorrectAnswers List:**
1. "B"
2. "C"
3. "A"
4. "D"
