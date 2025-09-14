# AgroAI: Agricultural AI Assistant

AgroAI is a comprehensive AI-powered platform designed to assist farmers and agricultural professionals with actionable insights, decision support, and practical tools. The system combines advanced AI models with user-friendly interfaces for crop management, disease detection, weather forecasting, market analysis, and more.

---

## 🚀 Quick Start

1. **Clone the repository**:
   ```bash
   git clone https://github.com/sanskaryo/AgroAI.git
   ```
2. **Install dependencies** (see respective frontend/backend directories for details).
3. **Configure environment variables** as required for backend agents and frontend authentication.
4. **Run Backend Services** (Python):
   ```bash
   cd backend-main
   # See each agent's README or main.py for running instructions
   ```
5. **Run Frontend (Next.js)**:
   ```bash
   cd Frontend
   npm install
   npm run dev
   ```
6. **Access the app** at [http://localhost:3000](http://localhost:3000)

---

## 🌾 Features

### Core Features

- **AI Chat Assistant**: Multilingual agricultural advice for crops, farming practices, and market trends.
- **Crop Disease Detection**: Image-based identification of crop diseases.
- **Weather Forecasting**: Local weather predictions and climate advisories.
- **Irrigation Scheduling**: Smart irrigation planning based on weather and crop type.
- **Fertilizer Recommendations**: Soil- and crop-specific fertilizer suggestions.
- **Crop Yield Prediction**: AI-powered forecasting using historical and real-time data.
- **Market Price Scraper**: Fetches and analyzes commodity prices from multiple sources.
- **Risk Management Analysis**: Quantifies agricultural risks including weather, market, credit, and operational.
- **Deep Agricultural Research**: Supports complex research queries with detailed agent-based answers.

### Agent Ecosystem

- **Crop Recommender**: Suggests best crops for a given location, soil, and season.
- **Weather Advisory**: Provides localized weather updates and impact analysis.
- **Location Assistant**: Handles logistics, mapping, and farm contact queries.
- **News & Policy Agent**: Summarizes recent agricultural news and policy updates.
- **Credit & Market Policy**: Analyzes market trends and financial guidance.
- **Yield & Risk Agents**: Predict yield potential and assess variable risks.

### Authentication

- Secure registration and login (NextAuth.js).
- Aadhar number verification.
- Session management.

### Multi-language Support

- Supports multiple Indian languages.
- Real-time message translation.
- Language preference settings.

### Mobile & Responsive Support

- Works on desktops, tablets, and mobile phones.
- QR code scanning for mobile access.

### Security

- Password hashing (bcrypt).
- JWT authentication.
- Input validation (Zod).
- CSRF protection.
- Rate limiting.

---

## 📁 Project Structure

### Frontend (`Frontend/`)

- `app/` – Next.js application (API routes, dashboard, auth pages)
- `components/` – Reusable React components
  - `agricultural-ai-chatbot.tsx` – Main AI chatbot interface
  - `crop-disease-prediction.tsx` – Disease detection tool
  - `irrigation-calendar.tsx`, `fertilizer-recommendation.tsx`, etc.
- `lib/` – API clients, utilities, auth, Prisma DB setup
- `prisma/` – DB schema and migrations
- `hooks/` – Custom React hooks
- `types/` – TypeScript types
- `data/` – Static files, agent definitions
- `docs/` – Project documentation

### Backend (`backend-main/`)

- `Agents/` – Modular Python agents for crop recommendation, risk management, web scraping, guardrails, etc.
- `Deep_Research/` – Orchestrator for multi-agent research queries
- `Tools/` – Utility scripts for weather, crop, market, etc.

---

## 🛠️ Development Scripts

- Frontend: `npm run dev`, `npm run build`
- Backend: Run agents via Python scripts, see each agent folder for CLI usage.

---

## 📚 Documentation

- Detailed docs in `Frontend/docs/` and inline agent docstrings.
- Each agent includes usage instructions and API details.
- API types and request/response structures in `Frontend/lib/agricultural-api.ts`.

---

## 🤝 Contributing

1. Fork the repo and create your branch (`git checkout -b feature-name`)
2. Commit your changes (`git commit -am 'Add new feature'`)
3. Push to the branch (`git push origin feature-name`)
4. Open a Pull Request

---

## 🐛 Troubleshooting

- Check `.env` configuration and database migrations.
- Ensure Python and Node.js versions match requirements.
- See agent logs for errors in backend services.
- For frontend issues, check browser console and Next.js logs.

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgments

- OpenAI, Google Gemini, Llama for AI models.
- Contributors and supporters in the agricultural AI community.
- Farmers and agricultural experts for domain insights and testing.

---

## 💬 Contact

For queries or support, open an issue or reach out at [GitHub Issues](https://github.com/sanskaryo/AgroAI/issues).
