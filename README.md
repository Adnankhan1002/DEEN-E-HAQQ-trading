# PulseTrade — Modern Trading Platform MVP

A polished paper-trading web platform demo built with React, Vite, Recharts and Lucide icons.

## Included
- Modern responsive trading dashboard
- NSE-style market overview and market movers
- Stock search
- Interactive price chart with timeframe controls
- Watchlist and stock selection
- Buy / Sell order ticket
- Market and Limit order demo
- Quantity shortcuts and estimated order value
- Simulated order execution
- Order history
- Portfolio / holdings page
- Funds / wallet page
- QR-based demo payment flow
- Demo balance top-up
- Responsive mobile navigation
- Demo/paper-trading safety messaging

## Run
```bash
npm install
npm run dev
```

## Build
```bash
npm run build
```

## Important
This is a front-end MVP/demo. Market data, holdings, orders, authentication, KYC, payment verification and broker execution are simulated in browser state. Do not use this implementation for real-money trading.

## Production architecture suggestion
Next.js/React frontend + Node.js/Express APIs + PostgreSQL/MongoDB + Redis + Kafka + broker APIs + verified UPI/payment gateway + KYC provider + audit/event store.

## Payment screenshot upload
The Add Funds modal now lets a user attach a payment screenshot. To have the screenshot actually reach you/admin, configure an n8n webhook in `.env`:

```env
VITE_PAYMENT_PROOF_WEBHOOK_URL=https://YOUR-N8N-DOMAIN/webhook/payment-proof
```

The browser sends a `multipart/form-data` POST containing:
- `payment_screenshot` — uploaded image file
- `amount` — selected deposit amount
- `submitted_at` — ISO timestamp

The frontend validates image type and limits uploads to 8 MB. The n8n webhook should handle storing/forwarding the proof to your preferred destination (Google Drive, Telegram, email, etc.).
