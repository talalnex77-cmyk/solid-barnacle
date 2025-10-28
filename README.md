# Private Telegram Bot (Render-ready)

بوت تيليجرام خاص، يعمل 24/7 على Render. ميزات:
- أوامر: `/start`, `/gmap`, `/generate_image`, `/request_capture`, `/design`
- صفحة موافقة لمشاركة الموقع + التقاط صورة أمامية
- تصاميم جاهزة للسوشيال بمقاسات مضبوطة وثيمات: noir/gradient/candy/classic
- حماية JWT وروابط منتهية الصلاحية
- محصور على OWNER_ID فقط

## تشغيل محليًا
```bash
npm install
cp .env.example .env
# عبّي .env
node src/server.js
```

## نشر على Render
- Web Service → Start Command: `node src/server.js`
- Add Environment:
  - BOT_TOKEN, OWNER_ID, SERVER_URL, JWT_SECRET, EXPIRY_MINUTES
  - (اختياري) IMAGE_API_PROVIDER, IMAGE_API_KEY

## أوامر
- `/gmap <query>`
- `/generate_image <prompt>`
- `/request_capture <id>`
- `/design <platform> <type> | <title> | <subtitle?> | theme=<noir|gradient|candy|classic>`
```



## Integration with OpenAI (GPT-4o-mini)
This project now includes a lightweight OpenAI wrapper at `src/lib/openai.js` that calls the Responses API.
To enable the AI features:

1. Create a `.env` file (copy `.env.example`) and set:
```
BOT_TOKEN=your_telegram_bot_token
OWNER_ID=your_numeric_telegram_id
OPENAI_API_KEY=sk-xxxxxx
OPENAI_MODEL=gpt-4o-mini
```

2. Install dependencies and run:
```
npm install
npm start
```

Security notes:
- **Never share your OPENAI_API_KEY** publicly. Keep it in `.env` or environment variables on your server.
- The bot enforces owner-only access for private chats when `OWNER_ID` is set.

