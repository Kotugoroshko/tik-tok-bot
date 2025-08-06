TikTok Bot – Selenium Firefox Automation
Overview
This Python script automates interactions with TikTok using Selenium WebDriver and Firefox (GeckoDriver).
It is capable of:

Logging into TikTok using stored cookies (or creating them if they don’t exist).

Liking TikTok posts by URL.

Saving cookies locally for persistent sessions.

The bot supports logging in via Google as a third-party login option.

Features
Cookie Management

Checks if login cookies exist for a given account.

Saves cookies after a successful login to avoid re-entering credentials.

Google Login Automation

Automates Google login inside TikTok’s embedded iframe.

Like Automation

Opens a specific TikTok post and likes it if not already liked.

Session Persistence

Uses saved cookies to keep the session active between runs.

File Structure
TikTokBot class — Main automation logic.

get_cookies() — Logs in and stores cookies.

set_like(post_url) — Likes a post at the given TikTok URL.

Helper methods —

xpath_exists() → Checks if an element exists by XPath.

class_exists() → Checks if an element exists by CSS class.

closes_driver() → Closes the browser and ends the WebDriver session.

Requirements"
Python 3.8+

Firefox Browser.

Python packages:

bash:

pip install selenium
Setup
Install Firefox and GeckoDriver.

Place your TikTok login credentials in tiktok/config.py:

python:

mail = "your_email"
password = "your_password"
Adjust the executable_path in TikTokBot.__init__() to your GeckoDriver location.

Create a folder where cookies will be stored (/absolute_path/ in code).

Usage
1. Save Login Cookies
python

from bot import TikTokBot
from tiktok.config import mail, password

bot = TikTokBot(mail, password)
bot.get_cookies()
This will:

Open TikTok.

Click Login → Login with Google.

Enter credentials.

Save cookies to /absolute_path/{mail}_cookies.

2. Like a TikTok Post
python
from bot import TikTokBot
from tiktok.config import mail, password

bot = TikTokBot(mail, password)
bot.set_like(post_url="https://www.tiktok.com/@username/video/1234567890")
This will:

Load saved cookies.

Open the given post.

Like it if not already liked.
