# PRD.md

# Product Requirements Document

## Project Name

Instagram Reels Finder AI

---

# Product Goal

Telegram orqali yuborilgan filmni avtomatik tahlil qilib, Instagram Reels uchun eng yuqori viral potensialga ega sahnalarni topish va administratorga tanlash imkoniyatini beruvchi professional Telegram bot.

---

# Target User

Hozirgi versiyada yagona foydalanuvchi mavjud.

Administrator.

Oddiy foydalanuvchilar botdan foydalana olmaydi.

---

# Supported Platform

Telegram Bot

---

# Supported Operating System

Windows

(Linux va macOS keyinchalik qo'llab-quvvatlanishi mumkin.)

---

# Working Mode

Lokal kompyuter.

Internet faqat Telegram API uchun ishlatiladi.

Barcha AI tahlili lokal bajariladi.

---

# Authentication

Bot ishga tushganda:

Faqat ADMIN_ID tekshiriladi.

Boshqa foydalanuvchilar:

"Kirish taqiqlangan."

xabari oladi.

Hech qanday boshqa menyu ochilmaydi.

---

# Main Menu

Bot ochilganda:

📥 Film yuborish

📂 Faol jarayon

⚙️ Sozlamalar

ℹ️ Yordam

---

# Workflow

## Step 1

Administrator filmni Telegram orqali Forward qiladi.

Bot:

Videoni tekshiradi.

---

## Step 2

Bot quyidagilarni ko'rsatadi:

Nomi

Davomiyligi

Hajmi

Format

Tasdiqlaysizmi?

Inline tugmalar:

✅ Boshlash

❌ Bekor qilish

---

## Step 3

Tasdiqlansa,

Bot videoni yuklaydi.

Progress xabari:

0%

↓

100%

Har safar edit_message orqali yangilanadi.

Yangi xabar yuborilmaydi.

---

## Step 4

Video yuklab bo'lingach:

AI tahlili boshlanadi.

Progress:

Video tayyorlanmoqda...

↓

Scene Detection...

↓

Audio ajratilmoqda...

↓

Whisper...

↓

Visual Analysis...

↓

Ranking...

↓

Preview...

↓

Tayyor.

Har bosqich bitta xabar ichida edit qilinadi.

---

# Analysis Result

Bot:

TOP sahnalarni chiqaradi.

Har biri uchun:

Preview

Kategoriya

Viral Score

Confidence

Boshlanish vaqti

Tugash vaqti

Davomiyligi

Sababi

---

# Scene Card

Misol:

Plot Twist

92/100

Confidence: 95%

00:34:14

↓

00:34:34

Sabab:

• Kuchli dialog

• Kutilmagan burilish

• Yuqori Hook

• Replay ehtimoli yuqori

Inline:

▶ Preview

✂ Kesish

➡ Keyingisi

---

# Preview

Preview:

Past sifatli.

Qisqa.

Faqat tanlash uchun.

Original video o'zgarmaydi.

---

# Cutting

Administrator:

✂ Kesish

ni bossa,

Bot:

Original videodan

Buffer bilan

aniq kesadi.

Formula:

Start - 3 sec

End + 3 sec

---

# Output

Natija:

MP4

Original sifat

Original FPS

Original Audio

---

# Temporary Files

Jarayon tugaganda:

Preview

Audio

Frame

Temp

Cache

Avtomatik o'chiriladi.

---

# Cancel

Har uzun jarayonda:

Bekor qilish

tugmasi mavjud.

Bekor qilinsa:

Jarayon to'xtaydi.

Temp fayllar o'chadi.

Bot bosh menyuga qaytadi.

---

# Back

Kerakli joylarda:

⬅ Ortga

tugmasi mavjud.

---

# Error Handling

Har bir xatolik:

O'zbek tilida.

Misollar:

Video yuklab bo'lmadi.

Audio ajratilmadi.

Whisper ishlamadi.

FFmpeg topilmadi.

Diskda joy yetarli emas.

Video buzilgan.

Jarayon bekor qilindi.

---

# Progress Rules

Progress:

Doimo bitta xabar.

Faqat edit qilinadi.

Spam bo'lmaydi.

---

# Chat Cleanliness

Keraksiz xabarlar:

Avtomatik o'chiriladi.

Faqat kerakli natijalar qoladi.

---

# Logging

Ichki log:

DEBUG

INFO

WARNING

ERROR

Administratorga faqat tushunarli xabar ko'rsatiladi.

---

# Performance Requirements

CPU uchun optimallashtirilgan.

RAM isrof qilinmaydi.

Parallel ishlov berish imkon qadar ishlatiladi.

Bir vaqtning o'zida faqat bitta analiz.

---

# Security

Faqat administrator.

Temp fayllar saqlanmaydi.

Original video o'zgarmaydi.

Tashqi serverga video yuborilmaydi.

---

# Future Features

OpenAI Analysis

Ko'p administrator

GPU Acceleration

Subtitle Analysis

Instagram Trend Analysis

Batch Processing

Auto Reel Generator

Learning Model

---

# Out of Scope

Quyidagilar ushbu versiyada YO'Q:

Foydalanuvchi registratsiyasi

Database

TMDB

Cloud Storage

Railway

Docker

Web Panel

Mobil ilova

Avtomatik Instagram joylash

---

# Product Success

Mahsulot muvaffaqiyatli hisoblanadi agar:

Administrator filmni to'liq ko'rishga majbur bo'lmasa.

AI eng yaxshi sahnalarni topa olsa.

Preview tez tayyorlansa.

Kesilgan video sifatini yo'qotmasa.

Bot tez ishlasa.

Interfeys sodda va tushunarli bo'lsa.

Chat doimo toza qolsa.

Bot har doim javob qaytarsa.
