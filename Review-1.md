# ORCA: Marine EcOsystem Reasoning with Collaborative Agents

## SIH 2026 | Problem Statement 26176 | ISRO | Software

Bro, this is actually a **strong SIH problem statement**, but there is an important trap:

> **ORCA is not simply “build a chatbot for ocean data.”**
>
> The real challenge is building a **trustworthy agentic decision-support system** that can understand a marine question, find the right data, perform spatial-temporal reasoning, coordinate specialized agents, and produce an **evidence-backed recommendation**.

The official-style description asks for natural-language interaction, multilingual support, multi-turn context, autonomous dataset discovery, spatial/temporal reasoning, explainable recommendations, safety alerts, geofencing, route planning, and evidence supporting the final answer.

---

## 0. ORCA in One Picture

Think of the system like this:

```text
			  USER
				│
	   "Can I go fishing tomorrow?"
				│
				▼
		ORCA MASTER AGENT
				│
		Understand + Decompose
				│
	  ┌────────────┼────────────┐
	  ▼            ▼            ▼
 Ocean Agent    Weather       Geo Agent
	  │            │                │
 SST / Chl.      Wind/Waves       Location
 Currents        Cyclone          Boundaries
	  │            │                │
	  └────────────┼────────────┘
				▼
		   Risk Agent
				│
				▼
		  Reasoning Engine
				│
				▼
	  Evidence + Recommendation
				│
				▼
 "Not recommended: high waves
  + strong winds between 5–9 AM"
				│
				▼
	  Map + Charts + Sources
```

**This architecture is much more defensible than simply putting an LLM on top of an ocean database.**

---

## 1. Pain Points & Core Understanding

### What exact problem is being addressed?

Marine information already exists — the problem is that it is **fragmented, technical and difficult to turn into decisions**.

For example, a fisherman might ask:

> *“ kal subha Pune/Goa coast ke paas fishing karna safe hai kya?”*

The answer could require:

- weather forecast
- wind speed
- wave height
- sea-surface temperature
- currents
- tides
- chlorophyll
- potential fishing zones (https://incois.gov.in/MarineFisheries/PfzAdvisory)
- cyclone information  (https://www.windy.com/-Hurricane-tracker/hurricanes/one?20.797,77.771,5)
- location/boundaries
- vessel-specific constraints

The user shouldn't have to manually visit 6 different portals and understand scientific datasets.

### The core problem:

> **Convert heterogeneous marine data → understandable → contextual → actionable intelligence.**

---

### Root Causes

| Root Cause | Consequence |
|---|---|
| Huge ocean datasets | Difficult for ordinary users |
| Data scattered across agencies | Multiple portals/tools |
| Scientific formats | Non-experts struggle |
| Time-sensitive information | Delayed decisions |
| Spatial information | Requires GIS expertise |
| Different datasets | Difficult to correlate |
| Generic LLMs | Hallucination risk |
| Language barrier | Regional users excluded |
| Lack of contextual reasoning | Raw data ≠ useful decision |

This is why the PS specifically emphasizes **autonomous planning, tool selection, collaboration, spatial-temporal reasoning and explainability**.

---

## Who are the stakeholders?

### Primary

**Fishermen**

- fishing-zone discovery
- sea safety
- route planning
- weather alerts
- boundary alerts

### Secondary

**Marine researchers**

- data exploration
- ecosystem analysis
- correlations
- historical trends

**Government / Coastal Authorities**

- marine monitoring
- disaster response
- protected-zone management

**Disaster Management**

- cyclone/wave risk
- coastal hazards
- emergency planning

**Maritime Operators**

- navigation
- route planning
- weather awareness

**Environmental Agencies**

- ecosystem health
- fishing pressure analysis
- protected-area awareness
- harmful environmental conditions
- climate trend analysis

---

## 2. Feasibility of Execution

### Can this be built during a hackathon?

### **YES — but only if you control the scope.**

Trying to build:

> 10 autonomous agents + real-time satellite ingestion + voice + multilingual AI + route optimization + IoT + mobile app + predictive ML

would be a disaster.

Instead:

### Build ONE killer workflow.

> **“Ask ORCA whether it is safe and useful to fish at a particular location/time.”**

Then demonstrate how agents collaborate.

---

## 🟢 Hackathon MVP

### User enters:

> **“Is it safe to fish near Ratnagiri tomorrow morning, and where is the nearest promising fishing zone?”**

ORCA does:

```text
Query
 ↓
Planner Agent
 ↓
 ├── Weather Agent
 ├── Ocean Agent
 ├── Fishing Zone Agent
 ├── Geo Agent
 └── Risk Agent
 ↓
Reasoning Engine
 ↓
Recommendation
 ↓
Map + Evidence
```

### Output:

**Fishing recommendation: CAUTION**

| Parameter | Result |
|---|---|
| 🌊 Wave height | 1.8 m |
| 💨 Wind | 28 km/h |
| 🌡️ SST | 28.4°C |
| 🟢 Fishing potential | Moderate |
| ⚠️ Risk | Medium |
| 🚧 Boundary | 8 km away |
| 🕘 Best window | 6–9 AM |

Then:

> **“Fishing is possible with caution between 6–9 AM. Avoid the western zone because wave height is expected to increase after 10 AM.”**

And crucially:

### 📚 Evidence

```text
Ocean data      → Source A
Weather         → Source B
Fishing data    → Source C
Boundary data   → Source D
```

That's your **judge-winning moment**.

---

## 🧰 Technical Requirements

### Frontend

- React / Next.js
- MapLibre / Leaflet / Mapbox
- Recharts / Plotly
- multilingual UI
- chat interface

### Backend

- Python
- FastAPI
- PostgreSQL/PostGIS
- Redis optional

### AI

- LLM
- Agent orchestration
- RAG
- tool calling
- structured outputs

### Geospatial

- GeoPandas
- Shapely
- PostGIS
- GeoJSON

### Data

- SST
- chlorophyll
- wind
- waves
- currents
- weather
- fishing zones
- maritime boundaries

---

## 🚧 Biggest Technical Blockers

### 1. Data integration

Different sources may have:

- different coordinate systems
- resolutions
- timestamps
- formats
- APIs
- access policies

### 2. Real-time APIs

Never assume an API will work during the demo.

### 3. LLM hallucination

This is probably your **#1 risk**.

If the LLM says:

> "Wave height is 0.8 m"

but the actual dataset says:

> 2.1 m

your system becomes dangerous.

### 4. Safety recommendations

Don't position ORCA as:

> ❌ "AI guarantees that it is safe."

Position it as:

> ✅ **"Evidence-based decision support using authoritative marine data."**

---

## 3. Impact & Relevance

This PS is particularly strong because it sits at the intersection of:

**AI + Satellite Data + GIS + Oceanography + Disaster Management + Fisheries**

That's a very SIH-friendly combination.

### Economic Impact

Better fishing-zone discovery

→ reduced fuel consumption

→ increased catch efficiency

Better route planning

→ reduced operational costs

Better forecasting

→ reduced losses from hazardous conditions

### Environmental Impact

Potential applications:

- marine ecosystem monitoring
- fishing pressure analysis
- protected-area awareness
- harmful environmental conditions
- climate trend analysis

### National-Level Potential

```text
Hackathon Prototype
	  ↓
Pilot coastal district
	  ↓
State fisheries department
	  ↓
National marine intelligence platform
	  ↓
Integration with ISRO / INCOIS ecosystem
```

India already has significant ocean-information infrastructure.

For example, INCOIS's Ocean State Forecast provides variables including **winds, waves, currents, SST, mixed-layer depth and chlorophyll**, with forecasts extending several days ahead.

And ISRO's EOS-06/Oceansat-3 carries instruments for ocean colour, scatterometry and SST observation.

---

## 4. Scope of Innovation & Competitor Analysis

This is where things get interesting.

ORCA **does have competition** — but mostly at the data/platform level rather than exactly the proposed agentic conversational workflow.

### Competitor 1 — INCOIS

[INCOIS Ocean Information Services](https://incois.gov.in/)

INCOIS already provides sophisticated ocean-state information including:

- waves
- winds
- currents
- SST
- chlorophyll
- forecasts
- vessel advisories

Its **Small Vessel Advisory and Forecast Services (SVAS)** even calculates a Boat Safety Index using wave and wind characteristics for small vessels.

#### ❌ Limitation relative to ORCA

The user still largely interacts with **information products**, not a generalized conversational reasoning layer that coordinates multiple specialized agents.

#### ORCA advantage

```text
INCOIS
Data → Visualization → Human interpretation

ORCA
Question → Agents → Data → Reasoning → Recommendation
```

### Competitor 2 — Global Fishing Watch

[Global Fishing Watch](https://globalfishingwatch.org/)

This is a serious competitor.

It combines satellite technology, machine learning and vessel tracking to visualize human activity at sea. Its platform includes vessel activity, fishing effort and marine-management capabilities.

It also provides APIs for vessel identity, fishing effort, events and other marine information.

#### ❌ Limitation

Its primary strength is **monitoring and analysis of human activity at sea**, rather than being an Indian-context conversational marine decision assistant.

#### ORCA advantage

Potentially combine:

> vessel + ocean + weather + ecosystem + geography + conversational reasoning

### Competitor 3 — NOAA / ERDDAP

[NOAA ERDDAP](https://www.ncei.noaa.gov/erddap/)

ERDDAP makes oceanographic datasets easier to retrieve, graph and map and provides standardized access across different data servers.

#### Limitation

Still fundamentally a **data-access infrastructure**, not an end-user marine reasoning assistant.

### Competitor 4 — OceanAI

This is perhaps your **most important research competitor**.

A 2025 research project called **OceanAI** created a conversational platform connecting LLMs to authoritative NOAA oceanographic data. Queries trigger API calls, data retrieval and synthesis, with references and visualizations.

### Why judges could mention it

Because it proves:

> **"LLM + live ocean data + citations" is already possible.**

Therefore:

### Don't claim:

> "We are the first AI ocean chatbot."

Instead claim:

> **"We extend conversational ocean intelligence into an Indian, multi-agent, geospatial decision-support architecture."**

### Competitor 5 — OceanGPT

OceanGPT is an ocean-domain LLM research project designed specifically for ocean-science tasks. The authors highlight that general LLMs struggle with the complexity and granularity of ocean data.

This supports your fundamental architecture:

> **Don't trust a generic LLM to reason directly from marine datasets.**

---

## 📊 Competitor Matrix

| Capability | INCOIS | GFW | ERDDAP | OceanAI | **ORCA** |
|---|---:|---:|---:|---:|---:|
| Ocean data | Yes | Yes | Yes | Yes | Yes |
| Satellite data | Yes | Yes | Yes | Yes | Yes |
| Vessel monitoring | Partial | Yes | No | No | Yes |
| Conversational UI | No | No | No | Yes | Yes |
| Multi-agent reasoning | No | No | No | Partial | Yes |
| Spatial reasoning | Yes | Yes | Yes | Yes | Yes |
| Indian context | Yes | Partial | No | No | Yes |
| Multilingual | Partial | Partial | No | Partial | Yes |
| Safety recommendation | Yes | Partial | No | Partial | Yes |
| Geofencing | Partial | Yes | No | No | Yes |
| Explainable evidence | Partial | Yes | Yes | Yes | Yes |
| Multi-turn context | No | No | No | Yes | Yes |

---

## 🔥 What Should Make ORCA Different?

Don't make the innovation:

> "We use 8 AI agents."

That's **not enough anymore**.

Instead:

## Innovation = **Agentic Marine Evidence Graph**

Every answer should have:

```text
USER QUESTION
	↓
INTENT
	↓
TASK GRAPH
	↓
DATA SOURCES
	↓
AGENT OUTPUTS
	↓
CROSS-CHECK
	↓
RISK SCORE
	↓
RECOMMENDATION
	↓
EVIDENCE
```

That gives you **traceability**.

---

## 5. Clarity of Problem Statement

## What exactly is ISRO asking for?

The PS effectively expects:

### 1. Natural-language understanding

> "What's the weather near Mumbai tomorrow?"

### 2. Multilingual interaction

Especially Indian regional languages.

### 3. Multi-turn conversation

```text
User:
Where should I fish?

ORCA:
I found 3 promising areas.

User:
Which one is safest?

ORCA:
Zone B.

User:
What about tomorrow morning?

ORCA:
Risk increases after 10 AM.
```

### 4. Autonomous task decomposition

```text
Question
 ↓
Planner
 ↓
Weather
Ocean
Geo
Fishing
Risk
 ↓
Synthesizer
```

### 5. Spatial-temporal reasoning

Not just:

> "SST = 28°C"

But:

> "SST increased by 1.2°C over the past week in this region."

### 6. Explainability

Show **why** the recommendation was generated.

### 7. Safety

Weather + waves + cyclone + lightning etc.

### 8. Geofencing

Alert for:

- international boundaries
- restricted waters
- marine protected areas
- ecological zones

### 9. Route optimization

Potentially use:

> A* / Dijkstra + marine cost function.

---

## Where Teams May Misinterpret It

### Mistake #1

> "I'll build a chatbot."

Too shallow.

### Mistake #2

> "I'll make 10 agents."

Agent count isn't innovation.

### Mistake #3

> "I'll train a marine LLM."

Completely unnecessary for MVP.

### Mistake #4

> "I'll scrape random websites."

Bad grounding.

### Mistake #5

> "I'll give fishermen a risk score."

Without explaining how that score was calculated.

---

## Correct Framing

Tell judges:

> **"ORCA is a grounded multi-agent marine decision-support system, not a generic chatbot."**

---

## 6. Evaluator's Perspective

A judge will probably mentally score you like this:

| Factor | Importance |
|---|---:|
| Alignment with PS | Very high |
| Technical innovation | Very high |
| Impact | Very high |
| Working prototype | Very high |
| Data grounding | Very high |
| Agentic behavior | High |
| UI/UX | Medium |
| Presentation | High |
| Scalability | High |

---

## Biggest Red Flags

### 1. Fake agents

If all agents are just:

```text
agent1()
agent2()
agent3()
```

but they don't actually perform different tasks, judges will notice.

### 2. Hallucinated data

This is potentially fatal.

### 3. No real data

A beautiful UI with fake values = weak project.

### 4. No evidence

If ORCA says:

> "Fishing is dangerous."

Judge:

> **WHY?**

You need:

> Wave 2.3m + wind 35 km/h + advisory issued at X time.

### 5. No spatial reasoning

A marine intelligence platform without a strong map is leaving a major opportunity unused.

---

## 7. Strategy for Team Fit

For a **6-person SIH team**, I'd structure it:

| Role | People | Responsibility |
|---|---:|---|
| AI/Agent Engineer | 1 | Agents + orchestration |
| AI/RAG Engineer | 1 | LLM + retrieval + grounding |
| Data/GIS Engineer | 1 | Marine data + spatial reasoning |
| ⚙️ Backend Engineer | 1 | FastAPI + DB + APIs |
| Frontend/UX | 1 | Dashboard + map + chat |
| Integration/Research | 1 | Testing + documentation + PPT + demo |

### If you have only 4 members:

```text
AI + Agents
Backend + Data
Frontend + GIS
Research + Integration + Presentation
```

### Recommended Research to Build Process

#### Phase 1 — Understand the domain

Study:

- SST
- chlorophyll
- currents
- wave height
- wind
- tides
- PFZ
- marine boundaries

#### Phase 2 — Map the data ecosystem

Create:

```text
Parameter → Source → API/File → Frequency → Format
```

Example:

| Parameter | Possible Source |
|---|---|
| SST | ISRO / Copernicus |
| Chlorophyll | ISRO / Copernicus |
| Ocean state | INCOIS |
| Weather | Weather/ocean forecast source |
| Vessel activity | Global Fishing Watch |
| Boundaries | GeoJSON / GIS datasets |

EOS-06 is particularly relevant because its payloads directly target ocean colour, surface winds and SST observation.

---

#### Phase 3 — Design agents

Don't create agents randomly.

### Recommended:

```text
				MASTER AGENT
					│
	   ┌────────────────┼────────────────┐
	   │                │                │
	DATA AGENT       WEATHER          GEO AGENT
	   │              AGENT              │
	   │                │                │
    SST/CHL          Wind/Wave       Boundaries
	   │                │                │
	   └────────────────┼────────────────┘
					▼
				RISK AGENT
					│
					▼
			   REASONING AGENT
					│
					▼
			   RESPONSE AGENT
```

---

## 8. AI-Buildability Split: 20/80

This is one of the most important sections.

### AI can build the 20%

LLMs can rapidly generate:

- FastAPI boilerplate
- React UI
- chat interface
- basic agents
- API clients
- RAG pipeline
- prompt templates
- database schemas
- map components
- chart components
- multilingual translation layer
- JSON schemas
- test cases

You could probably generate **60–80% of the basic code scaffolding** with AI.

---

### But the important 80% is human/system design

AI cannot reliably decide:

### 1. Which data source should be trusted?

### 2. What does "safe" actually mean?

### 3. How should wave + wind + current interact?

### 4. How should conflicting sources be handled?

### 5. What spatial resolution is appropriate?

### 6. What timestamp matters?

### 7. What constitutes a dangerous condition?

### 8. How do you prove the recommendation?

### 9. How do you prevent hallucinations?

### 10. What happens when the API fails?

That's the **actual engineering challenge**.

---

## Risk of AI-Only Development

You can end up with:

```text
Beautiful UI
+
Cool agents
+
Confident LLM
=
Scientifically unreliable system
```

Judges who understand ISRO/oceanography could destroy such a demo with 2–3 questions.

---

## Judge asks one structural change

Imagine the judge says:

> **"Your system gives a fishing recommendation, but I want the recommendation to be generated only when at least two independent data sources agree. Otherwise show UNCERTAIN."**

Can you implement it?

### If architecture is good:

**YES.**

Add:

```text
Source Validator
	  ↓
Cross-source agreement
	  ↓
Confidence threshold
	  ↓
Recommendation
```

### If everything is hard-coded inside prompts:

Very difficult.

This is why **modular architecture matters more than number of agents.**

---

## 9. Data & Resource Availability

This PS is unusually feasible because **real marine data already exists**.

### ISRO / MOSDAC

[MOSDAC — ISRO's Meteorological & Oceanographic Satellite Data Archival Centre](https://mosdac.gov.in/)

Oceansat-2 data has historically supported applications including:

- chlorophyll estimation
- phytoplankton bloom detection
- primary productivity
- potential fishing zones
- ocean winds
- coastal applications

EOS-06/Oceansat-3 provides physical, biological and atmospheric ocean measurements through OCM-3, scatterometer and SST instruments.

### INCOIS

[INCOIS](https://incois.gov.in/)

Extremely relevant.

Ocean State Forecast provides:

- wind
- waves
- currents
- SST
- mixed-layer depth
- chlorophyll
- other ocean variables

and forecasts can extend **5–10 days** depending on service/product.

### Copernicus Marine

Copernicus Marine is another strong source for ocean products.

Google Earth Engine also exposes Copernicus marine datasets; for example, its global ocean-colour collection contains chlorophyll-a at approximately 4 km pixel size.

### Global Fishing Watch

Useful for:

- vessel activity
- fishing effort
- vessel identity
- encounters
- maritime activity

Its API requires registration/API credentials and has usage conditions, so don't make your entire demo dependent on it.

### NOAA / ERDDAP

Excellent backup source.

ERDDAP provides standardized access to oceanographic datasets including satellite and buoy data.

---

### What if the real API fails?

This is where smart hackathon teams differentiate themselves.

## Build a 3-layer data architecture:

```text
		    ORCA DATA LAYER
				 │
	  ┌─────────────┼─────────────┐
	  ▼             ▼             ▼
   LIVE APIs     CACHED DATA   SYNTHETIC
	  │             │             │
	  └─────────────┼─────────────┘
				 ▼
		    NORMALIZED SCHEMA
```

### Production

Live APIs.

### Demo fallback

Cached snapshots.

### Last resort

Synthetic but scientifically plausible data.

Clearly label:

> **DEMO / SIMULATED DATA**

Never pretend synthetic data is real.

---

## Synthetic Data Strategy

Create historical-like records:

```json
{
  "location": "Ratnagiri",
  "timestamp": "2026-09-04T06:00",
  "sst": 28.4,
  "chlorophyll": 0.73,
  "wave_height": 1.8,
  "wind_speed": 22,
  "current_speed": 0.8
}
```

Then clearly label:

> **DEMO / SIMULATED DATA**

Never pretend synthetic data is real.

---

## 10. Judge Q&A Stress-Test

Now let's get serious.

### Q1. "Why do you need multiple agents? Why not one LLM?"

#### Strong answer:

> "Because the problem isn't only language generation. Different marine variables require different tools, data sources and reasoning procedures. Our planner decomposes the query, specialized agents retrieve and analyze the relevant information, and a final reasoning layer synthesizes their outputs. This also allows us to validate individual outputs instead of trusting one unconstrained LLM."

#### Follow-up:

> **"But aren't these just multiple API calls?"**

Your answer:

> "API calls retrieve information; agents decide which information is required, interpret the task, invoke the appropriate tools and return structured evidence to the reasoning layer."

### Q2. "How do you prevent hallucinations?"

#### Strong answer:

> "The LLM does not generate marine measurements. Numerical values are retrieved from structured data sources. The LLM operates primarily as an orchestrator and explanation layer. Every recommendation is linked to the underlying observations, timestamps and sources, and if required data is unavailable or conflicting, ORCA returns an uncertainty state instead of inventing a value."

### Q3. "Can you really trust your safety recommendation?"

Don't say:

> ❌ "Yes, our AI is accurate."

Say:

> "ORCA is a decision-support system, not a replacement for official marine advisories. Safety decisions are grounded in authoritative forecast data and our system exposes the variables contributing to the risk assessment. Official warnings take precedence, and when confidence is insufficient we explicitly report uncertainty."

### Q4. "What's innovative here? ChatGPT can already answer these questions."

#### Strong answer:

> "A general LLM knows language but doesn't inherently know the current ocean state at a particular coordinate and time. ORCA converts a natural-language question into a spatial-temporal data query, dynamically selects relevant marine tools, correlates heterogeneous datasets, and produces an evidence-linked recommendation. The innovation is therefore the grounded reasoning pipeline, not simply the chatbot interface."

### Q5. "What happens if one data source is unavailable?"

#### Strong answer:

> "The architecture separates live data, cached data and synthetic demonstration data. Each response carries source and freshness metadata. If a critical source is unavailable, ORCA doesn't silently substitute fabricated information; it either falls back to an approved cached dataset or marks the recommendation as uncertain."

---

## The Weakest Part a Sharp Judge Will Attack

## **Your risk/recommendation engine.**

Everything else is relatively easy:

- Chat UI → easy
- Agents → easy
- APIs → manageable
- Maps → easy
- RAG → easy

But:

> **"How exactly did you decide that this location is safe?"**

That's where you need a serious answer.

---

## Build a Deterministic Risk Engine

Instead of asking an LLM:

> "Is this safe?"

Use:

```text
Wave Risk
	+
Wind Risk
	+
Current Risk
	+
Cyclone Risk
	+
Boundary Risk
	+
Official Advisory
	↓
Risk Engine
	↓
LOW / MODERATE / HIGH / EXTREME
```

Then let the LLM **explain** the result.

---

## This architecture is stronger

```text
			  USER
			    │
			    ▼
		  🧠 ORCA PLANNER
			    │
	   ┌──────────┼──────────┐
	   ▼          ▼          ▼
	 🌊 Ocean   🌦 Weather   🗺 GIS
	  Agent      Agent       Agent
	   │          │           │
	   └──────────┼───────────┘
			    ▼
		   📊 Data Fusion
			    │
			    ▼
		⚙️ DETERMINISTIC
		   RISK ENGINE
			    │
			    ▼
		   🔬 VALIDATOR
			    │
			    ▼
		  🤖 LLM EXPLAINER
			    │
			    ▼
	   ┌──────────┼──────────┐
	   ▼          ▼          ▼
	  💬         🗺️         📈
	Answer       Map       Evidence
```

This separates:

### **Reasoning from language generation.**

That's excellent engineering.

---

## Research You Should Know

There is already research validating several pieces of your concept.

### OceanAI

Conversational oceanographic intelligence with authoritative NOAA data, visualizations and references.

### OceanGPT

Domain-specific LLM research for ocean science, highlighting the limitations of generic LLMs for complex ocean datasets.

### FloatChat

A 2026 paper describes a conversational framework for Indian Ocean Argo data using **PostgreSQL + FAISS + RAG + knowledge graphs + agentic architecture**. It reported high structured-query accuracy and emphasized deterministic retrieval before generative responses.

That paper is **extremely relevant to your architecture**.

### Compass

A 2026 marine-data agent framework uses expert-guided knowledge structures and multi-layer validation to improve reliability of LLM-based marine data extraction.

---

## What I Would Build for SIH

If I were your technical mentor, I would **NOT** build every feature in the PS.

I'd build:

## ORCA: Marine Decision Intelligence Copilot

### Killer workflow:

> **"Should I fish here tomorrow morning?"**

ORCA:

### 1. Understands language

English / Hindi / Marathi etc.

↓

### 2. Identifies location

GPS / map / named place

↓

### 3. Plans tasks

```text
Weather
Ocean
Fishing potential
Boundaries
Risk
```

↓

### 4. Agents retrieve data

↓

### 5. Spatial-temporal fusion

↓

### 6. Deterministic risk scoring

↓

### 7. LLM explains

↓

### 8. Visual result

```text
┌──────────────────────────────┐
│ 🎣 FISHING RECOMMENDATION    │
│                              │
│ 🟡 MODERATE CAUTION          │
│                              │
│ Best window: 06:00–09:00     │
│                              │
│ 🌊 Wave: 1.4m                │
│ 💨 Wind: 19 km/h             │
│ 🌡️ SST: 28.2°C               │
│ 🟢 Fishing potential: High   │
│                              │
│ ⚠️ Main risk: rising waves   │
└──────────────────────────────┘
```

And alongside:

🗺️ **Interactive map**

📈 **Parameter charts**

📚 **Evidence**

🧠 **Reasoning trace**

---

## Your "WOW" Demo

Don't start with:

> "Hello, welcome to ORCA."

Start with:

### Demo prompt

> **"Imagine I'm a fisherman near Ratnagiri. I don't understand satellite datasets. I simply ask ORCA..."**

Then type:

> **"Kal subah 6 baje fishing ke liye jaana safe hai kya? Aur sabse accha area kaha hai?"**

ORCA responds:

```text
🔎 Understanding query...

📍 Location identified: Ratnagiri
🕕 Time: Tomorrow 06:00
🎣 Intent: Fishing + Safety

🤖 Activating:

✓ Ocean Agent
✓ Weather Agent
✓ Fishing Agent
✓ GIS Agent
✓ Risk Agent

━━━━━━━━━━━━━━━━━━

🟡 MODERATE CAUTION

Recommended area:
18.45°N, 73.82°E

Best window:
06:00 – 09:00

Reason:
✓ Favorable SST
✓ Elevated chlorophyll
✓ Moderate fishing potential
⚠️ Wave height expected to increase
⚠️ Avoid western boundary zone

[VIEW MAP] [VIEW EVIDENCE]
```

### THAT is a hackathon demo.

---

## Final Verdict

# GREEN LIGHT

### **Single biggest reason:**

> **The problem has real users, real government/ISRO marine-data infrastructure, strong AI/GIS relevance, and a prototype can be built without inventing the underlying data ecosystem.**

The biggest caution is that **multi-agent AI itself is no longer sufficiently novel**. Existing platforms and research already demonstrate conversational ocean-data access and agentic ocean-data reasoning.

Therefore your competitive advantage should be:

# **🇮🇳 Indian marine data + 🗺️ spatial-temporal reasoning + 🤖 genuine agent collaboration + ⚙️ deterministic risk engine + 📚 evidence-backed explanations + 🌐 regional languages**

Not:

> ❌ "We have 10 AI agents."
