# Postfix Gmail SMTP Automation Script

A fully automated Bash script to configure **Postfix** to send emails via **Gmail SMTP** on **Debian-based systems**. The script guides users through Gmail app password setup, validates input, manages packages, updates configs, and securely stores credentials—all with minimal interaction.

### Features

- Detects Debian-based OS
- Verifies root privileges
- Guides through Gmail 2FA & App Password setup
- Validates Gmail address and password format
- Removes previous Postfix/mailutils configurations
- Auto-answers Postfix debconf prompts (non-interactive setup)
- Installs necessary packages
- Securely stores and hashes Gmail credentials
- Configures `/etc/postfix/main.cf` automatically
- Restarts Postfix service
- Offers test email and syntax guide from terminal

---
### Requirements
- Debian/Ubuntu-based system
- Gmail account with 2-Step Verification enabled
- App password generated for Postfix
- Run as `root` or via `sudo`

---

### How to Use
---
## Gmail App Password Setup (One-time)

> Detailed step-by-step guide is in [GMAIL_SETUP.md](./GMAIL_SETUP.md) (with screenshots)

1. Go to: https://myaccount.google.com  
2. Navigate to `Security` → Enable **2-Step Verification**  
3. Go to **App Passwords**  
4. Select "Other (Custom Name)" → type `Postfix` → click **Generate**  
5. Copy the **16-character app password**

_This app password replaces your Gmail login password for SMTP._

---

### Running the Script

```bash
chmod +x postfix-setup.sh
sudo ./postfix-setup.sh
 Project Structure
postfix-gmail-smtp-setup/
├── postfix-setup.sh          # Main automation script
├── README.md                 # Main documentation and instructions
├── GMAIL_SETUP.md            # Gmail 2FA and App Password setup guide
├── MISTAKES_AND_FIXES.md     # Developer mistakes & resolutions
├── images/                   # Gmail setup screenshots (used in markdown docs)
└── LICENSE                   # (Optional) MIT or preferred license

📧 Sending a Test Email
After setup, you will be prompted with this menu:

markdown
Copy
Edit
1. Send a test email
2. View command syntax for sending emails
3. Exit
Use option 1 to send a test Gmail message using Postfix.
The script will validate recipient email, accept a subject/message, and send the mail securely using Gmail SMTP.

🛠️ Troubleshooting
If something doesn't work:

Double-check your Gmail App Password

Ensure port 587 is open and not blocked by a firewall

View /var/log/mail.log for Postfix errors

Check /etc/postfix/main_backup.cf if you need to restore original config

🧠 Mistakes & Lessons Learned
The MISTAKES_AND_FIXES.md file documents problems encountered during development and how they were solved.
This includes Bash syntax issues, debconf misbehavior, Gmail relay quirks, and permission errors.

🙋 Author
Danyal

Diploma in Cloud Cybersecurity (Alnafi.com)

Passionate about automation, Linux, and cloud tooling

📜 License
This script is provided for educational purposes and internal use.
Use responsibly. You may modify and distribute under your preferred license (MIT recommended).

⚠️ Disclaimer
This script stores Gmail credentials in a hashed file using postmap and applies strict file permissions (chmod 600).
Even so, you are advised to never share your machine, and avoid running this on shared systems.

yaml
Copy
Edit

---

Let me know if you'd like the `GMAIL_SETUP.md` and `MISTAKES_AND_FIXES.md` templates as well.
