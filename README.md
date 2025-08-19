# 🥔 Potato Disease Classification

A comprehensive machine learning solution for identifying potato diseases using Convolutional Neural Networks (CNN). This project helps farmers and agricultural professionals quickly diagnose potato plant diseases through image analysis, supporting early intervention and crop protection.

![Potato Disease Classification](https://img.shields.io/badge/Machine%20Learning-CNN-green)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.5.0-orange)
![FastAPI](https://img.shields.io/badge/FastAPI-Latest-blue)
![React](https://img.shields.io/badge/React-17.0.2-cyan)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Disease Classifications](#disease-classifications)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Model Performance](#model-performance)
- [Contributing](#contributing)
- [License](#license)

## 🌟 Overview

This project implements an end-to-end machine learning pipeline for potato disease classification. It can identify three key conditions in potato plants:

- **Early Blight** - Caused by *Alternaria solani*
- **Late Blight** - Caused by *Phytophthora infestans*  
- **Healthy** - No disease detected

The system provides both a web interface and REST API for disease prediction, making it accessible to various user types from farmers to agricultural researchers.

## ✨ Features

- 🔍 **Accurate Disease Detection**: High-precision CNN model for reliable plant disease identification
- 🌐 **Web Interface**: User-friendly React frontend for image upload and instant results
- 🚀 **REST API**: FastAPI backend for integration with other applications
- 📱 **Responsive Design**: Works seamlessly across desktop and mobile devices
- ⚡ **Fast Inference**: Optimized model for quick disease prediction
- 🔒 **Input Validation**: Robust file handling and error management
- 📊 **Confidence Scores**: Provides prediction confidence levels

## 🦠 Disease Classifications

### Early Blight
- **Pathogen**: *Alternaria solani*
- **Symptoms**: Circular dark brown lesions with target-like concentric rings
- **Impact**: Affects older leaves first, can cause significant yield loss
- **Optimal Conditions**: Warm temperatures (24-29°C), high humidity

### Late Blight
- **Pathogen**: *Phytophthora infestans*
- **Symptoms**: Water-soaked lesions with pale green halos, rapid spread
- **Impact**: Highly destructive, can destroy entire crops within days
- **Optimal Conditions**: Cool temperatures (12-18°C), moist conditions

### Healthy Plants
- **Characteristics**: Normal leaf color and structure
- **No visible disease symptoms**
- **Optimal growth conditions maintained**

## 🛠 Tech Stack

### Backend
- **TensorFlow 2.5.0**: Deep learning framework for CNN model
- **FastAPI**: Modern web framework for building APIs
- **Uvicorn**: ASGI server for serving the application
- **Pillow**: Image processing library
- **NumPy**: Numerical computing library

### Frontend
- **React 17.0.2**: JavaScript library for building user interfaces
- **Material-UI**: React components implementing Google's Material Design
- **Axios**: HTTP client for API requests
- **Material-UI Dropzone**: Drag-and-drop file upload component

### Development
- **Jupyter Notebook**: Model training and experimentation
- **Python 3.8+**: Programming language
- **Node.js**: JavaScript runtime for frontend development

## 📁 Project Structure

```
Potato-disease-classification/
├── potato-disease-classification-github/
│   ├── api/
│   │   ├── main.py              # FastAPI application
│   │   └── requirements.txt     # Python dependencies
│   ├── frontend/
│   │   ├── src/
│   │   │   ├── App.js          # Main React component
│   │   │   ├── home.js         # Image upload component
│   │   │   └── bg.png          # Background image
│   │   ├── package.json        # Node.js dependencies
│   │   └── public/             # Static files
│   ├── training/
│   │   └── potato-disease-classification-model.ipynb
│   └── saved_models/
│       └── 1/                  # Trained TensorFlow model
└── README.md                   # Project documentation
```

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- Node.js 14 or higher
- npm or yarn package manager

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Gauravdub-git/Potato-disease-classification.git
   cd Potato-disease-classification
   ```

2. **Navigate to the API directory**
   ```bash
   cd potato-disease-classification-github/api
   ```

3. **Create a virtual environment**
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

4. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

### Frontend Setup

1. **Navigate to the frontend directory**
   ```bash
   cd ../frontend
   ```

2. **Install Node.js dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

## 💻 Usage

### Starting the Backend

1. **Navigate to the API directory**
   ```bash
   cd potato-disease-classification-github/api
   ```

2. **Start the FastAPI server**
   ```bash
   python main.py
   ```

   The API will be available at `http://localhost:8000`

3. **Access API documentation**
   - Swagger UI: `http://localhost:8000/docs`
   - ReDoc: `http://localhost:8000/redoc`

### Starting the Frontend

1. **Navigate to the frontend directory**
   ```bash
   cd potato-disease-classification-github/frontend
   ```

2. **Start the React development server**
   ```bash
   npm start
   # or
   yarn start
   ```

   The web application will be available at `http://localhost:3000`

### Using the Application

1. **Web Interface**:
   - Open your browser to `http://localhost:3000`
   - Upload an image of a potato leaf using the drag-and-drop interface
   - View the prediction results with confidence scores

2. **API Usage**:
   ```python
   import requests
   
   # Upload image for prediction
   with open('potato_leaf.jpg', 'rb') as image_file:
       response = requests.post(
           'http://localhost:8000/predict',
           files={'file': image_file}
       )
   
   result = response.json()
   print(f"Disease: {result['class']}")
   print(f"Confidence: {result['confidence']}")
   ```

## 📚 API Documentation

### Endpoints

#### Health Check
```http
GET /
```
Returns API status and basic information.

#### Ping
```http
GET /ping
```
Simple health check endpoint.

#### Disease Prediction
```http
POST /predict
```

**Parameters:**
- `file`: Image file (JPEG, PNG, etc.)

**Response:**
```json
{
  "class": "Early Blight",
  "confidence": 0.95
}
```

**Possible Classes:**
- `Early Blight`
- `Late Blight`
- `Healthy`

### Error Responses

- **400 Bad Request**: Invalid image file
- **500 Internal Server Error**: Model prediction error

## 📊 Model Performance

The CNN model is trained on high-quality potato leaf images and achieves:

- **Architecture**: Custom CNN with multiple convolutional layers
- **Input Size**: 256x256 RGB images
- **Training Framework**: TensorFlow/Keras
- **Model Size**: Optimized for fast inference
- **Preprocessing**: Automatic image resizing and normalization

### Training Dataset
- Comprehensive collection of potato leaf images
- Balanced representation of all disease classes
- High-resolution images for detailed feature extraction
- Data augmentation techniques applied during training

## 🤝 Contributing

We welcome contributions to improve the project! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add some amazing feature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Areas for Contribution

- 🔬 **Model Improvements**: Enhance accuracy and performance
- 🎨 **UI/UX**: Improve user interface and experience
- 📖 **Documentation**: Expand documentation and tutorials
- 🧪 **Testing**: Add comprehensive test coverage
- 🌍 **Internationalization**: Support for multiple languages
- 📱 **Mobile App**: Native mobile application development

## 🔧 Development Setup

### Model Training

To retrain the model with your own dataset:

1. **Prepare your dataset** with the following structure:
   ```
   dataset/
   ├── Early_Blight/
   ├── Late_Blight/
   └── Healthy/
   ```

2. **Open the training notebook**:
   ```bash
   jupyter notebook potato-disease-classification-github/training/potato-disease-classification-model.ipynb
   ```

3. **Follow the notebook instructions** to train and save your model

### Environment Variables

Create a `.env` file in the frontend directory:

```env
REACT_APP_API_URL=http://localhost:8000/predict
```

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **PlantVillage Dataset**: For providing high-quality plant disease images
- **TensorFlow Community**: For the excellent deep learning framework
- **FastAPI**: For the modern and efficient web framework
- **React Community**: For the powerful frontend library
- **Agricultural Research Community**: For domain expertise and validation

## 📞 Contact

- **Author**: Gauravdub-git
- **Repository**: [Potato Disease Classification](https://github.com/Gauravdub-git/Potato-disease-classification)
- **Issues**: [GitHub Issues](https://github.com/Gauravdub-git/Potato-disease-classification/issues)

---

## 🌱 Impact

This project contributes to:
- **Sustainable Agriculture**: Early disease detection reduces pesticide usage
- **Food Security**: Protecting crops from disease outbreaks
- **Farmer Education**: Accessible disease identification tools
- **Research**: Open-source platform for agricultural AI development

**Made with ❤️ for the agricultural community**
