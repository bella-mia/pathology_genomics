# Contain the Outbreak

An interactive epidemiology game built on a SEIRD (Susceptible → Exposed → Infectious → Recovered → Dead) agent-based model. Pick a real-world pathogen, deploy public-health interventions under realistic constraints, and try to contain the outbreak before it overwhelms the population.

Lives in `outbreak_game.ipynb`.

---

## How to play

1. **Pick a pathogen** from the dropdown. The card updates with that disease's R₀, incubation period, case fatality rate, transmission mode, and historical context.
2. **Click `▶ Start / Reset`** to seed the simulation with those parameters.
3. Each click on an intervention advances the simulation by one step. The game ends when:
   - the pathogen is **eradicated** (no infectious + no incubating) → success
   - the population is **wiped out** → failure
   - **100 steps** elapse → partial outcome with final stats

## The seven outbreaks

All parameters come from published epidemiological data (WHO, CDC, peer-reviewed reviews).

| Pathogen | R₀ | Incubation | CFR | Vaccine? | Why it's interesting |
|---|---|---|---|---|---|
| 🦠 **COVID-19** (2020) | 2.8 | 5 d | 1.5% | Yes | Moderate everything; asymptomatic spread is the killer |
| 🩸 **Ebola** (2014) | 1.8 | 8 d | 50% | Yes (+2 step delay) | High CFR burns out contact networks fast |
| 🌬️ **1918 Flu (H1N1)** | 2.5 | 2 d | 2.5% | **No** | Short incubation = rapid spread; must research vaccine |
| 🦇 **Nipah** | 0.48 | 10 d | 72% | **No** | Low R₀ but lethal; WHO priority pathogen |
| 👶 **Measles** | 15.0 | 11 d | 0.2% | Yes | Most contagious human virus — coverage gaps = outbreaks |
| 💨 **SARS** (2003) | 2.9 | 5 d | 9.6% | **No** | Historically contained by quarantine alone |
| 🐦 **H5N1** (pandemic-adapted) | 2.0 | 3 d | 53% | Yes (+3 step delay) | Hypothetical: if H5N1 gained H2H transmission |

## Your interventions

| Action | Effect | Cost |
|---|---|---|
| 💉 **Vaccinate** | Immunizes up to 5 susceptibles (priority: those in safe zones) | 1 dose, 5-step cooldown. Grayed out if pathogen has no vaccine |
| 🚧 **Quarantine** | Cuts transmission chance by ~78% **for that step only** | 3-step cooldown |
| 🏥 **Supply** | Every infectious person has 35% chance of recovering; vaccine stock +2 | 4-step cooldown |
| 🔬 **Research** | Adds 12–22% progress toward developing a vaccine. At 100%, 4 doses become available | No cooldown. Only useful when pathogen has no vaccine |
| ⏩ **Wait** | Advance one step with no intervention | Free |

## Reading the dashboard

**KPI row** (top):
- **R₀ (observed)** — rolling estimate of new infections per existing case; turns green when <1 (outbreak declining)
- **Susceptible / Incubating / Infectious / Recovered / Deaths** — live SEIRD counts
- **CFR observed** vs. the pathogen's real CFR — noisy early, converges with more cases

**Map** (left plot):
- Blue dots = susceptible · Teal ✚ = vaccinated · Purple ◆ = incubating (hidden threat) · Red ✖ = infectious · Green ■ = recovered
- Blue dashed circles = safe zones, labeled `occupied/capacity` and `hit points`
- Zones degrade when infectious agents attack them or when incubating agents inside turn infectious

**SEIRD curves** (right plot):
- All five state counts over time, plus R₀ estimate on a second axis

## The model in one paragraph

Agents random-walk on a 50×50 grid. Infection fires when an infectious agent comes within a pathogen-specific radius of a susceptible, with a per-contact probability tuned to reproduce the target R₀. Exposed agents progress to infectious after the pathogen's incubation period. Each step an infectious agent has a per-step mortality derived from `1 − (1 − CFR)^(1/recovery_steps)`; survivors recover and gain immunity. Safe zones are opportunistic shelters — susceptibles passing near them enter when capacity permits and gain infection immunity while inside, but zones decay from external attacks and from within when incubating occupants turn. Every 10–15 steps, a mutation event can fire (+22% radius, +18% transmission chance) to model viral evolution.

## Tips

- **High-CFR, low-R₀ pathogens** (Ebola, Nipah) mostly self-limit. Don't waste vaccine doses — focus on zones and supply.
- **High-R₀ pathogens** (Measles, COVID) need **vaccinate early, vaccinate often**. Quarantine buys you time.
- **No-vaccine pathogens** (1918 flu, SARS, Nipah) require **Research** from turn one. Expect losses before it lands.
- **Watch for purple dots inside zones** — they'll breach from within when they turn infectious.
- **Mutations** make late-game harder. Try to end the outbreak before step 30.

## Running it

```bash
source venv/bin/activate
jupyter lab outbreak_game.ipynb        # or: voila outbreak_game.ipynb
```

Voilà gives the cleanest play experience — it hides the code and renders just the dashboard.
