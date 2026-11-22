# SARA C2 demo in Google AI Studio: project context

Date: 22 November 2026 (v1). Owner: Israel.

Read this before any task in this repository. It decides what is built here and how. Only Israel changes it.

## 1. What this repository is

A demo of the SARA C2 screens, built with Google AI Studio (Build mode), so that Uri and rescue operators can see and click through the product.

It is a demo, not the product. It is not for operational use.

## 2. Separate from `sara-rescue-project-dev`

This repository and `sara-rescue-project-dev` are disconnected.

- No shared code, no submodule, no package from one used in the other.
- The rules of that repository (`CLAUDE.md`, `docs/PROJECT_CONTEXT.md`, its agents and skills, its stack) do not apply here.
- This document does not apply there. Nothing here changes that repository's plan, issues or context.
- Work in this repository never edits, opens issues in, or opens pull requests against `sara-rescue-project-dev`.

## 3. What Uri wants

The source is Uri's UI design, `design/SARA_C2_simulation.html` in this repository (November 2026): a single-page simulation of a rescue command post console. It is the UX spec: screens, panes, flows, status chips and wording. Open it in a browser to click through it. It is a reference, not part of the app: do not edit it.

Three screens:

1. **Command.** List of events, and event setup in three steps: event type, location and time, and data sources; mark the hit buildings on the map by click or polygon, with a severity per building; building files created.
2. **Area view.** KPI row; map with modes (current aerial, swipe compare, pre-disaster, GIS map, 3D area); layer panel; side tabs: Priority, Phones, Reports, Residents, Buildings, Assets, Log.
3. **Building file.** Header (address, severity, facts, priority, file completeness, team, previous and next) and a grid of panes: Current aerial, 3D model, Location, Pre-disaster aerial, Street view, Blueprint and architecture, Residents, Reports, Phones detected, Data layers in this file.

The top bar shows the event, the T+ clock, the simulation speed controls (pause, 1×, 5×, 20×, +15m, +1h) and the field kit or Starlink state.

Uri's answers on the demo (20 November 2026):

1. Every screen in the design appears in the demo, even where it shows simulated data.
2. The residents register per building and per flat is in the first demo.
3. The UI is in English.
4. The commander sets the priority. There is no formula and no computed score.
5. The demo must run over any building, without breaking one. Severity can be "No damage".
6. The demo is in Israel.

Where the design and these answers disagree, the answers win. Two places are known:

- The design computes a priority score from 0 to 99. Here the commander orders the buildings and can write a reason; buildings not yet ordered show as "Not ranked".
- The design offers preset locations, one of them outside Israel. Here locations are in Israel only.

## 4. Rules for this demo

- **Simulated data only.** No real names, phone numbers, IMSI, addresses of real residents, drone footage or incident data, in the code, the seed data, the prompts or the deployed app.
- **Simulated is always visible.** Every pane, chip and KPI that shows simulated data carries a "Simulated" label. The Phones panes also carry the design's "Phase 2" label.
- **Residents show no names.** Flat number, floor, number of registered residents and status only.
- **A missing layer shows as unavailable, never empty.** Keep the design's chips: Pending, Loading, Ready, Needs Starlink, Inferred.
- **No secrets in the repository.** API keys stay in AI Studio's server-side secrets and in the hosting environment, never in client code or in git.
- **English UI.**

## 5. How it is built

- Google AI Studio Build mode generates the app: a web frontend (React by default) and a Node.js server side. This repository holds the code AI Studio produces.
- Google services that AI Studio offers (for example Google Maps data, Gemini) may be used here.
- The app is published from AI Studio to Cloud Run.
- The demo needs a network connection. Working offline is out of scope here.

## 6. Order of work

Each slice ends in something Uri can open and click.

1. Shell and Command: top bar, event setup in three steps, building files.
2. Area view: map modes, layer panel, KPIs, side tabs.
3. Building file: header and the pane grid, with Data layers.
4. Residents register: pane, tab and KPI.
5. Commander's priority: ordered list with reasons, shown on the map and in the building file header.
6. The remaining simulated panes: Reports, Phones, Blueprint by floor, Street view, Assets, Log.
7. The timeline: events appear over simulated time, driven by the speed controls.

## 7. Open for Israel and Uri

- Which Google account holds the AI Studio project and its billing.
- Who works in AI Studio (Israel, Uri or an agent), and whether code is also edited directly in this repository.
- Who may open the published app, and whether its URL is shared outside the team.
