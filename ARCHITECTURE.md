# ARCHITECTURE.md

# System Architecture

## Overview

Instagram Reels Finder AI modulli (Modular Architecture) tamoyili asosida quriladi.

Har bir modul faqat bitta vazifani bajaradi.

Modullar o'zaro faqat aniq belgilangan interfeyslar orqali muloqot qiladi.

Bu arxitektura kelajakda yangi AI algoritmlari yoki texnologiyalarni qo'shishni osonlashtiradi.

---

# High-Level Flow

```text
Telegram Video
        │
        ▼
Download Manager
        │
        ▼
Video Validator
        │
        ▼
Analysis Pipeline
        │
 ┌──────┼───────────────┐
 ▼      ▼               ▼
Scene   Audio        Frames
Detect  Extract      Extract
 │        │              │
 ▼        ▼              ▼
Motion  Whisper     OpenCV
 │        │              │
 └──────┬───────────────┘
        ▼
Feature Collector
        ▼
Viral Scoring Engine
        ▼
Ranking Engine
        ▼
Preview Generator
        ▼
Scene Selector
        ▼
Video Cutter
        ▼
Telegram Sender
```

---

# Folder Structure

```text
project/

bot/
    handlers/
    callbacks/
    middlewares/
    filters/
    keyboards/

core/
    analyzer/
    scorer/
    detector/
    preview/
    cutter/
    whisper/
    ffmpeg/
    opencv/

services/
    telegram/
    download/
    progress/
    cleanup/

utils/
    logger/
    config/
    validators/
    helpers/

temp/

logs/

main.py
```

---

# Layer Responsibilities

## Bot Layer

Faqat Telegram bilan ishlaydi.

Vazifalari:

* handler
* callback
* message
* keyboard
* progress
* edit_message

Bu qatlam AI haqida hech narsa bilmaydi.

---

## Service Layer

Jarayonlarni boshqaradi.

Masalan:

Download

Progress

Cleanup

Temp

Logger

Bu qatlam Telegram va AI orasidagi ko'prik hisoblanadi.

---

## Core Layer

Loyihaning yuragi.

Bu yerda:

AI

Whisper

FFmpeg

OpenCV

Scene Detection

Viral Score

joylashadi.

---

## Utils

Yordamchi funksiyalar.

Masalan:

format_time()

bytes_to_mb()

safe_delete()

generate_filename()

---

# Pipeline

Pipeline qat'iy ketma-ketlikda ishlaydi.

Download

↓

Validate

↓

Extract Metadata

↓

Scene Detection

↓

Frame Analysis

↓

Audio Extraction

↓

Whisper

↓

Feature Collection

↓

Scoring

↓

Ranking

↓

Preview

↓

Selection

↓

Cut

↓

Cleanup

---

# Download Manager

Vazifasi:

Telegram videoni yuklash.

Tekshiradi:

format

hajm

davomiylik

buzilgan emasligini

---

# Scene Detection Module

Video segmentlarga bo'linadi.

Har bir segment:

boshlanish

tugash

davomiylik

ID

oladi.

Bu hali AI emas.

Faqat segmentatsiya.

---

# Frame Analyzer

OpenCV ishlatadi.

Har segment uchun:

asosiy frame

rang

harakat

kamera almashishi

yorqinlik

kontrast

aniqlanadi.

---

# Audio Analyzer

Audio alohida ajratiladi.

Baholanadi:

ovoz balandligi

pauzalar

keskin o'zgarishlar

musiqa

shovqin

---

# Whisper Module

Audio matnga aylantiriladi.

Natija:

Timestamp

↓

Text

↓

Language

↓

Confidence

---

# Feature Collector

Barcha modullardan kelgan natijalarni bitta obyektga yig'adi.

Misol:

SceneFeatures

Visual

Motion

Dialogue

Emotion

Hook

Curiosity

Replay

Duration

---

# Viral Scoring Engine

Faqat bitta vazifa:

Feature

↓

Viral Score

↓

Reason

↓

Confidence

---

# Ranking Engine

Natijalarni saralaydi.

Masalan:

TOP 5

TOP 10

TOP 20

---

# Preview Generator

Original videodan:

past sifatli

tez render

preview yaratadi.

Preview faqat tanlash uchun.

---

# Cutter

Administrator tanlagandan keyin ishlaydi.

Original video:

copy mode

orqali kesiladi.

Maksimal sifat saqlanadi.

---

# Buffer Manager

Kesishdan oldin:

Start

↓

-3 sec

End

↓

+3 sec

Agar video chegarasidan chiqsa,

avtomatik to'g'rilanadi.

---

# Cleanup Manager

Jarayon tugagach:

preview

frame

wav

cache

temp

o'chiriladi.

---

# Progress Manager

Progress faqat bitta message orqali boshqariladi.

Har safar:

edit_message_text()

ishlatiladi.

Yangi xabar yuborilmaydi.

---

# Cancel Manager

Har uzun jarayon:

Cancellation Token

tekshiradi.

Administrator:

Bekor qilish

bossa,

jarayon xavfsiz to'xtatiladi.

---

# Error Flow

Har modul:

Exception

ushlamaydi.

Xatolik yuqoriga uzatiladi.

Faqat Error Handler foydalanuvchiga xabar beradi.

Bu barcha xatoliklarni yagona usulda boshqarishni ta'minlaydi.

---

# Logging

Har modul:

INFO

DEBUG

WARNING

ERROR

yozadi.

Loglar:

logs/

papkasida saqlanadi.

---

# Configuration

Barcha sozlamalar:

config.py

orqali boshqariladi.

Masalan:

ADMIN_ID

TEMP_PATH

BUFFER_SECONDS

PREVIEW_LENGTH

MAX_VIDEO_SIZE

MAX_RESULTS

WHISPER_MODEL

LOG_LEVEL

---

# Dependency Direction

Qoidalar:

Bot

↓

Services

↓

Core

↓

Utils

Hech qachon teskari bog'lanish bo'lmaydi.

Masalan:

Core Telegram haqida bilmaydi.

Bot Whisper haqida bilmaydi.

---

# Scalability

Kelajakda quyidagilarni qo'shish mumkin:

GPU

OpenAI

YOLO

Face Recognition

LLM Analysis

Subtitle AI

Instagram Analytics

Arxitektura qayta yozilmaydi.

Faqat yangi modul ulanadi.

---

# Final Architecture Rule

Har bir modul almashtirilishi mumkin bo'lishi kerak.

Masalan:

Bugun Whisper.

Ertaga boshqa Speech-to-Text.

Kodning qolgan qismi o'zgarmasligi kerak.

Bu Modular Architecture ning asosiy maqsadidir.
