# User Reference Guide

The User Reference Guide for the Fake News Detection Chatbot provides detailed instructions, information, and resources to help users effectively utilize this advanced tool. It serves as a reference resource for users to consult whenever they have questions or need guidance on specific features or functions of the system.

## Key Components of the User Reference Guide

### Step 1: Scan the QR Code
- Open your phone’s camera or a QR code scanning app.

### Step 2: Install Telegram
- **Download Telegram:**
  - If you do not have Telegram installed, download it from the App Store (iOS) or Google Play Store (Android).
- **Follow the Installation Instructions:**
  - Set up your Telegram account.

### Step 3: Start the Chat
- After scanning the QR code, you will be redirected to the chatbot in Telegram.
- Click the **'Start'** button or type `/start` to interact with the chatbot.

### Step 4: Check the Authenticity of a News Article
- You can either:
  - Copy and paste the text of the news article into the chat.
  - Send the URL of the news article.

### Step 5: Receiving Analysis
- After submitting the text or URL, the chatbot will process the information using advanced AI models (Gemini 1.5 Pro).
- The chatbot will return a response indicating whether the news is likely to be fake or real.
- It will also provide a confidence score and highlight key features influencing the decision.

## Additional Features and Functionalities

### News Verification
- **Text Analysis:** The chatbot analyzes the textual content to identify patterns indicative of fake news.
- **External Verification:** The chatbot cross-references information using the Gemini API to validate facts against credible sources.

### User Commands
- `/start`: Initializes the chatbot interaction.

### Privacy and Security
- The chatbot handles user data responsibly, ensuring compliance with data protection regulations.

### Continuous Improvement
- The chatbot undergoes regular updates to improve its accuracy and adapt to new misinformation tactics.

### Feedback
- Users are encouraged to provide feedback on the chatbot’s performance to help enhance its functionality.

---

# Using Gemini 1.5 Pro API

Gemini 1.5 Pro offers powerful API capabilities for various natural language processing tasks. This guide walks you through the steps to obtain an API token from aigooglestudio.com and use it with the `generativeai` package.

## Steps to Obtain and Use the API Token

### 1. Sign Up for a Gemini Account on AI Google Studio
- **Visit AI Google Studio Website:** Open your web browser and go to [aigooglestudio.com](https://aigooglestudio.com).
- **Create an Account:**
  - Click on the **Sign-Up** button, usually located at the top right corner of the homepage.
  - Fill in the required details, such as your name, email address, and a secure password.
  - Verify your email address by clicking on the link sent to your email.

### 2. Obtain an API Token
- **Log In to Your Account:**
  - Go back to [aigooglestudio.com](https://aigooglestudio.com) and click on the **Log In** button.
  - Enter your email and password to access your account.
- **Navigate to API Tokens:**
  - Click on the **Get API Key** from the left panel to manage your tokens.
- **Create a New API Token:**
  - Click on the **Create API Key** button.
  - Create a new project if you don’t already have one or add API keys to an existing project.
  - Click **Generate** to create a new API token.
  - **Important:** Copy and save this token securely. You will need it to interact with the Gemini API.

### 3. Install the `generativeai` Package
To interact with the Gemini 1.5 Pro API, you need the `generativeai` package. Install it using pip:

```bash
pip install generativeai
```

---
# Creating a Bot in Telegram and Obtaining the Token

Telegram bots are third-party applications that run inside Telegram. Users can interact with bots by sending messages, commands, and inline requests. This guide will walk you through the steps required to create a bot in Telegram and obtain the token needed for API access.

## Steps to Create a Telegram Bot

### 1. Install Telegram
- **Download Telegram:**
  - If you have not already, download the Telegram app from the [official website](https://telegram.org/) or your device’s app store.
  - Install the app on your device.

- **Sign Up / Log In:**
  - Open the Telegram app.
  - Sign up for a new account or log in if you already have an account.

### 2. Create a New Bot
- **Open a Chat with BotFather:**
  - In the Telegram app, search for “BotFather” using the search bar. BotFather is the official bot that helps you create and manage Telegram bots.
  - Start a chat with BotFather.

- **Create a New Bot:**
  - Send the command `/newbot` to BotFather.
  - BotFather will ask for a name for your bot. Choose a name that you like (this name can be anything).
  - BotFather will then ask for a username for your bot. The username must end in `bot` (e.g., `mynewbot` or `my_new_bot`). This username must be unique.

- **Get the Bot Token:**
  - After you provide a unique username, BotFather will create the bot and provide you with an API token.
  - **Important:** Copy and save this token securely. You will need it to interact with the Telegram Bot API.

### 3. Customize Your Bot (Optional)
- **Set Bot Profile Picture:**
  - Send the command `/setuserpic` to BotFather.
  - Select your bot from the list and then upload an image to set as the bot’s profile picture.

- **Set Bot Description:**
  - Send the command `/setdescription` to BotFather.
  - Select your bot and then provide a description for your bot. This description will appear in the bot’s profile.

- **Set Bot About Info:**
  - Send the command `/setabouttext` to BotFather.
  - Select your bot and then provide a short bio for your bot. This text will appear in the bot’s profile and will be visible in the chat.

- **Set Bot Commands:**
  - Send the command `/setcommands` to BotFather.
  - Select your bot and then provide a list of commands that your bot can respond to. This helps users understand what commands they can use.

### 4. Use the Bot Token in Your Application
- **Install Required Libraries:**
  - To interact with the Telegram Bot API, you can use the `python-telegram-bot` library.
  - Install the library using pip:

    ```bash
    pip install python-telegram-bot
    ```

- **Create a Simple Bot Script:**
  - Use the following Python script to create a simple bot that responds to messages.

    ```python
    from telegram import Update
    from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, filters, CallbackContext

    # Define your bot token
    BOT_TOKEN = 'YOUR_TELEGRAM_BOT_TOKEN'

    # Function to handle the /start command
    async def start(update: Update, context: CallbackContext) -> None:
        await update.message.reply_text('Hi! I am your new bot.')

    # Function to handle text messages
    async def echo(update: Update, context: CallbackContext) -> None:
        await update.message.reply_text(update.message.text)

    def main():
        # Create the application and pass it your bot’s token
        application = ApplicationBuilder().token(BOT_TOKEN).build()

        # Add handlers for commands and messages
        application.add_handler(CommandHandler("start", start))
        application.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, echo))

        # Run the bot
        application.run_polling()

    if __name__ == '__main__':
        main()
    ```

### Running Your Bot
1. Save the script to a file, e.g., `bot.py`.
2. Run the script using Python:

    ```bash
    python bot.py
    ```

By following these steps, you can create a Telegram bot, obtain the necessary token, and set up a basic bot script to respond to messages. This bot can be further customized and extended based on your requirements. For more advanced features and configurations, refer to the [Telegram Bot API documentation](https://core.telegram.org/bots/api).
