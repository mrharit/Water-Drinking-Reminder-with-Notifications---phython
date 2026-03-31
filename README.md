# 💧 Water Drinking Reminder with Notifications  
### Mini Project 6 (Python + plyer)

---

## 📌 Project Overview

This is a lightweight Python script that sends **system notifications at regular intervals** to remind you to drink water. It runs from the terminal and uses the cross‑platform **`plyer`** library to trigger native notifications (Windows, macOS, Linux).

---

## ✨ Features

- Customizable reminder interval (in minutes)
- Native OS notifications (Notification Center / Action Center / libnotify)
- Minimal code and no external windows
- Runs continuously until you stop it (Ctrl + C)

---

## 🧰 Tech Stack

- **Python 3.8+**
- **plyer** (for notifications)
- Standard library: `time`

---

## ✅ Requirements & Installation

1. **Install Python** (3.8 or newer recommended).

2. **Install dependencies:**
   ```bash
   pip install plyer


3.  **(Linux only) Ensure notification backend is present**  
    On many distros, `libnotify`/`notify-send` is needed:
    ```bash
    # Debian/Ubuntu
    sudo apt-get update && sudo apt-get install -y libnotify-bin
    # Fedora
    sudo dnf install -y libnotify
    ```

> macOS and Windows typically work out of the box with `plyer`.

***

## ▶️ How to Run

1.  Save the script as `water_reminder.py`.
2.  From the same folder, run:
    ```bash
    python water_reminder.py
    ```
3.  By default (as in the sample code), reminders appear **every 30 minutes**.  
    Change the interval by editing the final line, e.g.:
    ```python
    water_reminder(20)  # every 20 minutes
    ```

***

## 🧠 How It Works

*   Converts the chosen **minutes → seconds**
*   Enters an infinite loop:
    *   Sleeps for the interval
    *   Sends a native system notification with:
        *   **Title:** “Drink Water”
        *   **Message:** “Time to drink water and stay hydrated.”
        *   **Timeout:** 10 seconds (where supported)

> Stop the script anytime with **Ctrl + C** in the terminal.

***

## 🧪 Example Console Output

    Water Drinking Reminder Started
    You will get a notification every 30 minutes

(You’ll then receive a notification every 30 minutes.)

***

## 🛠️ Code (for quick reference)

`python
import time
from plyer import notification

def water_reminder(interval_minutes):
    interval_seconds = interval_minutes * 60

    print("Water Drinking Reminder Started")
    print(f"You will get a notification every {interval_minutes} minutes\n")

    while True:
        time.sleep(interval_seconds)
        notification.notify(
            title="Drink Water",
            message="Time to drink water and stay hydrated.",
            timeout=10
        )

water_reminder(30)
``

***

## 🧩 Customization Ideas

*   **Immediate first reminder:** send a notification before the first `sleep()`.
*   **Custom title/message:** pass them as function parameters.
*   **Sound/alert:** pair with a short sound using platform tools or `playsound`.
*   **Work hours only:** run between specific times.
*   **Tray app / GUI:** wrap with Tkinter or PySimpleGUI and a Start/Stop button.
*   **Persist settings:** read interval from a config file or CLI arg (e.g., `python water_reminder.py --minutes 25`).

***

## 🔁 Run on Startup (Optional)

*   **Windows:** Task Scheduler → *Create Basic Task* → trigger *At log on* → action `python path\to\water_reminder.py`
*   **macOS:** Use **launchd** (create a LaunchAgent) or Automator app to run the script at login.
*   **Linux:** Add a crontab entry:
    ```bash
    crontab -e
    # Add line (adjust paths):
    @reboot /usr/bin/python3 /home/you/water_reminder.py
    ``

***

## 🧯 Troubleshooting

*   **No notifications appear (Linux):** ensure `libnotify-bin`/`notify-send` exists and a notification daemon is running.
*   **Terminal closes → script stops:** run in a persistent terminal (tmux/screen) or schedule at login.
*   **Notifications stack too often:** increase interval or reduce work hours.

***

## ⚠️ Health Note

This tool is for **general wellness reminders** and is **not medical advice**. Adjust intervals to your personal needs or professional guidance.

***

## 👤 Author

**Aakash Harit**  
Python Mini Projects | Productivity Utilities

***

## 📄 License

This project is intended for **educational and personal use**. Feel free to fork and adapt.


