# PRAGATI Frontend Documentation

## Project Overview

PRAGATI is a comprehensive agricultural assistance platform built with Next.js, designed to help farmers with various agricultural activities through AI-powered tools and insights. The platform offers multilingual support and various smart farming features.

## Table of Contents
1. [Architecture](#architecture)
2. [Tech Stack](#tech-stack)
3. [Features](#features)
4. [Setup Requirements](#setup-requirements)
5. [Project Structure](#project-structure)
6. [Authentication & Security](#authentication--security)
7. [Database Schema](#database-schema)
8. [Features Implementation Details](#features-implementation-details)
9. [API Integration](#api-integration)
10. [Deployment](#deployment)

## Architecture

### Frontend Architecture
- Built with Next.js 15.2.4 (React 19)
- Uses App Router for routing
- Implements server-side rendering
- Component-based architecture
- Tailwind CSS for styling
- Radix UI for accessible components

### Backend Integration
- Connects to a FastAPI backend
- PostgreSQL database through Prisma ORM
- RESTful API communication
- Cloudflare Turnstile for bot protection

## Tech Stack

### Core Technologies
- **Frontend Framework**: Next.js 15.2.4
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Database ORM**: Prisma
- **Authentication**: NextAuth.js
- **UI Components**: Radix UI
- **State Management**: React Hooks
- **Form Handling**: React Hook Form with Zod validation

### Additional Libraries
- **Charts**: Recharts
- **Date Handling**: date-fns
- **Markdown**: react-markdown with remark-gfm
- **QR Code**: html5-qrcode
- **Carousel**: embla-carousel-react
- **Icons**: Lucide React

## Features

### Working Features
1. **Authentication System**
   - Sign up with username and Aadhar number
   - Secure password handling
   - Session management

2. **Chat Interface**
   - Multilingual support
   - Chat history preservation
   - Agent-based conversations
   - Message translation

3. **Agricultural Tools**
   - Weather forecast display
   - Crop disease prediction interface
   - Crop recommendation system
   - Fertilizer recommendation
   - Irrigation calendar

4. **User Profile Management**
   - Personal information management
   - Language preferences
   - Chat history access

### Partially Working/In Development
1. **QR Scanner**
   - Implementation present but may need backend integration
   
2. **Voice Controls**
   - Basic implementation present
   - Needs more language support

3. **Market Prices Interface**
   - UI implemented
   - Needs real-time data integration

### Planned Features
1. **Pest Prediction**
2. **Crop Yield Analytics**
3. **Agricultural News Feed**
4. **Community Features**

## Setup Requirements

### Prerequisites
1. Node.js (Latest LTS version)
2. PostgreSQL database
3. FastAPI backend service
4. pnpm package manager

### Environment Variables
```env
DATABASE_URL="postgresql://user:password@localhost:5432/db_name"
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="your-secret-key"
NEXT_PUBLIC_API_URL="http://localhost:8000"
TURNSTILE_SITE_KEY="your-turnstile-key"
TURNSTILE_SECRET_KEY="your-turnstile-secret"
```

### Installation Steps
1. Clone the repository
2. Run `pnpm install`
3. Set up environment variables
4. Run `pnpm prisma generate`
5. Run `pnpm dev` for development

## Project Structure

### Key Directories
- `/app`: Next.js application routes
- `/components`: Reusable React components
- `/lib`: Utility functions and API clients
- `/hooks`: Custom React hooks
- `/types`: TypeScript type definitions
- `/prisma`: Database schema and migrations
- `/public`: Static assets
- `/styles`: Global styles and Tailwind config
- `/docs`: Project documentation

## Database Schema

### Core Tables

1. **User**
   - Personal information
   - Authentication details
   - Linked to chat sessions and irrigation records

2. **ChatSession**
   - Chat metadata
   - Agent information
   - Language preferences
   - Links to messages

3. **ChatMessage**
   - Message content
   - Translation data
   - Metadata and attachments

4. **IrrigationCalendar**
   - Irrigation records
   - Water usage tracking
   - Area coverage data

## Features Implementation Details

### Authentication Flow
1. User registration with Aadhar validation
2. Password hashing using bcrypt
3. Session management with NextAuth.js
4. Protected routes in Next.js

### Chat System
1. Real-time messaging interface
2. Multiple AI agents for different agricultural purposes
3. Session management and history
4. Multi-language support with translation

### Agricultural Tools Integration
1. Weather data integration
2. ML model integration for predictions
3. Calendar management for irrigation
4. Image processing for disease detection

## API Integration

### FastAPI Backend Requirements
- Endpoint: `/api/v1/agriculture/respond`
- Authentication handling
- Multi-language support
- File upload capabilities

### API Service Layer
- Located in `lib/agricultural-api.ts`
- Handles all backend communication
- Implements error handling
- Manages request/response types

## Deployment

### Production Build
```bash
pnpm build
pnpm start
```

### Requirements
- Node.js runtime
- PostgreSQL database
- Environment variables configured
- FastAPI backend deployed
- Proper CORS configuration

### Recommended Platforms
- Vercel (Frontend)
- Railway/Heroku (Database)
- Cloud Platform for FastAPI backend

## Security Considerations

1. **Authentication**
   - Password hashing
   - Session management
   - CSRF protection
   - Rate limiting

2. **Data Protection**
   - Input validation
   - SQL injection prevention
   - XSS protection
   - Secure headers

3. **API Security**
   - Request validation
   - Error handling
   - Rate limiting
   - CORS configuration

## Performance Optimization

1. **Frontend**
   - Image optimization
   - Code splitting
   - Lazy loading
   - Caching strategies

2. **API Calls**
   - Request debouncing
   - Response caching
   - Error retries
   - Optimistic updates

## Testing

### Current Test Coverage
- Basic component tests
- API integration tests
- Authentication flow tests

### Needed Tests
- End-to-end testing
- Performance testing
- Security testing
- Mobile responsiveness testing

## Known Issues and Limitations

1. **Performance**
   - Large bundle size needs optimization
   - Image optimization needed
   - API response caching needed

2. **Compatibility**
   - Limited browser support testing
   - Mobile optimization needed
   - Offline support lacking

3. **Features**
   - Some AI features need backend integration
   - Real-time updates needed for certain features
   - Limited language support in voice controls

## Future Improvements

1. **Technical Improvements**
   - Implement PWA support
   - Add offline capabilities
   - Optimize bundle size
   - Improve test coverage

2. **Feature Additions**
   - Community features
   - Advanced analytics
   - Mobile app version
   - Enhanced ML capabilities

3. **Integration Improvements**
   - More language support
   - Additional payment gateways
   - Third-party service integration
   - Enhanced data visualization

## Contributing

Guidelines for contributing to the project:
1. Fork the repository
2. Create feature branch
3. Follow coding standards
4. Write tests
5. Submit pull request

## Support and Maintenance

### Regular Maintenance Tasks
1. Dependency updates
2. Security patches
3. Database backups
4. Performance monitoring

### Support Channels
- GitHub issues
- Documentation updates
- Community forums
- Email support
