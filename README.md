# 🎯 AI Slide Deck Generator

> **Transform your ideas into stunning presentations with the power of AI**

A cutting-edge web application that leverages Google's Gemini AI to automatically generate professional PowerPoint presentations from simple text input. Features a modern cyberpunk-themed interface with advanced customization options.

![AI Slide Deck Generator](https://img.shields.io/badge/AI-Powered-00ffff?style=for-the-badge&logo=artificial-intelligence)
![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python)
![Flask](https://img.shields.io/badge/Flask-2.3.3-green?style=for-the-badge&logo=flask)
![Gemini AI](https://img.shields.io/badge/Gemini-AI-ff0080?style=for-the-badge&logo=google)

## ✨ Features

### 🤖 AI-Powered Content Generation
- **Smart Content Creation**: Automatically generates slide content, titles, and bullet points
- **Context-Aware**: Understands your topic and creates relevant, structured presentations
- **Multiple Styles**: Choose from Professional, Creative, Academic, or Business presentation styles
- **Intelligent Structuring**: Creates logical flow and coherent narrative

### 🎨 Advanced Customization
- **5 Presentation Styles**: Professional, Creative, Academic, Business, and Minimalist
- **Dynamic Slide Count**: Generate 3-20 slides based on your content needs
- **Chart Integration**: Automatically includes relevant charts and data visualizations
- **Speaker Notes**: Optional detailed speaker notes for each slide
- **Color Themes**: Each style has carefully crafted color schemes

### 🚀 Modern Interface
- **Cyberpunk Theme**: Futuristic dark interface with neon accents
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile
- **Real-time Feedback**: Loading animations and progress indicators
- **Intuitive Controls**: Easy-to-use form with smart defaults
- **Animated Background**: Dynamic particle effects and circuit patterns

### 📊 Technical Features
- **File Upload Support**: Process existing documents (TXT, PDF, DOC, DOCX)
- **Batch Processing**: Handle multiple presentations efficiently
- **Error Handling**: Comprehensive error management and user feedback
- **Health Monitoring**: Built-in health check endpoints
- **Production Ready**: Configured for deployment on major platforms

## 🛠️ Technology Stack

- **Backend**: Python 3.11, Flask 2.3.3
- **AI Engine**: Google Gemini 1.5 Flash
- **Presentation**: python-pptx for PowerPoint generation
- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Styling**: Custom CSS with cyberpunk theme
- **Deployment**: Ready for Heroku, Railway, Render, and more

## 🚀 Quick Start

### Prerequisites

- Python 3.7 or higher
- Google Gemini API key (free tier available)

### Installation

1. **Clone or download this project**
   ```bash
   cd "AI Slide Deck"
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure API Key**
   - Open `app.py`
   - Replace `'AIzaSyByOveS5Ic80U6T0fY56kdkJJcp_lsTawQ'` with your actual Gemini API key
   - Or set it as an environment variable:
     ```bash
     set GEMINI_API_KEY=your_api_key_here
     ```

4. **Run the application**
   ```bash
   python app.py
   ```

5. **Open your browser**
   - Navigate to `http://localhost:5000`
   - Start generating presentations!

## 🎮 How to Use

1. **Input Your Content**
   - Paste any text content (articles, reports, notes, etc.)
   - The more detailed your content, the better the AI can structure it

2. **Generate Presentation**
   - Click "Generate Presentation"
   - Wait for AI processing (usually 10-30 seconds)

3. **Download Your Slides**
   - Download the generated PowerPoint file
   - Open in PowerPoint, Google Slides, or any compatible software
   - Customize as needed

## 📁 Project Structure

```
AI Slide Deck/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── README.md             # This file
├── templates/
│   ├── index.html        # Main input page
│   └── download.html     # Download success page
└── static/               # Generated presentations (auto-created)
```

## 🔧 Configuration

### API Key Setup

You can configure your Gemini API key in several ways:

1. **Direct replacement in app.py** (easiest for testing)
2. **Environment variable** (recommended for production)
3. **Config file** (for advanced users)

### Customization Options

- **Slide layouts**: Modify the PowerPoint generation code in `app.py`
- **UI styling**: Edit the CSS in the HTML templates
- **AI prompts**: Adjust the Gemini prompts for different output styles

## 🛠️ Technical Details

- **Backend**: Flask (Python)
- **AI Model**: Google Gemini Pro
- **Presentation Library**: python-pptx
- **Frontend**: HTML5, CSS3, JavaScript

## 📝 Example Use Cases

- **Business Reports**: Convert quarterly reports into executive presentations
- **Research Papers**: Transform academic content into conference slides
- **Meeting Notes**: Turn meeting minutes into action item presentations
- **Educational Content**: Create lecture slides from course materials
- **Project Updates**: Generate status presentations from project documentation

## 🔒 Security Notes

- Keep your API key secure and never commit it to version control
- The application runs locally by default for privacy
- Generated files are stored temporarily and can be cleaned up regularly

## 🐛 Troubleshooting

### Common Issues

1. **"Invalid API key" error**
   - Verify your Gemini API key is correct
   - Check if the API key has proper permissions

2. **"Module not found" error**
   - Run `pip install -r requirements.txt`
   - Ensure you're using the correct Python environment

3. **"Port already in use" error**
   - Change the port in `app.py`: `app.run(port=5001)`
   - Or stop other applications using port 5000

4. **Slow generation**
   - Large text inputs take longer to process
   - Check your internet connection
   - Gemini API rate limits may apply

## 📄 License

This project is open source and available under the MIT License.

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

---

**Happy Presenting! 🎉**