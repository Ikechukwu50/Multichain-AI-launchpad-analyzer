# 🔍 MultiChain AI Launchpad Analyzer

Automated token launch intelligence across **Ethereum**, **BNB Chain**, and **Solana** — built entirely on free-tier infrastructure.

When new tokens launch, this agent evaluates them across four dimensions and fires a scored Telegram alert before you'd ever find it manually.

---

## What It Does

Every 15 minutes the workflow:
1. Pulls newly launched tokens from DexScreener across ETH, BSC, and SOL
2. Runs each contract through GoPlus Security — honeypot detection, tax scan, mint/blacklist checks
3. Feeds all signals into Gemini Flash for deep analysis
4. Scores the token 0–100 across tokenomics, contract risk, sentiment, and liquidity
5. Sends a formatted Telegram alert and logs everything to Google Sheets

---

## Analysis Pillars

| Pillar | What Gets Checked |
|---|---|
| 📊 Tokenomics | Supply distribution, team allocation, vesting, burn mechanics |
| 🔐 Contract Risk | Honeypot, buy/sell tax, mint function, ownership, proxy patterns |
| 📣 Sentiment | Mention velocity, dev communication, bot signals |
| 💧 Liquidity | Pool size, LP lock status, volume/mcap ratio, rug probability |

Chain-specific risk modifiers are applied automatically — BSC gets a -5 penalty, ETH gets +5, Solana -3 — reflecting real-world rug rates per chain.

---

## Free Tier Stack

| Service | Usage | Cost |
|---|---|---|
| n8n Cloud | Workflow automation | Free |
| DexScreener API | New token detection | Free |
| GoPlus Security API | Contract scanning | Free |
| Google Gemini Flash | AI analysis | Free |
| Telegram Bot API | Alerts | Free |
| Google Sheets | Audit log | Free |

**Total monthly cost: $0**

---

## Sample Telegram Alert

```
🔔 ◈ BSC — NEW TOKEN
━━━━━━━━━━━━━━━━━━
Token: $BLAZE
Contract: 0xc4a1...f920
DEX: pancakeswap · Age: 12m

📊 SCORES
Tokenomics : 55/100
Contract   : 40/100
Sentiment  : 72/100
Liquidity  : 35/100

💰 MARKET
Liquidity  : $3,200
LP Locked  : ❌ NO
Honeypot   : ✅ NO
Tax B/S    : 14% / 14%

🚩 FLAGS
⚠️ sell_tax 14% — above safe threshold
⚠️ LP unlocked
⚠️ Mint function active

🚨 VERDICT: DANGER · 44/100
ACTION: AVOID
```

---

## Setup

1. Import `multichain_ai_analyzer_v5.json` into your n8n Cloud workspace
2. Add credentials — Google Gemini API, Telegram Bot, Google Sheets OAuth2
3. In the **Chain Config** node replace `ETHERSCAN_KEY_HERE` and `BSCSCAN_KEY_HERE` with your free keys from etherscan.io and bscscan.com
4. Set your Telegram Chat ID in the **Send Telegram Alert** node
5. Create a Google Sheet named `Analyzer Log` and paste its ID into the **Log to Google Sheets** node
6. Hit **Execute Workflow** to test, then toggle **Active: ON**

---

## Built With

`n8n` `Google Gemini Flash` `DexScreener API` `GoPlus Security API` `Telegram Bot API` `Google Sheets` `JavaScript`

---

> Part of a broader suite of free-tier AI automation projects. See more at [github.com/Ikechukwu50](https://github.com/Ikechukwu50)
> 
