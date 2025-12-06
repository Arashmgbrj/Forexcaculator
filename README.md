# 📊 Forex Calculator - ماشین حساب معاملات فارکس

یک اپلیکیشن ساده و کاربردی برای محاسبات ضروری در معاملات فارکس، ساخته شده با React Native و Expo.

## ✨ ویژگی‌ها

- 🔢 **محاسبه حجم معامله (لات)** بر اساس درصد ریسک
- 📈 **محاسبه مقدار پیپ** برای جفت‌ارزهای مختلف
- 💰 **محاسبه سود/ضرر** به دلار و درصد
- 🎯 **پشتیبانی از جفت‌ارزهای اصلی و کراس**
- 📱 **رابط کاربری ساده و ریسپانسیو**
- 🌙 **حالت تاریک/روشن** (اختیاری)

## 🧮 قابلیت‌های محاسباتی

### ۱. محاسبه لات (Position Size)
```
لات = (سرمایه × درصد ریسک) ÷ (تعداد پیپ × ارزش هر پیپ)
```

### ۲. محاسبه ارزش هر پیپ
```
برای جفت‌ارزهای مبتنی بر USD:
ارزش پیپ = (0.0001 ÷ نرخ ارز) × حجم معامله

برای جفت‌ارزهای غیر USD:
ارزش پیپ = (0.0001 × حجم معامله) ÷ نرخ USD/ارز پایه
```

### ۳. محاسبه ریسک به ریوارد
```
Risk/Reward = (حد سود - نقطه ورود) ÷ (نقطه ورود - حد ضرر)
```

## 🚀 نصب و راه‌اندازی

### پیش‌نیازها
- Node.js (ورژن 14 یا بالاتر)
- npm یا yarn
- Expo CLI

### مراحل نصب
```bash
# 1. کلون کردن ریپازیتوری
git clone https://github.com/your-username/forex-calculator.git

# 2. رفتن به پوشه پروژه
cd forex-calculator

# 3. نصب dependencies
npm install
# یا
yarn install

# 4. راه‌اندازی اپلیکیشن
npx expo start
```

### برای اندروید
```bash
npx expo run:android
```

### برای iOS
```bash
npx expo run:ios
```

### برای وب
```bash
npx expo start --web
```

## 🎮 راهنمای استفاده

### صفحه اصلی
1. **انتخاب جفت ارز** از لیست کشویی
2. **وارد کردن سرمایه حساب** (Balance)
3. **تعیین درصد ریسک** (Risk %)
4. **وارد کردن حد ضرر** (Stop Loss) بر اساس پیپ
5. **محاسبه اتوماتیک** حجم معامله

### مثال عملی
```
جفت ارز: EUR/USD
سرمایه حساب: $10,000
درصد ریسک: 2%
حد ضرر: 50 پیپ

نتایج:
- حجم معامله: 0.4 لات
- ریسک واقعی: $200
- ارزش هر پیپ: $4
```

## 📁 ساختار پروژه

```
forex-calculator/
├── src/
│   ├── components/     # کامپوننت‌های قابل استفاده مجدد
│   ├── screens/        # صفحات اپلیکیشن
│   ├── utils/          # توابع کمکی و محاسبات
│   ├── constants/      # داده‌های ثابت
│   └── styles/         # استایل‌های مشترک
├── assets/             # تصاویر و فونت‌ها
├── App.js              # نقطه ورود اپلیکیشن
└── package.json
```

## 🛠 تکنولوژی‌های استفاده شده

- **React Native** - فریم‌ورک اصلی
- **Expo** - توسعه و build سریع‌تر
- **React Navigation** - مدیریت navigation
- **React Native Paper** یا **NativeBase** (اختیاری) - کامپوننت‌های UI
- **React Hook Form** - مدیریت فرم‌ها
- **Victory Native** یا **React Native Charts** (اختیاری) - نمودارها

## 📊 فرمول‌های محاسباتی

### محاسبه لات استاندارد
```javascript
function calculateLotSize(balance, riskPercent, stopLossPips, currencyPair) {
  const riskAmount = balance * (riskPercent / 100);
  const pipValue = calculatePipValue(currencyPair);
  const lotSize = riskAmount / (stopLossPips * pipValue);
  return Math.round(lotSize * 100) / 100; // گرد کردن به دو رقم اعشار
}
```

### محاسبه ارزش پیپ
```javascript
function calculatePipValue(currencyPair, lotSize = 1) {
  const [baseCurrency, quoteCurrency] = currencyPair.split('/');
  
  if (quoteCurrency === 'USD') {
    return 10 * lotSize; // برای جفت‌های XXX/USD
  } else if (baseCurrency === 'USD') {
    return 10 / exchangeRate; // برای جفت‌های USD/XXX
  }
  
  // برای کراس‌ها
  return 10 * exchangeRateToUSD;
}
```

-
