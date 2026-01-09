# AgroAI: Agricultural AI Assistant

AgroAI is a comprehensive AI-powered platform designed to assist farmers and agricultural professionals with actionable insights, decision support, and practical tools. The system combines advanced AI models with user-friendly interfaces for crop management, disease detection, weather forecasting, market analysis, and more.

---

## 📖 Table of Contents

1. [🚀 Quick Start](#-quick-start)
2. [🔐 Environment Variables](#-environment-variables)
3. [🌾 Features](#-features)
4. [⚡ Performance & Optimization](#-performance--optimization)
5. [🏗️ System Architecture](#-system-architecture)
6. [🎯 Use Cases](#-use-cases)
7. [🧠 RAG (Retrieval Augmented Generation) System](#-rag-retrieval-augmented-generation-system)
8. [🤖 Agent Ecosystem](#-agent-ecosystem)
9. [🛡️ Guardrails System](#-guardrails-system)
10. [🔬 Deep Research Orchestrator](#-deep-research-orchestrator)
11. [📊 State Management & Workflow](#-state-management--workflow)
12. [📁 Project Structure](#-project-structure)
13. [🔧 Technology Stack](#-technology-stack)
14. [🛠️ Development Scripts](#-development-scripts)
15. [📚 Documentation](#-documentation)
16. [📊 Evaluation & Quality Metrics](#-evaluation--quality-metrics)
17. [❓ FAQ](#-faq)
18. [🤝 Contributing](#-contributing)
19. [🐛 Troubleshooting](#-troubleshooting)
20. [📄 License](#-license)
21. [🙏 Acknowledgments](#-acknowledgments)
22. [💬 Contact](#-contact)

---

## 🚀 Quick Start

### Prerequisites

- **Node.js**: 18.x or higher
- **Python**: 3.8 or higher
- **PostgreSQL**: 14 or higher (for frontend database)
- **API Keys**: 
  - Google Gemini API key
  - Groq API key (optional)
  - Cohere API key (optional, for reranking)

### Installation Steps

1. **Clone the repository**:
   ```bash
   git clone https://github.com/sanskaryo/AgroAI.git
   cd AgroAI
   ```

2. **Backend Setup**:
   ```bash
   cd backend-main
   
   # Create virtual environment (recommended)
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   
   # Install dependencies
   pip install -r requirements.txt
   
   # Create .env file
   cp .env.example .env
   # Edit .env and add your API keys (see Environment Variables section)
   ```

3. **Frontend Setup**:
   ```bash
   cd ../Frontend
   
   # Install dependencies
   npm install
   
   # Setup database
   npx prisma generate
   npx prisma db push
   
   # Create .env.local file
   cp .env.example .env.local
   # Edit .env.local and add your configurations
   ```

4. **Run Backend Services**:
   ```bash
   cd ../backend-main
   python main.py
   # Or use specific agents as needed
   ```

5. **Run Frontend**:
   ```bash
   cd ../Frontend
   npm run dev
   ```

6. **Access the application**:
   - Frontend: [http://localhost:3000](http://localhost:3000)
   - Backend API: [http://localhost:8000](http://localhost:8000) (if using FastAPI)

---

## 🔐 Environment Variables

### Backend (`backend-main/.env`)

```bash
# AI Model API Keys
GOOGLE_API_KEY=your_gemini_api_key_here
GROQ_API_KEY=your_groq_api_key_here
COHERE_API_KEY=your_cohere_api_key_here

# Model Configuration
DEFAULT_MODEL=gemini-2.0-flash
EMBEDDING_MODEL=models/text-embedding-004

# RAG Configuration
VECTOR_DB_PATH=./vectorstore
CACHE_DIR=./cache
MAX_RETRIEVAL_DOCS=5

# Offline Mode
OFFLINE_MODEL_DIR=./models/Qwen1.5-Base
OFFLINE_ADAPTER_DIR=./models/Qwen_1.5_Finetuned

# Agent Configuration
MAX_AGENT_RETRIES=3
AGENT_TIMEOUT=30

# Deep Research
MAX_RESEARCH_ITERATIONS=3
RESEARCH_PARALLEL_WORKERS=5
```

### Frontend (`Frontend/.env.local`)

```bash
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/agroai

# NextAuth
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your_nextauth_secret_here

# API Endpoints
NEXT_PUBLIC_API_URL=http://localhost:8000
NEXT_PUBLIC_BACKEND_URL=http://localhost:8000/api

# Cloudflare Turnstile (Bot Protection)
NEXT_PUBLIC_TURNSTILE_SITE_KEY=your_turnstile_site_key
TURNSTILE_SECRET_KEY=your_turnstile_secret_key

# Feature Flags
NEXT_PUBLIC_ENABLE_VOICE=true
NEXT_PUBLIC_ENABLE_QR_SCANNER=true
```

---

## 🌾 Features

### Core Features

- **AI Chat Assistant**: Multilingual agricultural advice powered by multi-agent system
  - Intelligent query routing via RouterAgent
  - Context-aware responses using Adaptive RAG
  - Real-time language translation support
  - Session persistence and chat history

- **Crop Disease Detection**: Image-based disease identification
  - Computer vision models for leaf analysis
  - Disease confidence scoring
  - Treatment recommendations with evidence-based approaches
  - Support for multiple crop types

- **Weather Forecasting**: Climate intelligence for farming
  - Location-specific weather predictions
  - Monsoon and seasonal forecasts
  - Crop-specific weather impact analysis
  - Advisory generation for farming activities

- **Irrigation Scheduling**: Smart water management
  - Weather-integrated irrigation planning
  - Crop water requirement calculations
  - Seasonal irrigation calendars
  - Soil moisture considerations

- **Fertilizer Recommendations**: Precision nutrient management
  - Soil test-based recommendations
  - Crop-specific nutrient requirements
  - NPK ratio optimization
  - Application timing guidance

- **Crop Yield Prediction**: Data-driven yield forecasting
  - Historical data analysis
  - Real-time condition integration
  - Location and season-specific predictions
  - Model comparison and validation

- **Market Price Scraper**: Real-time commodity pricing
  - Multi-state market price aggregation
  - Price trend analysis and visualization
  - District-level granularity
  - Historical price tracking

- **Risk Management Analysis**: Comprehensive risk assessment
  - Weather risk quantification
  - Market volatility analysis
  - Credit and financial risk evaluation
  - Operational risk identification
  - Risk mitigation strategy recommendations

- **Deep Agricultural Research**: Multi-agent research orchestration
  - Complex query decomposition
  - Parallel agent execution
  - Iterative quality refinement
  - Comprehensive research reports

### Agent Ecosystem

**Intelligent Routing**: RouterAgent analyzes queries and dynamically selects appropriate agents

**Image Analysis Agents** (for visual crop diagnostics):
- **CropDiseaseDetectionAgent**: Disease identification and treatment
- **PestPredictionAgent**: Pest detection and IPM strategies
- **ImageAnalysisAgent**: General agricultural image insights

**Advisory Agents** (for farming recommendations):
- **CropRecommenderAgent**: Crop selection based on soil, climate, and market
- **WeatherForecastAgent**: Weather predictions and impact analysis
- **FertilizerRecommendationAgent**: Soil-specific fertilizer guidance
- **CropYieldAgent**: Yield prediction and estimation

**Market & Finance Agents** (for economic decisions):
- **MarketPriceAgent**: Real-time commodity pricing
- **CreditPolicyMarketAgent**: Loans, subsidies, and financial schemes

**Risk & Analytics Agents** (for decision support):
- **RiskManagementAgent**: Multi-dimensional risk assessment
- **RiskModellingAgent**: Quantitative risk modeling

**Information & Research Agents** (for knowledge access):
- **NewsAgent**: Agricultural news and policy updates
- **LocationAgriAssistant**: Geospatial services and logistics
- **WebScrapingAgent**: Targeted data extraction from web sources
- **MultiLingualAgent**: Language translation and localization

**Utility Agents** (for workflow support):
- **ChartAgent**: Data visualization and analytics
- **SynthesizerAgent**: Multi-agent response aggregation
- **QueryRewriterAgent**: Query optimization
- **AnswerGraderAgent**: Quality assessment
- **GuardrailsAgent**: Content validation and filtering

### Intelligent Capabilities

1. **Adaptive Processing**
   - Automatic complexity detection (simple/moderate/complex)
   - Dynamic workflow routing based on query characteristics
   - Fallback mechanisms for unsupported queries

2. **Quality Assurance**
   - Multi-stage validation: Guardrails → Grading → Fact-checking
   - Hallucination detection and prevention
   - Confidence scoring for all responses
   - Iterative refinement for research queries

3. **Context Awareness**
   - RAG-based document retrieval
   - Hybrid search (semantic + keyword)
   - Document reranking for relevance
   - Web search integration for latest information

4. **Multi-modal Support**
   - Text query processing
   - Image analysis (crop diseases, pests)
   - Chart and visualization generation
   - Voice input support (frontend)

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
- Guardrails-based content filtering.
- Agriculture-domain validation.

---

## ⚡ Performance & Optimization

### Caching Strategies

1. **LLM Response Caching** (GPTCache)
   - Reduces API calls and costs
   - Improves response latency
   - SHA-256 hashed cache keys
   - Persistent cache storage

2. **Document Embedding Cache**
   - FAISS index persistence
   - Incremental updates
   - Memory-mapped file support

3. **Session State Management**
   - LangGraph memory saver
   - Workflow state persistence
   - Resume from checkpoints

### Parallel Processing

- **Parallel RAG**: Concurrent document retrieval across sources
- **Multi-Agent Execution**: Simultaneous agent invocation
- **ThreadPoolExecutor**: Python threading for I/O-bound tasks
- **Async Operations**: FastAPI async routes

### Offline Mode Support

- **Internet Detection**: Automatic connectivity checking
- **Offline Models**: HuggingFace Qwen 1.5 (fine-tuned)
  - Base model: Qwen1.5-Base
  - Adapter: Fine-tuned for agriculture domain
- **Local Inference**: CPU/GPU support for offline environments
- **Graceful Degradation**: Falls back to offline mode seamlessly

### Optimization Techniques

- **Contextual Compression**: Reduces context window size
- **Semantic Chunking**: Optimal chunk boundaries
- **Reranking**: Cohere reranker for top-k selection
- **Query Rewriting**: Improves retrieval effectiveness
- **Introspective Refinement**: Self-improvement loops

---

## 🏗️ System Architecture

### High-Level Architecture Overview

AgroAI is built on a **multi-agent, RAG-enhanced architecture** that combines adaptive retrieval, intelligent routing, and specialized agents to deliver comprehensive agricultural assistance. The system operates in three main layers:

```
┌─────────────────────────────────────────────────────────────────┐
│                     FRONTEND LAYER (Next.js)                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   Chat UI    │  │  Dashboard   │  │ Agent Tools  │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                  ORCHESTRATION LAYER (Python)                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │  Guardrails  │  │    Router    │  │  Synthesizer │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    PROCESSING LAYER                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │  Adaptive    │  │  Multi-Agent │  │   Deep       │          │
│  │     RAG      │  │   Executor   │  │  Research    │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                      AGENT ECOSYSTEM                             │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐       │
│  │  Crop  │ │Weather │ │Disease │ │  Pest  │ │  Risk  │ ...   │
│  │  Agent │ │ Agent  │ │ Agent  │ │ Agent  │ │ Agent  │       │
│  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘       │
└─────────────────────────────────────────────────────────────────┘
```

### Core Architectural Principles

1. **Modular Agent Design**: Each agent is self-contained with specific expertise
2. **Adaptive Processing**: System dynamically routes queries based on complexity and content
3. **Quality Assurance**: Multi-stage validation with guardrails, grading, and fact-checking
4. **Retrieval-Augmented Generation**: Context-aware responses using vector databases and web search
5. **State Management**: LangGraph-based workflow orchestration with state persistence

### Request Flow Example

```
1. User: "What crops should I plant in Punjab for winter 2025?"
   ↓
2. Guardrails: ✓ Agriculture-related (confidence: 0.95)
   ↓
3. Router: → CropRecommenderAgent, WeatherForecastAgent
   ↓
4. Parallel Execution:
   - CropRecommenderAgent → "Wheat, mustard, potato recommended"
   - WeatherForecastAgent → "Cold, dry winter predicted"
   ↓
5. Fact Checker: ✓ Verified against knowledge base
   ↓
6. Synthesizer: Combines responses coherently
   ↓
7. Answer Grader: ✓ Complete and relevant
   ↓
8. Final Response: "For Punjab winter 2025, we recommend wheat 
   (high demand, suitable climate), mustard (cold-resistant), 
   and potato (profitable). Expected weather: cold and dry."
```

---

## 🎯 Use Cases

### For Farmers

1. **Crop Planning**: Get data-driven recommendations for crop selection
2. **Disease Management**: Early detection and treatment of crop diseases
3. **Weather Preparedness**: Plan activities based on accurate forecasts
4. **Market Intelligence**: Make informed decisions with real-time pricing
5. **Risk Mitigation**: Understand and manage agricultural risks
6. **Financial Planning**: Access information on loans and subsidies

### For Agricultural Advisors

1. **Research Support**: Quick access to agricultural knowledge
2. **Client Consultation**: Evidence-based recommendations
3. **Policy Updates**: Stay informed about agricultural policies
4. **Data Analysis**: Visualize trends and patterns

### For Researchers

1. **Deep Research**: Multi-agent orchestration for complex queries
2. **Data Aggregation**: Collect information from multiple sources
3. **Literature Review**: Automated research paper mining
4. **Trend Analysis**: Market and climate trend identification

### For Agricultural Organizations

1. **Farmer Support**: Scalable advisory services
2. **Knowledge Dissemination**: Multilingual information delivery
3. **Risk Assessment**: Portfolio-level risk analysis
4. **Market Analysis**: Commodity price monitoring

---

## 🧠 RAG (Retrieval Augmented Generation) System

### Adaptive RAG Architecture

AgroAI implements a sophisticated **Adaptive RAG** system that intelligently routes queries based on complexity:

#### Query Complexity Classification

```
User Query → Document Retrieval → Document Grading → Complexity Analysis
                                                              ▼
                                    ┌─────────────────────────┴─────────────────────────┐
                                    ▼                         ▼                         ▼
                            SIMPLE PATH              MODERATE PATH              COMPLEX PATH
                         (Direct Answer)         (Iterative Refine)         (Multi-step Research)
                                    │                         │                         │
                                    └─────────────────────────┴─────────────────────────┘
                                                              ▼
                                                     Final Response
```

#### RAG Components

1. **Document Loading & Chunking**
   - Supports multiple formats: CSV, PDF, TXT, DOCX, JSON, MD
   - Semantic chunking for context preservation
   - RecursiveCharacterTextSplitter for optimal chunk sizes

2. **Hybrid Retrieval**
   - **FAISS Vector Store**: Dense semantic retrieval using Gemini embeddings
   - **BM25 Retriever**: Sparse keyword-based retrieval
   - **Ensemble Retriever**: Combines both approaches for optimal results
   - **Contextual Compression**: Cohere reranking for relevance optimization

3. **Adaptive Query Routing**
   ```python
   - SIMPLE: Direct questions with clear answers in documents
   - MODERATE: Requires synthesis or iterative refinement
   - COMPLEX: Multi-hop reasoning, research-grade queries
   ```

4. **Quality Control Pipeline**
   - **Document Grader**: Evaluates document relevance to query
   - **Answer Grader**: Assesses response completeness and accuracy
   - **Hallucination Grader**: Detects and prevents factual errors
   - **Introspective Agent**: Self-reflection for quality improvement

5. **Fallback Mechanisms**
   - Query rewriting for better retrieval
   - Web search integration when documents insufficient
   - Introspective agent responses for unsupported queries

### Parallel RAG System

For high-throughput scenarios, AgroAI uses a **Parallel RAG** implementation:
- Concurrent document processing across multiple sources
- Optimized for real-time chat interactions
- Model-agnostic (supports Gemini, Groq, etc.)

---

## 🤖 Agent Ecosystem

### Router Agent

The **RouterAgent** is the intelligent gateway that analyzes queries and routes them to appropriate specialized agents.

#### Routing Logic

```python
Query Analysis:
1. Image Detection: Checks for image paths, visual content
   → Routes to: CropDiseaseDetectionAgent, PestPredictionAgent, ImageAnalysisAgent

2. Text Query Analysis: Categorizes by agricultural domain
   → Routes to: Domain-specific agents (Weather, Crop, Market, etc.)

3. Multi-Agent Coordination: Can route to multiple agents in parallel
   → Synthesizes results from multiple sources
```

#### Routing Strategy

- **Priority-based**: Image queries get exclusive image-agent routing
- **Context-aware**: Understands agricultural terminology and concepts
- **Multi-agent support**: Can invoke multiple agents for complex queries
- **Justification-driven**: Provides reasoning for each routing decision

### Specialized Agents

#### 1. **Image Analysis Agents**

- **CropDiseaseDetectionAgent**
  - Computer vision-based disease identification
  - Treatment and management recommendations
  - Disease confidence scoring

- **PestPredictionAgent**
  - Pest detection from crop images
  - Species identification
  - Integrated pest management strategies

- **ImageAnalysisAgent**
  - General agricultural image analysis
  - Crop health assessment
  - Visual insights and recommendations

#### 2. **Agricultural Advisory Agents**

- **CropRecommenderAgent**
  - Location and season-based crop recommendations
  - Soil, climate, and market analysis
  - Multi-model comparison (different AI models)

- **WeatherForecastAgent**
  - Weather predictions and forecasts
  - Monsoon analysis and crop impact
  - Climate-based farming advisories

- **FertilizerRecommendationAgent**
  - Soil-specific fertilizer recommendations
  - Nutrient deficiency analysis
  - Application timing and dosage

- **CropYieldAgent**
  - Yield prediction using historical data
  - Real-time condition integration
  - Season and location-specific estimates

#### 3. **Market & Financial Agents**

- **MarketPriceAgent**
  - Real-time commodity price fetching
  - State and district-level market data
  - Price trend analysis

- **CreditPolicyMarketAgent**
  - Agricultural loan information
  - Subsidy and scheme details
  - Financial risk assessment
  - Market trend analysis

#### 4. **Risk & Management Agents**

- **RiskManagementAgent**
  - Comprehensive risk profiling
  - Weather, market, credit, and operational risks
  - Mitigation strategy recommendations
  - Risk scoring and categorization

- **RiskModellingAgent**
  - Quantitative risk modeling
  - Probability-based assessments

#### 5. **Information & Research Agents**

- **NewsAgent**
  - Latest agricultural news extraction
  - Policy update summaries
  - Regional and national news coverage

- **LocationAgriAssistant**
  - Geocoding and mapping
  - Farm location services
  - Logistics and proximity analysis

- **WebScrapingAgent**
  - Targeted data extraction
  - Research paper mining
  - Online database querying

- **MultiLingualAgent**
  - Translation between languages
  - Support for Indian regional languages
  - Code-switched query handling

#### 6. **Utility Agents**

- **ChartAgent**
  - Data visualization generation
  - Agricultural analytics charts
  - Trend graphs and insights

- **SynthesizerAgent**
  - Multi-agent response synthesis
  - Coherent answer generation
  - Duplicate information removal

- **QueryRewriterAgent**
  - Query optimization for better retrieval
  - Ambiguity resolution
  - Context enhancement

- **AnswerGraderAgent**
  - Response quality evaluation
  - Completeness checking
  - Accuracy verification

### Agent Orchestration Workflow

```
User Query
    ▼
Guardrails (Agriculture Validation)
    ▼
Router (Agent Selection)
    ▼
┌──────────────────────────────────┐
│  Parallel Agent Execution        │
│  ┌────────┐ ┌────────┐ ┌────────┐│
│  │Agent 1 │ │Agent 2 │ │Agent N ││
│  └────────┘ └────────┘ └────────┘│
└──────────────────────────────────┘
    ▼
Fact Checking (Likert Scoring)
    ▼
Synthesizer (Response Merging)
    ▼
Answer Grading (Quality Check)
    ▼
Final Response
```

---

## 🛡️ Guardrails System

### AgriculturalGuardrailsAgent

The **Guardrails** system acts as the first line of defense and query validation:

#### Capabilities

1. **Query Classification**
   ```python
   Categories:
   - "agriculture": Farming/agriculture related queries
   - "greeting": Casual greetings, pleasantries
   - "general": Non-agriculture but appropriate queries
   - "inappropriate": Harmful, offensive, or irrelevant content
   ```

2. **Agriculture Relevance Detection**
   - Crop cultivation and farming practices
   - Plant diseases, pests, fertilizers
   - Weather forecasting for agriculture
   - Agricultural equipment and machinery
   - Livestock and animal husbandry
   - Market prices and commodities
   - Agricultural policies and subsidies
   - Organic and sustainable farming
   - Farm management and economics

3. **Greeting Handling**
   - Detects casual greetings
   - Provides agriculture-focused welcome messages
   - Maintains conversational warmth

4. **Confidence Scoring**
   - 0.0 to 1.0 confidence scale
   - Threshold-based decision making
   - Uncertainty handling

5. **Response Generation**
   - Greetings: Warm, agriculture-focused welcome
   - Agriculture queries: Pass to agent system
   - Non-agriculture: Polite redirection
   - Inappropriate: Rejection with guidance

#### Guardrails Workflow

```
User Query
    ▼
┌─────────────────────────────────┐
│  Guardrails Agent               │
│  - Is agriculture related?      │
│  - Is greeting?                 │
│  - Category classification      │
│  - Confidence score             │
└─────────────────────────────────┘
    ▼
┌─────────────────────────────────┐
│  Routing Decision:              │
│  - Agriculture → Agent System   │
│  - Greeting → Welcome Response  │
│  - Other → Redirect Message     │
│  - Inappropriate → Block        │
└─────────────────────────────────┘
```

---

## 🔬 Deep Research Orchestrator

### Multi-Agent Research System

For complex research queries, AgroAI employs a **Deep Research Orchestrator** that coordinates multiple agents in a planned workflow:

#### Research Planning Agent

1. **Query Analysis**: Breaks down complex queries into subtasks
2. **Tool Assignment**: Maps tools to specific subtasks
3. **Execution Planning**: Determines priority and order
4. **Time Estimation**: Estimates research duration

#### Research Workflow

```
Research Query
    ▼
Planning Agent (Task Decomposition)
    ▼
┌─────────────────────────────────────────┐
│  Task Queue with Tool Assignments       │
│  - Task 1: Weather Tool (Priority 5)    │
│  - Task 2: Market Tool (Priority 4)     │
│  - Task 3: Research Tool (Priority 3)   │
└─────────────────────────────────────────┘
    ▼
Subsearch Agents (Parallel Execution)
    ▼
Grader Agent (Quality Check)
    ▼
┌─────────────────────────────────────────┐
│  Iterative Refinement                   │
│  If grade = "no" → Retry with new query │
│  If grade = "yes" → Accept result       │
│  Max iterations: 3                      │
└─────────────────────────────────────────┘
    ▼
Final Research Report
```

#### Available Research Tools

- Fertilizer Recommendation Tool
- Web Search Tool
- Market Price Tool
- Weather Forecast Tool
- Crop Recommendation Tool
- Crop Yield Prediction Tool
- Pest Detection Tool
- Translation Tool
- Crop Disease Tool
- Google Maps Location Tool
- Web Scraper Tool
- Risk Management Tool
- Agricultural News Tool
- Farm Credit Policy Tool

---

## 📊 State Management & Workflow

### LangGraph State Management

AgroAI uses **LangGraph** for sophisticated workflow orchestration:

#### MainWorkflowState

```python
{
    query: str                      # User query
    image_path: str                 # Optional image path
    initial_mode: str               # "rag" or "tooling"
    current_mode: str               # Current processing mode
    rag_response: str               # RAG system response
    router_result: Dict             # Router decisions
    agent_responses: Dict           # All agent outputs
    fact_checked_responses: Dict    # Verified responses
    synthesized_result: str         # Final synthesized answer
    grading: Any                    # Quality grades
    guardrails_result: Dict         # Guardrails output
    is_agriculture_related: bool    # Validation flag
    has_switched_mode: bool         # Mode switch tracking
    is_image_query: bool            # Image query flag
    chart_path: str                 # Generated chart path
}
```

#### Workflow Modes

1. **RAG Mode**: Document-based retrieval and generation
2. **Tooling Mode**: Direct agent execution
3. **Hybrid Mode**: Combines RAG with agent tools

### Execution Flow

```
START
  ▼
Guardrails Check
  ▼
┌─────────────────────────┐
│  Is Agriculture Related? │
└─────────────────────────┘
  Yes ▼              No ▼
Router           Redirect Response
  ▼
┌─────────────────────────┐
│  Mode: RAG or Tooling?  │
└─────────────────────────┘
  ▼                    ▼
RAG Path          Tooling Path
  ▼                    ▼
Document Retrieval   Agent Execution
  ▼                    ▼
Quality Grading    Fact Checking
  ▼                    ▼
  └──────┬──────┘
         ▼
    Synthesizer
         ▼
   Answer Grader
         ▼
   Final Response
         ▼
       END
```

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

- **`Agents/`** – Modular Python agents
  - `Router.py` – Intelligent query routing
  - `Guardrails/` – Query validation and filtering
  - `Crop_Recommender/`, `Weather_forcast/`, etc. – Specialized agents
  - `synthesizer_agent.py` – Response synthesis
  - `answer_grader.py` – Quality evaluation
  - `Query_rewriter.py` – Query optimization
  - `fact_checker/` – Fact verification

- **`RAG/`** – Retrieval Augmented Generation
  - `adaptive_rag_class.py` – Adaptive RAG implementation
  - `parallel_rag_main.py` – Parallel processing
  - `workflow.py` – LangGraph workflow
  - `stategraph.py` – State definitions
  - `document_scorer.py` – Document relevance grading
  - `Agents/` – RAG-specific agents (grader, hallucination checker, search, etc.)

- **`Deep_Research/`** – Research orchestration
  - `orchastrator.py` – Multi-agent research coordinator
  - `routers.py` – Research task routing

- **`Tools/`** – Utility scripts for weather, crop, market data

- **`workflow.py`** – Main orchestration workflow

- **`utils/`** – Helper functions
  - `Internet_checker.py` – Connectivity detection
  - `hf_model.py` – HuggingFace model loader
  - `model_downloader.py` – Model management

---

## 🔧 Technology Stack

### Backend Technologies

- **Language**: Python 3.8+
- **Framework**: FastAPI (for API routes)
- **AI/ML Libraries**:
  - LangChain / LangGraph – Workflow orchestration and state management
  - Google Gemini API – Primary LLM for generation and embeddings
  - Groq API – Alternative LLM provider
  - Agno – Agent framework for structured outputs
  - Pydantic – Data validation and schema definition
- **Vector Databases**:
  - FAISS – Dense vector retrieval
  - BM25 – Sparse keyword retrieval
- **Caching**: GPTCache – LLM response caching
- **Reranking**: Cohere – Document reranking
- **Document Processing**:
  - PyPDF, UnstructuredWordDocument – PDF/DOCX parsing
  - Pandas – CSV/JSON handling
- **Utilities**: 
  - dotenv – Environment configuration
  - requests – HTTP client

### Frontend Technologies

- **Framework**: Next.js 15.2.4 (React 19)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: Radix UI (accessible components)
- **Authentication**: NextAuth.js
- **Database ORM**: Prisma (PostgreSQL)
- **State Management**: React Hooks
- **Form Validation**: React Hook Form + Zod
- **Charts**: Recharts
- **QR Code**: html5-qrcode
- **Markdown**: react-markdown

### AI Models

- **Primary**: Google Gemini 2.0 Flash (multimodal, fast inference)
- **Embeddings**: Gemini Embeddings
- **Offline Mode**: Qwen 1.5 (fine-tuned for agriculture)
- **Reranking**: Cohere

### Infrastructure

- **Containerization**: Docker + Docker Compose
- **Monitoring**: Logging with Python logging module
- **Evaluation**: RAGAS (RAG assessment), Custom MCQ evaluators

---

## 🛠️ Development Scripts

### Frontend

```bash
cd Frontend
npm install              # Install dependencies
npm run dev             # Development server (http://localhost:3000)
npm run build           # Production build
npm run start           # Start production server
```

### Backend

```bash
cd backend-main
pip install -r requirements.txt  # Install dependencies

# Run main workflow
python main.py

# Run specific agents (see agent folders for details)
python -m Agents.Crop_Recommender.agent
python -m RAG.adaptive_rag_main

# Run evaluations
python -m Evaluation.Agricultural\ QNA.eval_agri_qna_gemini
python -m RAG.eval
```

### Docker Deployment

```bash
# Development environment
docker-compose -f docker-compose.dev.yml up

# Production environment  
docker-compose up
```

---

## 📚 Documentation

### Architecture Documentation

- **Main README** (this file): System overview, architecture, and setup
- **Frontend Docs** (`Frontend/docs/`):
  - `PROJECT_DOCUMENTATION.md`: Frontend architecture and features
  - `API_INTEGRATION.md`: API integration patterns
  - `DEVELOPMENT_STAGES.md`: Development roadmap
- **Agent Docstrings**: Inline documentation in each agent's `agent.py`
- **API Types**: `Frontend/lib/agricultural-api.ts` – TypeScript interfaces

### Agent-Specific Documentation

Each agent folder contains:
- `agent.py`: Implementation with docstrings
- `routers.py`: FastAPI routes (where applicable)
- Usage examples in agent initialization

### RAG System Documentation

- **`RAG/adaptive_rag_class.py`**: Adaptive RAG implementation
- **`RAG/workflow.py`**: LangGraph workflow definition
- **`RAG/stategraph.py`**: State type definitions

### Deep Research Documentation

- **`Deep_Research/orchastrator.py`**: Multi-agent research orchestrator
- Includes planning, execution, and grading workflows

---

## 📊 Evaluation & Quality Metrics

### RAG Evaluation

1. **RAGAS Framework** (`RAG/ragas_evaluation.py`)
   - Context relevance
   - Answer relevance
   - Faithfulness
   - Context recall
   - Context precision

2. **Custom Metrics** (`RAG/eval.py`)
   - Document grading accuracy
   - Retrieval effectiveness
   - Generation quality

### Agent Evaluation

1. **MCQ Benchmarks** (`Evaluation/BharatgenAI/`)
   - BhashaBench-Krishi dataset
   - Multi-language agricultural QA
   - Model comparison (Gemini, Llama, Pragati)

2. **Agricultural QA** (`Evaluation/Agricultural QNA/`)
   - Domain-specific evaluation
   - Accuracy and F1 scores
   - Response completeness

### Quality Metrics

- **Answer Completeness**: Binary yes/no grading
- **Confidence Scoring**: 0.0-1.0 scale for all classifications
- **Hallucination Detection**: Factual accuracy verification
- **Fact Checking**: Likert scale scoring (1-5)
- **Response Grading**: Multi-dimensional assessment

### Monitoring & Logging

```python
- Workflow path tracking
- Processing time measurements
- Mode switching detection
- Agent selection justifications
- Error and exception logging
```

---

## ❓ FAQ

### General Questions

**Q: What makes AgroAI different from other agricultural AI platforms?**
A: AgroAI uses a unique multi-agent architecture with adaptive RAG, allowing it to intelligently route queries to specialized agents. It combines retrieval-augmented generation with domain-specific tools and provides quality assurance through multi-stage validation.

**Q: Can I use AgroAI offline?**
A: Yes! AgroAI supports offline mode using a fine-tuned Qwen 1.5 model. The system automatically detects internet connectivity and switches to local inference when offline.

**Q: What languages does AgroAI support?**
A: AgroAI supports multiple Indian languages through the MultiLingualAgent, including Hindi, Tamil, Telugu, Bengali, Marathi, and more. The frontend also has multilingual support.

**Q: Is AgroAI free to use?**
A: The codebase is open-source under MIT license. However, you'll need your own API keys for services like Google Gemini, Groq, and Cohere. Offline mode can reduce API costs.

### Technical Questions

**Q: How does the Adaptive RAG system work?**
A: The Adaptive RAG classifies queries into three complexity levels (simple, moderate, complex) and routes them through appropriate workflows. Simple queries get direct answers, moderate queries use iterative refinement, and complex queries employ multi-step research.

**Q: What is the role of the Guardrails system?**
A: Guardrails validate that queries are agriculture-related, classify query types (greeting, agriculture, general, inappropriate), and provide confidence scores. This ensures the system only processes relevant agricultural queries.

**Q: How do multiple agents work together?**
A: The RouterAgent analyzes queries and selects appropriate agents. These agents execute in parallel, and their responses are fact-checked, synthesized, and graded before being returned to the user.

**Q: What evaluation metrics does AgroAI use?**
A: AgroAI uses RAGAS framework (context relevance, faithfulness, answer relevance), custom MCQ benchmarks, agricultural QA datasets, and multi-dimensional quality metrics including hallucination detection.

**Q: Can I add my own custom agents?**
A: Yes! The architecture is modular. You can create custom agents following the existing agent patterns in the `backend-main/Agents/` directory and register them in the router.

**Q: How is data privacy handled?**
A: User data is stored securely in PostgreSQL with encrypted passwords (bcrypt). JWT authentication manages sessions. The system includes CSRF protection and input validation. API keys are stored in environment variables, never in code.

### Deployment Questions

**Q: Can I deploy AgroAI on my own servers?**
A: Yes, AgroAI can be deployed using Docker (docker-compose files included) or manually. You'll need to configure environment variables and ensure all dependencies are installed.

**Q: What are the hardware requirements?**
A: Minimum: 4GB RAM, 2 CPU cores. Recommended: 8GB+ RAM, 4+ CPU cores, GPU (optional, for offline mode). For production: consider load balancing and caching strategies.

**Q: How do I scale AgroAI for multiple users?**
A: Use the Parallel RAG system, implement load balancing, leverage the caching layer (GPTCache), and consider deploying multiple agent instances. FastAPI supports async operations for better concurrency.

---

## 🤝 Contributing

We welcome contributions to AgroAI! Here's how you can help:

### How to Contribute

1. **Fork the repository** and create your branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes**:
   - Follow existing code style and conventions
   - Add tests for new features
   - Update documentation as needed
   - Ensure all tests pass

3. **Commit your changes**:
   ```bash
   git commit -am 'Add new feature: description'
   ```

4. **Push to your branch**:
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Open a Pull Request**:
   - Provide a clear description of changes
   - Reference any related issues
   - Include screenshots for UI changes

### Contribution Areas

- **New Agents**: Add specialized agricultural agents
- **RAG Improvements**: Enhance retrieval and generation quality
- **Frontend Features**: Improve UI/UX and add new tools
- **Documentation**: Improve guides, add tutorials, fix typos
- **Testing**: Add unit tests, integration tests, or benchmarks
- **Bug Fixes**: Fix reported issues
- **Performance**: Optimize queries, caching, or workflows
- **Localization**: Add support for more languages

### Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on what's best for the community
- Show empathy towards others

---

## 🐛 Troubleshooting

### Common Issues

**Issue: "Module not found" errors in backend**
```bash
Solution:
1. Ensure virtual environment is activated
2. Reinstall dependencies: pip install -r requirements.txt
3. Check Python version (3.8+)
```

**Issue: Database connection errors in frontend**
```bash
Solution:
1. Verify PostgreSQL is running
2. Check DATABASE_URL in .env.local
3. Run: npx prisma generate && npx prisma db push
4. Check database credentials
```

**Issue: API key errors or rate limiting**
```bash
Solution:
1. Verify API keys in .env file
2. Check API key quotas and limits
3. Consider using offline mode for development
4. Implement caching to reduce API calls
```

**Issue: RAG retrieval returns no documents**
```bash
Solution:
1. Check if vector store is populated
2. Verify file paths in RAG configuration
3. Ensure embeddings are generated
4. Check VECTOR_DB_PATH in .env
```

**Issue: Agents not responding or timing out**
```bash
Solution:
1. Check internet connectivity
2. Verify agent timeout settings
3. Review agent logs for specific errors
4. Increase AGENT_TIMEOUT in .env
```

**Issue: Frontend build failures**
```bash
Solution:
1. Clear node_modules and reinstall: rm -rf node_modules && npm install
2. Clear Next.js cache: rm -rf .next
3. Check for TypeScript errors: npm run build
4. Verify all environment variables are set
```

**Issue: Docker container crashes**
```bash
Solution:
1. Check docker logs: docker-compose logs
2. Verify environment variables in docker-compose.yml
3. Ensure sufficient resources (memory, CPU)
4. Check port conflicts
```

### Getting Help

- **Check Logs**: Review application logs for detailed error messages
- **Documentation**: See `Frontend/docs/` for detailed guides
- **GitHub Issues**: Search or create an issue at [GitHub Issues](https://github.com/sanskaryo/AgroAI/issues)
- **Agent Logs**: Check backend console output for agent-specific errors

### Performance Optimization Tips

1. **Enable Caching**: GPTCache reduces API calls significantly
2. **Use Offline Mode**: For development, use local models
3. **Optimize Vector Store**: Reduce chunk sizes for faster retrieval
4. **Parallel Processing**: Leverage parallel RAG for multiple queries
5. **Database Indexing**: Add indexes to frequently queried fields

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
