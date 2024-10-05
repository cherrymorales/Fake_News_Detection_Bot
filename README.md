# Fake News Detection Bot

The AI-Powered Fake News Detection Bot is an interactive tool designed to verify the authenticity of news articles using advanced AI models. This system leverages Google Gemini's API for natural language processing to determine if the submitted news content is fake or real.

## Key Features
- **Text Analysis**: The system analyzes the textual content of news articles for patterns indicating fake news.
- **External Verification**: Cross-references facts with credible sources using the Gemini API.
- **Confidence Score**: Provides a confidence score and highlights key factors influencing the decision.

## Prerequisites
To run the Fake News Detection System, you will need:
- **Python 3.8+**
- A **Telegram bot token** from BotFather (if using the Telegram interface)
- A **Google Gemini API key**

## Setup Instructions

### 1. Clone the Repository
Begin by cloning the repository to your local machine:
```bash
git clone https://github.com/your-username/fake_news_detection_bot.git
cd fake-news-detection-bot
```

### 2. Install Required Libraries
Install the required dependencies by running the following command:
```bash
pip install -r requirements.txt
```

Key libraries include:
- `python-telegram-bot`
- `google.generativeai`
- `newspaper3k`
- `pandas`

### 3. Set Environment Variables
You need to set the following environment variables to ensure secure operation:
- **GEMINI_API_KEY**: Your API key for the Google Gemini AI
- **TELEGRAM_FAKE_NEWS_BOT_TOKEN**: Your Telegram bot token

On **Linux/Mac**:
```bash
export GEMINI_API_KEY="your-google-gemini-api-key"
export TELEGRAM_FAKE_NEWS_BOT_TOKEN="your-telegram-bot-token"
```

On **Windows**:
```bash
set GEMINI_API_KEY="your-google-gemini-api-key"
set TELEGRAM_FAKE_NEWS_BOT_TOKEN="your-telegram-bot-token"
```

### 4. Run the Bot
After setting up the environment, you can run the bot using:
```bash
python app.py
```
The bot will now be ready to interact with users through Telegram or other interfaces.

## Usage

1. **Start the Bot**: Open Telegram, search for your bot's username, and start a conversation.
2. **Authenticate News**: You can send a news article's text or URL to the bot for verification.
3. **Receive Analysis**: The bot will analyze the news content using AI and respond with a confidence score on whether the news is likely to be fake or real.

### Step-by-Step Commands:
1. **Scan the QR Code** (if integrated with a web interface) or start interacting directly via Telegram.
2. **Submit the Article**: Paste the news article or submit the URL.
3. **Get Feedback**: Receive the result, a confidence score, and the key factors influencing the decision.

## Example Code

Here is a sample portion of the system's code, showing how the Google Gemini API is used for content verification:

```python
import generativeai as genai

# Set your API key
API_KEY = os.environ["GEMINI_API_KEY"]
genai.configure(api_key=API_KEY)

# Configure the generation model
generation_config = {
  "temperature": 1,
  "top_p": 0.95,
  "top_k": 64,
  "max_output_tokens": 8192,
  "response_mime_type": "text/plain",
}

# Function to analyze news content
def analyze_news(prompt):
    response = genai.generate(prompt=prompt, **generation_config)
    return response['text']
```

## Security Considerations
- **Environment Variables**: Sensitive API keys are stored securely in environment variables.
- **Safety Measures**: The system employs Google Gemini's safety settings to ensure generated content is appropriate and free of harmful material.

## Future Enhancements
- Expanding the scope to include more types of content verification, such as video and multimedia.
- Introducing multi-language support for a global user base.
- Integrating with additional external verification sources to further enhance fact-checking accuracy.

## Contribution
We welcome community contributions! Feel free to fork this repository and submit pull requests with improvements, additional features, or bug fixes.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
