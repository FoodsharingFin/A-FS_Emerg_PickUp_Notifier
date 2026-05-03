# 🍲 Food Sharing Emergency Pickup Notifier

A Streamlit-based web application designed to streamline food-sharing by notifying **Foodsavers** about available leftovers in real-time. This app collects pickup details through a user-friendly, multi-step form and broadcasts them to a designated Telegram group via a custom bot.

## 🚀 Features

*   **Multi-Step Workflow:** A guided 4-page interface to ensure high-quality data collection.
*   **Smart Time Filtering:** Automatically hides past time slots based on the local time in **Helsinki (EEST)**.
*   **Dynamic Date Selection:** Users can report leftovers for "Today" or schedule up to 14 days in advance.
*   **Telegram Integration:** Directly connects to the Telegram Bot API to notify volunteers instantly.
*   **Privacy-Focused:** Explicitly informs users about data retention (15-minute number deletion policy).
*   **Mobile-Optimized UI:** Custom CSS styling for a clean, modern look on all devices.

---

## 🛠️ Tech Stack

*   **Frontend:** [Streamlit](https://streamlit.io/)
*   **Language:** Python 3.14+
*   **Timezone Handling:** `pytz`
*   **API Communication:** `requests`

---

## 📋 Prerequisites

Before running the app, you will need:
1.  **Python 3.10+** installed.
2.  A **Telegram Bot Token** (created via [@BotFather](https://t.me/botfather)).
3.  A **Group Chat ID** where the bot has admin/message-sending permissions.

---

## 📥 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/a-fs_emerg_pickup_notifier.git
cd a-fs_emerg_pickup_notifier
```

### 2. Configure Dependencies
Ensure your `requirements.txt` file contains only the third-party libraries (Standard libraries like `json` or `os` should **not** be included):
```text
streamlit
pandas
pytz
requests
```

### 3. Local Secrets Management
Create a folder named `.streamlit` in your root directory and add a `secrets.toml` file to store your credentials:
```toml
# .streamlit/secrets.toml
TELEGRAM_BOT_TOKEN = "your_bot_token_here"
GROUP_CHAT_ID = "your_group_chat_id_here"
```

---

## 🖥️ Usage

To run the application locally, execute:
```bash
streamlit run streamlit_app.py
```
The app will be available in your browser at `http://localhost:8501`.

---

## 📂 Project Structure

```text
├── .streamlit/
│   └── secrets.toml          # Local secrets (ignored by git)
├── streamlit_app.py          # Main UI and logic
├── config.py                 # TelegramPickupBot class logic
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
```

---

## 🌍 Timezone Configuration

The app is hardcoded to the `Europe/Helsinki` timezone to ensure time-slot filtering remains accurate regardless of where the server is hosted (Streamlit Cloud typically uses UTC).

```python
# logic found in streamlit_app.py
local_tz = pytz.timezone('Europe/Helsinki')
current_hour = datetime.datetime.now(local_tz).hour
```

---

## 🛡️ Security Note
**Never** commit your `secrets.toml` file to GitHub. It is included in the `.gitignore` by default in standard Streamlit templates. When deploying to Streamlit Cloud, enter these secrets in the **App Settings > Secrets** dashboard.

---

## 🤝 Contributing
Contributions are welcome! If you find a bug or have a feature request, please open an issue or submit a pull request.
