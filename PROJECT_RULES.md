# PROJECT_RULES.md

# Project Rules

## Purpose

Ushbu hujjat loyiha davomida barcha kod, modul va qarorlar uchun majburiy qoidalarni belgilaydi.

Har qanday yangi kod ushbu qoidalarga mos bo'lishi shart.

Agar kod ushbu qoidalarga zid bo'lsa, u noto'g'ri hisoblanadi.

---

# Rule 1 — Product First

Kod mahsulot maqsadiga xizmat qilishi kerak.

Mahsulot maqsadi:

Film ichidan Instagram Reels uchun Telegram kanaliga eng ko'p obunachi olib kelish ehtimoli yuqori bo'lgan sahnalarni topish.

Har bir modul o'zidan:

"Men ushbu maqsadga xizmat qilyapmanmi?"

deb so'rashi kerak.

---

# Rule 2 — Modular Design

Har bir modul bitta vazifa bajaradi.

Masalan:

Video yuklash.

Whisper.

OpenCV.

Scoring.

Preview.

Cutting.

Bir modul ichida bir nechta mustaqil logika aralashtirilmaydi.

---

# Rule 3 — Low Coupling

Modullar bir-biriga kuchli bog'lanmasligi kerak.

Bir modulni almashtirish boshqalarga ta'sir qilmasligi kerak.

---

# Rule 4 — High Cohesion

Bir fayl ichidagi barcha funksiyalar bitta mavzuga tegishli bo'lishi kerak.

Masalan:

preview.py

ichida

download()

bo'lmaydi.

---

# Rule 5 — Clean Code

Kod:

o'qilishi oson

nomlari tushunarli

izchil

minimal

bo'lishi kerak.

Qisqa nomlar taqiqlanadi.

Misol:

x

tmp1

abc

func2

ishlatilmaydi.

---

# Rule 6 — Type Hints

Barcha public funksiyalar:

type hints

ga ega bo'lishi shart.

Misol:

```python
def analyze(video_path: Path) -> AnalysisResult:
    ...
```

---

# Rule 7 — Docstrings

Murakkab funksiyalar uchun:

docstring yoziladi.

Funksiya:

nima qiladi

parametr

natija

istisnolar

tushuntiriladi.

---

# Rule 8 — Logging

print()

ishlatilmaydi.

Faqat logger.

Darajalar:

DEBUG

INFO

WARNING

ERROR

---

# Rule 9 — Error Handling

Har Exception yutilmaydi.

Hech qachon:

except:
pass

yozilmaydi.

Xatolik:

log qilinadi

va yuqoriga uzatiladi.

---

# Rule 10 — Configuration

Hardcode qiymatlar taqiqlanadi.

Masalan:

ADMIN_ID

BUFFER

TEMP

MAX_SIZE

config.py orqali olinadi.

---

# Rule 11 — Temporary Files

Har yaratilgan temp fayl:

finally

blokida yoki

Cleanup Manager

orqali o'chiriladi.

---

# Rule 12 — Async First

Telegram bilan ishlash:

async

bo'lishi shart.

Bloklovchi operatsiyalar event loopni to'xtatmasligi kerak.

---

# Rule 13 — Progress

Har uzun jarayon:

Progress Manager

orqali ishlaydi.

Yangi message yuborilmaydi.

Faqat edit qilinadi.

---

# Rule 14 — Cancel Support

30 soniyadan uzun har bir jarayon:

Bekor qilish

imkoniyatiga ega bo'lishi shart.

---

# Rule 15 — Uzbek Interface

Foydalanuvchiga ko'rinadigan barcha matn:

100% o'zbek tilida.

Kod ichidagi nomlar:

ingliz tilida.

---

# Rule 16 — Original Video

Original video:

hech qachon

o'zgartirilmaydi.

---

# Rule 17 — Non-Destructive Processing

Har qanday ishlov:

copy

temp

buffer

orqali bajariladi.

---

# Rule 18 — Explainability

AI har doim sababini yozadi.

Faqat ball chiqarmaydi.

---

# Rule 19 — Deterministic Logic

Bir xil video

bir xil konfiguratsiya

↓

bir xil natija.

Tasodifiy qarorlar bo'lmaydi.

---

# Rule 20 — Security

Faqat administrator.

Video tashqi serverga yuborilmaydi.

API orqali uchinchi tomonga uzatilmaydi.

---

# Rule 21 — Dependency Control

Keraksiz kutubxona qo'shilmaydi.

Har dependency:

asoslangan

zarur

bo'lishi kerak.

---

# Rule 22 — Performance

Keraksiz:

copy

RAM

CPU

ishlatilmaydi.

Har modul samarali ishlashi kerak.

---

# Rule 23 — Reusable Components

Kod qayta ishlatiladigan bo'lishi kerak.

Copy-paste taqiqlanadi.

---

# Rule 24 — Single Source of Truth

Bir xil ma'lumot bir nechta joyda saqlanmaydi.

Masalan:

BUFFER_SECONDS

faqat bitta joyda mavjud bo'ladi.

---

# Rule 25 — Testability

Har modul alohida test qilinishi mumkin bo'lishi kerak.

Telegramsiz ham.

---

# Rule 26 — AI Independence

AI moduli Telegram haqida bilmaydi.

Telegram moduli AI haqida bilmaydi.

---

# Rule 27 — Resource Safety

Har ochilgan resurs:

file

stream

ffmpeg

subprocess

yopilishi shart.

---

# Rule 28 — Naming Convention

Fayllar:

snake_case

Sinflar:

PascalCase

Funksiyalar:

snake_case

Konstantalar:

UPPER_CASE

---

# Rule 29 — Git Discipline

Har commit:

bitta mantiqiy o'zgarish.

Bir commitda 20 xil vazifa bajarilmaydi.

---

# Rule 30 — Documentation

Har yangi modul:

README

yoki

docstring

bilan tushuntiriladi.

---

# Rule 31 — No Dead Code

Foydalanilmaydigan:

funksiya

klass

import

kommentlangan kod

loyihada qolmaydi.

---

# Rule 32 — Fail Fast

Noto'g'ri parametr aniqlansa:

jarayon imkon qadar erta to'xtatiladi.

---

# Rule 33 — Preview Is Temporary

Preview faqat tanlash uchun.

Original natija emas.

---

# Rule 34 — Buffer Rule

Har kesishda:

3 soniya oldin

*

3 soniya keyin.

Buffer konfiguratsiyadan boshqariladi.

---

# Rule 35 — Final Goal

Loyiha video kesuvchi dastur emas.

Loyiha AI yordamida Instagram uchun eng kuchli sahnalarni topuvchi tizimdir.

Kod yozishda ushbu qoida barcha boshqa qarorlardan ustun turadi.
