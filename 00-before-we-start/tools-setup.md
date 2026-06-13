# راهنمای ابزارها

اولویت این دوره با ابزارهای تحت وب است. یعنی بیشتر کارها را می‌توانی مستقیم در مرورگر انجام بدهی، بدون نصب چیزی. این صفحه ابزارها را به ترتیب اولویت معرفی می‌کند.

---

## خلاصه سریع

| ابزار | کاربرد | نیاز به نصب؟ | ضروری از |
|-------|---------|--------------|----------|
| مرورگر به‌روز | همه چیز | خیر | فصل ۰۰ |
| Google Account | Sheets و Colab | خیر | فصل ۰۱ |
| Google Sheets | تحلیل ساده داده | خیر | فصل ۰۱ |
| Datawrapper | نمودار بدون کد | خیر | فصل ۰۲ |
| Google Colab | Python در مرورگر | خیر | فصل ۰۳ |
| Pandas | کار با جدول داده | خیر (در Colab) | فصل ۰۳ |
| Matplotlib | نمودار پایه | خیر (در Colab) | فصل ۰۳ |
| Altair | بصری‌سازی پیشرفته‌تر | یک خط در Colab | فصل ۰۴ |
| Flourish | روایت بصری تعاملی | خیر | فصل ۰۴ |
| ChatGPT یا معادل | دستیار هوش مصنوعی | خیر | فصل ۰۵ |

---

## ۱. مرورگر

Chrome، Edge یا Firefox — هر کدام که داری و به‌روز است کافی است. تمام ابزارهای اصلی این دوره در مرورگر اجرا می‌شوند.

---

## ۲. حساب Google

برای Google Sheets و Google Colab به یک حساب Google نیاز داری.

با این حساب می‌توانی:
- فایل‌های CSV و Excel را در Sheets باز و ویرایش کنی.
- کدهای Python را بدون هیچ نصبی در Colab اجرا کنی.
- فایل‌هایت را در Drive ذخیره کنی.

اگر به هر دلیل نمی‌خواهی از Google استفاده کنی، Python را روی سیستم نصب کن (بخش ۶ همین فایل).

---

## ۳. Google Sheets

برای فصل‌های اول، Google Sheets ابزار اصلی ماست. کافی است بتوانی:

- یک فایل CSV را import کنی (File > Import).
- ستون‌ها را مرتب و فیلتر کنی.
- یک فرمول ساده مثل `=AVERAGE()` یا `=COUNTIF()` بنویسی.

### تست سریع

این جدول را در یک Sheet جدید وارد کن:

| city | year | value |
|------|------|-------|
| Tehran | 2022 | 120 |
| Tehran | 2023 | 145 |
| Shiraz | 2022 | 80 |
| Shiraz | 2023 | 95 |

بعد ستون `value` را از بزرگ به کوچک مرتب کن. اگر انجام شد، آماده‌ای.

---

## ۴. Datawrapper

برای ساخت نمودارهای تمیز و قابل انتشار بدون کد.

**چرا Datawrapper؟**
- استاندارد رسانه‌های داده‌محور مثل New York Times و The Economist است.
- خروجی‌اش تمیز، تعاملی و قابل embed است.
- رایگان برای استفاده عمومی.

**شروع:**
1. وارد [datawrapper.de](https://datawrapper.de) شو.
2. یک حساب رایگان بساز.
3. با همان جدول تست بالا یک نمودار ستونی بساز.

---

## ۵. Google Colab — محیط اصلی Python

Google Colab یک محیط Jupyter Notebook تحت مرورگر است. Python، Pandas و Matplotlib همه از قبل نصب‌اند. نیازی به هیچ کاری نداری.

**شروع:**
1. به [colab.research.google.com](https://colab.research.google.com) برو.
2. یک Notebook جدید بساز (File > New Notebook).
3. این را در اولین سلول بنویس و اجرا کن (Shift+Enter):

```python
import pandas as pd
print(pd.__version__)
```

اگر یک عدد نسخه دیدی، همه چیز آماده است.

---

## ۶. Pandas

Pandas اصلی‌ترین کتابخانه‌ای است که در فصل‌های کم‌کد باهاش کار می‌کنیم. در Google Colab از قبل نصب است.

اگر Python روی سیستم داری:

```bash
pip install pandas
```

### تست سریع در Colab

```python
import pandas as pd

data = {
    'city': ['Tehran', 'Tehran', 'Shiraz', 'Shiraz'],
    'year': [2022, 2023, 2022, 2023],
    'value': [120, 145, 80, 95]
}

df = pd.DataFrame(data)
print(df.sort_values('value', ascending=False))
```

---

## ۷. Matplotlib

کتابخانه نمودار پایه در Python. در Colab آماده است.

```python
import matplotlib.pyplot as plt

cities = ['Tehran 2022', 'Tehran 2023', 'Shiraz 2022', 'Shiraz 2023']
values = [120, 145, 80, 95]

plt.bar(cities, values)
plt.title('مقایسه مقادیر')
plt.tight_layout()
plt.show()
```

---

## ۸. Altair

Altair یک کتابخانه بصری‌سازی declarative در Python است — یعنی به جای اینکه بگویی «چطور» نمودار را بکش، می‌گویی «چه» می‌خواهی نشان دهی. برای روایتگران که می‌خواهند سریع نمودارهای قابل‌فهم بسازند، خیلی مناسب است.

در Colab با یک خط نصب می‌شود:

```python
!pip install altair
```

### تست سریع

```python
import altair as alt
import pandas as pd

df = pd.DataFrame({
    'city': ['Tehran', 'Tehran', 'Shiraz', 'Shiraz'],
    'year': [2022, 2023, 2022, 2023],
    'value': [120, 145, 80, 95]
})

alt.Chart(df).mark_bar().encode(
    x='year:O',
    y='value:Q',
    color='city:N'
)
```

---

## ۹. Flourish

برای روایت‌های بصری تعاملی که می‌خواهی منتشر کنی یا embed کنی.

- [flourish.studio](https://flourish.studio) — حساب رایگان بساز.
- مناسب برای race bar charts، نقشه، scrollytelling.
- نیازی به کد ندارد.

---

## ۱۰. ابزار هوش مصنوعی

برای فصل ۰۵، به یک مدل زبانی نیاز داری. گزینه‌ها:

- ChatGPT (openai.com)
- Claude (claude.ai)
- Gemini (gemini.google.com)

هر کدام که دسترسی داری کافی است. در استفاده:

- اطلاعات شخصی یا محرمانه وارد نکن.
- خروجی مدل را منبع قطعی حساب نکن.
- برای ادعاهای مهم، منبع مستقل پیدا کن.

### تست سریع

این پرامپت را امتحان کن:

```
من یک روزنامه‌نگارم و می‌خواهم درباره افزایش اجاره‌خانه گزارش بنویسم.
۵ سوال داده‌محور پیشنهاد بده که بتوانم با داده‌های عمومی بررسی کنم.
برای هر سوال بگو چه نوع داده‌ای لازم دارم.
```

اگر خروجی گرفتی و توانستی کیفیتش را نقد کنی، آماده‌ای.

---

## اگر می‌خواهی Python را روی سیستم نصب کنی

برای اکثر کارهای این دوره، Google Colab کافی است. اما اگر می‌خواهی محیط محلی داشته باشی:

**Windows:**
1. از [python.org](https://python.org) نصب کن.
2. هنگام نصب، گزینه **Add Python to PATH** را فعال کن.
3. در Command Prompt: `python --version`

**macOS / Linux:**
```bash
python3 --version
# اگر نصب نبود:
brew install python  # macOS با Homebrew
```

بعد از نصب:
```bash
pip install pandas matplotlib altair jupyter openpyxl
```

---

## چک‌لیست آماده‌سازی

قبل از فصل ۰۱:

- [ ] مرورگر به‌روز دارم.
- [ ] حساب Google دارم.
- [ ] می‌توانم یک فایل CSV را در Google Sheets باز کنم.
- [ ] حساب Datawrapper ساخته‌ام.
- [ ] Google Colab را باز کرده‌ام و یک سلول ساده اجرا کرده‌ام.

همین کافی است. بقیه ابزارها را به‌موقع اضافه می‌کنیم.

---

**فصل ۰۱: داده را بشناس →**
