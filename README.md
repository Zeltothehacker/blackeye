# Pluto

Pluto is a local, terminal-based phishing simulation toolkit for cybersecurity awareness training. It bundles a set of realistic phishing pages, a public tunneling flow, live visitor logging, and an SMTP-based email crafter in one script.

This project is designed for authorized security awareness exercises and controlled lab environments. It is not intended for unauthorized or malicious activity.

---

## What it includes

- 33 phishing page targets, including Instagram, Facebook, Google, Microsoft, Netflix, PayPal, Steam, Twitter, Spotify, GitHub, LinkedIn, and more
- Cloudflare, Ngrok, or localhost tunnel options
- Automatic Cloudflare tunnel download if needed
- Visitor detection with IP and geolocation enrichment
- Device detection from user-agent strings
- Real-time credential capture
- Email crafting workflow with SMTP testing and template support
- Session summary output when you stop the tool

---

## Requirements

Before running the toolkit, make sure these are installed:

- php
- curl
- python3
- Optional: ngrok (only needed for the ngrok tunnel method)

The script also auto-downloads the Cloudflare tunnel binary if it is missing.

---

## Installation

```bash
git clone https://github.com/Zeltothehacker/Pluto--Phishing_tool.git
cd Pluto--Phishing_tool
bash Pluto.sh
```

You only need to run the main script: `Pluto.sh`.

---

## Quick start

Launch the menu:

```bash
bash Pluto.sh
```

From the main menu:

- Select a phishing page by number, such as `01` for Instagram
- Or press `E` to open the email crafter
- Or press `Q` to quit

When you choose a phishing page, the script asks for a tunnel method:

1. Cloudflare
2. Ngrok
3. Localhost

It then starts a local PHP server and exposes it through the selected tunnel or local loopback address.

---

## Supported phishing pages

The project includes the following live targets in the menu:

- Instagram
- Facebook
- Google
- Microsoft
- Netflix
- PayPal
- Steam
- Twitter
- Spotify
- Adobe
- Badoo
- CryptoCurrency
- DeviantArt
- Dropbox
- GitHub
- GitLab
- LinkedIn
- Messenger
- MySpace
- Origin
- Pinterest
- ProtonMail
- Shopify
- Snapchat
- Shopping
- Twitch
- Verizon
- VK
- WordPress
- Yahoo
- Yandex
- InstaFollowers
- Custom site folder

---

## Real-time behavior

When a target visits a phishing page:

- The PHP server runs locally on `127.0.0.1:3333`
- The public tunnel exposes the page to the visitor
- Visitor IPs are logged in the target site folder
- Credentials are written to `usernames.txt`
- Captured data is appended to `master_creds.log`
- A session summary is shown when you interrupt the process with `Ctrl+C`

The script also checks for geolocation and enrichment data using the public IP API, including:

- city
- region
- country
- ISP
- organisation
- proxy/VPN indicator
- hosting/datacenter indicator

It attempts to identify the device from the browser user agent, such as:

- iPhone
- Android
- Windows
- macOS
- Linux

---

## Email crafter

Press `E` from the main menu to open the spear-phishing email builder.

It supports:

- Gmail, Outlook, Yahoo, or custom SMTP provider
- Saved SMTP configuration
- Template selection
- Custom subject and body input
- Single-send or bulk CSV send
- Draft saving to the `drafts/` directory

The built-in templates include:

- Password Reset
- Security Alert
- Shared Document
- Invoice / Payment

The script sends HTML content via `curl` with SMTP credentials and shows delivery status.

---

## Project structure

```text
Pluto/
├── Pluto.sh
├── README.md
├── master_creds.log
├── smtp_config
├── sent_log.txt
├── cloudflared
├── drafts/
├── sites/
│   ├── adobe/
│   ├── facebook/
│   ├── google/
│   ├── instagram/
│   └── ...
├── templates/
│   ├── invoice.html
│   ├── password_reset.html
│   ├── security_alert.html
│   └── shared_document.html
└── ...
```

---

## Logging and output files

The script creates and updates several files during use:

- `master_creds.log` — aggregated captured credentials
- `sent_log.txt` — log of email delivery attempts
- `smtp_config` — saved SMTP account configuration
- `sites/<site>/ip.txt` — visitor IP and UA log
- `sites/<site>/usernames.txt` — captured login values
- `drafts/` — saved email drafts

---

## Ethics and legal use

Pluto is intended for:

- controlled security awareness training
- ethics-focused lab environments
- authorized exercises with explicit consent

It must not be used against any target without prior approval and legal authorization.

The user is responsible for complying with all local, state, and federal laws. The maintainers assume no liability for misuse.

---

## Troubleshooting

### Cloudflare tunnel problems

- Check that you have internet access
- Make sure the Cloudflare binary can download successfully
- If Cloudflare fails, use Ngrok or Localhost instead

### SMTP failures

- Verify the SMTP host and port
- For Gmail, use a 2FA app password instead of the account password
- Try port 465 for some providers
- Confirm that the sender address and credentials are valid

### Visitor info missing

- IP lookup may fail on some networks
- Credential logging still works even if geolocation fails

---

## License and ownership

This repository is provided as-is for educational and lab-oriented use. Review the project files and use them in an environment where you have permission to simulate phishing scenarios.

---

## Credits

This project builds on the original phishing page concept and extends it with modern terminal automation, tunnel support, email capability, and live visitor tracking.

The current version includes:

- original page-based tooling concept
- expanded template set
- Cloudflare tunnel automation
- SMTP email crafter
- IP enrichment and session tracking
- educational banner/disclaimer messaging

---

## Notes

The repo is primarily meant to demonstrate how phishing simulations and awareness training can be built in a local environment. Use it strictly in approved training contexts and never outside of informed, consent-based testing.
