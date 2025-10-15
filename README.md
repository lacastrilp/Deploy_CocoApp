# CocoaApp

Web application for detecting and monitoring ripening and disease in cocoa crops using computer vision and IoT sensors.

The system allows cocoa farmers, researchers, and managers to record data in the field, view it on an interactive map, and receive alerts about the fruit's status in real-time.

## Project Description

The application offers:
- **Field data recording**: Fruit status (unripe, ripe, diseased), geographic location, and detailed metrics
- **Interactive map**: Visualization of plots, crops, and trees on a georeferenced map (GeoJSON)
- **Real-time alerts**: Automatic generation of notifications based on data analysis
- **Zone management**: Hierarchical view of farms, lots, crops, trees, and fruits
- **Statistics dashboard**: Comprehensive analytics and metrics
- **Dark/Light theme**: Modern UI with theme switching
- **Responsive design**: Works on desktop and mobile devices

## Architecture

The system follows a **Client-Server** model:

- **Frontend**: React + TypeScript + Vite
- **Backend**: FastAPI (Python)
- **Database**: PostgreSQL (via Supabase)
- **Storage**: Supabase Storage (for images and assets)

## Prerequisites

Before starting, make sure you have installed:

- **Python 3.8+**
- **Node.js 16+**
- **npm** or **yarn**
- **Git**

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/your-username/CocoaApp.git
cd CocoaApp
```

### 2. Backend Setup

#### Create and activate virtual environment

```bash
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate.ps1
# On macOS/Linux:
source venv/bin/activate
```

#### Install Python dependencies

```bash
pip install -r requirements.txt
```

#### Environment variables

Copy the example environment file and configure your Supabase credentials:

```bash
cp ../.env.example backend/.env
```

Edit `backend/.env` with your Supabase project details:

```env
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_SERVICE_ROLE_KEY=your_service_role_key_here
```

#### Start the backend server

```bash
python -m uvicorn src.db.main:app --reload --port 8000
```

The backend will be available at `http://localhost:8000`

### 3. Frontend Setup

#### Install dependencies

```bash
cd ../frontend-vite
npm install
```

#### Environment variables

Copy the example environment file:

```bash
cp ../.env.example .env.local
```

Edit `.env.local` with your Supabase project details:

```env
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_SERVICE_ROLE_KEY=your_service_role_key_here
```

#### Start the frontend development server

```bash
npm run dev
```

## API Endpoints

### Backend Endpoints

- `GET /` - Health check
- `GET /arboles` - Get all trees with fruits
- `GET /cultivos` - Get all crops (GeoJSON)
- `GET /lotes` - Get all lots (GeoJSON)
- `GET /stats/` - Get comprehensive statistics
- `GET /stats/zones` - Get hierarchical zone data
- `GET /notificaciones` - Get all notifications
- `POST /notificaciones` - Create notification
- `PUT /notificaciones/{id}/read` - Mark notification as read
- `DELETE /notificaciones/{id}` - Delete notification
- `GET /zone-analysis` - Get zone analysis with notifications

## Features Implemented

### Core Features
- **Interactive Map**: Satellite view with lot boundaries, crop areas, and tree markers
- **Tree Management**: View individual trees with fruit status and metrics
- **Zone Hierarchy**: Navigate through farms > lots > crops > trees > fruits
- **Notifications**: Toast notifications and notification dropdown
- **Statistics**: Comprehensive dashboard with metrics

### UI/UX Features
- **Dark/Light Theme**: Toggle between themes with persistent settings
- **Responsive Design**: Works on desktop and mobile
- **Modern UI**: Clean, professional interface with smooth animations
- **Navigation**: Bottom navigation bar for easy access
- **Settings**: Configurable app settings (theme, notifications, etc.)

### Data Features
- **Geographic Data**: GeoJSON format for spatial visualization
- **Fruit Status Tracking**: Inmaduro, Maduro, Transición, Enfermo
- **Clustering**: DBSCAN algorithm for grouping spatial data
- **Metrics**: Raw sensor data, voltage, capacitance measurements
- **Hierarchical Structure**: Organized data from farms to individual fruits

### Technical Features
- **TypeScript**: Full type safety in frontend
- **Error Handling**: Comprehensive error handling and validation
- **Performance**: Optimized queries and efficient data loading
- **Security**: Supabase authentication and authorization
- **Scalability**: Modular architecture for easy expansion

## Development

### Running Tests

```bash
# Backend tests
cd backend
python -m pytest

# Frontend tests
cd frontend-vite
npm test
```

### Code Formatting

```bash
# Backend formatting
cd backend
black src/
isort src/

# Frontend formatting
cd frontend-vite
npm run format
```

### Building for Production

```bash
# Build frontend
cd frontend-vite
npm run build

# The built files will be in the dist/ directory
```

## Environment Variables

Create a `.env` file in both `backend/` and `frontend-vite/` directories with the following variables:

```env
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_SERVICE_ROLE_KEY=your_service_role_key_here
```

## Authors

- [Luis Alejandro Castrillón](https://github.com/lacastrilp)
- [Sara López Marín](https://github.com/slopma)
- [Nicolás Ospina](https://github.com/niosto)
- [Samuel Enrique Rivero](https://github.com/SamuelRivero50)