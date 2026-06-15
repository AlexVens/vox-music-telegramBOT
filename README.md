🤖 Vox Music Telegram Bot
A stylish and powerful Python-based Telegram bot for searching, downloading, and processing music from open sources. Fully containerized with Docker, ensuring it runs on any server in just a couple of commands without the hassle of long environment setups.

✨ Core Features
🔍 Smart Search: Finds and downloads audio from YouTube using either direct links or keywords.

✂️ Built-in Audio Cutter: Allows users to trim downloaded audio files directly inside Telegram using the FFmpeg utility.

📊 Automated Reports: Logs user requests and saves the complete history into an Excel spreadsheet (history.xlsx).

🔐 Data Security: Interactively prompts for API tokens on the first launch and stores them securely in an isolated tokens.json file.

🛠 Tech Stack
Language: Python 3.10+

API Wrapper: Telebot (pyTelegramBotAPI) / Aiogram (specify your library)

Audio Processing: FFmpeg

Containerization: Docker

🚀 Quick Start Guide
1. Clone the Repository
To get started, clone the project to your server or local machine:
git clone https://github.com/AlexVens/vox-music-telegramBOT.git
cd vox-music-telegramBOT

2. Building the Docker Image
Docker will automatically download the required version of Linux and Python, install FFmpeg, and set up all dependencies from requirements.txt:
docker build -t vox-music-bot .

Here is the English translation for sections 3 and 4:

3. First Launch and Configuration (Interactive Mode)
On the very first launch, the bot will politely ask you to enter your Telegram token from @BotFather directly into the console. Run it in interactive mode:

Bash
docker run -it --name vox-bot-live vox-music-bot
💡 How to exit the console: Once the bot has successfully started and responds to you on Telegram, press Ctrl + P, followed immediately by Ctrl + Q. The bot will continue running in the background, and you will return to your server terminal.

4. Running in the Background (with Persistent Data)
To ensure that your Excel search history and authentication data are not lost when the container or the server restarts, use volume mounting:
docker run -d \
  --name vox-bot-live \
  --restart unless-stopped \
  -v $(pwd)/tokens.json:/app/tokens.json \
  -v $(pwd)/history.xlsx:/app/history.xlsx \
  vox-music-bot

Project Structure
vox2.py — The main source code of the Telegram bot.

Dockerfile — Instructions for building the isolated Docker container.

requirements.txt — A list of all required Python libraries.

.gitignore — Prevents your private tokens and database from accidentally being pushed to GitHub.
