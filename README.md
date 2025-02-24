# Drop Blast - Telegram WebApp Game

[![Telegram WebApp](https://img.shields.io/badge/Telegram-WebApp-2AABEE?logo=telegram)](https://core.telegram.org/bots/webapps)
![License](https://img.shields.io/badge/License-MIT-green)

An addictive arcade-style game built for Telegram WebApps where players tap falling elements to score points while avoiding bombs and using power-ups.

![Gameplay Screenshot](/path/to/screenshot.png) <!-- Add actual screenshot path -->

## Features

🎮 **Core Gameplay**
- Dynamic falling elements with varying speeds/sizes
- Bomb avoidance mechanics
- Ice power-up to slow down elements
- Real-time score tracking
- High score system with cloud storage

💎 **Premium Features**
- Telegram user profile integration
- Emoji status rewards for premium users
- Story sharing with score challenges
- Home screen installation prompts

✨ **Special Effects**
- Particle explosion animations
- Screen freeze effect with ice particles
- Bomb shake effect
- Floating UI elements with glassmorphism design

📱 **Telegram Integration**
- Native WebApp UI components
- Cloud storage for high scores
- Fullscreen mode support
- Telegram BackButton integration
- Device vibration feedback

# 🎮 Game Guide

## How It Works

### 1. **Starting the Game**
- **Launch the Game**: Open the game through your Telegram bot or WebApp link.
- **Main Menu**:
  - See your profile (name, avatar, and high score).
  - Tap **"Start Game"** to begin.
  - Use **"Fullscreen"** (if available) for an immersive experience.

![Main Menu Screenshot](path_to_screenshot.jpg)

```javascript
// Initialize Telegram WebApp
const tg = window.Telegram.WebApp;
tg.expand(); // Expands the app to full height
tg.setHeaderColor('#0f172a'); // Sets the header color
tg.setBackgroundColor('#1e293b'); // Sets the background color
```

---

### 2. **Gameplay Basics**
- **Objective**: Tap falling elements to score points while avoiding bombs.
- **Falling Elements**:
  - 🟢 **Normal Elements**: Tap to collect (+10 points).
  - 💣 **Bombs**: Avoid tapping (lose -30 points if hit).
  - ❄️ **Ice Power-Ups**: Tap to freeze time and slow down elements.
- **Timer**: You have **60 seconds** to score as many points as possible.

![Gameplay Screenshot](path_to_screenshot.jpg)

```javascript
// Element spawning logic
function spawnElement() {
  const type = Math.random() < 0.15 ? 'bomb' : 'element';
  elements.push({
    type,
    x: Math.random() * canvas.width,
    y: -50,
    speed: 120 + Math.random() * 40
  });
}
```

---

### 3. **Power-Ups**
- **Freeze Power-Up**:
  - Temporarily slows down all falling elements.
  - Activates for **4 seconds** (configurable).
  - Limited uses per game.
- **Combo System**:
  - Chain consecutive taps for bonus points.
  - Multiplier increases with each successful hit.

![Power-Up Screenshot](path_to_screenshot.jpg)

```javascript
// Freeze power-up logic
function activateFreeze() {
  isFrozen = true;
  elements.forEach(el => el.speed *= 0.2); // Slow down elements
  setTimeout(() => isFrozen = false, 4000); // Reset after 4 seconds
}
```

---

### 4. **Game Over**
- When the timer runs out, the game ends.
- **Game Over Screen**:
  - See your final score.
  - Compare with your **high score** (saved via Telegram Cloud Storage).
  - Options:
    - 🔄 **Play Again**: Restart the game.
    - 📤 **Share to Story**: Post your score on Telegram (if supported).
    - 🏠 **Main Menu**: Return to the start screen.

![Game Over Screenshot](path_to_screenshot.jpg)

```javascript
// Save high score to Telegram Cloud Storage
function saveHighScore(score) {
  const highScore = Math.max(score, Telegram.CloudStorage.getItem('highScore') || 0);
  Telegram.CloudStorage.setItem('highScore', highScore);
}
```

---

### 5. **Advanced Features**
- **Telegram Integration**:
  - **Profile Display**: Shows your Telegram name and avatar.
  - **Story Sharing**: Share your score with friends.
  - **Emoji Status**: Premium users can set a custom emoji status.
- **Fullscreen Mode**: Optimized for mobile and desktop play.
- **Haptic Feedback**: Vibrates on bomb hits (if supported by the device).

![Advanced Features Screenshot](path_to_screenshot.jpg)

```javascript
// Share to Telegram Story
function shareToStory(score) {
  Telegram.WebApp.shareToStory({
    media: 'screenshot.jpg',
    caption: `I scored ${score} points in Drop Blast! 🚀`
  });
}
```

---

### 6. **Winning Strategy**
- Focus on tapping **normal elements** for consistent points.
- Use **ice power-ups** strategically during high-speed moments.
- Avoid **bombs** to prevent score penalties.
- Aim for **combos** to maximize your score multiplier.

![Winning Strategy Screenshot](path_to_screenshot.jpg)

```javascript
// Combo system logic
let comboCount = 0;
function processClick(el) {
  if (el.type === 'element') {
    comboCount++;
    score += 10 * Math.min(comboCount, 4); // Max 4x multiplier
  } else {
    comboCount = 0; // Reset combo on bomb hit
  }
}
```

---

### 7. **Emoji Status System**
For Premium Users: Players with Telegram Premium can set a custom emoji status.

**How It Works**:
- Tap the emoji button next to your profile avatar.
- Grant permission to set your emoji status.
- A special emoji status is activated for **1 hour**.

![Emoji Status Screenshot](path_to_screenshot.jpg)

```javascript
// Emoji status logic
function setEmojiStatus() {
  tg.requestEmojiStatusAccess((isGranted) => {
    if (isGranted) {
      tg.setEmojiStatus('6064140861539618361', { duration: 3600 }, (success) => {
        if (success) {
          tg.showAlert("Special status activated! 🎉");
        } else {
          tg.showAlert("Failed to set emoji status. Try again!");
        }
      });
    } else {
      tg.showAlert("Permission denied. Enable emoji status access in settings.");
    }
  });
}
```

---

This section provides a step-by-step explanation of how the game works, with **key code snippets** for each major feature. It’s designed to be both **user-friendly** and **developer-friendly**, helping players understand the game mechanics while giving developers insights into the implementation.

## Installation & Setup

### Prerequisites
- Telegram client (mobile or desktop)
- Web server for hosting
- Basic understanding of Telegram Bot API

### Deployment
1. Clone repository:
   ```bash
   git clone https://github.com/yourusername/drop-blast.git



# Drop Blast - Telegram WebApp Game 🚀

[![Telegram WebApp](https://img.shields.io/badge/Telegram-WebApp-2AABEE?logo=telegram)](https://core.telegram.org/bots/webapps)
![License](https://img.shields.io/badge/License-MIT-green)
![GitHub Last Commit](https://img.shields.io/github/last-commit/yourusername/drop-blast)

<img src="assets/gameplay.gif" alt="Game Preview" width="300" align="right">

An addictive arcade-style game built for Telegram WebApps with customizable gameplay mechanics and deep Telegram integration. Players collect falling elements while avoiding bombs and using power-ups to achieve high scores.

## 🎮 Core Features

### Gameplay Mechanics
| Feature                | Customization Point          | Default Value     |
|------------------------|------------------------------|-------------------|
| Element Spawning       | `config.spawnRate`           | 300ms            |
| Element Speeds         | `config.elementSpeed`        | 120-160px/s      |
| Bomb Probability       | `config.bombChance`          | 15%              |
| Freeze Duration        | `config.iceDuration`         | 4000ms           |
| Score Values           | `processClick()` multipliers | +10/-30 points   |

### Telegram Integration Features
```javascript
// Main integration points (telegram-webapp.js)
const tgConfig = {
  expandOnStart: true,
  disableSwipes: true,
  themeColors: {
    header: '#0f172a',
    bg: '#1e293b',
    text: '#f8fafc'
  },
  socialFeatures: {
    storySharing: true,
    homeScreenPrompt: true,
    emojiStatus: true
  }
};
