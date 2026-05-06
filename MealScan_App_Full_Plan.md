# NutriLens — AI Meal Scan App: Full Professional Build Plan

> A comprehensive analysis and development blueprint for building a next-generation, offline-first, regionally intelligent AI diet tracking application.

---

## Table of Contents

1. [App Concept & Vision](#1-app-concept--vision)
2. [Advantages of This App Category](#2-advantages-of-this-app-category)
3. [Disadvantages & Current Gaps](#3-disadvantages--current-gaps)
4. [What Existing Apps Have Done So Far](#4-what-existing-apps-have-done-so-far)
5. [Technologies Used by Existing Apps](#5-technologies-used-by-existing-apps)
6. [Technologies We Will Adopt + New Technologies to Add](#6-technologies-we-will-adopt--new-technologies-to-add)
7. [Key Improvements Over Existing Apps](#7-key-improvements-over-existing-apps)
8. [Full App Architecture](#8-full-app-architecture)
9. [Feature Breakdown](#9-feature-breakdown)
10. [Database & Data Strategy](#10-database--data-strategy)
11. [AI/ML Model Strategy](#11-aiml-model-strategy)
12. [Offline-First Implementation Plan](#12-offline-first-implementation-plan)
13. [Regional Food Intelligence Strategy](#13-regional-food-intelligence-strategy)
14. [UI/UX Design Principles](#14-uiux-design-principles)
15. [Development Phases & Roadmap](#15-development-phases--roadmap)
16. [Tech Stack Summary](#16-tech-stack-summary)
17. [Monetization Strategy](#17-monetization-strategy)
18. [Security & Privacy](#18-security--privacy)
19. [Testing Strategy](#19-testing-strategy)
20. [Launch Strategy](#20-launch-strategy)

---

## 1. App Concept & Vision

**App Name (Working Title):** NutriLens

**Core Proposition:**
An offline-first, AI-powered meal scanning and nutrition tracking app that works accurately for regional cuisines — starting with South Asian / Indian food — without requiring a constant internet connection.

**The Problem It Solves:**
- Existing apps are cloud-dependent, breaking in low/no connectivity areas
- Global apps (MyFitnessPal, Cal AI) fail on regional foods like biryani, dosa, sambar, roti sabzi
- Manual logging is tedious and users quit within weeks
- Invisible ingredients (cooking oil, masala, ghee) are never counted
- No app currently offers strong offline + regional accuracy simultaneously

**Target Users:**
- Health-conscious individuals in India, Southeast Asia, Middle East, and African markets
- Fitness enthusiasts who eat regional home-cooked meals
- People with medical dietary requirements (diabetes, hypertension, PCOS)
- Users in semi-urban and rural areas with limited mobile data
- Gym-goers tracking protein/macros on Indian diets

**Vision Statement:**
> Build the most accurate, accessible, and culturally intelligent nutrition tracker in the world — one that works whether you're in a metro with 5G or a village with no signal.

---

## 2. Advantages of This App Category

### For Users
| Advantage | Detail |
|-----------|--------|
| **Speed** | Logging a meal takes 3–5 seconds vs 5–10 minutes manually |
| **Consistency** | Low friction = higher habit formation rate |
| **Accuracy** | AI portion estimation beats human guessing |
| **Awareness** | Users learn calorie density of foods they never tracked |
| **Holistic tracking** | Macros + micros + meal timing + patterns all in one |
| **Motivation** | Visual streaks, progress graphs keep users engaged |
| **Medical utility** | Diabetics, hypertensive patients can track glycemic/sodium impact |

### For the Market
- Massive underserved market: 1.4B people in India alone, with almost no India-first nutrition app
- Diet tracking app market globally projected to exceed $15B by 2027
- Rising fitness consciousness post-pandemic across South/Southeast Asia
- Affordable smartphones + cheap data in target markets = large addressable audience
- No dominant player for regional food — the category is wide open

---

## 3. Disadvantages & Current Gaps

### Technical Disadvantages
| Disadvantage | Impact |
|--------------|--------|
| **Cloud dependency** | App unusable without internet; dead in rural areas |
| **Western food bias** | 60–80% of training data is American/European food |
| **Invisible ingredient blindness** | Cooking oil, ghee, masala amounts never captured |
| **Portion size errors** | 2D image estimation can be off by 30–50% without depth data |
| **Mixed dish confusion** | Dal rice, biryani, curry are misidentified or lumped |
| **Model staleness** | On-device models go stale quickly without update pipelines |
| **High battery usage** | Cloud upload + inference drains battery during every scan |

### User Experience Disadvantages
| Disadvantage | Impact |
|--------------|--------|
| **Paywall fatigue** | Key features locked behind $10–20/month subscriptions |
| **No regional language support** | Apps are English-only; excluded non-English speakers |
| **No cooking context** | "Fried" vs "steamed" same food = completely different calories; not captured |
| **No household serving size** | Apps use grams; Indian users think in "katori", "ladle", "roti" |
| **No family/shared meal mode** | Can't split a shared dish between two people |
| **Poor camera UX** | Poor guidance for lighting, angle — results in failed scans |

### Business/Data Disadvantages
- Training data for Indian/Asian foods is sparse and poorly labelled
- Ground truth calorie data for Indian homemade recipes varies enormously by region and cook
- User corrections are siloed per-app and not shared to improve models
- GDPR and local data regulations add compliance complexity

---

## 4. What Existing Apps Have Done So Far

### MyFitnessPal
- **Founded:** 2005, acquired by Under Armour (2015), now independent
- **Database:** 18M+ food items (mostly user-generated)
- **AI Scan:** Partnered with Passio.ai for computer vision meal scan (Premium only, English only)
- **Barcode:** Locked behind Premium paywall since 2023
- **Offline:** Basic logging only; AI scan requires cloud
- **Regional support:** Minimal — heavily Western-centric database
- **Strength:** Largest food database in the world
- **Weakness:** Accuracy of user-submitted entries is poor; expensive; no regional AI

### Cal AI
- **Founded:** ~2022; viral through fitness influencers
- **AI Scan:** Fast photo → calories in under 2 seconds (cloud inference)
- **Depth sensor:** Uses iPhone depth sensor for volume estimation
- **Accuracy:** Self-reported 92%; user reviews show systematic undercounting (50–76% errors on some foods)
- **Offline:** None — fully cloud-dependent
- **Regional support:** None
- **Strength:** Speed, viral UX, clean interface
- **Weakness:** Accuracy is inconsistent; subscription required; no offline; fails on non-Western food

### SnapCalorie
- **Founded by:** Ex-Google AI researchers (Google Lens / Cloud Vision founders)
- **Technology:** Nutrition5k dataset (5,000 dishes, every ingredient weighed); LiDAR depth sensing; USDA-verified database
- **Accuracy:** 16% mean error rate (peer-reviewed, published)
- **Offline:** Partial — some cached data, but AI scan is cloud-based
- **Regional support:** Western-centric; limited Indian food coverage
- **Strength:** Most scientifically rigorous; free; excellent accuracy for Western food
- **Weakness:** Training data is Western; limited regional support; LiDAR only on iPhone Pro

### HealthifyMe
- **Founded:** 2012, India
- **Database:** 1 lakh+ (100,000+) Indian food items
- **AI Scan:** Ria AI coach; photo logging added recently
- **Offline:** Limited
- **Regional support:** Best Indian food coverage among existing apps
- **Strength:** Indian database depth; dietitian access; regional focus
- **Weakness:** Photo AI accuracy still weak for complex dishes; expensive premium; not offline-first

### Cronometer
- **Founded:** 2005
- **Database:** 1.2M items (verified, peer-reviewed sources)
- **AI Scan:** Added in 2025; accuracy varies
- **Offline:** Basic tracking works offline
- **Strength:** Best micronutrient tracking (84 nutrients); clean verified data
- **Weakness:** No meaningful AI scan; no regional food; primarily Western

### Lose It!
- **Founded:** 2008
- **AI Scan:** Decent food recognition; clean UX
- **Offline:** Basic features offline
- **Strength:** Clean design; good free tier; barcode scanning
- **Weakness:** No regional food; no meaningful offline AI

---

## 5. Technologies Used by Existing Apps

### AI / Machine Learning
| Technology | Used By | Purpose |
|-----------|---------|---------|
| **Convolutional Neural Networks (CNN)** | All apps | Image classification — identifying food type |
| **YOLO (You Only Look Once)** | Research / SnapCalorie | Multi-object detection in a single image |
| **MobileNet / EfficientNet** | Mobile apps | Lightweight CNN for on-device inference |
| **Google Cloud Vision API** | MyFitnessPal (via Passio) | Cloud-based food recognition |
| **Passio.ai Nutrition AI SDK** | MyFitnessPal | Patented food recognition + database mapping |
| **Depth / LiDAR sensing** | SnapCalorie, Cal AI | 3D volume estimation for portion sizing |
| **Transfer Learning** | All AI apps | Fine-tuning ImageNet-pretrained models on food datasets |
| **Nutrition5k Dataset** | SnapCalorie | 5,000 real dishes with full nutritional ground truth |
| **Food-101 Dataset** | Research baseline | 101 food categories, 101,000 images |

### Mobile Frameworks
| Technology | Used By | Purpose |
|-----------|---------|---------|
| **Swift / SwiftUI** | iOS apps | Native iOS development |
| **Kotlin / Jetpack Compose** | Android apps | Native Android development |
| **React Native** | Some apps | Cross-platform (faster, less optimal) |
| **Flutter** | Newer apps | Cross-platform with near-native performance |
| **CoreML** | iOS apps | Apple's on-device ML framework |
| **TensorFlow Lite (TFLite)** | Android apps | Google's on-device ML framework |
| **ML Kit** | Cross-platform | Google's mobile ML SDK (barcode, text, object detection) |

### Backend & Infrastructure
| Technology | Used By | Purpose |
|-----------|---------|---------|
| **AWS / GCP** | Most apps | Cloud inference, model hosting, database |
| **PostgreSQL / MySQL** | All apps | Relational database for food and user data |
| **Redis** | High-traffic apps | Caching frequent food lookups |
| **REST APIs** | All apps | Communication between app and server |
| **Firebase** | Mobile-first apps | Auth, analytics, push notifications |

### Data Sources
| Source | Used By | Purpose |
|--------|---------|---------|
| **USDA FoodData Central** | SnapCalorie, Cronometer | Verified nutritional ground truth |
| **OpenFoodFacts** | Multiple apps | Open-source barcode / packaged food DB |
| **User-generated entries** | MyFitnessPal | Crowd-sourced food database (quality varies) |
| **Restaurant APIs** | Lose It!, MFP | Restaurant menu nutrition data |

---

## 6. Technologies We Will Adopt + New Technologies to Add

### Technologies to Adopt from Existing Apps

| Technology | Why Adopt It |
|-----------|-------------|
| **TensorFlow Lite + CoreML** | Proven on-device inference; 90% model size reduction via quantization |
| **YOLO-based multi-food detection** | Best-in-class for detecting multiple items on a single plate |
| **Transfer learning on EfficientNetV2** | Strong accuracy with small model footprint |
| **USDA FoodData Central** | Gold standard for nutritional ground truth |
| **OpenFoodFacts** | Free, open, large barcode database |
| **Firebase Auth + Analytics** | Fast, reliable auth and usage analytics |
| **Depth/LiDAR sensing** | Use where available (iPhone Pro, Android depth sensors) |
| **Barcode scanning (ML Kit)** | Offline barcode reads via on-device OCR |

### New Technologies to Add (Our Differentiators)

#### 1. Regional Food Dataset — Built from Scratch
- Curate a proprietary dataset of 2,000+ Indian/South Asian dishes with:
  - Standardized recipe nutritional profiles
  - Regional variants (Tamil Nadu sambar ≠ Andhra sambar — different calorie density)
  - Cooking method tags (steamed / fried / pressure-cooked / roasted)
  - Household serving size units: katori, ladle, tablespoon, roti count
- Partner with ICMR (Indian Council of Medical Research) nutritional tables as ground truth

#### 2. Cooking Context Engine
- A pre-scan "context prompt" that asks:
  - "Was this fried, steamed, or roasted?"
  - "Did you add oil/ghee? How much — a drizzle, a tablespoon, or more?"
  - "Home-cooked or restaurant?"
- These 2–3 quick taps can reduce calorie estimation error by 30–40% for Indian food

#### 3. Invisible Ingredient Estimator
- A probabilistic model that adds a cooking-method-based calorie correction:
  - Tadka/tempering = +80–120 kcal estimate
  - Deep frying = +60% calorie multiplier on surface area
  - Pressure-cooked dal = no oil correction needed
- This alone beats every existing app for Indian food accuracy

#### 4. Household Portion Unit System
- A local unit database mapping Indian units to grams:
  - 1 standard katori ≈ 150 ml / ~200g for dal
  - 1 medium roti ≈ 35g raw / ~30g cooked
  - 1 ladle of curry ≈ 80–100g
  - 1 cup of rice (cooked) ≈ 185–200g
- Users log in their natural language — "2 rotis and 1 katori dal" — not in grams

#### 5. On-Device Federated Learning (Phase 3+)
- User corrections on misidentified foods train a personalized local model
- Aggregated corrections (privacy-safe, never raw data) improve the global model
- Framework: TensorFlow Federated or Apple's Federated Learning APIs
- This means the app gets smarter for every user without sending personal data to servers

#### 6. Meal Photo Queue (Offline Scan Holding)
- When offline, the app captures and stores the photo + metadata locally
- On reconnection, queued photos are processed by the cloud model in the background
- Results sync back and notify the user: "Your lunch scan is ready"
- Works like an email outbox — nothing is lost when offline

#### 7. Regional Language Support
- Tamil, Hindi, Telugu, Kannada, Malayalam UI translations
- Voice logging in regional languages via on-device speech recognition (Whisper.cpp or Apple/Google on-device STT)
- Food search in regional script: "இட்லி" finds idli correctly

#### 8. Glycemic & Diabetic Intelligence Layer
- Tag foods with Glycemic Index (GI) and Glycemic Load (GL)
- Special mode for diabetic users: flags high-GI meals; suggests lower-GI swaps
- Tracks cumulative daily GL — particularly useful for Type 2 diabetes management
- Common need in India (highest diabetic population in the world)

#### 9. Family / Shared Meal Mode
- Scan a shared dish (e.g., a pot of biryani)
- Divide by number of portions served
- Each person in the household logs their share
- Useful for family-style meals which are universal in Indian households

#### 10. AR Plate Guide (Phase 2+)
- Augmented Reality overlay guides the user to optimal scan position
- "Move camera higher" / "Separate the items" / "Better lighting needed"
- Reduces failed/inaccurate scans dramatically through real-time feedback

---

## 7. Key Improvements Over Existing Apps

| Area | Existing Apps | Our Improvement |
|------|--------------|-----------------|
| **Offline capability** | Cloud-only AI scan | Full on-device model for common foods; queue for complex scans |
| **Regional food** | Western-centric | 2,000+ Indian dishes with regional variants |
| **Portion units** | Grams only | Katori, roti, ladle, cup — natural Indian units |
| **Cooking context** | Not captured | Pre-scan cooking method + oil/ghee context prompt |
| **Invisible ingredients** | Ignored | Probabilistic oil/masala calorie correction |
| **Language** | English only | Tamil, Hindi, Telugu, Kannada, Malayalam |
| **Connectivity** | Hard-required | Offline-first; cloud is enhancement not requirement |
| **Diabetic support** | Generic | GI/GL tracking, high-GI alerts, swap suggestions |
| **Family meals** | Single-person | Shared dish splitting |
| **Cost** | $10–20/month | Free core; affordable regional premium |
| **Accuracy on Indian food** | Poor–moderate | Purpose-built dataset + cooking context = significantly better |
| **Battery/data usage** | High (constant cloud) | Low (on-device inference for common meals) |

---

## 8. Full App Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     MOBILE APP                          │
│                                                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │  Camera /    │  │  Voice       │  │  Manual      │  │
│  │  AR Guide    │  │  Logging     │  │  Entry       │  │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  │
│         │                 │                 │           │
│         └─────────────────┴─────────────────┘           │
│                           │                             │
│              ┌────────────▼─────────────┐               │
│              │   LOCAL INFERENCE ENGINE │               │
│              │  TFLite / CoreML model   │               │
│              │  ~500 regional foods     │               │
│              │  Runs fully offline      │               │
│              └────────────┬─────────────┘               │
│                           │                             │
│         ┌─────────────────┼──────────────────┐          │
│         │                 │                  │           │
│  ┌──────▼──────┐  ┌───────▼──────┐  ┌───────▼──────┐   │
│  │  Local Food │  │  Cooking     │  │  Portion     │   │
│  │  DB Cache   │  │  Context     │  │  Unit        │   │
│  │  (SQLite)   │  │  Engine      │  │  Converter   │   │
│  └─────────────┘  └──────────────┘  └──────────────┘   │
│                                                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │         OFFLINE QUEUE / SYNC MANAGER             │   │
│  │  Holds unprocessed scans; syncs when online      │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────┬───────────────────────────┘
                              │ (when online)
                              │
┌─────────────────────────────▼───────────────────────────┐
│                      CLOUD LAYER                        │
│                                                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │  Large Model │  │  Food DB     │  │  Federated   │  │
│  │  Inference   │  │  API         │  │  Model       │  │
│  │  (complex    │  │  (18M+       │  │  Updater     │  │
│  │   dishes)    │  │   items)     │  │              │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
│                                                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │  User Data   │  │  Analytics   │  │  Model       │  │
│  │  Sync        │  │  Engine      │  │  Training    │  │
│  │  (encrypted) │  │              │  │  Pipeline    │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 9. Feature Breakdown

### Core Features (MVP — Phase 1)

#### Meal Scanning
- [ ] Photo scan with on-device model (offline)
- [ ] Multi-food detection on a single plate
- [ ] Cooking context prompt (fried/steamed/roasted + oil/ghee)
- [ ] Portion size in Indian units (katori, roti, ladle, cup)
- [ ] Edit / correct AI predictions
- [ ] Barcode scan for packaged foods (offline-capable via ML Kit)
- [ ] Manual food search (offline via local DB cache)

#### Nutrition Display
- [ ] Calories, protein, carbs, fat (macros)
- [ ] Fiber, sugar, sodium, cholesterol
- [ ] Glycemic Index tag per food
- [ ] Daily summary dashboard
- [ ] Meal timeline (breakfast / lunch / dinner / snacks)

#### User Profile & Goals
- [ ] Age, gender, weight, height, activity level
- [ ] Goal selection: weight loss / muscle gain / maintenance / diabetic management / PCOS
- [ ] Custom calorie and macro targets
- [ ] Daily water intake tracking

#### Offline Core
- [ ] All basic tracking works without internet
- [ ] Local SQLite database with 2,000+ Indian foods
- [ ] Offline barcode cache (top 50,000 products)
- [ ] Scan queue for offline photos → sync on reconnect

---

### Enhanced Features (Phase 2)

#### AI Improvements
- [ ] Cloud inference for complex/rare dishes (when online)
- [ ] Invisible ingredient estimator (oil/ghee/masala calorie correction)
- [ ] Personal learning — app remembers your frequent meals
- [ ] Voice logging in English and Indian languages
- [ ] AR camera guide for optimal scan angle and lighting

#### Insights & Intelligence
- [ ] Weekly nutrition trends and pattern analysis
- [ ] High-GI meal alerts for diabetic users
- [ ] Low-protein day alerts for muscle-builders
- [ ] Smart swap suggestions ("Try steamed instead of fried")
- [ ] Eating time pattern analysis (late-night eating, skipped meals)

#### Social & Family
- [ ] Shared dish mode (split a meal between N people)
- [ ] Family profile management (track nutrition for multiple household members)
- [ ] Meal sharing / recipe logging

---

### Premium Features (Phase 3)

#### Advanced Tracking
- [ ] 50+ micronutrient tracking (vitamins, minerals, amino acids)
- [ ] Federated on-device learning (personalized model)
- [ ] Restaurant menu integration (Swiggy/Zomato menu parsing)
- [ ] Integration with fitness trackers (Google Fit, Apple Health, Fitbit, Garmin)
- [ ] Blood sugar correlation for diabetic users (manual BGL log)
- [ ] Export reports (PDF/CSV for doctor consultations)

#### AI Nutritionist
- [ ] Chat-based AI nutritionist (regional diet knowledge)
- [ ] Personalized meal planning (7-day/28-day plans using foods you actually eat)
- [ ] Grocery list generation from meal plan

---

## 10. Database & Data Strategy

### Local Database (On-Device SQLite)

```sql
-- Foods table (core nutrition data)
CREATE TABLE foods (
    id           TEXT PRIMARY KEY,
    name_en      TEXT NOT NULL,
    name_ta      TEXT,  -- Tamil
    name_hi      TEXT,  -- Hindi
    name_te      TEXT,  -- Telugu
    category     TEXT,  -- "south_indian", "north_indian", "street_food", etc.
    calories     REAL,
    protein_g    REAL,
    carbs_g      REAL,
    fat_g        REAL,
    fiber_g      REAL,
    sugar_g      REAL,
    sodium_mg    REAL,
    gi_index     INTEGER,  -- Glycemic Index
    serving_unit TEXT,     -- "katori", "roti", "g", "ml"
    serving_size REAL,     -- grams equivalent per 1 serving unit
    source       TEXT,     -- "ICMR", "USDA", "verified_recipe"
    last_updated TEXT
);

-- User meals log
CREATE TABLE meal_logs (
    id           TEXT PRIMARY KEY,
    user_id      TEXT,
    food_id      TEXT,
    meal_type    TEXT,  -- "breakfast", "lunch", "dinner", "snack"
    servings     REAL,
    cooking_method TEXT,  -- "fried", "steamed", "boiled", "raw"
    oil_added    TEXT,  -- "none", "drizzle", "tablespoon", "more"
    logged_at    TEXT,
    synced       INTEGER DEFAULT 0,
    FOREIGN KEY (food_id) REFERENCES foods(id)
);

-- Offline scan queue
CREATE TABLE scan_queue (
    id           TEXT PRIMARY KEY,
    image_path   TEXT,
    meal_type    TEXT,
    cooking_context TEXT,  -- JSON of context answers
    queued_at    TEXT,
    status       TEXT   -- "pending", "processing", "done", "failed"
);
```

### Cloud Database (PostgreSQL)
- Full food database (18M+ items via USDA + OpenFoodFacts + proprietary Indian DB)
- User account data, sync records
- Model feedback logs (anonymized correction data for retraining)
- Restaurant menu integrations

### Data Sources Priority
1. **ICMR Nutritive Value of Indian Foods** — primary source for Indian dish ground truth
2. **USDA FoodData Central** — Western foods and packaged items
3. **OpenFoodFacts** — barcode / packaged product database
4. **Proprietary recipe database** — curated 2,000+ Indian dishes with regional variants
5. **Swiggy / Zomato menu API** (Phase 2) — restaurant-specific nutrition

---

## 11. AI/ML Model Strategy

### On-Device Model (Offline)

**Architecture:** EfficientNetV2-S fine-tuned → quantized to INT8 via TFLite/CoreML

**Training Data:**
- Food-101 (baseline, 101 categories)
- ETHZ Food-256 (broader categories)
- Proprietary Indian food dataset (2,000+ dishes, 50,000+ images — to be collected)
- Data augmentation: rotation, brightness, blur, partial occlusion

**Model Specs (target):**
- Size: 40–80 MB (after INT8 quantization — ~90% size reduction)
- Inference time: < 200ms on mid-range Android
- Food categories: 500–800 (top Indian + common global foods)
- Accuracy target: > 85% top-3 accuracy on Indian food test set

**Deployment:**
- iOS: CoreML (.mlpackage format)
- Android: TensorFlow Lite (.tflite format)
- OTA model updates via Wi-Fi (delta updates, not full re-download)

### Cloud Model (Online, Complex Dishes)

**Architecture:** Vision Transformer (ViT-L) or EfficientNetV2-XL
- Handles rare dishes, mixed complex meals, ambiguous inputs
- Returns top-5 predictions with confidence scores
- Falls back to this when on-device confidence < 0.65

**Portion Estimation:**
- Monocular depth estimation (MiDaS model) for non-LiDAR devices
- LiDAR volume calculation where available (iPhone Pro, select Androids)
- Reference object detection (plate diameter, fork, spoon) as scale calibration

### Cooking Context Correction Model

A lightweight regression model that adjusts calorie estimates based on:
- Cooking method (fried / steamed / baked / raw)
- Oil/ghee added (none / drizzle ≈ 5ml / 1 tbsp ≈ 15ml / heavy ≈ 30ml+)
- Home-cooked vs restaurant (restaurant = +20–40% fat assumption)

This runs entirely on-device (< 1 MB model) and applies a multiplier to the base calorie estimate.

---

## 12. Offline-First Implementation Plan

### Principle: "Offline is default; cloud is enhancement"

### Connectivity Tiers

| Tier | Connection State | App Behavior |
|------|-----------------|--------------|
| **Full offline** | No internet | On-device scan + local DB + queue photos |
| **Slow connection** | 2G / weak 3G | On-device scan + background sync queued |
| **Normal connection** | 4G / Wi-Fi | Hybrid: on-device first, cloud for ambiguous cases |
| **Strong connection** | 5G / fast Wi-Fi | Full cloud model + real-time sync |

### Offline Implementation Steps

**Step 1 — Bundle the on-device model**
- Ship the quantized TFLite/CoreML model inside the app (40–80 MB)
- Model covers 500–800 most common Indian + global foods
- Updated OTA in background when on Wi-Fi

**Step 2 — Local food database**
- SQLite database with 2,000+ Indian foods + 50,000 barcode entries
- Packaged into app at install time
- Delta updates pushed periodically (new foods, corrected nutritional values)

**Step 3 — Scan queue**
- Every scan photo is saved locally first (compressed HEIC/WebP, ~100–300 KB)
- If on-device confidence is high (> 0.80): result used immediately
- If confidence is low (< 0.65): photo enters the sync queue
- Queue processes when internet is available; user notified of results

**Step 4 — Data sync architecture**
- All user logs stored locally first (SQLite)
- Background sync pushes to cloud when connected (last-write-wins conflict resolution)
- User never waits for a network response to log a meal

**Step 5 — Progressive enhancement**
- On-device result shown instantly
- If cloud result arrives later (queued scan) and differs significantly: offer user a correction prompt
- User chooses which result to keep

---

## 13. Regional Food Intelligence Strategy

### Phase 1 — Indian Food Dataset (Launch)

**Data Collection Plan:**
- Partner with 50–100 nutritionists and home cooks across India (paid)
- Photograph 2,000+ dishes with controlled lighting and measured weights
- Cover regional variants:
  - South India: Tamil Nadu, Kerala, Karnataka, Andhra/Telangana variants
  - North India: Punjab, UP, Rajasthan, Delhi street food
  - East India: Bengal, Odisha
  - West India: Maharashtra, Gujarat
- Tag every dish with: region, cooking method, oil used, serving unit

**Nutritional Ground Truth:**
- Primary: ICMR Nutritive Value of Indian Foods (2017 edition)
- Secondary: NIN (National Institute of Nutrition) food composition tables
- Tertiary: Peer-reviewed journal articles on Indian food composition

**Serving Unit Mapping:**

| Unit | Food Context | Gram Equivalent |
|------|-------------|----------------|
| 1 katori | Dal, curry, sabzi | 150–200g |
| 1 medium roti | Wheat chapati | 28–35g |
| 1 paratha | Stuffed/plain | 60–90g |
| 1 ladle | Liquid curry, sambar | 80–100g |
| 1 cup (cooked) | Rice, poha, upma | 150–200g |
| 1 piece | Idli, vada, dosa | 40–80g |
| 1 tablespoon | Oil, ghee, chutney | 12–15g |

### Phase 2 — Southeast Asia Expansion

- Add 500+ dishes from: Sri Lanka, Bangladesh, Myanmar, Thailand, Malaysia
- Partner with local nutritionists and culinary institutes

### Phase 3 — Middle East & Africa

- Focus on Egypt, Saudi Arabia, Nigeria, Kenya
- Large populations; no nutrition app currently serves them in local food context

---

## 14. UI/UX Design Principles

### Design Philosophy
- **Speed over completeness** — a logged meal in 10 seconds beats a perfect log that takes 3 minutes
- **No friction for the core action** — scanning must be ≤ 3 taps from home screen
- **Progressive disclosure** — basic view shows calories + protein; detailed view shows all 50 nutrients
- **Culturally appropriate** — use thali imagery, katori icons, regional food photography
- **Accessible** — works in bright sunlight, readable in regional scripts, large touch targets

### Core Screens

1. **Home / Dashboard**
   - Today's calories (ring/bar), protein/carbs/fat bars
   - Meal timeline (breakfast / lunch / dinner / snack cards)
   - Streak counter and daily water tracker
   - Quick-add FAB (camera icon — primary action)

2. **Scan Screen**
   - Full-screen camera with AR guide overlay
   - Real-time food detection bounding boxes (as user frames the plate)
   - Context prompt cards (cooking method, oil added) — appear after photo taken
   - Results card: list of detected foods with servings, calories, edit button

3. **Food Detail / Edit**
   - Detected food name (editable)
   - Serving size in natural units (katori / roti / g) with slider
   - Nutritional breakdown (calories, macros, GI badge)
   - "Add invisible ingredients" toggle (oil, ghee, sugar)

4. **Search / Manual Entry**
   - Search in English or regional language (Tamil/Hindi)
   - Recent and frequent foods at top
   - Barcode scan button inline

5. **Insights / Weekly View**
   - 7-day calorie trend chart
   - Macro distribution pie chart
   - GI / diabetic health score
   - "Your eating patterns" — e.g., "You tend to skip breakfast on weekdays"

6. **Profile / Goals**
   - Personal metrics, goal, activity level
   - Language preference
   - Connected devices (Apple Health, Fitbit)
   - Offline model status + download

### Color System
- **Primary:** Deep saffron-orange `#E8593C` — evocative of Indian spices/turmeric
- **Secondary:** Leaf green `#2E7D32` — freshness, health
- **Neutral:** Warm off-white `#FAF8F5` backgrounds
- **Accent:** Gold `#F9A825` — highlights, GI badges
- **Danger:** Standard red for over-limit alerts

---

## 15. Development Phases & Roadmap

### Phase 0 — Foundation (Months 1–3)

**Team Required:** 1 iOS dev, 1 Android dev, 1 backend dev, 1 ML engineer, 1 UI/UX designer, 1 nutritionist

| Task | Owner | Duration |
|------|-------|----------|
| Define app architecture | Tech Lead | Week 1–2 |
| Set up backend (FastAPI + PostgreSQL + Redis) | Backend | Week 1–3 |
| Set up CI/CD pipeline (GitHub Actions) | DevOps | Week 2 |
| Design system and all screen wireframes | Designer | Week 1–4 |
| Integrate USDA + OpenFoodFacts + ICMR data | ML + Backend | Week 2–6 |
| Build SQLite local DB + sync layer | Backend + Mobile | Week 3–6 |
| Train baseline food classifier (Food-101 + Indian data) | ML Engineer | Week 2–8 |
| Quantize model for TFLite / CoreML | ML Engineer | Week 6–8 |
| Build camera + scan UI skeleton | Mobile Devs | Week 3–6 |
| Build cooking context prompt flow | Mobile Devs | Week 5–7 |
| Build offline scan queue | Mobile Devs | Week 6–8 |
| Unit + integration tests | All | Week 8–12 |
| Internal alpha (team + 20 beta users) | All | Week 10–12 |

---

### Phase 1 — MVP Launch (Months 4–6)

**Goal:** Closed beta with 500 users; validate accuracy on Indian food

| Task | Owner | Duration |
|------|-------|----------|
| Fix issues from alpha feedback | All | Week 1–2 |
| Expand Indian food dataset to 1,000 dishes | ML + Nutritionist | Week 1–4 |
| Implement barcode scanning (offline ML Kit) | Mobile | Week 2–3 |
| Manual search in Tamil + Hindi | Mobile | Week 3–4 |
| Build dashboard and meal timeline UI | Mobile | Week 2–4 |
| Add GI/GL tagging to food database | Nutritionist | Week 2–4 |
| Push notifications (meal reminders, streak alerts) | Mobile + Backend | Week 4–5 |
| Launch on TestFlight (iOS) + Play Store (Android) beta | All | Week 5 |
| Collect accuracy feedback from 500 beta users | PM | Week 5–8 |
| Model retraining on user correction data | ML | Week 6–8 |

---

### Phase 2 — Public Launch (Months 7–12)

**Goal:** Public launch on App Store + Play Store; 50,000 downloads in 6 months

| Task | Owner | Duration |
|------|-------|----------|
| AR camera guide overlay | Mobile | Month 7–8 |
| Voice logging (English + Hindi + Tamil) | ML + Mobile | Month 7–9 |
| Invisible ingredient estimator | ML | Month 7–8 |
| Cloud model for complex dishes | ML + Backend | Month 8–9 |
| Insights / weekly trends screen | Mobile | Month 8–9 |
| Family / shared meal mode | Mobile + Backend | Month 9–10 |
| Apple Health + Google Fit integration | Mobile | Month 9–10 |
| App Store + Play Store launch | All | Month 10 |
| Regional language UI (Tamil, Telugu, Kannada) | Mobile | Month 10–12 |
| Diabetic tracking mode | Mobile + ML | Month 11–12 |
| Swiggy / Zomato menu integration | Backend | Month 11–12 |

---

### Phase 3 — Scale & Intelligence (Year 2)

| Feature | Priority |
|---------|---------|
| Federated on-device learning | High |
| AI nutritionist chatbot (regional diet knowledge) | High |
| 7-day and 28-day meal planning | Medium |
| Micronutrient tracking (50+ nutrients) | Medium |
| Southeast Asia food expansion (Sri Lanka, Bangladesh, etc.) | High |
| Wearable integration (Garmin, Mi Band) | Medium |
| Doctor-share reports (PDF export) | High |
| Blood sugar correlation mode | Medium |
| Web app version | Low |

---

## 16. Tech Stack Summary

### Mobile
| Layer | iOS | Android |
|-------|-----|---------|
| **Language** | Swift 5.9+ | Kotlin 1.9+ |
| **UI Framework** | SwiftUI | Jetpack Compose |
| **On-device ML** | CoreML + Vision | TFLite + ML Kit |
| **Local DB** | SQLite via GRDB | SQLite via Room |
| **Camera** | AVFoundation + ARKit | CameraX + ARCore |
| **Networking** | URLSession + Combine | Retrofit + Coroutines |
| **Analytics** | Firebase Analytics | Firebase Analytics |
| **Auth** | Firebase Auth | Firebase Auth |

### Backend
| Layer | Technology |
|-------|-----------|
| **API Framework** | FastAPI (Python) |
| **Database** | PostgreSQL 15 |
| **Cache** | Redis |
| **Object Storage** | AWS S3 (scan images, model files) |
| **Cloud ML** | AWS SageMaker or Google Vertex AI |
| **Search** | Elasticsearch (food name search across languages) |
| **Queue** | AWS SQS or RabbitMQ (offline scan processing) |
| **Auth** | Firebase Auth + JWT |
| **Hosting** | AWS EC2 / ECS or GCP Cloud Run |
| **CDN** | CloudFront (model file delivery) |

### ML / AI
| Component | Technology |
|-----------|-----------|
| **Training framework** | PyTorch (training) → TFLite/CoreML (inference) |
| **Base model** | EfficientNetV2-S (on-device), ViT-L (cloud) |
| **Object detection** | YOLOv8 (multi-food plate detection) |
| **Depth estimation** | MiDaS (monocular) + LiDAR where available |
| **Speech-to-text** | Whisper.cpp (on-device, multilingual) |
| **Model optimization** | TensorFlow Model Optimization Toolkit (quantization, pruning) |
| **Experiment tracking** | MLflow or Weights & Biases |
| **Data versioning** | DVC (Data Version Control) |

### DevOps
| Component | Technology |
|-----------|-----------|
| **CI/CD** | GitHub Actions |
| **Containerization** | Docker + Docker Compose |
| **Orchestration** | AWS ECS or Kubernetes (EKS) |
| **Monitoring** | Datadog or Grafana + Prometheus |
| **Error tracking** | Sentry |
| **Feature flags** | LaunchDarkly |

---

## 17. Monetization Strategy

### Freemium Model

**Free Tier (Always Free):**
- Unlimited meal scans (on-device model)
- 3 meals/day logging
- Basic macro tracking (calories, protein, carbs, fat)
- 2,000+ Indian foods database
- Offline capability
- Barcode scanning
- Basic daily dashboard

**Premium — ₹199/month or ₹1,499/year (~$18/year):**
- Unlimited meal logging
- Cloud model for complex dish recognition
- 50+ micronutrient tracking
- Diabetic mode (GI/GL tracking + alerts)
- Family mode (up to 4 profiles)
- AI nutritionist chat (5 messages/day)
- Weekly insight reports
- Restaurant menu integration (Swiggy/Zomato)
- Apple Health / Google Fit sync
- PDF export for doctor consultations

**Pro — ₹399/month or ₹2,999/year:**
- Everything in Premium
- Unlimited AI nutritionist chat
- Personalized 28-day meal plans
- Priority cloud processing
- Human nutritionist review (1 session/month)
- Early access to new features

### Revenue Targets
| Month | MAU | Conversion | Monthly Revenue |
|-------|-----|-----------|-----------------|
| 6 | 10,000 | 5% | ₹1,00,000 |
| 12 | 50,000 | 7% | ₹7,00,000 |
| 24 | 2,00,000 | 10% | ₹40,00,000 |

---

## 18. Security & Privacy

### Data Minimization
- Meal photos are not stored permanently in the cloud after processing
- Photos are deleted from server within 24 hours of scan completion
- On-device photos are stored only if user explicitly saves a meal photo

### Encryption
- All data in transit: TLS 1.3
- All data at rest (user logs, personal data): AES-256 encryption
- Local SQLite database: SQLCipher encryption

### Privacy Compliance
- **India:** IT Act 2000 + Personal Data Protection Bill (PDPB) compliance
- **Europe:** GDPR Article 17 (right to erasure) — full account deletion
- **DPDPA 2023 (India):** Data Principal rights implemented
- No data sold to third parties — ever
- Federated learning: only model gradients shared, never raw user data

### Account Security
- Firebase Auth with email + Google/Apple sign-in
- Optional biometric lock for app access
- Session timeout after 30 days inactivity
- Secure token refresh

---

## 19. Testing Strategy

### Unit Testing
- All business logic (calorie calculation, unit conversion, cooking correction) → 90%+ coverage
- ML model input/output schema validation
- Database CRUD operations

### Integration Testing
- API endpoint testing (pytest + httpx for FastAPI)
- Offline sync integration tests (simulate network loss → reconnect → verify sync)
- Scan queue processing tests

### UI / E2E Testing
- iOS: XCUITest
- Android: Espresso + UI Automator
- Critical flows: onboarding, scan meal, manual log, view dashboard

### ML Model Testing
- Accuracy benchmarking on held-out Indian food test set (500 dishes)
- Top-1 and top-3 accuracy metrics
- Per-category accuracy (South Indian, North Indian, street food, packaged food)
- Regression testing: new model version must not regress accuracy on any category

### Beta Testing Strategy
- Phase 1: 20 internal testers (team + friends) — catch critical bugs
- Phase 2: 500 beta users recruited via fitness communities, nutritionist partners, Instagram
- Focus beta on: Indian food accuracy, offline behavior, battery usage
- A/B test cooking context prompt placement (before vs after photo)

### Performance Benchmarks
| Metric | Target |
|--------|--------|
| On-device scan time (mid-range Android) | < 1 second |
| App cold start time | < 2 seconds |
| Battery usage per scan | < 0.1% battery |
| Offline scan queue sync time | < 5 seconds per item on 4G |
| Local DB query time | < 50ms |

---

## 20. Launch Strategy

### Pre-Launch (Months 1–9)
- Build waitlist via Instagram + fitness YouTubers (South Indian fitness community)
- Partner with 10–20 Indian nutritionists / dietitians as brand advisors
- Create content: "How many calories is your favorite dosa?" — drives organic interest
- Submit to App Store + Play Store for review (allow 2–4 weeks)

### Launch Week
- Press release to Indian tech media (YourStory, Inc42, The Ken)
- Product Hunt launch
- Soft launch to 5,000 waitlist users in Week 1
- Fitness influencer posts (micro-influencers in Tamil Nadu, Andhra, Maharashtra)

### Post-Launch Growth
- SEO content: "Calories in biryani", "Dosa calories", "Indian diet tracker" — massive organic search volume
- Referral program: invite a friend, both get 1 month Premium free
- Partner with gyms, yoga studios, and corporate wellness programs
- Hospital partnerships for diabetic patient nutrition tracking

### Key Metrics to Track
| Metric | 30-Day Target | 90-Day Target |
|--------|--------------|--------------|
| Downloads | 5,000 | 25,000 |
| DAU/MAU ratio | 30% | 40% |
| Scans per user per day | 2.0 | 2.5 |
| 7-day retention | 45% | 55% |
| Scan accuracy rating (user-reported) | > 3.8/5 | > 4.2/5 |
| Crash-free rate | > 99% | > 99.5% |

---

## Appendix A — Competitive Positioning Map

```
                    HIGH REGIONAL ACCURACY
                            │
           NutriLens ●      │
           (our app)        │      HealthifyMe ●
                            │
OFFLINE ───────────────────────────────── CLOUD ONLY
FIRST                       │                ONLY
                            │
                            │  SnapCalorie ●
          Cronometer ●      │
                            │       Cal AI ●
                MFP ●       │
                            │
                    LOW REGIONAL ACCURACY
```

**Our unique position:** Top-left quadrant — the only app combining offline-first with high regional accuracy. No competitor currently occupies this space.

---

## Appendix B — Indian Food Training Dataset — Priority List

| Priority | Dish | Region | Variants |
|----------|------|--------|---------|
| 1 | Idli | South India | Small, medium, large; rava idli |
| 2 | Dosa | South India | Plain, masala, rava, set dosa |
| 3 | Sambar | South India | Tamil, Andhra, Kerala variants |
| 4 | Rice (cooked) | Pan-India | White, brown, matta |
| 5 | Roti / Chapati | North India | Thin, thick, with ghee |
| 6 | Dal | Pan-India | Toor, masoor, chana, moong, tadka |
| 7 | Biryani | Pan-India | Hyderabadi, Lucknowi, Kolkata |
| 8 | Sabzi (curry) | North India | 20+ common vegetable curries |
| 9 | Chicken curry | Pan-India | North, South variants |
| 10 | Poha | Central/West India | Plain, kanda poha |
| 11 | Upma | South India | Rava, vermicelli |
| 12 | Paratha | North India | Aloo, gobi, paneer, plain |
| 13 | Chole | North India | With bhature, with rice |
| 14 | Paneer dishes | Pan-India | Butter masala, palak, bhurji |
| 15 | Vada | South India | Medu vada, dahi vada |
| ... | ... (2,000 total) | ... | ... |

---

## Appendix C — Estimated Build Cost

| Category | Monthly Cost | Annual Cost |
|----------|-------------|------------|
| 2 Mobile Devs (iOS + Android) | ₹2,00,000 | ₹24,00,000 |
| 1 Backend Dev | ₹1,20,000 | ₹14,40,000 |
| 1 ML Engineer | ₹1,50,000 | ₹18,00,000 |
| 1 UI/UX Designer | ₹80,000 | ₹9,60,000 |
| 1 Nutritionist (part-time) | ₹40,000 | ₹4,80,000 |
| AWS / GCP infrastructure | ₹30,000 | ₹3,60,000 |
| Tools & services | ₹20,000 | ₹2,40,000 |
| **Total (Year 1)** | **₹6,40,000/mo** | **₹76,80,000** |

> *Estimated Year 1 build cost: ~₹75–80 lakh (~$90,000 USD). Seed funding or bootstrapping with a lean team of 3–4 is viable at ~₹40–50 lakh.*

---

*Document version 1.0 — May 2026*
*Prepared for internal use — NutriLens founding team*
