Key Improvements 

1. Regional Food Dataset — Built from Scratch

Curate a proprietary dataset of 2,000+ Indian/South Asian dishes with:

Regional variants (Tamil Nadu sambar ≠ Andhra sambar — different calorie density)
Cooking method tags (steamed / fried / pressure-cooked / roasted)
Household serving size units: tablespoon, roti count

Partner with ICMR (Indian Council of Medical Research) nutritional tables as ground truth

2. Cooking Context Engine

A pre-scan "context prompt" that asks:

"Was this fried, steamed, or roasted?"
"Did you add oil/ghee? How much — a drizzle, a tablespoon, or more?"
"Home-cooked or restaurant?"

These 2–3 quick taps can reduce calorie estimation error by 30–40% for Indian food

3. On-Device Federated Learning 

User corrections on misidentified foods train a personalized local model
Aggregated corrections (privacy-safe, never raw data) improve the global model
Framework: TensorFlow Federated or Apple's Federated Learning APIs
This means the app gets smarter for every user without sending personal data to servers

4. Meal Photo Queue (Offline Scan Holding)

When offline, the app captures and stores the photo + metadata locally
On reconnection, queued photos are processed by the cloud model in the background
Results sync back and notify the user: "Your lunch scan is ready"
Works like an email outbox — nothing is lost when offline

5. Glycemic & Diabetic Intelligence Layer

Tag foods with Glycemic Index (GI) and Glycemic Load (GL)
Special mode for diabetic users: flags high-GI meals; suggests lower-GI swaps
Tracks cumulative daily GL — particularly useful for Type 2 diabetes management

6. AR Plate Guide (Phase 2+)

Augmented Reality overlay guides the user to optimal scan position
"Move camera higher" / "Separate the items" / "Better lighting needed"
Reduces failed/inaccurate scans dramatically through real-time feedback





