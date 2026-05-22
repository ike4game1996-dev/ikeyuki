# Ikeyuki Admin Dashboard

A Next.js admin dashboard for managing events, participants, and game divisions.

## Features

- **Event Management**: Create and manage events
- **Participant Management**: Add participants to events and select them with checkboxes
- **Event Selection**: Choose from a dropdown of event types (Football, Basketball, etc.)
- **Game Creation**: Automatically create and divide participants into games
- **Database Integration**: PostgreSQL with Prisma ORM

## Tech Stack

- Next.js 14
- React 18
- TypeScript
- Prisma ORM
- Tailwind CSS
- PostgreSQL

## Getting Started

### Prerequisites

- Node.js 18+ installed
- PostgreSQL database

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ike4game1996-dev/ikeyuki.git
   cd ikeyuki
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables:
   ```bash
   cp .env.example .env.local
   ```
   Update `.env.local` with your PostgreSQL database URL.

4. Run database migrations:
   ```bash
   npx prisma migrate dev --name init
   ```

5. Start the development server:
   ```bash
   npm run dev
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
├── app/
│   ├── api/              # API routes
│   ├── events/           # Events pages
│   ├── participants/     # Participants page
│   ├── games/            # Games page
│   ├── layout.tsx        # Root layout
│   ├── page.tsx          # Home page
│   └── globals.css       # Global styles
├── prisma/
│   └── schema.prisma     # Database schema
├── package.json
└── tsconfig.json
```

## Database Schema

### Event
- `id`: Primary key
- `name`: Unique event name
- `description`: Optional event description
- `createdAt`: Creation timestamp
- `updatedAt`: Update timestamp

### Participant
- `id`: Primary key
- `name`: Participant name
- `eventId`: Foreign key to Event
- `createdAt`: Creation timestamp
- `updatedAt`: Update timestamp

### Game
- `id`: Primary key
- `name`: Game name
- `eventId`: Foreign key to Event
- `createdAt`: Creation timestamp
- `updatedAt`: Update timestamp

### GameParticipant
- `id`: Primary key
- `gameId`: Foreign key to Game
- `participantId`: Foreign key to Participant
- `createdAt`: Creation timestamp

## Usage

1. **Create an Event**: Go to Events page and create a new event
2. **Add Participants**: Click on an event and add participants
3. **Select Participants**: Check the participants you want to add to a game
4. **Choose Event Type**: Select a game event from the dropdown
5. **Save to Game**: Click "Save to Game" to assign participants

## API Endpoints

- `GET /api/events` - Get all events
- `POST /api/events` - Create a new event
- `GET /api/events/[id]` - Get specific event
- `DELETE /api/events/[id]` - Delete an event
- `GET /api/events/[id]/participants` - Get event participants
- `POST /api/events/[id]/participants` - Add participant to event
- `POST /api/events/[id]/assign-to-game` - Assign participants to game
- `GET /api/participants` - Get all participants
- `GET /api/games` - Get all games
- `POST /api/games` - Create a new game
- `DELETE /api/games/[id]` - Delete a game

## License

MIT
