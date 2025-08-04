# DataScrapeKit
</p>

<h1 align="center">Persian Web Crawler 🕸️📰</h1>

<p align="center"><b>
ابزاری ماژولار برای استخراج محتوای فارسی از وب‌سایت‌های ایرانی، جهت ساخت کورپوس‌های زبانی
</b></p>

<p align="center">
  <i>A modular asynchronous web scraping tool for collecting Persian-language content from Iranian websites — suitable for training/fine-tuning LLMs.</i>
</p>

---

## 🚀 ویژگی‌ها (Features)

- ماژولار: هر وب‌سایت یک خزنده‌ی جداگانه دارد  
- پردازش و دانلود صفحات به صورت `async` با استفاده از `aiohttp`  
- ذخیره‌سازی سریع در دیتابیس SQLite با `aiosqlite`  
- مناسب برای آماده‌سازی کورپوس خام برای مدل‌های زبانی فارسی  
- طراحی ساده، قابل توسعه برای وب‌سایت‌های جدید  
- پشتیبانی از ابزارهای پردازش زبان طبیعی و LLMها (مثل ساخت dataset و فرمت‌های fine-tune)

## 📁 ساختار پروژه (Project Structure)

```
.
├── scrapers/               # خزنده‌های اختصاصی برای هر وب‌سایت
│   ├── site1_scraper.py
│   └── site2_scraper.py
│
├── configs/                # فایل‌های پیکربندی برای هر خزنده (config YAML/JSON)
│   ├── site1.yaml
│   └── site2.yaml
│
├── db/
│   └── articles.db         # دیتابیس SQLite نهایی
│
├── utils/
│   └── cleaner.py          # ابزارهای پاک‌سازی و پردازش متن
│
├── llm_tools/              # ابزارهای آماده‌سازی داده برای LLM
│   └── convert_to_jsonl.py
│
├── main.py                 # کنترل‌گر اصلی
├── requirements.txt        # وابستگی‌ها
└── README.md
```

---

## ✍️ افزودن خزنده جدید

برای افزودن یک خزنده جدید:

1. یک فایل Python جدید در مسیر `scrapers/` اضافه کن (مثلاً `mynews_scraper.py`)
2. در این فایل تابع `fetch_articles(session)` را پیاده‌سازی کن که خروجی‌اش لیستی از دیکشنری‌ها باشد:
```python
[
  {
    "url": "...",
    "title": "...",
    "content": "...",
    "published_at": "..."
  }
]
```
3. یک فایل پیکربندی (YAML یا JSON) مربوط به آن خزنده در `configs/` اضافه کن که تعیین کند چه بخش‌هایی ذخیره شوند.
4. خزنده را در `main.py` ثبت و اجرا کن.

---

## 🧠 ابزارهای LLM (LLM Tools)

در پوشه `llm_tools/` می‌توانید ابزارهایی برای:

- تبدیل خروجی به فرمت `JSONL` جهت fine-tune مدل
- تمیزسازی داده‌ها (cleaning, filtering)
- تنظیم داده‌ها در فرمت‌های instruction-style

پیدا کنید.

---

## ⚙️ نصب و اجرا (Install & Run)

### 1. نصب پیش‌نیازها

```bash
pip install -r requirements.txt
```

محتوای فایل `requirements.txt`:
```text
aiohttp
aiosqlite
beautifulsoup4
pyyaml
```

### 2. اجرای خزنده‌ها

```bash
python main.py
```

---

## 🎯 هدف پروژه

این ابزار با هدف استخراج محتوای زبانی باکیفیت از وب فارسی طراحی شده تا بتوان از آن در:

- آموزش مدل‌های زبانی فارسی  
- ساخت دیتاست‌های عمومی  
- پژوهش‌های NLP در زبان فارسی  

استفاده کرد.

---

## 📄 License

### 🧠 Code

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it with attribution.

### 📚 Data

Any datasets produced by this scraper are released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

> لطفاً در صورت استفاده از داده‌های استخراج‌شده، منبع پروژه را ذکر کنید.

---

## 🤝 مشارکت

پروژه در مرحله اولیه است و به‌زودی خزنده‌های بیشتری برای وب‌سایت‌های فارسی‌زبان اضافه خواهد شد.  
اگر تمایل به مشارکت دارید، PR باز کنید یا issue ثبت کنید.

---

## 📬 ارتباط

در صورت سوال یا پیشنهاد، می‌توانید از طریق issueها یا [GitHub Discussions](#) با ما در ارتباط باشید.

---

### ✨ ساخته شده با ❤️ برای زبان فارسی
