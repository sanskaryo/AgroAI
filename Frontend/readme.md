# Agro pluse ai - Agricultural AI Assistant

A comprehensive agricultural assistance platform built with Next.js, designed to help farmers with various agricultural activities through AI-powered tools and insights.

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ (LTS recommended)
- PostgreSQL database
- pnpm package manager
- FastAPI backend (optional, for full functionality)

### Installation



2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   ```

   Edit `.env.local` with your configuration:
   ```env
   DATABASE_URL="postgresql://user:password@localhost:5432/pragati_db"
   NEXTAUTH_URL="http://localhost:3000"
   NEXTAUTH_SECRET="your-nextauth-secret"
   NEXT_PUBLIC_API_URL="http://localhost:8000"
   ```

4. **Set up the database**
   ```bash
   # Generate Prisma client
   pnpm prisma generate

   # Run database migrations
   pnpm prisma db push
   ```

5. **Run the development server**
   ```bash
   pnpm dev
   ```

   Open [http://localhost:3000](http://localhost:3000) in your browser.

## 📁 Project Structure

```
├── app/                    # Next.js app directory
│   ├── api/               # API routes
│   ├── dashboard/         # Dashboard pages
│   ├── signin/           # Authentication pages
│   └── ...
├── components/            # Reusable React components
│   ├── ui/               # UI components (Radix UI)
│   ├── agricultural-ai-chatbot.tsx
│   └── ...
├── lib/                   # Utility functions and configurations
│   ├── auth.ts           # Authentication setup
│   ├── prisma.ts         # Database client
│   └── ...
├── prisma/               # Database schema and migrations
│   ├── schema.prisma     # Database schema
│   └── migrations/       # Database migrations
├── hooks/                # Custom React hooks
├── types/                # TypeScript type definitions
├── data/                 # Static data files
└── docs/                 # Documentation
```

## 🔧 Configuration

### Required Environment Variables

Copy `.env.example` to `.env.local` and configure:

- **DATABASE_URL**: PostgreSQL connection string
- **NEXTAUTH_URL**: Your app's URL (http://localhost:3000 for development)
- **NEXTAUTH_SECRET**: Random secret for NextAuth.js
- **NEXT_PUBLIC_API_URL**: FastAPI backend URL (optional)

### Database Setup

The project uses PostgreSQL with Prisma ORM. The schema includes:

- **User**: User authentication and profile
- **ChatSession**: Chat conversation sessions
- **ChatMessage**: Individual chat messages
- **IrrigationCalendar**: Irrigation scheduling records

### Optional: FastAPI Backend

For full AI functionality, set up the FastAPI backend:

1. Clone the backend repository
2. Install Python dependencies
3. Run the FastAPI server on port 8000
4. Update `NEXT_PUBLIC_API_URL` in your environment

## 🛠️ Development Scripts

```bash
# Development
pnpm dev              # Start development server
pnpm build           # Build for production
pnpm start           # Start production server
pnpm lint            # Run ESLint
pnpm type-check      # Run TypeScript type checking

# Database
pnpm prisma studio   # Open Prisma Studio
pnpm prisma generate # Generate Prisma client
pnpm prisma db push  # Push schema changes to database

# Setup
./scripts/dev-setup.sh help  # Show setup options
```

## 🌾 Features

### Core Features
- **AI Chat Assistant**: Multilingual agricultural advice
- **Crop Disease Detection**: Image-based disease identification
- **Weather Forecasting**: Local weather information
- **Irrigation Scheduling**: Smart irrigation planning
- **Fertilizer Recommendations**: Crop-specific fertilizer advice

### Authentication
- Secure user registration and login
- Aadhar number verification
- Session management with NextAuth.js

### Multi-language Support
- Support for multiple Indian languages
- Real-time message translation
- Language preference settings

## 📱 Mobile Support

The application is fully responsive and works on:
- Desktop computers
- Tablets
- Mobile phones
- QR code scanning for mobile devices

## 🔒 Security

- Password hashing with bcrypt
- JWT token authentication
- Input validation with Zod
- CSRF protection
- Rate limiting (recommended for production)

## 🚀 Deployment

### Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Add environment variables in Vercel dashboard
3. Deploy automatically on push

### Manual Deployment
```bash
pnpm build
pnpm start
```

### Production Checklist
- [ ] Set up production database
- [ ] Configure environment variables
- [ ] Set up domain and SSL
- [ ] Configure monitoring and logging
- [ ] Set up backup strategy

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📚 Documentation

- [API Integration Guide](./docs/API_INTEGRATION.md)
- [Development Stages](./docs/DEVELOPMENT_STAGES.md)
- [Project Documentation](./docs/PROJECT_DOCUMENTATION.md)

## 🐛 Troubleshooting

### Common Issues

**Database Connection Error**
- Ensure PostgreSQL is running
- Check DATABASE_URL in .env.local
- Run `pnpm prisma db push`

**Build Errors**
- Clear .next folder: `rm -rf .next`
- Reinstall dependencies: `pnpm install`
- Check Node.js version (18+ required)

**Authentication Issues**
- Verify NEXTAUTH_SECRET is set
- Check NEXTAUTH_URL matches your domain

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Built with [Next.js](https://nextjs.org/)
- UI components from [Radix UI](https://www.radix-ui.com/)
- Database ORM with [Prisma](https://prisma.io/)
- Authentication with [NextAuth.js](https://next-auth.js.org/)