# Drop Blast - Telegram Arcade Game 🚀

[![Telegram WebApp](https://img.shields.io/badge/Telegram-WebApp-2AABEE?logo=telegram)](https://core.telegram.org/bots/webapps)
[![MIT License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![BB Contest Ready](https://img.shields.io/badge/BB_Contest-2024_Entry-blue)](https://bots.business)

<img src="assets/game-preview.gif" alt="Game Preview" width="300" align="right">

A high-performance arcade game built natively for Telegram WebApps, featuring dynamic gameplay mechanics and deep platform integration. Designed for the Bots.Business Development Contest with extensible architecture and modular configuration.

## 🌟 Key Features

### Core Gameplay Mechanics
| Feature                | Description                                  | Tech Implementation          |
|------------------------|----------------------------------------------|-------------------------------|
| Dynamic Element System | Procedurally generated falling objects      | HTML5 Canvas + RequestAnimationFrame |
| Power-up System        | Freeze time, score multipliers, bomb defuse | Custom Event Bus + Tween.js   |
| Collision Detection    | Pixel-perfect click detection               | Bounding Box + Ray Casting    |
| Progressive Difficulty | Adaptive speed scaling                      | Time-based curve algorithms   |

### Telegram Integration
- **User Profile System**  
  ```javascript
  // src/telegram/integration.js
  export function loadTelegramProfile() {
    const user = Telegram.WebApp.initDataUnsafe.user;
    return {
      name: `${user.first_name} ${user.last_name}`,
      avatar: user.photo_url,
      premium: user.is_premium
    };
  }
