# FlexaBrain Core

<div align="center">

![FlexaBrain Logo](https://github.com/sonnier-ventures/flexa-core/blob/main/docs/assets/flexabrain-logo.png)

**Intelligence Without Limits**

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/sonnier-ventures/flexa-core/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Docker](https://img.shields.io/badge/docker-ready-blue.svg)](https://hub.docker.com/r/sonnier-ventures/flexa-core)
[![Node.js](https://img.shields.io/badge/node.js-20+-green.svg)](https://nodejs.org/)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org/)

*The first truly self-hosted AI platform designed to adapt to your needs, not the other way around.*

[🚀 Quick Start](#-quick-start) • [📖 Documentation](#-documentation) • [🤖 AI Agents](#-ai-agents) • [🔧 Installation](#-installation) • [💡 Examples](#-examples)

</div>

---

## 🌟 What is FlexaBrain Core?

FlexaBrain Core is a revolutionary **self-hosted AI platform** that delivers enterprise-grade artificial intelligence without external dependencies. Built on the principle of "Intelligence Without Limits," it provides complete control over your AI infrastructure while delivering cutting-edge analytics, predictions, and insights.

### ✨ Key Features

🧠 **Three Specialized AI Agents**
- **Oracle**: Predictive analytics and forecasting
- **Sentinel**: Monitoring and anomaly detection  
- **Sage**: Business intelligence and insights

🔒 **Complete Privacy**
- Zero external API dependencies
- All AI processing stays local
- Full data sovereignty and control

⚡ **Enterprise Ready**
- Sub-2-second response times
- 99.9% uptime capability
- Horizontal scaling support

🎯 **Flexible Architecture**
- Custom model training
- Plugin ecosystem
- Multi-modal processing

## 🚀 Quick Start

Get FlexaBrain running in under 15 minutes:

```bash
# Clone the repository
git clone https://github.com/sonnier-ventures/flexa-core.git
cd flexa-core

# Install dependencies
pnpm install

# Setup environment
cp .env.example .env.local

# Start AI models (this may take 10-20 minutes for first download)
ollama serve &
pnpm ai:pull

# Initialize database
pnpm db:init && pnpm db:migrate && pnpm db:seed

# Start development servers
pnpm dev

# Verify installation
pnpm verify
```

**Access your FlexaBrain:**
- 📊 **Dashboard**: http://localhost:3000
- 🔌 **API Docs**: http://localhost:8000/docs
- 🧠 **AI Engine**: http://localhost:11434

## 🤖 Meet Your AI Agents

### 🔮 Oracle Agent
**The Predictor** - Specializes in predictive analytics and future-focused insights

```javascript
// Example: Sales forecasting
const prediction = await oracle.query({
  query: "Predict Q4 sales based on last 18 months of data",
  context: "SaaS platform with seasonal patterns"
});
```

### 🛡️ Sentinel Agent  
**The Guardian** - Monitors systems and detects anomalies in real-time

```javascript
// Example: Data quality check
const quality = await sentinel.query({
  query: "Check data quality in customer database",
  dataset: "customer_data.csv"
});
```

### 🧙 Sage Agent
**The Analyst** - Provides comprehensive business intelligence and insights

```javascript
// Example: Business analysis
const insights = await sage.query({
  query: "Analyze customer satisfaction trends and suggest improvements",
  timeframe: "last_6_months"
});
```

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    FlexaBrain Core                          │
├─────────────────────────────────────────────────────────────┤
│  FlexaDash Pro (Next.js)     │  Brain Server (Node.js)      │
│  ┌─────────────────────────┐  │  ┌─────────────────────────┐ │
│  │ • Real-time Dashboard   │  │  │ • AI Agent Orchestration│ │
│  │ • Natural Language UI   │  │  │ • Data Processing       │ │
│  │ • Customizable Widgets  │  │  │ • API Endpoints         │ │
│  └─────────────────────────┘  │  └─────────────────────────┘ │
├─────────────────────────────────────────────────────────────┤
│                    AI Engine (Ollama)                      │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │   Oracle    │ │  Sentinel   │ │    Sage     │           │
│  │ (Mistral)   │ │ (Llama2)    │ │ (CodeLlama) │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
├─────────────────────────────────────────────────────────────┤
│              Data Layer (SQLite/PostgreSQL)                │
└─────────────────────────────────────────────────────────────┘
```

## 🔧 Installation

### Prerequisites

- **Node.js** 20+ (LTS recommended)
- **Python** 3.11+
- **Docker** & Docker Compose
- **8GB RAM** minimum (16GB recommended)
- **20GB** free disk space

### Development Setup

```bash
# 1. Clone and setup
git clone https://github.com/sonnier-ventures/flexa-core.git
cd flexa-core
pnpm install

# 2. Environment configuration
cp .env.example .env.local
# Edit .env.local with your settings

# 3. Start AI models
ollama serve &
ollama pull llama2:7b-chat
ollama pull mistral:7b-instruct
ollama pull codellama:7b-instruct

# 4. Database setup
pnpm db:init
pnpm db:migrate
pnpm db:seed

# 5. Start development
pnpm dev
```

### Production Deployment

#### Docker Compose (Recommended)
```bash
# Production deployment
docker-compose -f docker-compose.prod.yml up -d

# With monitoring
docker-compose -f docker-compose.prod.yml --profile monitoring up -d
```

#### Kubernetes
```bash
# Deploy to Kubernetes
kubectl apply -f k8s/

# Check deployment status
kubectl get pods -l app=flexabrain
```

## 💡 Examples

### Basic Agent Interaction

```javascript
import { FlexaBrainClient } from '@flexabrain/js-sdk';

const fb = new FlexaBrainClient({
  apiKey: 'your-api-key',
  baseUrl: 'http://localhost:8000'
});

// Predictive analysis
const forecast = await fb.agents.oracle.query({
  query: "Forecast next quarter's revenue based on current trends",
  data: salesData,
  confidence_threshold: 0.8
});

// Anomaly detection
const anomalies = await fb.agents.sentinel.query({
  query: "Detect unusual patterns in user behavior",
  dataset: userActivityData,
  real_time: true
});

// Business insights
const insights = await fb.agents.sage.query({
  query: "Analyze customer segmentation and provide strategic recommendations",
  context: "B2B SaaS company, 10k users"
});
```

### Multi-Agent Workflow

```python
from flexabrain import FlexaBrain

fb = FlexaBrain(api_key="your-api-key")

# Sequential analysis pipeline
workflow = fb.workflows.create({
    "name": "Customer Analysis Pipeline",
    "steps": [
        {
            "agent": "sentinel",
            "task": "Check data quality in customer dataset",
            "output": "quality_report"
        },
        {
            "agent": "sage", 
            "task": "Analyze customer segments and behavior",
            "depends_on": "quality_report",
            "condition": "quality_score > 0.9"
        },
        {
            "agent": "oracle",
            "task": "Predict churn risk for each segment",
            "uses": "customer_segments"
        }
    ]
})

# Execute workflow
results = workflow.execute()
```

### Real-time Data Processing

```bash
# Stream processing with webhooks
curl -X POST http://localhost:8000/api/v1/streams \
  -H "Content-Type: application/json" \
  -d '{
    "source": "kafka://localhost:9092/user-events",
    "agent": "sentinel",
    "window": "5m",
    "trigger": "anomaly_detected",
    "webhook": "https://your-app.com/alerts"
  }'
```

## 🛠️ Development

### Project Structure

```
flexa-core/
├── apps/
│   ├── dashboard/          # FlexaDash Pro (Next.js)
│   ├── brain-server/       # AI Engine & API (Node.js)
│   └── command-cli/        # CLI Interface
├── packages/
│   ├── ai-core/           # Shared AI utilities
│   ├── ui-components/     # React components
│   └── shared-types/      # TypeScript definitions
├── docker/                # Container configurations
├── k8s/                   # Kubernetes manifests
├── docs/                  # Documentation
└── scripts/               # Utility scripts
```

### Available Scripts

```bash
# Development
pnpm dev              # Start all services
pnpm build            # Build for production
pnpm test             # Run test suite
pnpm lint             # Lint and format code

# Database
pnpm db:init          # Initialize database
pnpm db:migrate       # Run migrations  
pnpm db:seed          # Seed with sample data
pnpm db:reset         # Reset database

# AI Models
pnpm ai:pull          # Download AI models
pnpm ai:status        # Check model status
pnpm ai:models        # List available models

# Docker
pnpm docker:build     # Build containers
pnpm docker:up        # Start containers
pnpm docker:down      # Stop containers

# Monitoring
pnpm logs             # View all logs
pnpm health           # Health check
pnpm status           # Service status
```

## 📖 Documentation

- **[User Guide](docs/user-guide.md)** - Complete usage documentation
- **[API Reference](docs/api-reference.md)** - REST API documentation
- **[Setup Guide](docs/setup-guide.md)** - Installation and configuration
- **[Best Practices](docs/best-practices.md)** - Optimization guidelines
- **[Troubleshooting](docs/troubleshooting.md)** - Problem resolution
- **[Contributing](CONTRIBUTING.md)** - Development guidelines

## 🔒 Security & Privacy

FlexaBrain Core is designed with privacy and security as core principles:

- **🔐 Zero External Dependencies**: All AI processing happens locally
- **🛡️ Data Sovereignty**: Your data never leaves your infrastructure  
- **🔑 Enterprise Security**: SOC 2, GDPR, HIPAA compliance ready
- **🚨 Audit Logging**: Comprehensive activity tracking
- **⚡ Encryption**: End-to-end encryption for data at rest and in transit

## 🌟 Community & Support

### Getting Help

- **📚 Documentation**: Comprehensive guides and API docs
- **💬 Discord**: Join our community for real-time help
- **🐛 GitHub Issues**: Report bugs and request features
- **📧 Support**: Enterprise support available

### Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

```bash
# Quick contribution setup
git clone https://github.com/sonnier-ventures/flexa-core.git
cd flexa-core
pnpm install
pnpm dev

# Create feature branch
git checkout -b feature/amazing-feature
# Make your changes
git commit -m "Add amazing feature"
git push origin feature/amazing-feature
# Open a Pull Request
```

## 🎯 Roadmap

### 2025 Q2 - FlexaBrain Platform
- [ ] No-code/low-code AI application builder
- [ ] Visual workflow designer
- [ ] Marketplace for AI agents and plugins
- [ ] Advanced model fine-tuning interface

### 2025 Q3 - FlexaCommand IDE  
- [ ] Natural language programming environment
- [ ] Real-time code generation and modification
- [ ] Voice-based development workflows
- [ ] Multi-agent collaboration for coding

### 2026 - FlexaEnterprise
- [ ] White-label licensing opportunities
- [ ] Advanced enterprise features
- [ ] Multi-tenant architecture
- [ ] Global deployment options

## 📊 Performance

FlexaBrain Core is optimized for performance:

- **⚡ Response Time**: <2 seconds for 95% of queries
- **🚀 Throughput**: 1000+ concurrent users per instance
- **💾 Memory Usage**: <8GB RAM for full deployment
- **📈 Scalability**: Horizontal scaling with Kubernetes

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Ollama** - For providing excellent local AI model serving
- **OpenAI** - For advancing the field of artificial intelligence
- **Anthropic** - For safety-focused AI development
- **The Open Source Community** - For the amazing tools and libraries

---

<div align="center">

**Built with ❤️ by Sonnier Ventures**

[Website](https://sonnierventures.com) • [Documentation](https://docs.flexabrain.ai) • [Twitter](https://twitter.com/sonnierventures) • [Discord](https://discord.gg/flexabrain)

**FlexaBrain Core: Intelligence Without Limits**

⭐ **Star us on GitHub** if you find FlexaBrain useful!

</div>
# 5. Start development
pnpm dev
```

### Production Deployment

#### Docker Compose (Recommended)
```bash
# Production deployment
docker-compose -f docker-compose.prod.yml up -d

# With monitoring
docker-compose -f docker-compose.prod.yml --profile monitoring up -d
```

#### Kubernetes
```bash
# Deploy to Kubernetes
kubectl apply -f k8s/

# Check deployment status
kubectl get pods -l app=flexabrain
```

## 💡 Examples

### Basic Agent Interaction

```javascript
import { FlexaBrainClient } from '@flexabrain/js-sdk';

const fb = new FlexaBrainClient({
  apiKey: 'your-api-key',
  baseUrl: 'http://localhost:8000'
});

// Predictive analysis
const forecast = await fb.agents.oracle.query({
  query: "Forecast next quarter's revenue based on current trends",
  data: salesData,
  confidence_threshold: 0.8
});

// Anomaly detection
const anomalies = await fb.agents.sentinel.query({
  query: "Detect unusual patterns in user behavior",
  dataset: userActivityData,
  real_time: true
});

// Business insights
const insights = await fb.agents.sage.query({
  query: "Analyze customer segmentation and provide strategic recommendations",
  context: "B2B SaaS company, 10k users"
});
```

### Multi-Agent Workflow

```python
from flexabrain import FlexaBrain

fb = FlexaBrain(api_key="your-api-key")

# Sequential analysis pipeline
workflow = fb.workflows.create({
    "name": "Customer Analysis Pipeline",
    "steps": [
        {
            "agent": "sentinel",
            "task": "Check data quality in customer dataset",
            "output": "quality_report"
        },
        {
            "agent": "sage", 
            "task": "Analyze customer segments and behavior",
            "depends_on": "quality_report",
            "condition": "quality_score > 0.9"
        },
        {
            "agent": "oracle",
            "task": "Predict churn risk for each segment",
            "uses": "customer_segments"
        }
    ]
})

# Execute workflow
results = workflow.execute()
```

### Real-time Data Processing

```bash
# Stream processing with webhooks
curl -X POST http://localhost:8000/api/v1/streams \
  -H "Content-Type: application/json" \
  -d '{
    "source": "kafka://localhost:9092/user-events",
    "agent": "sentinel",
    "window": "5m",
    "trigger": "anomaly_detected",
    "webhook": "https://your-app.com/alerts"
  }'
```

## 🛠️ Development

### Project Structure

```
flexabrain-core/
├── apps/
│   ├── dashboard/          # FlexaDash Pro (Next.js)
│   ├── brain-server/       # AI Engine & API (Node.js)
│   └── command-cli/        # CLI Interface
├── packages/
│   ├── ai-core/           # Shared AI utilities
│   ├── ui-components/     # React components
│   └── shared-types/      # TypeScript definitions
├── docker/                # Container configurations
├── k8s/                   # Kubernetes manifests
├── docs/                  # Documentation
└── scripts/               # Utility scripts
```

### Available Scripts

```bash
# Development
pnpm dev              # Start all services
pnpm build            # Build for production
pnpm test             # Run test suite
pnpm lint             # Lint and format code

# Database
pnpm db:init          # Initialize database
pnpm db:migrate       # Run migrations  
pnpm db:seed          # Seed with sample data
pnpm db:reset         # Reset database

# AI Models
pnpm ai:pull          # Download AI models
pnpm ai:status        # Check model status
pnpm ai:models        # List available models

# Docker
pnpm docker:build     # Build containers
pnpm docker:up        # Start containers
pnpm docker:down      # Stop containers

# Monitoring
pnpm logs             # View all logs
pnpm health           # Health check
pnpm status           # Service status
```

## 📖 Documentation

- **[User Guide](docs/user-guide.md)** - Complete usage documentation
- **[API Reference](docs/api-reference.md)** - REST API documentation
- **[Setup Guide](docs/setup-guide.md)** - Installation and configuration
- **[Best Practices](docs/best-practices.md)** - Optimization guidelines
- **[Troubleshooting](docs/troubleshooting.md)** - Problem resolution
- **[Contributing](CONTRIBUTING.md)** - Development guidelines

## 🔒 Security & Privacy

FlexaBrain Core is designed with privacy and security as core principles:

- **🔐 Zero External Dependencies**: All AI processing happens locally
- **🛡️ Data Sovereignty**: Your data never leaves your infrastructure  
- **🔑 Enterprise Security**: SOC 2, GDPR, HIPAA compliance ready
- **🚨 Audit Logging**: Comprehensive activity tracking
- **⚡ Encryption**: End-to-end encryption for data at rest and in transit

## 🌟 Community & Support

### Getting Help

- **📚 Documentation**: Comprehensive guides and API docs
- **💬 Discord**: Join our community for real-time help
- **🐛 GitHub Issues**: Report bugs and request features
- **📧 Support**: Enterprise support available

### Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

```bash
# Quick contribution setup
git clone https://github.com/flexaai/flexabrain-core.git
cd flexabrain-core
pnpm install
pnpm dev

# Create feature branch
git checkout -b feature/amazing-feature
# Make your changes
git commit -m "Add amazing feature"
git push origin feature/amazing-feature
# Open a Pull Request
```

## 🎯 Roadmap

### 2025 Q2 - FlexaBrain Platform
- [ ] No-code/low-code AI application builder
- [ ] Visual workflow designer
- [ ] Marketplace for AI agents and plugins
- [ ] Advanced model fine-tuning interface

### 2025 Q3 - FlexaCommand IDE  
- [ ] Natural language programming environment
- [ ] Real-time code generation and modification
- [ ] Voice-based development workflows
- [ ] Multi-agent collaboration for coding

### 2026 - FlexaEnterprise
- [ ] White-label licensing opportunities
- [ ] Advanced enterprise features
- [ ] Multi-tenant architecture
- [ ] Global deployment options

## 📊 Performance

FlexaBrain Core is optimized for performance:

- **⚡ Response Time**: <2 seconds for 95% of queries
- **🚀 Throughput**: 1000+ concurrent users per instance
- **💾 Memory Usage**: <8GB RAM for full deployment
- **📈 Scalability**: Horizontal scaling with Kubernetes

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Ollama** - For providing excellent local AI model serving
- **OpenAI** - For advancing the field of artificial intelligence
- **Anthropic** - For safety-focused AI development
- **The Open Source Community** - For the amazing tools and libraries

---

<div align="center">

**Built with ❤️ by the FlexaAI Team**

[Website](https://flexabrain.ai) • [Documentation](https://docs.flexabrain.ai) • [Twitter](https://twitter.com/flexaai) • [Discord](https://discord.gg/flexabrain)

**FlexaBrain Core: Intelligence Without Limits**

⭐ **Star us on GitHub** if you find FlexaBrain useful!

</div>
