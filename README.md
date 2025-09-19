# HealthGuard - Personal Health Monitoring System

A comprehensive web-based health monitoring platform that integrates with various devices, provides AI-powered health analysis, and includes automated emergency response capabilities.

## 🏥 Project Overview

HealthGuard is a **web-only** prototype designed for real-time health monitoring and emergency response. The system integrates with Google Fit and Web Bluetooth devices to collect vital signs, uses AI for health analysis, and provides automated emergency alerts to contacts and medical services.

### Key Constraints
- **Web-only implementation** - No native mobile app
- **HealthKit is intentionally NOT supported** - Future companion iOS app planned
- Chrome/Edge browsers required for Web Bluetooth functionality

## ✨ Features

### 🔐 Authentication & Security
- Email/password registration with bcrypt password hashing
- **6-digit email verification** via SendGrid
- **4-digit SMS phone verification** via Twilio (optional)
- JWT access + refresh token system
- Session management with secure token refresh

### 👤 User Profile & Medical History
- Comprehensive medical profile with structured data
- Allergy tracking and medication management
- Emergency contact management with consent tracking
- Medical history with tags and free-text notes
- Audit logging for all profile changes

### 📱 Device Integration
- **Google Fit OAuth 2.0** integration (server-side)
  - Heart rate, blood pressure, sleep data import
  - Encrypted refresh token storage
  - Automatic data synchronization
- **Web Bluetooth API** support (Chrome/Edge only)
  - Heart Rate Service (0x180D) support
  - Blood Pressure Service (0x1810) support
  - Auto-reconnect with exponential backoff
  - Local IndexedDB buffering for offline support

### 📊 Vitals Monitoring
- Real-time vital signs collection and storage
- Time-series PostgreSQL storage with proper indexing
- Support for heart rate, blood pressure, SpO2, and sleep data
- Historical data visualization with interactive charts
- Live monitoring dashboard with WebSocket updates

### 🤖 AI Health Analysis (Gemini)
- **Server-side only** AI analysis using Google Gemini
- Strict JSON schema validation with fallback rules
- Risk scoring (0-100) with confidence intervals
- Deterministic emergency detection rules
- Comprehensive logging of all AI interactions

### 🚨 Emergency Response System
- Automatic emergency detection based on vital signs
- **Multi-channel alert system:**
  - Full-screen browser alerts with audio
  - Email notifications to emergency contacts
  - SMS alerts via Twilio
  - Nearest hospital lookup using Google Places API
- Manual emergency trigger option
- Complete audit trail of emergency events

### 📈 Analytics & Reporting
- Historical health data visualization
- Trend analysis and pattern recognition
- Data export capabilities (CSV, PDF)
- AI analysis history tracking

## 🛠 Tech Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for responsive design
- **Recharts** for data visualization
- **React Hook Form** with Zod validation
- **TanStack Query** for state management
- **Wouter** for routing
- **shadcn/ui** component library

### Backend
- **Express.js** with TypeScript
- **PostgreSQL** with Drizzle ORM
- **Passport.js** for authentication
- **WebSocket** for real-time updates
- **Zod** for API validation

### External Services
- **Google Gemini AI** for health analysis
- **SendGrid** for email delivery
- **Twilio** for SMS notifications
- **Google Fit API** for health data import
- **Google Places API** for hospital lookup
- **Web Bluetooth API** for device connectivity

### Development Tools
- **Docker** for local development
- **TypeScript** for type safety
- **ESLint/Prettier** for code quality
- **OpenAPI/Swagger** for API documentation

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ and npm
- PostgreSQL 14+
- Docker (optional, for local setup)

### 1. Clone and Install
```bash
git clone <repository-url>
cd healthguard
npm install
