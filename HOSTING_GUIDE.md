# 🚀 AI Slide Deck Generator - Hosting Guide

This guide will help you deploy your AI Slide Deck Generator to various hosting platforms.

## 🌐 Hosting Options

### 1. Heroku (Recommended for Beginners)

**Pros:** Easy deployment, free tier available, automatic scaling
**Cons:** Cold starts on free tier, limited free hours

#### Setup Steps:

1. **Install Heroku CLI**
   ```bash
   # Download from https://devcenter.heroku.com/articles/heroku-cli
   ```

2. **Create required files:**
   
   Create `Procfile` in project root:
   ```
   web: python app.py
   ```
   
   Create `runtime.txt` in project root:
   ```
   python-3.11.0
   ```

3. **Deploy to Heroku:**
   ```bash
   # Login to Heroku
   heroku login
   
   # Create new app
   heroku create your-app-name
   
   # Set environment variables
   heroku config:set GEMINI_API_KEY=your_api_key_here
   
   # Deploy
   git init
   git add .
   git commit -m "Initial commit"
   git push heroku main
   ```

### 2. Railway

**Pros:** Modern platform, generous free tier, easy GitHub integration
**Cons:** Newer platform, smaller community

#### Setup Steps:

1. **Connect GitHub:**
   - Go to [railway.app](https://railway.app)
   - Connect your GitHub account
   - Import your repository

2. **Configure Environment:**
   - Add `GEMINI_API_KEY` in Railway dashboard
   - Railway auto-detects Python and installs dependencies

3. **Deploy:**
   - Railway automatically deploys on git push

### 3. Render

**Pros:** Free tier, automatic deployments, good performance
**Cons:** Limited free tier resources

#### Setup Steps:

1. **Create Web Service:**
   - Go to [render.com](https://render.com)
   - Connect GitHub repository
   - Choose "Web Service"

2. **Configure Build:**
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `python app.py`
   - Add environment variable: `GEMINI_API_KEY`

### 4. PythonAnywhere

**Pros:** Python-focused, easy setup, good for beginners
**Cons:** Limited free tier, slower performance

#### Setup Steps:

1. **Upload Files:**
   - Create account at [pythonanywhere.com](https://pythonanywhere.com)
   - Upload project files via Files tab

2. **Create Web App:**
   - Go to Web tab
   - Create new web app
   - Choose Flask framework
   - Point to your `app.py` file

3. **Install Dependencies:**
   ```bash
   # In PythonAnywhere console
   pip3.10 install --user -r requirements.txt
   ```

### 5. Google Cloud Platform (Advanced)

**Pros:** Scalable, integrated with Google services, professional grade
**Cons:** More complex setup, costs can add up

#### Setup Steps:

1. **Create App Engine app:**
   
   Create `app.yaml`:
   ```yaml
   runtime: python311
   
   env_variables:
     GEMINI_API_KEY: "your_api_key_here"
   
   automatic_scaling:
     min_instances: 0
     max_instances: 10
   ```

2. **Deploy:**
   ```bash
   # Install Google Cloud SDK
   gcloud app deploy
   ```

### 6. AWS Elastic Beanstalk (Advanced)

**Pros:** AWS ecosystem, highly scalable, professional features
**Cons:** Complex setup, AWS knowledge required

#### Setup Steps:

1. **Create application.py:**
   ```python
   from app import app as application
   
   if __name__ == "__main__":
       application.run()
   ```

2. **Create .ebextensions/python.config:**
   ```yaml
   option_settings:
     aws:elasticbeanstalk:application:environment:
       GEMINI_API_KEY: your_api_key_here
   ```

3. **Deploy with EB CLI:**
   ```bash
   eb init
   eb create
   eb deploy
   ```

## 🔧 Pre-Deployment Checklist

### 1. Environment Variables
- [ ] Set `GEMINI_API_KEY` in hosting platform
- [ ] Update `SECRET_KEY` for production
- [ ] Configure any other sensitive data

### 2. Code Modifications for Production

**Update app.py for production:**
```python
# Change debug mode
if __name__ == '__main__':
    port = int(os.environ.get('PORT', 5000))
    app.run(debug=False, host='0.0.0.0', port=port)
```

**Add error handling:**
```python
@app.errorhandler(500)
def internal_error(error):
    return render_template('error.html', error="Internal server error"), 500

@app.errorhandler(404)
def not_found(error):
    return render_template('error.html', error="Page not found"), 404
```

### 3. Security Considerations
- [ ] Use environment variables for API keys
- [ ] Enable HTTPS (most platforms do this automatically)
- [ ] Set secure session cookies
- [ ] Implement rate limiting if needed
- [ ] Validate file uploads

### 4. Performance Optimization
- [ ] Add caching for static files
- [ ] Optimize image sizes
- [ ] Implement request timeout handling
- [ ] Add logging for monitoring

## 🔐 Environment Variables Setup

### Required Variables:
```bash
GEMINI_API_KEY=your_google_gemini_api_key
SECRET_KEY=your_flask_secret_key_for_production
FLASK_ENV=production
```

### Optional Variables:
```bash
MAX_CONTENT_LENGTH=16777216  # 16MB file upload limit
UPLOAD_FOLDER=static
ALLOWED_EXTENSIONS=txt,pdf,doc,docx
```

## 📊 Monitoring and Maintenance

### 1. Logging
Add comprehensive logging:
```python
import logging
from logging.handlers import RotatingFileHandler

if not app.debug:
    file_handler = RotatingFileHandler('logs/app.log', maxBytes=10240, backupCount=10)
    file_handler.setFormatter(logging.Formatter(
        '%(asctime)s %(levelname)s: %(message)s [in %(pathname)s:%(lineno)d]'
    ))
    file_handler.setLevel(logging.INFO)
    app.logger.addHandler(file_handler)
    app.logger.setLevel(logging.INFO)
```

### 2. Health Checks
Add a health check endpoint:
```python
@app.route('/health')
def health_check():
    return {'status': 'healthy', 'timestamp': datetime.now().isoformat()}
```

### 3. Analytics
Consider adding:
- Google Analytics for usage tracking
- Error tracking (Sentry)
- Performance monitoring
- User feedback collection

## 🚨 Troubleshooting Common Issues

### 1. Application Won't Start
- Check Python version compatibility
- Verify all dependencies are installed
- Check environment variables are set
- Review application logs

### 2. API Key Issues
- Ensure GEMINI_API_KEY is correctly set
- Verify API key has proper permissions
- Check API quota limits

### 3. File Upload Problems
- Check file size limits
- Verify upload directory permissions
- Ensure static folder exists

### 4. Performance Issues
- Monitor memory usage
- Check API response times
- Implement caching if needed
- Consider upgrading hosting plan

## 💰 Cost Considerations

### Free Tier Limitations:
- **Heroku:** 550-1000 free hours/month
- **Railway:** $5 credit monthly
- **Render:** 750 hours/month
- **PythonAnywhere:** Limited CPU seconds

### Paid Plans Start At:
- **Heroku:** $7/month (Hobby)
- **Railway:** $5/month (Pro)
- **Render:** $7/month (Starter)
- **PythonAnywhere:** $5/month (Hacker)

## 🎯 Recommended Deployment Strategy

1. **Start with Railway or Render** for ease of use
2. **Use Heroku** if you need more features
3. **Move to GCP/AWS** when you need enterprise features
4. **Always test in staging** before production deployment
5. **Monitor usage and costs** regularly

## 📞 Support Resources

- **Heroku:** [devcenter.heroku.com](https://devcenter.heroku.com)
- **Railway:** [docs.railway.app](https://docs.railway.app)
- **Render:** [render.com/docs](https://render.com/docs)
- **PythonAnywhere:** [help.pythonanywhere.com](https://help.pythonanywhere.com)
- **Google Cloud:** [cloud.google.com/docs](https://cloud.google.com/docs)
- **AWS:** [docs.aws.amazon.com](https://docs.aws.amazon.com)

---

**Need help?** Create an issue in the repository or contact the development team.

**Happy Deploying! 🚀**