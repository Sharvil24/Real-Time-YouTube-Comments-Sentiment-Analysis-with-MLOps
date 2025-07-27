# Real-Time YouTube Comments Sentiment Analysis with MLOps

A comprehensive MLOps project that analyzes YouTube video comments to determine sentiment (positive, negative, or neutral) using machine learning.

## Architecture Overview

![alt text](<YT Sentiments Architecture diagram.jpg>)

The system consists of several key components:

1. **Data Sources**: YouTube API v3 for fetching comments
2. **Data Processing & ML**: Preprocessing, feature engineering, and model training
3. **MLOps & Monitoring**: MLflow for experiment tracking and model versioning
4. **Application Layer**: Flask REST API and Chrome Extension
5. **AWS Infrastructure**: EC2, ECR, and S3 for deployment and storage
6. **CI/CD Pipeline**: GitHub Actions for automated deployment

## Features

- **Real-time Sentiment Analysis**: Analyze YouTube video comments instantly
- **Chrome Extension**: User-friendly interface with visual analytics
- **MLOps Pipeline**: Complete experiment tracking with MLflow
- **Automated Deployment**: CI/CD using GitHub Actions and AWS
- **Containerized Application**: Docker-based deployment for scalability
- **REST API**: Flask-based API for sentiment prediction

## Getting Started

### Prerequisites

- Python 3.8+
- Docker
- AWS Account
- YouTube Data API v3 Key
- Chrome Browser

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/Sharvil24/Youtube-Sentiment-Insights.git
cd Youtube-Sentiment-Insights
```

2. **Set up Python environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. **Configure YouTube API**
```bash
# Add your YouTube Data API key to config file
export YOUTUBE_API_KEY="your-api-key-here"
```

4. **Install Chrome Extension**
- Open Chrome and navigate to `chrome://extensions/`
- Enable "Developer mode"
- Click "Load unpacked" and select the `chrome_extension` folder

## API Testing

The Flask API can be tested using Postman or curl:

![alt text](<postman ss.png>)

**Endpoint**: `POST http://localhost:5001/predict`

**Request Body**:
```json
{
  "comments": [
    "This video is awesome! I loved a lot",
    "Very bad explanation. poor video",
    "your video is good nice presentation",
    "your video is shit",
    "your video is ok"
  ]
}
```

**Response**:
```json
[
  {"comment": "This video is awesome! I loved a lot", "sentiment": 1},
  {"comment": "Very bad explanation. poor video", "sentiment": -1},
  {"comment": "your video is good nice presentation", "sentiment": 1},
  {"comment": "your video is shit", "sentiment": -1},
  {"comment": "your video is ok", "sentiment": 0}
]
```

## Chrome Extension Features

### Extension Interface

![alt text](<Chrome Extension.png>)

The Chrome extension provides:
- One-click sentiment analysis for any YouTube video
- Real-time comment fetching using YouTube Data API v3

### Analytics Dashboard

![alt text](<Analytics Dashboard.png>)

**Key Metrics**:
- Total Comments: 133
- Unique Commenters: 119
- Average Comment Length: 13.51 words
- Average Sentiment Score: 6.50/10

### Sentiment Distribution

![alt text](<Sentiment Distribution.png>)

Visual representation showing:
- **Positive**: 36.1% (Blue)
- **Neutral**: 57.9% (Gray)
- **Negative**: 6.0% (Red)

### Sentiment Trend Analysis

Track sentiment changes over time with monthly analysis showing positive, negative, and neutral comment trends.

### Comment Word Cloud

![alt text](<Comment Word Cloud.png>)

Visual representation of most frequently used words in comments. The word cloud highlights:
- **"thank"** - Most prominent word showing appreciation
- **"course"**, **"video"** - Core content references
- **"day"**, **"started"** - Temporal references
- Common technical terms and learning-related vocabulary

### Top Comments Analysis

![alt text](<Top Comments.png>)

View the top 25 comments with their sentiment scores:
- Sentiment: 1 (Positive)
- Sentiment: 0 (Neutral)
- Sentiment: -1 (Negative)

## Technology Stack

### Machine Learning
- **Jupyter Notebooks**: 7 notebooks for model development
- **MLflow**: Experiment tracking and model registry
- **Libraries**: scikit-learn, pandas, numpy, nltk

### Backend
- **Flask**: REST API framework
- **Docker**: Containerization
- **FastAPI**: High-performance API (optional)
- **Streamlit**: Web UI (optional)

### Infrastructure
- **AWS EC2**: Application hosting
- **AWS ECR**: Docker image registry
- **AWS S3**: Model and data storage
- **GitHub Actions**: CI/CD automation
- **GitHub Runner**: Self-hosted runner for deployments

### Frontend
- **Chrome Extension**: JavaScript, HTML, CSS
- **Charts**: Chart.js for visualizations
- **API Integration**: YouTube Data API v3

## MLOps Workflow

1. **Development**: Models developed in Jupyter notebooks
2. **Experiment Tracking**: MLflow tracks all experiments
3. **Model Registry**: Best models stored in MLflow
4. **Containerization**: Docker images built automatically
5. **CI/CD**: GitHub Actions triggered on push
6. **Deployment**: Automated deployment to AWS EC2
7. **Monitoring**: Performance metrics tracked

## Deployment

### Local Development

```bash
# Run Flask API
python flask_api/app.py

# API will be available at http://localhost:5001
```

### Docker Deployment

```bash
# Build Docker image
docker build -t youtube-sentiment-analyzer .

# Run container
docker run -p 5001:5001 youtube-sentiment-analyzer
```

### AWS Deployment

The project uses GitHub Actions for automated deployment:
1. Push code to GitHub
2. GitHub Actions builds Docker image
3. Image pushed to AWS ECR
4. EC2 instance pulls and runs latest image

## Model Performance

- **Accuracy**: ~85% on test dataset
- **Model Type**: Sentiment Classification (Logistic Regression/BERT)
- **Classes**: Negative (-1), Neutral (0), Positive (1)
- **Training Data**: YouTube comments dataset

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Authors

- **Sharvil** - *Initial work* - [Sharvil24](https://github.com/Sharvil24)

## Acknowledgments

- YouTube Data API v3 for providing comment data access
- MLflow for excellent experiment tracking capabilities
- AWS for cloud infrastructure
- The open-source community for various libraries used

## Contact

For any queries or suggestions, please reach out:
- Email: sharvilwadekar@gmail.com
- GitHub: [@Sharvil24](https://github.com/Sharvil24)

---

**Note**: Make sure to add your YouTube Data API key and AWS credentials before running the project.