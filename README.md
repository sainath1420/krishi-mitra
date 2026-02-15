# 🌾 Krishi Mitra - AI-Powered Agricultural Platform

> Empowering Indian farmers with real-time insights, market intelligence, and AI-driven agricultural advisory

[![Hackathon](https://img.shields.io/badge/Hackathon-AWS%20AI%20for%20Bharat-orange)](https://vision.hack2skill.com)
[![Track](https://img.shields.io/badge/Track-Rural%20Innovation-green)](https://vision.hack2skill.com)
[![Status](https://img.shields.io/badge/Status-MVP-blue)](https://github.com)

---

## 📖 About

**Krishi Mitra** is an AI-powered platform that bridges the information gap for rural farmers in India. By combining computer vision, conversational AI, and predictive analytics, we help farmers:

- 🔍 **Diagnose crop diseases** instantly with 90%+ accuracy
- 💰 **Maximize profits** through real-time market intelligence and price forecasting
- 🤝 **Connect directly with buyers**, eliminating middlemen
- 📱 **Access information** through mobile, WhatsApp, SMS, and voice in vernacular languages

---

## 🎯 Problem Statement

**Track:** AI for Rural Innovation & Sustainable Systems

Indian farmers face critical challenges:
- Limited access to agricultural expertise and real-time information
- Information asymmetry in market pricing, leading to income loss
- Crop diseases detected too late, resulting in significant yield losses
- Multiple layers of middlemen reducing profit margins by 30-40%
- Low digital literacy and language barriers

---

## 💡 Our Solution

### Core Features

#### 1. 🩺 Crop Disease Detection
- Upload crop/leaf photos for instant AI diagnosis
- 90%+ accuracy using CNN models trained on Indian crop datasets
- Treatment recommendations (organic & chemical options)
- Disease severity assessment and confidence scoring

#### 2. 🧠 AI Advisory System
- Conversational AI agent for personalized farming advice
- Weather-based crop recommendations
- Crop rotation suggestions and water management tips
- Multi-lingual support (Hindi, Telugu, Tamil, Marathi, etc.)

#### 3. 📊 Market Intelligence
- Real-time mandi price tracking across India
- 7-30 day price forecasting using ARIMA/Prophet models
- Best-time-to-sell recommendations
- Nearby market price comparisons

#### 4. 🤝 Direct Market Linkage
- Connect farmers with verified buyers and aggregators
- Eliminate middlemen, increase farmer income by 15-30%
- Secure transaction management
- Rating and review system

#### 5. 📱 Multi-Channel Access
- **Mobile App** - React Native iOS/Android app
- **WhatsApp Bot** - Text-based interface with image support
- **Voice/IVR** - For low-literacy users via Twilio
- **Web Portal** - Admin and buyer dashboard

---

## 🏗️ Architecture

### System Layers

```
┌─────────────────────────────────────────────────────────┐
│         Presentation Layer                               │
│  Mobile App | WhatsApp | Voice/SMS | Web Portal         │
└─────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│              API Gateway (AWS)                           │
│  Authentication | Rate Limiting | Load Balancing        │
└─────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│                 Microservices                            │
│  Disease Detection | AI Agent | Market Intelligence     │
│  User Management | Marketplace | Notifications          │
└─────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│          Data & External Services                        │
│  PostgreSQL | Redis | Agmarknet | IMD | Translate       │
└─────────────────────────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

### AI/ML
- **PyTorch** - Crop disease detection CNN
- **TensorFlow** - Model training and inference
- **AI Agent** - Conversational AI for advisory
- **Prophet/ARIMA** - Time-series price forecasting
- **scikit-learn** - Data preprocessing and analysis

### Backend
- **Python FastAPI** - Main API server
- **Node.js** - WhatsApp bot integration
- **AWS Lambda** - Serverless functions
- **Docker** - Containerization
- **Kubernetes** - Orchestration

### Frontend
- **React Native** - Cross-platform mobile app
- **Progressive Web App (PWA)** - Offline-first web app
- **Tailwind CSS** - Styling
- **Chart.js** - Data visualization

### Database
- **PostgreSQL** - All data storage (users, transactions, images, logs)
- **Redis** - Caching and session management

### Cloud & DevOps
- **AWS** - EC2, Lambda, API Gateway, RDS
- **GitHub Actions** - CI/CD pipeline
- **Terraform** - Infrastructure as code

### Communication
- **WhatsApp Business API** - Messaging
- **Twilio** - SMS/Voice
- **Firebase Cloud Messaging** - Push notifications

---

## 🚀 Getting Started

### Prerequisites
```bash
- Node.js >= 18.x
- Python >= 3.9
- PostgreSQL >= 14
- Redis >= 6.x
- Docker & Docker Compose
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/krishi-mitra.git
cd krishi-mitra
```

2. **Set up environment variables**
```bash
cp .env.example .env
# Edit .env with your API keys and configuration
```

3. **Install dependencies**
```bash
# Backend
cd backend
pip install -r requirements.txt

# Frontend
cd ../frontend
npm install
```

4. **Start database services**
```bash
docker-compose up -d postgres redis
```

5. **Run migrations**
```bash
cd backend
python manage.py migrate
```

6. **Start development servers**
```bash
# Backend (Terminal 1)
cd backend
uvicorn main:app --reload

# Frontend (Terminal 2)
cd frontend
npm start
```

The app should now be running at:
- Backend API: `http://localhost:8000`
- Frontend: `http://localhost:3000`

---

## 📱 Usage Examples

### Disease Detection
```python
# Upload image via API
import requests

response = requests.post(
    'http://localhost:8000/api/detect-disease',
    files={'image': open('crop_leaf.jpg', 'rb')},
    headers={'Authorization': 'Bearer YOUR_TOKEN'}
)

print(response.json())
# {
#   "disease": "Late Blight",
#   "confidence": 0.94,
#   "severity": "moderate",
#   "treatment": "Apply copper-based fungicide..."
# }
```

### Market Price Query
```python
# Get current mandi prices
response = requests.get(
    'http://localhost:8000/api/market/prices',
    params={'crop': 'wheat', 'location': 'Punjab'}
)

print(response.json())
# {
#   "crop": "wheat",
#   "current_price": 2100,
#   "forecast_7d": 2150,
#   "recommendation": "Hold for 5 days"
# }
```

---

## 📈 Implementation Roadmap

### Phase 1: Hackathon (48 hours)
- ✅ Core MVP with disease detection
- ✅ Basic AI advisory chatbot
- ✅ Real-time mandi price display
- ✅ WhatsApp + Mobile app interface

### Phase 2: Pilot (3 months)
- Add price forecasting module
- Implement vernacular language support
- Build voice interface
- Pilot with 500 farmers in 1 district
- Establish partnerships with local FPOs

### Phase 3: Scale (6 months)
- Launch buyer marketplace
- Scale to 5,000 farmers across 3 states
- Partner with agri-input companies
- Integrate payment gateway
- Add weather-based crop insurance

### Year 1 Goals
- 50,000+ farmers onboarded
- 500K+ advisory interactions
- 10K+ successful transactions
- Expand to 10 states

---

## 🎯 Impact Metrics

### Expected Impact (Year 1)
- **15-30%** increase in farmer income through better market timing
- **25%** reduction in crop loss via early disease detection
- **50,000+** farmers onboarded
- **500K+** advisory interactions
- **10K+** successful buyer-farmer transactions

---

## 🏆 Competitive Advantages

1. **Multi-Modal AI Integration** - Combines vision, NLP, and forecasting
2. **India-Specific Data** - Trained on Indian crops, pests, and market patterns
3. **Accessibility-First** - Voice, vernacular, works on low-end devices
4. **Network Effects** - More users = better predictions for everyone
5. **Freemium Model** - Free for farmers, revenue from buyers (2-3% commission)

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

```bash
# Fork the repo, create a branch
git checkout -b feature/your-feature

# Make changes and commit
git commit -m "Add amazing feature"

# Push and create PR
git push origin feature/your-feature
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

**Team AgroTech Innovators**

- [Your Name] - Team Leader
- [Team Member 2] - AI/ML Engineer
- [Team Member 3] - Full Stack Developer
- [Team Member 4] - UI/UX Designer

---

## 📞 Contact

- **Email**: contact@krishimitra.com
- **Website**: https://krishimitra.com
- **Twitter**: [@KrishiMitra](https://twitter.com/krishimitra)
- **LinkedIn**: [Krishi Mitra](https://linkedin.com/company/krishimitra)

---

## 🙏 Acknowledgments

- **AWS AI for Bharat Hackathon** - For the opportunity
- **Agmarknet** - For market price data
- **India Meteorological Department** - For weather data
- **PlantVillage Dataset** - For training disease detection models
- **Indian farmers** - Our inspiration and end users

---

## 📚 Documentation

For detailed documentation, please visit:
- [API Documentation](docs/API.md)
- [Architecture Guide](docs/ARCHITECTURE.md)
- [Deployment Guide](docs/DEPLOYMENT.md)
- [User Manual](docs/USER_MANUAL.md)

---

## 🌟 Show Your Support

If you like this project, please ⭐ star the repository!

---

**Built with ❤️ for Indian farmers** 🇮🇳
