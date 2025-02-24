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
