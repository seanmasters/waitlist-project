# Waitlist Project

A full-stack waitlist application with email notifications, built using modern web technologies.

## Project Structure

```
waitlist-project/
├── frontend/                # Next.js application
│   ├── src/
│   │   ├── app/            # Next.js app router
│   │   ├── components/     # React components
│   │   └── lib/           # Utility functions
│   └── public/            # Static assets
│
├── backend/               # Express API server
│   ├── src/
│   │   ├── controllers/  # Request handlers
│   │   ├── routes/       # API routes
│   │   └── config/      # Configuration files
│   └── prisma/          # Database schema and migrations
```

## Tech Stack

### Frontend
- Next.js 14 with App Router
- TypeScript
- TailwindCSS for styling
- React Hook Form for form handling

### Backend
- Express.js
- TypeScript
- Prisma ORM
- PostgreSQL database
- Email service (e.g., Resend/SendGrid)

## Getting Started

### Prerequisites
- Node.js 18 or higher
- PostgreSQL installed locally or a database URL
- Git

### Installation

1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/waitlist-project.git
cd waitlist-project
```

2. Install dependencies
```bash
# Install root dependencies
npm install

# Install frontend dependencies
cd frontend
npm install

# Install backend dependencies
cd ../backend
npm install
```

3. Set up environment variables

Frontend `.env`:
```plaintext
NEXT_PUBLIC_API_URL=http://localhost:3001
```

Backend `.env`:
```plaintext
PORT=3001
DATABASE_URL="postgresql://user:password@localhost:5432/waitlist"
EMAIL_API_KEY="your-email-service-api-key"
```

4. Set up the database
```bash
cd backend
npx prisma migrate dev
```

5. Start the development servers

In one terminal:
```bash
cd frontend
npm run dev
```

In another terminal:
```bash
cd backend
npm run dev
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:3001

## API Documentation

### Waitlist Endpoints

#### POST /api/waitlist/join
Create a new waitlist entry.

Request body:
```json
{
  "email": "user@example.com"
}
```

Response:
```json
{
  "success": true,
  "message": "Successfully joined waitlist"
}
```

## Database Schema

```prisma
model Subscriber {
  id        String   @id @default(cuid())
  email     String   @unique
  createdAt DateTime @default(now())
  status    String   @default("pending")
}
```

## Development

### Frontend Development

The frontend is built with Next.js and uses:
- TailwindCSS for styling
- TypeScript for type safety
- Modern React patterns and hooks

Key directories:
- `src/components`: Reusable React components
- `src/app`: Next.js app router pages
- `src/lib`: Utility functions and API clients

### Backend Development

The backend follows a modular structure:
- Controllers handle business logic
- Routes define API endpoints
- Config manages environment and setup
- Prisma handles database operations

## Deployment

### Frontend Deployment (Vercel)
1. Push your code to GitHub
2. Create a new project on Vercel
3. Connect your repository
4. Add environment variables
5. Deploy

### Backend Deployment (Railway/Heroku)
1. Create a new project
2. Connect your repository
3. Add environment variables
4. Configure build command: `npm run build`
5. Configure start command: `npm start`

### Database Deployment
1. Set up a PostgreSQL instance (e.g., Railway, Supabase)
2. Update DATABASE_URL in production environment
3. Run migrations: `npx prisma migrate deploy`

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.