Smart Community Messaging Application: AI-Based Messaging Bot
The AI-Based Messaging Bot (@AIChatAssistantBot2) is a Telegram bot designed to streamline group communication by automating the management of important messages, FAQs, and reminders. Built with AI-driven natural language processing (NLP) and a lightweight SQLite database, it helps academic, professional, and community groups stay organized and efficient. Deployed on Render’s free tier, this bot addresses common group chat challenges, such as missed announcements, repetitive questions, and forgotten tasks.
Features
The bot offers five key features to enhance group communication:

Important Message Detection:

Automatically identifies critical messages (e.g., meeting or event announcements) using NLP and keywords like “meeting,” “urgent,” or “deadline.”
Labels them with “📢 [Important]” in the Telegram group and stores them in the database for easy retrieval.
Example: Send “Team meeting tomorrow at 7pm” → Bot replies “📢 [Important] Team meeting tomorrow at 7pm.”


Dynamic FAQ Responses:

Answers common questions (e.g., “when is the meeting”) by retrieving the latest relevant message or predefined FAQ from the database.
Updates answers dynamically as new information is posted, reducing repetitive queries.
Example: After “Meeting rescheduled to tomorrow at 10pm,” asking “when is the meeting” returns “🤖 Auto-Answer: Meeting rescheduled to tomorrow at 10pm.”


Time-Aware Logic:

Tracks event times (e.g., meeting schedules) and informs users if an event has passed (e.g., “The meeting has completed”).
Parses time-related phrases like “tomorrow at 7pm” for accurate scheduling.
Example: If a meeting was at 08:00 AM IST, asking “when is the meeting” at 08:47 AM IST returns “🤖 Auto-Answer: The meeting has completed.”


Reminders:

Allows users to set reminders with commands like /setreminder Submit report | 2025-08-02 09:00, sending notifications at the specified time.
Stores reminders in the database for reliability.
Example: Set a reminder → Receive “⏰ Reminder: Submit report” at the scheduled time.


Pending FAQ Management:

Detects unanswered questions (e.g., “Where is the meeting held?”), prompts admins to clarify, and allows answers via /answer_pending.
Admins can view pending questions with /list_pending, building an evolving knowledge base.
Example: “Where is the meeting held?” → “Could you clarify...” → /answer_pending where is the meeting held | Conference Room A → “🤖 Auto-Answer: Conference Room A.”



Setup Instructions
Follow these steps to set up and run the AI-Based Messaging Bot locally or on Render.
Prerequisites

Python 3.12: Ensure Python 3.12 is installed on your system.
Telegram Account: Required to create and manage the bot via @BotFather.
Render Account: For deploying the bot online (free tier).
DB Browser for SQLite: Used to manage group_knowledge.db due to SQLite CLI issues.
Git: For version control and deploying to GitHub.

Local Setup

Clone the Repository:

Download the project from https://github.com/Tejaswani18/SCM2 or clone it:git clone https://github.com/Tejaswani18/SCM2.git
cd SCM2/ai_messaging_bot




Set Up Virtual Environment:

Create and activate a virtual environment:python -m venv env
.\env\Scripts\Activate  # On Windows




Install Dependencies:

Update requirements.txt with the following:python-telegram-bot==22.1
spacy==3.7.2
python-dotenv==1.0.1
python-dateutil==2.8.2
httpx==0.24.1
httpcore==0.17.3
numpy==1.26.4


Install dependencies:pip install -r requirements.txt


Install the spaCy language model:python -m spacy download en_core_web_sm




Configure the Bot Token:

Create a Telegram bot via @BotFather:
Send /newbot, follow prompts, and name it (e.g., @AIChatAssistantBot2).
Copy the token provided.


Create a .env file in D:\Documents\SCM2\ai_messaging_bot:
Add: BOT_TOKEN=your_new_token_here
Save the file.




Run the Bot Locally:

Start the bot:python ai_messaging_bot.py


Add the bot to a Telegram test group and send /start to verify it responds: “Hi! I'm an AI messaging assistant...”


Verify Database:

Open group_knowledge.db in DB Browser for SQLite.
Confirm tables: knowledge, important_messages, reminders.
Pre-populate for demos:
important_messages: Set event_time to “2025-08-02 08:00:00” for a past meeting.
knowledge: Add FAQ “when is the meeting” → “Team meeting tomorrow at 7pm.”
reminders: Add “Submit report” at “2025-08-02 09:00.”



Push to GitHub:

Commit changes to requirements.txt and .env (ensure .env is not tracked in .gitignore for Render):git add requirements.txt
git commit -m "Update dependencies for compatibility"
git push origin main



Demo Setup
To showcase the bot’s features in your pitch video:

Add @AIChatAssistantBot2 to a Telegram test group.
Send these test messages:
Important Message Detection: “Team meeting tomorrow at 7pm” → Expect “📢 [Important] Team meeting tomorrow at 7pm.”
Dynamic FAQ Responses: “when is the meeting” → “🤖 Auto-Answer: Team meeting tomorrow at 7pm.” Then “Meeting rescheduled to tomorrow at 10pm” → “when is the meeting” → “🤖 Auto-Answer: Meeting rescheduled to tomorrow at 10pm.”
Time-Aware Logic: Pre-edit event_time in group_knowledge.db to “2025-08-02 08:00:00,” send “when is the meeting” → “🤖 Auto-Answer: The meeting has completed.”
Reminders: /setreminder Submit report | 2025-08-02 09:00 → “Reminder set...” and pre-record “⏰ Reminder: Submit report.”
Pending FAQ Management: “Where is the meeting held?” → “Could you clarify...” → /answer_pending where is the meeting held | Conference Room A → “Where is the meeting held?” → “🤖 Auto-Answer: Conference Room A.”


Verify database entries in DB Browser for SQLite.

Troubleshooting

Dependency Conflicts:
Ensure requirements.txt matches the specified versions.
Recreate the virtual environment if issues persist:python -m venv env
.\env\Scripts\Activate
pip install -r requirements.txt
python -m spacy download en_core_web_sm




Bot Not Responding:
Verify BOT_TOKEN in .env or Render’s environment variables.
Check Render logs for errors.


Database Issues:
Use DB Browser for SQLite to inspect group_knowledge.db.
Reinitialize tables by running the bot if corrupted.


Demo Timing:
Pre-record the reminder notification for reliability.



Credits
Developed by a team of four for the SCM2 project:

Tejaswani: Project Lead, overseeing development and coordination.
Harini: Demo Expert, responsible for testing and demo setup.
Veena: Features Specialist, focusing on feature design and presentation.
Ravi Teja: Tech Lead, handling technical implementation and deployment.
