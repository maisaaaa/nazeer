# 🦅 Nazeer (نذير) | Team Falcon Shield (صقر الأمان)

**ScamShield AI Hackathon, AD Police x 42 Abu Dhabi**

Nazeer is an on-device scam detector for Gulf Arabic and English messages. It scores the risk, explains why, tells the user what to do, and alerts a trusted contact when the risk is high.

## 1. Problem and Solution

**Problem:** Scam messages and calls pressure victims into sharing OTPs or transferring money within minutes. The most exposed groups are elders, domestic workers and non-Arabic speakers, and most tools only detect the scam without involving anyone who can stop the victim.

**Solution:** Nazeer has three parts:
1. **Message analyzer:** Paste a suspicious message or call transcript. Nazeer returns a 0 to 100 risk score, the reasons, and clear next steps.
2. **Trust Circle:** At risk 60 or higher, a ready alert is prepared for a trusted person (son, brother, friend) who can call and stop the transaction.
3. **Police dashboard:** Anonymous reports are aggregated into scam-type statistics and a suggested proactive warning for the most active pattern.

## 2. Technical Choices and Trade-offs

- **Rule-based engine in the browser (single `index.html`, no dependencies).**
  - Why: it runs fully on the device, so **no message text ever leaves the phone** (privacy by design), and it works with zero setup.
  - Trade-off: rules are less flexible than a trained model and can miss new scam wording.
- **Weighted scoring:** 8 scam signals (OTP request, urgency, account-suspension threat, suspicious link, fake prize, official-body impersonation, payment request, secrecy request), each with a weight. Scores are capped at 100.
- **Bilingual patterns:** Arabic (including Gulf phrasing) and English.
- **Dashboard data:** The baseline numbers are **demo data**, clearly labeled. Reports made in the session are added anonymously and are not stored on any server.
- **Trust Circle alert:** Built as a WhatsApp share link, so it works without any backend.

**Left out (time limit):** a trained model, voice-call analysis, Urdu/Hindi/Tagalog, a real backend database.

## 3. What We Would Do With More Time

- Replace or complement rules with a fine-tuned multilingual classifier (Gulf Arabic, Urdu, Hindi, Tagalog), running on-device.
- Voice-clone detection on live calls.
- An AI "decoy" bot that wastes the scammer's time and collects phone numbers and accounts for the police.
- A real anonymous reporting backend with clustering to detect scam networks and predict the next wave by area.

## 4. How to Run

No build step is needed.

1. Download `index.html`.
2. Open it in any browser (double-click or open from your phone).
3. Try the example buttons, or paste your own message.

**Live demo:** https://claude.ai/artifact/3eRpPXteyMj9ENnhdh3SL
