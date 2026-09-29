# UNI STEP — Make better decisions. Move forward.

> **PS03 — The Next Decision**  
> *A University Decision-Support Platform that turns scattered student information into one personalized next step.*

---

## 🚀 Live Demo & Quick Launch

The project is located at:
`C:\Users\nallu\.gemini\antigravity-ide\scratch\uni_step`

### 1. Instant Interactive Web Prototype (Running Now)
The prototype is currently active and served locally:
* **URL:** [http://localhost:3000](http://localhost:3000)
* Or double-click `web_demo/index.html` in any browser.
* **Demo Credentials:**
  * **Username:** `demo` (or `rahul@srm.edu.in`)
  * **Password:** `demo123`
  * Or tap **"⚡ Try Demo Mode (Judge Instant Access)"** on the Welcome screen.

### 2. Verify Dart Decision Engine Tests
The multi-attribute decision scoring, hard constraints, and what-if engine were tested and verified with the native Dart SDK:
```powershell
dart test/decision_engine_test.dart
```

### 3. Run with Flutter CLI
```powershell
cd C:\Users\nallu\.gemini\antigravity-ide\scratch\uni_step
flutter pub get
flutter run
```

---

## 🎯 The Core Problem & Innovation

Students do **NOT** suffer from a lack of information. Information is already scattered across:
* Timetables & Attendance portals
* Assignment submission systems
* Exam schedules
* Campus maps & travel times
* Extracurricular club schedules
* Specialization branch catalogs
* Industry career boards

The real problem is:
> **“I have all this information, but what should I actually do right now?”**

**UNI STEP** solves this by converting raw signals into:
$$\text{Information} \longrightarrow \text{Context} \longrightarrow \text{Decision} \longrightarrow \text{Explanation} \longrightarrow \text{Action}$$

---

## 🌟 The Two Flagship Flows

### FLOW 1 — The Daily Decision Engine ("What Should I Do Next?")
1. **Context Ingestion:** Ingests current available time (90m), current location (Academic Block 3), upcoming exam (DBMS in 3 days), and due deadline (DBMS assignment tonight).
2. **Hard Constraints First:** Prunes activities that clash with scheduled classes or exceed available time + buffer.
3. **Multi-Attribute Scoring Model:**
   $$\text{Decision Score} = (\text{Urgency} \times w_u) + (\text{Academic Impact} \times w_i) + (\text{Exam Proximity} \times w_e) + (\text{Time Fit} \times w_t) + (\text{Travel Score} \times w_s)$$
4. **Transparent Output:** Delivers **ONLY ONE** primary recommendation:
   * **Recommendation:** *"Complete DBMS Assignment"* (60 mins, Central Library, 93% Fit).
   * **6 Deterministic Reasons:** Clear justification based on exam relevance, deadline, and travel efficiency.
   * **Trade-Off Analysis:** *"You will miss the AI Club event if you stay longer, but you can still attend after priority work."*
   * **Gains vs. Give-Ups:** Transparent breakdown.
5. **Interactive What-If Mode:**
   * Adjust available time from 90m down to 45m.
   * Recommendation immediately shifts to *"Revise DBMS Unit 3 (35m)"*.
   * Shows: **"YOUR DECISION CHANGED BECAUSE... Your available time decreased to 45 minutes. The full 60-min assignment would cause a schedule breach, so UNI STEP shifted to a high-yield 35-min revision."**

---

### FLOW 2 — The Specialization Decision Engine ("Which Specialization Should I Choose?")
1. **Multi-Dimensional Assessment:**
   * **Academic Profile:** CGPA (8.7), strongest subjects (DBMS, Linear Algebra, Python), enjoyed subjects.
   * **Technical Ratings:** 1–5 stars on Math, Stats, DSA, Databases, Systems, Networks.
   * **Interests & Goals:** AI/ML, Software Engineering, Target role (Machine Learning Engineer), Company type (Product).
   * **Decision Priorities:** Sliders for Interest, Salary, Flexibility, and Research.
2. **Personalized Evaluation:**
   * **Strong Alignment:** *AI / Machine Learning (88% Match)*
   * **Also Consider:** *Software Engineering (84% Match)* and *Data Science (82% Match)*
   * **Different Path:** *Cybersecurity (68% Match)*
   * **Advisory Disclaimer:** Explicit statement that recommendations are advisory decision support and do not guarantee placement or salary.
   * **Skill Gaps:** Highlights exact skills to close (PyTorch, RAG, Multivariable Calculus, MLOps).
3. **Personalized 6-Month Roadmap:**
   * **Month 1–2:** Math Foundations & Python Vectorization
   * **Month 3–4:** Deep Learning & PyTorch Models
   * **Month 5:** Generative AI & MLOps Deployment
   * **Month 6:** Interview Coding & Internship Applications
4. **Specialization What-If:**
   * Increase *Career Pathway Flexibility* to 5.
   * Engine dynamically re-ranks *Software Engineering & Systems* to the top.
   * Explains: **"Your recommendation changed to Software Engineering because you increased the priority of Career Flexibility."**

---

## 🏛️ Clean Architecture & Integration Readiness

```
lib/
├── main.dart                  # Application entry point & theme injection
├── app/
│   └── app_state.dart         # Central reactive state manager (ChangeNotifier)
├── theme/
│   ├── app_colors.dart        # Modern startup palette & gradients
│   └── app_theme.dart         # Material 3 typography & styling tokens
├── utils/
│   └── constants.dart         # Disclaimers, strings & demo credentials
├── models/
│   ├── student_profile.dart   # Student profile & academic metrics
│   ├── task_item.dart         # Academic tasks & constraints
│   ├── decision_item.dart     # Scored decisions, factors & trade-offs
│   ├── specialization_model.dart # Specialization profiles & roadmaps
│   └── campus_location.dart   # Campus nodes & travel times
├── data/
│   ├── demo_data.dart         # Realistic Rahul student baseline & tasks
│   └── specialization_data.dart # Sample market data & 6-month curriculum
├── engines/
│   ├── daily_decision_engine.dart # Multi-attribute decision utility & what-if logic
│   └── specialization_engine.dart # 6-criteria specialization analyzer
├── services/
│   ├── auth_service.dart      # Firebase Auth ready + local mock
│   ├── firestore_service.dart # Cloud Firestore ready + local store
│   ├── gemini_service.dart    # Gemini API ready + natural language explanation fallback
│   └── maps_service.dart      # Google Maps ready + campus travel-time matrix
├── widgets/
│   ├── factor_bar.dart        # Visual percentage progress indicators
│   ├── stat_chip.dart         # Pill badges
│   ├── custom_button.dart     # Styled buttons & loaders
│   └── campus_map_widget.dart # Interactive SVG/Canvas campus map
└── screens/
    ├── welcome_screen.dart    # Brand intro, tagline & quick demo button
    ├── login_screen.dart      # Credential validation & demo autofill
    ├── create_account_screen.dart # Registration form & legal acceptance
    ├── main_shell.dart        # Bottom navigation shell
    ├── home_screen.dart       # Context summary & hero next step
    ├── daily_decision_screen.dart # Core decision view with 6 reasons & trade-offs
    ├── decision_explanation_screen.dart # Visual factor inspector & gain/give-up breakdown
    ├── what_if_screen.dart    # Interactive time slider & dynamic recalculation
    ├── specialization_questionnaire_screen.dart # 4-step wizard
    ├── specialization_result_screen.dart # Alignment categories & skill gaps
    ├── specialization_what_if_screen.dart # Dynamic priority adjustments
    ├── career_roadmap_screen.dart # 6-month roadmap & sample market data
    ├── campus_map_screen.dart # Campus wayfinding & origin recalculation
    ├── decision_history_screen.dart # Recorded decision audit log
    ├── profile_screen.dart    # Profile metrics & editing
    ├── settings_screen.dart   # Preferences, notification toggles & legal
    ├── terms_screen.dart      # Advisory disclaimer & terms of service
    └── privacy_screen.dart    # Student privacy & data isolation standards
```

---

## 🏆 Demo Script for Hackathon Presentation

1. **Opening Hook (10s):**
   > *"Students have plenty of information — timetables, assignments, exams, clubs, campus maps. But having information isn't the problem. The problem is: what should I actually do right now?"*
2. **Welcome & Instant Login (15s):**
   > *Open http://localhost:3000, tap "Try Demo Mode". Notice the student greeting: "Good morning, Rahul".*
3. **The Daily Decision (30s):**
   > *Point to "YOUR NEXT STEP": "Complete DBMS Assignment". Explain how the engine didn't just look at deadlines: it evaluated the 3-day exam countdown, the 6-minute walk to Central Library, and the 90 minutes of available free time.*
4. **The "What-If" Innovation (25s):**
   > *Tap "What-If". Drag the slider to 45 minutes. Watch the engine prune the assignment to avoid a schedule breach, shifting to "Revise DBMS Unit 3 (35m)". Highlight the explanation banner: "Your decision changed because..."*
5. **Specialization & Career Roadmap (30s):**
   > *Tap "Track". Show the Strong Alignment for AI / Machine Learning (88% Match), the explicit non-guarantee disclaimer, the skill gaps, and the 6-month personalized preparation roadmap.*
6. **Closing (10s):**
   > *"UNI STEP doesn't just show information. It improves the decision itself."*
