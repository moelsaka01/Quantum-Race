# Quantum Race

Quantum Race is an AI-powered, 2026-era Formula-style race engineering and decision intelligence demo inspired by pit-wall strategy work, NASA-style mission control, and high-stakes simulation review.

Core principle:

**AI RECOMMENDS. PIT WALL APPROVES.**

The app opens in a no-live-data standby state. Use **Run Austrian GP 2026 Demo** to load the fictional demo replay, populate Mission Control, run the simulation universe, inspect rival twins, review agent debate evidence, and send strategies into Pit Wall Approval.

Use **Connect Live Data Source** to connect the OpenF1 public/latest or historical data path. OpenF1 public historical/latest data may be available without authentication, while true real-time OpenF1 access can require a subscription token. Quantum Race keeps connected OpenF1 source data separate from the Austrian GP 2026 demo replay.

The demo intentionally models the 2026 tactical environment: Active Aero, X-Mode Straight-Line Phase, Z-Mode Cornering Phase, Overtake Mode Armed, Boost Button Available, Battery SOC, Recharge Mode, Superclip Exposure, MGU-K Deployment, Energy Clipping Risk, Corner Entry Risk, Tyre Thermal Load, Rival Energy Attack Window, and Pit Wall Approval Required.

Earlier low-drag-era tactics are intentionally replaced with Active Aero, Overtake Mode, Boost Button, Battery SOC, Recharge Mode, and race engineer approval language.

For the flagship product showcase, open **Command Deck** in the sidebar or go directly to `#/command-deck`. It is the premium race-intelligence command surface for idle/demo review.

## Product Rules

- Demo data is fictional research/demo data and is not live telemetry.
- Demo mode and connected-source mode are separated. The app never silently fills connected-source gaps with Austrian GP demo results.
- The 2026 tactical layer is a simulation/demo model unless a connected source provides matching fields.
- OpenF1 connected mode labels public/latest or historical source data clearly and does not claim paid real-time access without a token.
- No official Formula 1, FIA, FOM, race promoter, driver, or team affiliation is implied.
- AI recommendations are not autonomous decisions.
- Final strategy requires race engineer approval before it is logged.
- Pit Wall Approval supports approve, adjust, or reject decisions with rationale.
- Current-session decisions and Race Memory entries use localStorage for this v1 demo workflow.

## Features

- Premium Mission Control standby screen with no-live-data status, dormant telemetry, idle agents, offline rival twins, and demo launch.
- Quantum Race Command Deck at `#/command-deck`, with a cinematic idle state, 2026 demo race command surface, Monte Carlo preview, threat radar, rival energy intelligence, and Pit Wall Approval handoff.
- OpenF1 data-source workflow with connect/disconnect status, public latest/historical session support, source-boundary messaging, and graceful fallback/error handling.
- Austrian GP 2026 demo replay with Active Aero, Battery SOC, Boost Button, Overtake Mode, MGU-K deployment, energy clipping risk, track visualization, threat radar, simulation preview, agent consensus, rival twins, telemetry, strategy timeline, and race memory insight.
- Race Command, Real-Time Data, and Advanced Telemetry pages for pit-wall operations and 2026 technical engineering review.
- Simulation Universe Explorer with interactive 2026 scenario chips, highlighted Monte Carlo futures, scenario inspector, and Pit Wall Approval handoff.
- Scenario Explorer for pit lap, tyre, rain, safety car, Battery SOC, Boost availability, Overtake Mode, Active Aero, recharge mode, superclip exposure, corner-entry risk, tyre thermal load, and rival energy attack behavior.
- Agent Debate Arena with rule-based strategy, tyre, weather, rival, energy, active aero, corner-entry, risk, performance, and team principal agents.
- Rival Twin Command Center for fictional competitor behavior modeling, rival Battery SOC, Overtake Mode eligibility, Boost defense probability, X-Mode/Z-Mode performance, and energy attack response review.
- Strategy Recommendations page with 2026 strategy options and Pit Wall Approval handoff for every option.
- Race Engineer Approval workflow with evidence links, audit log, required rationale, critical-risk acknowledgement, and Race Memory update.
- Race Memory Timeline and Performance Analytics for evaluation and institutional learning.

## Tech Stack

- Frontend: React, Vite, Recharts, Framer Motion, Lucide Icons, plain CSS.
- Backend: FastAPI, Pydantic, Python.
- Data: deterministic mock/demo data and rule-based simulation logic.
- Tests: Pytest with FastAPI TestClient.
- Deployment: Dockerfile and docker-compose.

## Local Run

Install backend dependencies:

```powershell
python -m pip install -r requirements.txt
```

Run the backend:

```powershell
$env:PYTHONPATH="backend"
uvicorn app.main:app --reload --app-dir backend
```

Install frontend dependencies:

```powershell
cd frontend
npm install
```

Or with pnpm:

```powershell
pnpm install
```

Run the frontend:

```powershell
npm run dev
```

Open `http://localhost:5173`. Quantum Race starts in standby mode; click **Run Austrian GP 2026 Demo** to populate the app, or **Connect Live Data Source** to inspect OpenF1 public/latest source telemetry.

## Docker Run

```powershell
docker compose up --build
```

Open `http://localhost:8000`.

In Docker, FastAPI serves the built frontend and the API from the same port.

## Tests and Build

Backend tests:

```powershell
$env:PYTHONPATH="backend"
pytest backend/tests
```

Frontend build:

```powershell
cd frontend
npm run build
```

The same scripts can be run with pnpm, for example `pnpm run build`.

## API Endpoints

- `GET /api/health`
- `GET /api/mission-control`
- `GET /api/race-state`
- `GET /api/telemetry`
- `GET /api/advanced-telemetry`
- `GET /api/simulations`
- `POST /api/scenario-simulation`
- `GET /api/agent-debate`
- `GET /api/rival-twins`
- `GET /api/strategy-recommendations`
- `GET /api/decisions`
- `POST /api/decisions/log`
- `GET /api/race-memory`
- `GET /api/memory/session`
- `GET /api/performance-analytics`
- `GET /api/settings`
- `GET /api/data-source/status`
- `POST /api/data-source/connect`
- `POST /api/data-source/disconnect`
- `GET /api/openf1/sessions`
- `GET /api/openf1/latest-session`
- `GET /api/openf1/drivers?session_key=`
- `GET /api/openf1/telemetry?session_key=&driver_number=`
- `GET /api/openf1/weather?session_key=`
- `GET /api/openf1/positions?session_key=`

## Folder Structure

```text
backend/
  app/
    main.py
    schemas.py
    data.py
  tests/
frontend/
  src/
    layout/
    pages/
    components/
    data/
    services/
    styles/
Dockerfile
docker-compose.yml
requirements.txt
```

## Demo Disclaimer

Quantum Race is a fictional demo and research project. It is not affiliated with Formula 1, FIA, Red Bull Ring, any driver, or any racing team. All race data, team names, strategy outputs, simulations, agents, and rival twins are synthetic demo data.
