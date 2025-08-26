# CodeClash Server

## Overview

CodeClash is a real-time competitive programming platform that allows developers to compete in coding challenges, participate in contests, and improve their programming skills through a rating-based system.

## Features

### 🎮 Live 1v1 Coding Battles
- Real-time matchmaking based on ELO-style ratings
- Multiple difficulty modes
- Skill-based opponent matching
- Live problem solving with immediate feedback

### 🏆 Contest System
- Create and manage programming contests
- Public and private contest options
- Leaderboards and rankings
- Custom problem creation and management

### ⚙️ Code Execution
- Support for multiple languages:
  - Python
  - JavaScript
  - Java
  - C
  - C++
- Secure sandboxed environment
- Real-time execution feedback

### 📊 User Progression
- ELO-based rating system (800-1600+ range)
- Skill level categorization (BEGINNER, INTERMEDIATE, PRO)
- Performance tracking and statistics
- Win streaks and personal records

## Technical Architecture

### Core Stack
- **Backend**: Node.js with TypeScript
- **Database**: PostgreSQL with Prisma ORM
- **Caching & Real-time**: Redis
- **Websockets**: Socket.io for real-time communication
- **Authentication**: JWT with OAuth 2.0 support (Google/GitHub)

### Key Components

#### User Authentication System
- Email/password authentication
- OAuth integration with Google and GitHub
- OTP verification for email validation
- Session management with device tracking

#### Matchmaking Service
- Dynamic rating-based opponent matching
- Adjustable rating ranges based on queue time
- Real-time match creation and management
- Multiple game modes

#### Rating System
- ELO-style rating calculations
- Initial ratings based on self-reported skill level:
  - BEGINNER: 800
  - INTERMEDIATE: 1200
  - PRO: 1600
- K-factor of 32 for rating adjustments
- Dynamic skill level reassignment based on performance

#### Code Execution System
- Serverless execution via AWS Lambda
- Job queue management with BullMQ
- Sandboxed environments for secure code testing
- Time and memory limit enforcement

#### Contest Management
- Full contest lifecycle management (creation, running, completion)
- Problem creation and management
- Participant registration and tracking
- Real-time leaderboard updates
- Contest-specific submissions and scoring

## API Structure

The API is organized into several major modules:

- **Auth**: User registration, login, OAuth, and session management
- **User**: Profile management, skill updates, submissions history
- **Match**: Real-time match creation, game state management, submissions
- **Contest**: Contest creation, management, participation, and submissions
- **Dashboard**: Stats, leaderboards, and user performance metrics
- **Admin**: Administrative functions for platform management

## Socket Events

Real-time functionality is implemented via Socket.io events:

- Matchmaking events (join queue, match found)
- Game events (start, state updates, submission results)
- Player events (join, disconnect, reconnect)

## Installation and Setup

```bash
# Clone repository
git clone https://github.com/your-org/codeclash-server.git
cd codeclash-server

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Run database migrations
npx prisma migrate dev

# Start development server
npm run dev
```

## Environment Requirements

- Node.js 16+
- PostgreSQL 12+
- Redis 6+
- AWS account for Lambda functions

## License

MIT License

---

*CodeClash - Where coding skills clash in real-time battles*