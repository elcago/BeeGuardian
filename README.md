# BeeGuardian - AI-Powered Bee Health Monitoring System

Live Demo: https://elcago.github.io/BeeGuardian/

## Overview
BeeGuardian is an integrated beekeeping management platform that combines AI-powered health analysis with localized resource matching, weather-based recommendations, and comprehensive education - making advanced beekeeping technology accessible to beekeepers of all experience levels.

The system analyzes visual and audio signals using a multimodal neural network  to detect hive health issues with 92.6% accuracy on 1,639+ samples, then provides actionable guidance including local suppliers, treatment timing based on weather conditions, and educational resources.

## Project Structure

(backtick)(backtick)(backtick)
BeeGuardian/
├── index.html              # Frontend web application
├── model_server.py         # Backend Flask API server
├── requirements.txt        # Python dependencies
├── README.md              # This file
└── bee_health_final_model.h5  # Trained ML model (not included - see below)
```

## Features

### Fully Functional (Web Demo)
- U.S. colony loss data visualization (2006-2024)
- Smart local resource finder with problem-specific search
- Weather-based beekeeping recommendations
- Comprehensive education hub with 9 learning modules

### Backend Required (ML Analysis)
- AI-powered hive health analysis (4 health categories)
- Image, audio, and video file analysis
- Bee counting and behavior detection

## Setup Instructions

### Frontend Only (Quick Start)

1. Visit the live site: https://elcago.github.io/BeeGuardian/
2. All features work except ML analysis (requires backend)

### Full System with Backend

**Prerequisites:**
- Python 3.8 or higher
- Trained model file: bee_health_final_model.h5 (contact for access)

**Step 1: Clone the repository**
git clone https://github.com/elcago/BeeGuardian.git
cd BeeGuardian

**Step 2: Install Python dependencies**
pip install -r requirements.txt

**Step 3: Add the model file**
Place bee_health_final_model.h5 in the project root directory.

**Step 4: Run the backend server**
python model_server.py

You should see:
Loading models...
Model loaded successfully!
Starting BeeGuardian server on http://localhost:5001

**Step 5: Serve the frontend** (in a new terminal)
python3 -m http.server 8000

**Step 6: Open in browser**
Navigate to http://localhost:8000

## API Endpoints

The backend provides several REST API endpoints:

- GET / - Server status page
- GET /api/health - Health check
- POST /api/analyze - Upload and analyze files
- POST /api/stream - Analyze live stream frames
- GET /api/model/info - Model information

## Model Details

**Architecture:** Cross-Attention Multimodal Neural Network (CAMNN)
- Visual pathway: CNN feature extraction (224x224 images to 4096 features)
- Audio pathway: MFCC + Mel Spectrogram + Chromagram + STFT to 4096 features
- Fusion: Cross-attention mechanism for multimodal integration

**Performance:**
- Training samples: 1,639+ images and audio recordings
- Accuracy: 93% on test set
- Classes: Healthy, Varroa Mites, Missing Queen, Hive Robbing

**Input formats:**
- Images: PNG, JPG, JPEG, GIF
- Audio: WAV, MP3
- Video: MP4, AVI

## Technologies Used

### Frontend
- HTML5, CSS3, JavaScript
- Chart.js for data visualization
- Google Maps Places API
- OpenWeatherMap API
- Responsive design with mobile support

### Backend
- Python 3.8+
- Flask web framework
- TensorFlow/Keras for ML inference
- OpenCV for image processing
- Librosa for audio feature extraction

## Data Sources
- Colony loss data: Bee Informed Partnership & USDA NASS (2006-2024)
- Educational content: University extension services, peer-reviewed research
- Weather data: OpenWeatherMap API
- Local resources: Google Maps Places API

## Project Background
 This application addresses the critical issue of declining bee populations (40% annual colony losses) by providing beekeepers with AI-powered diagnostic tools, practical local resources, and evidence-based educational content.

## For Users

### Quick Demo
1. Visit the live site to see working features: https://elcago.github.io/BeeGuardian/
2. Watch the demonstration video showing ML analysis in action
3. View source code directly on GitHub

### Running Backend Locally
While the backend can be run locally following the setup instructions above, the frontend demo showcases the complete user interface and integration design. The ML model file is not included in the repository due to size constraints (150MB+).

### Technical Highlights
- Intelligent problem-specific resource search with relevance categorization
- Asynchronous API coordination (geocoding to search to details)
- Real-time weather integration with beekeeping recommendations
- Multimodal ML model with cross-attention fusion
- Comprehensive error handling and graceful degradation

## License
MIT License - See LICENSE file for details

## Acknowledgments
- Bee Informed Partnership for colony loss data
- University extension services for educational resources
- Research institutions studying multimodal neural networks for agricultural applications

## Contact
For questions about the model or demo access, please open an issue on GitHub.
