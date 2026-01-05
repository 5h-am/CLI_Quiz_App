# 🎮 Akashic Records — CLI Quiz Application  
### A complete terminal-based quiz game built with Node.js

![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-CLI-green?style=for-the-badge)
![Project-Type](https://img.shields.io/badge/Project_Type-Quiz_App-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

---

## 📌 Overview  
**Akashic Records** is an interactive Command-Line Quiz Application built using **Node.js** and **readline-sync**.  
It supports multiple categories, sub-categories, randomized questions, answer validation, and both single and multiplayer modes.

The project was created as a learning exercise after mastering basic JavaScript concepts — showcasing a complete, functional CLI application with game logic, user input handling, and score tracking.

---

## ✨ Features

- ✔ **Single Player Mode** — Play solo and track your performance
- ✔ **Multiplayer Mode** — Compete with friends on the same device
- ✔ **Randomized Questions** — Fisher-Yates shuffle algorithm for fair gameplay
- ✔ **Clean Answer Validation** — Smart input parsing and matching
- ✔ **9 Major Categories** — Entertainment, Humanities, Science, Sports, Technology, Food, Lifestyle, Academic, Fun
- ✔ **Multiple Sub-categories** — Dive deep into specific topics
- ✔ **Score Tracking** — Complete history of all rounds played
- ✔ **Optional "Cheater Mode"** — Review correct answers after each round
- ✔ **Input Validation** — Handles invalid entries gracefully
- ✔ **Formatted CLI Output** — Clean, readable terminal interface

---

## 🧭 Table of Contents
- [Overview](#-overview)  
- [Features](#-features)  
- [Demo](#-demo)  
- [Installation](#-installation)  
- [Usage](#-usage)  
- [Project Structure](#-project-structure)  
- [Code Highlights](#-code-highlights)  
- [Future Improvements](#-future-improvements)  
- [Contributing](#-contributing)  
- [License](#-license)

---

## 🎥 Demo

```
Hello, Welcome to the Akashic Records

Modes: 

1.Single Player
2.MultiPlayer
3.Exit

What Do You Want to Play(1/2/3)?: 1

Enter your name: Alex

Select the categories you want to take quiz
1.Entertainment
2.Humanities
3.Science
4.Sports
5.Technology
6.Food
7.Lifestyle
8.Academic
9.Fun

Enter the category for the quiz: Science

Select a sub category
1. physics
2. chemistry
3. biology

Enter your sub category: physics

1. What is the speed of light in vacuum?
A. 299,792 km/s
B. 150,000 km/s
C. 400,000 km/s
D. 500,000 km/s

Enter your answer(A/B/C/D): a

[Question continues...]
```

---

## 🔧 Installation

### Prerequisites
- **Node.js** (v12 or higher)
- **npm** (comes with Node.js)

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/your-username/akashic-records.git
cd akashic-records
```

### 2️⃣ Install Dependencies
```bash
npm install readline-sync
```

### 3️⃣ Run the Application
```bash
node index.js
```

---

## 🚀 Usage

### Single Player Mode
1. Choose **Single Player** from the main menu
2. Enter your name
3. Select a **category** (e.g., Science, Entertainment, Sports)
4. Select a **sub-category** (e.g., Physics, Movies, Football)
5. Answer 20 randomized multiple-choice questions
6. View your score (right/wrong answers)
7. Optionally reveal correct answers
8. Continue with another round or exit
9. See your complete score history on exit

### Multiplayer Mode
1. Choose **Multiplayer** from the main menu
2. Enter the number of players
3. Each player enters their name sequentially
4. All players answer questions from the same category and sub-category
5. View individual scores after each player completes
6. See a final scoreboard with all players' results

---

## 📁 Project Structure

```
📦 akashic-records
 ┣ 📜 index.js              # Main quiz logic & CLI handling
 ┣ 📜 records.js            # Questions database (questions, answers, options)
 ┣ 📜 package.json          # Project dependencies
 ┗ 📜 README.md             # Project documentation
```

### Key Components

**`index.js`** — Contains:
- Game mode selection (single/multiplayer)
- Category and sub-category selection
- Quiz generation and question display
- Answer validation logic
- Score tracking and display
- User input handling

**`records.js`** — Contains:
- Question bank organized by category and sub-category
- Multiple choice options for each question
- Correct answers for validation

---

## 🧠 Code Highlights

### 🔹 Fisher–Yates Randomization Algorithm
Ensures truly random question order for fair gameplay:

```javascript
function randomness(ques, opt, ans) {
  for (let i = ques.length - 1; i > 0; i--) {
    let random = Math.floor(Math.random() * (i + 1));
    [ques[i], ques[random]] = [ques[random], ques[i]];
    [opt[i], opt[random]] = [opt[random], opt[i]];
    [ans[i], ans[random]] = [ans[random], ans[i]];
  }
  return [ques, opt, ans];
}
```

### 🔹 Clean Answer Validation
Smart matching that handles whitespace and case sensitivity:

```javascript
function answervalidation(options, correct, userInput) {
  const index = ["a", "b", "c", "d"].indexOf(userInput);
  if (index === -1) return NaN;
  return options[index].trim().toLowerCase() === correct ? 1 : NaN;
}
```

### 🔹 Object-Oriented Score Tracking
Using constructor functions to store player results:

```javascript
function Object_creator(rght, wrng, subc) {
  this.right = rght,
  this.wrong = wrng,
  this.sub_category = subc
}
```

### 🔹 Dynamic Category Selection
Input validation with retry logic:

```javascript
let categories_selector = () => {
  while (true) {
    console.log("\nSelect the categories you want to take quiz");
    console.log("1.Entertainment\n2.Humanities\n3.Science...");
    let category = input.question("\nEnter the category: ");
    let modified_category = category.replaceAll(" ", "").toLowerCase();
    for (let categ of categories) {
      if (modified_category === categ) {
        return modified_category;
      }
    }
    console.log("\nPlease, Enter a valid category");
  }
}
```

---

## 🌟 Future Improvements

Here are some ideas to take this project to the next level:

### Code Quality
- [ ] Convert global variables into a class-based structure
- [ ] Add comprehensive error handling
- [ ] Implement proper logging system
- [ ] Write unit tests for core functions
- [ ] Add JSDoc comments for better documentation

### Features
- [ ] Add difficulty levels (Easy, Medium, Hard)
- [ ] Implement question timer for timed challenges
- [ ] Add hints system (use a lifeline)
- [ ] Create a leaderboard with persistent high scores
- [ ] Export scores to JSON/CSV files
- [ ] Add category-specific achievements and badges

### User Experience
- [ ] Add colorful terminal UI using **Chalk** or **Colors**
- [ ] Implement progress bars using **CLI-Progress**
- [ ] Add ASCII art banners
- [ ] Include sound effects (terminal beeps)
- [ ] Create an animated loading screen

### Data Management
- [ ] Split questions into separate JSON files by category
- [ ] Implement a question management system
- [ ] Add ability to import custom question sets
- [ ] Create a question editor CLI tool

### Platform Expansion
- [ ] Build a **web version** using React or Vanilla JS
- [ ] Create a REST API for the question database
- [ ] Develop a mobile app version
- [ ] Add real-time multiplayer with WebSockets

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. Create a new branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a **Pull Request**

### Contribution Ideas
- Add more question categories
- Improve input validation
- Enhance the UI with colors and formatting
- Fix bugs or improve performance
- Write documentation or tutorials

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

Feel free to use, modify, or distribute this project for personal or commercial purposes.

---

## 👨‍💻 Author

Created with ❤️ as a learning project after mastering JavaScript fundamentals.

If you found this project helpful or interesting, please consider:
- ⭐ Starring the repository
- 🐛 Reporting bugs
- 💡 Suggesting new features
- 🤝 Contributing code

---

## 📞 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/5h-am/akashic-records/issues)
- **Discussions**: [GitHub Discussions](https://github.com/5h-am/akashic-records/discussions)

---

## 🙏 Acknowledgments

- **readline-sync** — For making CLI input handling simple
- **Fisher-Yates Algorithm** — For proper question randomization
- The JavaScript community for endless learning resources

---

<div align="center">

**[⬆ Back to Top](#-akashic-records--cli-quiz-application)**

Made with JavaScript and determination 🚀

</div>