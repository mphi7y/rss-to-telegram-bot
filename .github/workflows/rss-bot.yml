name: RSS to Telegram Bot

# متى يعمل البوت
on:
  schedule:
    # كل 5 دقائق (أسرع فترة مسموحة في GitHub)
    - cron: '*/5 * * * *'
  # يمكن تشغيله يدوياً أيضاً
  workflow_dispatch:

jobs:
  rss-to-telegram:
    runs-on: ubuntu-latest
    
    steps:
    # تحميل الكود
    - name: Checkout repository
      uses: actions/checkout@v4
    
    # إعداد Node.js
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '18'
    
    # تثبيت المكتبات المطلوبة
    - name: Install dependencies
      run: |
        npm init -y
        npm install rss-parser axios
    
    # تشغيل البوت
    - name: Run RSS to Telegram Bot
      env:
        TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
        TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
        RSS_URL: ${{ secrets.RSS_URL }}
      run: node bot.js
