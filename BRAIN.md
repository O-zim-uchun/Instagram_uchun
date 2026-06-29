# BRAIN.md

# AI Decision Engine

## Purpose

Instagram Reels Finder AI ning asosiy vazifasi videoni kesish emas.

Asosiy vazifa — film ichidan Instagram Reels uchun maksimal e'tibor tortadigan sahnalarni aniqlash.

AI videoni oddiy media fayl sifatida emas, balki ketma-ket voqealar va emotsiyalar oqimi sifatida tahlil qiladi.

---

# Thinking Model

AI hech qachon bitta belgi asosida qaror chiqarmaydi.

Har bir sahna o'nlab signallar bo'yicha baholanadi.

Yakuniy Viral Score barcha signallarning umumiy natijasidir.

Formula konseptual ko'rinishda:

Viral Score =
Visual +
Audio +
Emotion +
Dialogue +
Motion +
Curiosity +
Replay +
Hook +
Context

---

# Analysis Pipeline

Har bir video quyidagi bosqichlarda tahlil qilinadi:

1. Video Loading
2. Scene Detection
3. Keyframe Extraction
4. Motion Analysis
5. Face Detection
6. Emotion Detection
7. Audio Analysis
8. Whisper Transcription
9. Dialogue Analysis
10. Suspense Detection
11. Hook Detection
12. Viral Scoring
13. Ranking
14. Preview Generation

Har bir bosqich mustaqil modul sifatida ishlaydi.

---

# Brain Philosophy

AI hech qachon:

"Bu sahna yaxshi."

deb o'ylamaydi.

AI quyidagicha fikrlaydi:

"Bu sahna odamni videoni oxirigacha ko'rishga majbur qiladimi?"

---

# Viral Signals

Har bir sahna quyidagi omillar bo'yicha baholanadi.

## Visual Impact

Baholanadi:

* yorqin kadr
* keskin kamera almashishi
* katta obyekt
* yaqin plan
* portlash
* olov
* qurol
* qonunbuzarlik emas, balki vizual intensivlik
* maxsus effektlar
* kontrast

---

## Motion

Baholanadi:

* yugurish
* urush
* jang
* quvish
* yiqilish
* sakrash
* tez harakat

Statik sahnalar pastroq ball oladi.

---

## Emotion

Yuz ifodalari:

* qo'rquv
* hayrat
* g'azab
* yig'i
* kulish
* shok

Kuchli emotsiya yuqori ball beradi.

---

## Audio Energy

Baholanadi:

* ovoz balandligi
* musiqa kulminatsiyasi
* portlash
* qichqiriq
* dramatik pauza
* keskin sukut

---

## Dialogue Power

Whisper matni asosida:

AI qidiradi:

* mashhur iboralar
* tahdid
* sevgi izhori
* sir ochilishi
* kulgili gap
* motivatsion jumla
* keskin dialog

---

## Curiosity

Instagram uchun eng muhim signal.

Savol:

Tomoshabin keyin nima bo'lishini bilishni xohlaydimi?

Agar javob "ha" bo'lsa,

Curiosity Score oshadi.

---

## Hook Potential

Dastlabki 3 soniya baholanadi.

Hook quyidagilar bilan kuchayadi:

* baland ovoz
* tez harakat
* kutilmagan obraz
* savol
* hayrat
* xavf

---

## Replay Value

AI taxmin qiladi:

"Odam bu videoni yana ko'radimi?"

Replay ehtimoli yuqori bo'lsa,

ball oshadi.

---

## Context Independence

Ideal Reel filmni bilmasdan ham tushunarli bo'lishi kerak.

Shuning uchun:

Mustaqil ishlaydigan sahnalar ustunlik oladi.

---

# Negative Signals

Quyidagilar ballni kamaytiradi.

* uzoq jimlik
* juda qorong'i sahna
* uzun dialog
* harakatsizlik
* bir xil kadr
* titroq kamera
* sifatsiz audio
* tushunarsiz voqea

---

# Category Detection

Har bir sahna bitta yoki bir nechta kategoriya oladi.

Misollar:

* Jang
* Dramatik
* Hissiy
* Plot Twist
* Komediya
* Romantika
* Sirli
* Qo'rqinchli
* Motivatsion
* Epik
* Hayratlanarli

---

# Viral Score

Har bir sahna:

0–100 oralig'ida baholanadi.

Misol:

Visual...........91

Motion...........88

Emotion..........94

Dialogue.........82

Curiosity........97

Replay...........89

Hook.............95

Overall..........92

---

# Ranking

Barcha sahnalar Viral Score bo'yicha saralanadi.

Administrator faqat TOP natijalarni ko'radi.

Masalan:

TOP 5

yoki

TOP 10

---

# Buffer Rule

AI topgan vaqt oralig'i avtomatik kengaytiriladi.

Misol:

AI:

00:34:17
↓

00:34:31

Natija:

00:34:14

↓

00:34:34

Ya'ni:

3 soniya oldin

*

3 soniya keyin

Agar video boshi yoki oxiriga yaqin bo'lsa,

buffer xavfsiz tarzda qisqartiriladi.

---

# Duplicate Protection

O'xshash sahnalar alohida ko'rsatilmaydi.

Masalan:

00:10:12

00:10:15

00:10:18

Bir xil voqea bo'lsa,

AI ularni bitta kandidatga birlashtiradi.

---

# Confidence

Har bir tavsiya ishonchlilik darajasiga ega.

Masalan:

Confidence

96%

Past Confidence bo'lgan sahnalar administratorga alohida belgilanadi.

---

# Explainability

AI har doim sababini yozadi.

Masalan:

Kategoriya:

Plot Twist

Sabab:

* kuchli emotsiya;
* dialog kulminatsiyasi;
* yuqori curiosity;
* kuchli hook;
* qayta ko'rish ehtimoli yuqori.

---

# Learning Ready

Kelajakda AI quyidagilar orqali yaxshilanishi mumkin:

* administrator tanlovlari;
* Instagram statistikasi;
* ko'rish davomiyligi;
* ulashishlar soni;
* izohlar;
* saqlab qo'yishlar.

Buning uchun arxitektura boshidan tayyor bo'lishi kerak.

---

# Final Rule

AI ning maqsadi:

Eng chiroyli sahnani topish emas.

Eng ko'p odamni Telegram kanaliga olib keladigan sahnani topish.
