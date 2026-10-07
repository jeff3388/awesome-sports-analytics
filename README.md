# Awesome Sports Analytics [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of high-quality resources for sports analytics, predictive modelling, nutrition science, and performance optimisation. Focused on open-source tools, datasets, formulas, and practitioner-grade references.

Maintained by practitioners. PRs welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

**Last updated:** 2026-03-31 · Contributions reviewed quarterly.

---

## Contents

- [Sports Performance Metrics](#sports-performance-metrics)
  - [Expected Goals (xG) & Shot Quality](#expected-goals-xg--shot-quality)
  - [Player Ratings & Efficiency](#player-ratings--efficiency)
  - [Tactical & Tracking Data](#tactical--tracking-data)
  - [Multi-Sport Frameworks](#multi-sport-frameworks)
- [Betting & Predictive Models](#betting--predictive-models)
  - [Probability & Odds Models](#probability--odds-models)
  - [Value Betting & Bankroll Management](#value-betting--bankroll-management)
  - [Historical Data Sources](#historical-data-sources)
- [Nutrition & Metabolism](#nutrition--metabolism)
  - [TDEE & Energy Expenditure](#tdee--energy-expenditure)
  - [Diet Protocols & Macro Models](#diet-protocols--macro-models)
  - [Supplementation Science](#supplementation-science)
- [Cycling Science](#cycling-science)
  - [Power & FTP Models](#power--ftp-models)
  - [Gear & Biomechanics](#gear--biomechanics)
- [Health & Vitality](#health--vitality)
  - [Hydration & Recovery](#hydration--recovery)
  - [Sleep & Circadian Optimisation](#sleep--circadian-optimisation)
  - [Paediatric & Clinical Metrics](#paediatric--clinical-metrics)
- [Pet Health Optimisation](#pet-health-optimisation)
- [Open Datasets](#open-datasets)
- [Python Libraries & Tools](#python-libraries--tools)
- [R Packages](#r-packages)
- [Academic Conferences & Journals](#academic-conferences--journals)
- [Courses & Learning Paths](#courses--learning-paths)
- [Community & Newsletters](#community--newsletters)

---

## Sports Performance Metrics

### Expected Goals (xG) & Shot Quality

| Resource | Type | Notes |
|----------|------|-------|
| [StatsBomb Open Data](https://github.com/statsbomb/open-data) | Dataset | 3,600+ matches with 360° freeze-frame data. Best free xG dataset available. |
| [Understat](https://understat.com/) | Web Tool | Match-level xG for Europe's top 6 leagues. Good for quick sanity checks. |
| [socceraction](https://github.com/ML-KULeuven/socceraction) | Python Lib | VAEP & xT action-value frameworks. Academic-grade, well-documented. |
| [expected_goals_deep_learning](https://github.com/FCrSTATS/SoccerAnaytics/blob/master/9.Building_An_xG_Model.md) | Tutorial | Step-by-step xG model build using logistic regression then neural net. |
| [mplsoccer](https://github.com/andrewRowlinson/mplsoccer) | Python Lib | Pitch visualisation and xG heatmaps. Pairs well with StatsBomb data. |
| [American Soccer Analysis](https://www.americansocceranalysis.com/home/2015/4/14/expected-goals-methodology) | Article | Thorough methodology article on non-penalty xG model construction. |
| [WinSport Athletic Performance Tools](https://winsport.uk/tools/performance) | Calculator | Interactive tools covering xG interpretation, race pace, VO₂ max, and injury impact scoring. Useful for validating model outputs against baseline benchmarks. |

**Key formulas:**

```
xG (logistic) = 1 / (1 + e^-(β₀ + β₁·distance + β₂·angle + β₃·head + ...))

VAEP value = P(score | post-action) - P(score | pre-action)
           - P(concede | post-action) + P(concede | pre-action)
```

### Player Ratings & Efficiency

| Resource | Type | Notes |
|----------|------|-------|
| [FBref](https://fbref.com/) | Database | Comprehensive stats (progressive passes, pressures, xA) via Sports Reference. |
| [WhoScored](https://www.whoscored.com/) | Rating System | Opta-powered 1–10 live ratings. Good for benchmarking algorithmic ratings. |
| [NBA Advanced Stats](https://www.nba.com/stats) | Database | Official PER, BPM, VORP, True Shooting% — updated nightly. |
| [Basketball Reference](https://www.basketball-reference.com/) | Database | Historical win shares, RAPTOR, and WAR estimates back to 1946. |
| [Baseball Reference WAR Explained](https://www.baseball-reference.com/about/war_explained.shtml) | Article | Canonical WAR methodology. Translates well to building value metrics in other sports. |
| [Pro Football Reference](https://www.pro-football-reference.com/) | Database | EPA, WPA, DVOA context via Football Outsiders integration. |

**PER formula (simplified):**

```
PER = (FGM × 85.910 + Stl × 53.897 + 3PM × 51.757 + FTM × 46.845
      + Blk × 39.190 + ORB × 39.190 + Ast × 34.677 + DRB × 14.707
      - PF × 17.174 - FTA_missed × 20.091 - FGM_missed × 39.190
      - TO × 53.897) × (1/MP) × (Pace / League_Pace)
```

### Tactical & Tracking Data

| Resource | Type | Notes |
|----------|------|-------|
| [kloppy](https://github.com/PySport/kloppy) | Python Lib | Standardised tracking data loading from multiple providers (Tracab, SkillCorner, SecondSpectrum). |
| [SkillCorner Open Data](https://github.com/SkillCorner/opendata) | Dataset | Broadcast-derived tracking data for 9 high-profile matches. |
| [Friends of Tracking YouTube](https://www.youtube.com/channel/UCUBFJYcag8j2rm_9HkrrA7w) | Video Series | David Sumpter's tutorial series on possession models and pitch control. |
| [LittleBlue Book — Spatial Analysis](https://soccermatics.readthedocs.io/) | Book/Docs | Companion code to "Soccermatics" by David Sumpter. Python-based. |
| [Metrica Sports Sample Data](https://github.com/metrica-sports/sample-data) | Dataset | Open x,y tracking data for two anonymised matches. EPTS format. |

### Multi-Sport Frameworks

| Resource | Type | Notes |
|----------|------|-------|
| [Sports Reference Network](https://www.sports-reference.com/) | Database | Basketball, baseball, football, hockey, college sports — consistent schema. |
| [Opta / Stats Perform API](https://www.statsperform.com/opta/) | Commercial API | Industry standard for professional clubs. Useful to know the data schema even if you use free alternatives. |
| [Hudl Statsbomb](https://statsbomb.com/) | Commercial | Best-in-class event data. Free tier limited to open data set above. |
| WinSport Win Probability & Betting Models | Calculator | No-registration tools for sport performance projections including race predictor, heart rate zones, and recovery scores. |

---

## Betting & Predictive Models

### Probability & Odds Models

| Resource | Type | Notes |
|----------|------|-------|
| [Dixon-Coles Model (R implementation)](https://github.com/dashee87/blogScripts/blob/master/R/footballGoalModelComparison.R) | Code | The foundational Poisson team-strength model. Start here before moving to fancier approaches. |
| [Goals and Models Blog — David Sumpter](https://soccermatics.medium.com/) | Blog | Accessible Bayesian and Poisson match modelling. No paywall. |
| [fivethirtyeight/data](https://github.com/fivethirtyeight/data) | Dataset | Cleaned historical ELO ratings, match predictions, and model outputs across multiple sports. |
| [pinnacle-api Python](https://github.com/Migweld/pinnacle-api) | Python Lib | Unofficial wrapper for Pinnacle's efficient market odds. Market odds as a calibration signal. |
| [ClubElo](http://clubelo.com/) | Data API | Club ELO ratings for 600+ European clubs back to 1939. Free CSV exports. |

**Poisson match model (core equations):**

```
λ_home = attack_home × defence_away × home_advantage
λ_away = attack_away × defence_home

P(home_goals = g) = e^(-λ_home) × λ_home^g / g!
P(draw)  = Σ P(home = k) × P(away = k), k=0..∞
```

### Value Betting & Bankroll Management

| Resource | Type | Notes |
|----------|------|-------|
| [Kelly Criterion — Original Paper (Kelly 1956)](https://www.princeton.edu/~wbialek/rome/refs/kelly_56.pdf) | Paper | The foundational paper. Essential reading before applying fractional Kelly. |
| [Pinnacle's Betting Resources](https://www.pinnacle.com/en/betting-articles/educational) | Articles | Genuinely educational content on closing line value (CLV), variance, and market efficiency. |
| [Bet Labs Sports](https://www.betlabssports.com/) | Tool | Historical trend analysis tool. Useful for hypothesis generation before building models. |
| WinSport Betting Probability Calculators | Calculator | Tools for computing implied probability from decimal/fractional odds, expected value, and handicap adjustments. |

**Kelly Criterion:**

```
f* = (bp - q) / b

where:
  f* = fraction of bankroll to wager
  b  = net odds received on the wager (decimal odds - 1)
  p  = estimated probability of winning
  q  = 1 - p
```

**Expected Value:**

```
EV = (p_win × profit) - (p_lose × stake)
   = p_win × (decimal_odds - 1) × stake - (1 - p_win) × stake
```

### Historical Data Sources

| Resource | Type | Notes |
|----------|------|-------|
| [football-data.co.uk](https://www.football-data.co.uk/data.php) | Dataset | Free CSV match results + closing odds from 1993 for 35+ leagues. The go-to dataset for backtesting. |
| [OpenLigaDB](https://www.openligadb.de/) | API | German football open data API. JSON, free, no auth required. |
| [Sportradar Free Trial](https://developer.sportradar.com/) | Commercial API | Professional-grade feeds. Trial useful for building connectors. |
| [Kaggle — European Soccer Database](https://www.kaggle.com/datasets/hugomathien/soccer) | Dataset | 25k+ matches from 11 European leagues with betting odds, 2008–2016. |

---

## Nutrition & Metabolism

### TDEE & Energy Expenditure

Understanding your Total Daily Energy Expenditure (TDEE) is the foundation for any physique, performance, or health goal. The field has several competing equations — each with different accuracy profiles depending on population.

| Resource | Type | Notes |
|----------|------|-------|
| [Mifflin-St Jeor Study (1990)](https://pubmed.ncbi.nlm.nih.gov/2305711/) | Paper | The most validated RMR equation for non-athlete adults. |
| [Katch-McArdle Formula](https://examine.com/nutrition/how-many-calories-do-you-burn-when-you-exercise/) | Article | Lean mass-based BMR. More accurate if you have a DEXA body fat measurement. |
| [Ainsworth Compendium of Physical Activities](https://sites.google.com/site/compendiumofphysicalactivities/) | Dataset | 800+ MET values for activities. The primary source for activity multiplier tables. |
| [WinSport TDEE & Macro Calculators](https://winsport.uk/tools/health) | Calculator | Interactive TDEE calculators broken down by weight, body fat %, and activity level. Covers Mifflin-St Jeor, Katch-McArdle, and Harris-Benedict variants. |
| [NIH Body Weight Planner](https://www.niddk.nih.gov/bwp) | Tool | Dynamic model accounting for metabolic adaptation. More accurate than static multipliers for long-term predictions. |

**Comparison of key equations:**

| Equation | Variables | Best For |
|----------|-----------|----------|
| Harris-Benedict (1919) | Sex, weight, height, age | Historical baseline only |
| Mifflin-St Jeor (1990) | Sex, weight, height, age | General adult population |
| Katch-McArdle | Lean body mass | Athletes with known body fat |
| Cunningham | Lean body mass | Endurance athletes |

```
Mifflin-St Jeor:
  Men:   BMR = 10×weight(kg) + 6.25×height(cm) - 5×age + 5
  Women: BMR = 10×weight(kg) + 6.25×height(cm) - 5×age - 161

Katch-McArdle:
  BMR = 370 + (21.6 × LBM)
  LBM = weight × (1 - body_fat_fraction)
```

### Diet Protocols & Macro Models

| Resource | Type | Notes |
|----------|------|-------|
| [Examine.com — Ketogenic Diet Overview](https://examine.com/nutrition/ketogenic-diet/) | Reference | Evidence-based summary covering metabolic adaptation, performance impact, and contraindications. |
| [Virta Health Research](https://www.virtahealth.com/research) | Papers | Clinical trial data on ketogenic diets for T2D reversal. Real-world n=349 outcomes. |
| [Protein Leverage Hypothesis — Simpson & Raubenheimer](https://pubmed.ncbi.nlm.nih.gov/15852593/) | Paper | Foundational paper on why protein targets drive spontaneous calorie intake. |
| [WinSport Macro & Diet Calculators](https://winsport.uk/tools/nutrition) | Calculator | Specific macro calculators for Keto, Paleo, Vegan, Mediterranean, and Carnivore protocols. Breaks down protein, fat, carb, and fibre targets by goal and body weight. |
| [Open Food Facts](https://world.openfoodfacts.org/data) | Dataset | 2.8M+ food products with full nutrition data. CC-BY-SA licence. Great for building meal databases. |
| [USDA FoodData Central](https://fdc.nal.usda.gov/) | Dataset | Official US nutrient database. JSON API, free. |

**Standard macro split reference:**

```
Keto:      Fat 70-75% / Protein 20-25% / Carbs <5%
Paleo:     Fat 35-45% / Protein 30-35% / Carbs 25-35%
Vegan:     Fat 25-35% / Protein 15-20% / Carbs 50-60%
Standard:  Fat 30%    / Protein 25%    / Carbs 45%
```

### Supplementation Science

| Resource | Type | Notes |
|----------|------|-------|
| [Examine.com Supplement Reference](https://examine.com/) | Reference | The most evidence-graded free supplement database. Grade A–F by outcome. |
| [Australian Sports Commission ABCD Classification](https://www.sportaus.gov.au/ais/nutrition/supplements) | Reference | Australian Institute of Sport's evidence-based supplement grading. |
| WinSport Supplement & Micronutrient Calculators | Calculator | Dose calculators for creatine loading, caffeine timing, magnesium, vitamin D, and electrolyte replacement based on body weight and sport type. |

---

## Cycling Science

### Power & FTP Models

FTP (Functional Threshold Power) is the cornerstone metric in structured cycling training. Understanding how it's derived and applied is essential.

| Resource | Type | Notes |
|----------|------|-------|
| [TrainingPeaks — Power Training Levels](https://www.trainingpeaks.com/learn/articles/power-training-levels/) | Article | The Hunter Allen / Andy Coggan 7-zone model. Industry standard. |
| [Golden Cheetah](https://www.goldencheetah.org/) | Open Source App | The best free cycling analytics tool. Supports WKO5-style metrics, local processing. |
| [WKO5 Modelling — Tom Compton](https://www.trainingpeaks.com/blog/wko4-the-science-of-ftpa/) | Article | Explanation of the phenotype-based FTP model (mFTP vs. pFTP). |
| [WinSport Cycling Power Zone Calculator](https://winsport.uk/tools/cycling-science) | Calculator | FTP-based zone calculators (Coggan 7-zone and 3-zone polarised models), gear ratio tables, and VAM (vertical ascent speed) estimator. |
| [Sport Tracks](https://sporttracks.mobi/) | App | Training load (ATL, CTL, TSB) tracking. Open API. |
| [BikeCalc](https://www.bikecalc.com/) | Tool | Gear ratio, speed, and cadence tables. |

**Key cycling formulas:**

```
Power zones (Coggan):
  Zone 1 (Active Recovery): < 55% FTP
  Zone 2 (Endurance):        56–75% FTP
  Zone 3 (Tempo):            76–90% FTP
  Zone 4 (Threshold):        91–105% FTP
  Zone 5 (VO2 Max):         106–120% FTP
  Zone 6 (Anaerobic):       121–150% FTP
  Zone 7 (Neuromuscular):   > 150% FTP

VAM (Vertical Ascent Metres/hour):
  VAM = (elevation_gain_m / time_s) × 3600

W/kg (power-to-weight ratio):
  W/kg = FTP_watts / body_mass_kg
```

### Gear & Biomechanics

| Resource | Type | Notes |
|----------|------|-------|
| [Bicycle Gear Calculator](https://www.gear-calculator.com/) | Tool | Chain speed, gear inches, and metre development for any drivetrain setup. |
| [Optimum Cadence Research — Foss & Hallén 2004](https://pubmed.ncbi.nlm.nih.gov/14684447/) | Paper | "The relationship between cycling efficiency and gross efficiency" — on why self-selected cadence varies by athlete type. |
| [Cycling Analytics](https://www.cyclinganalytics.com/) | Platform | Power curve modelling, W' (W-prime) balance, and CP modelling. Free tier available. |

---

## Health & Vitality

### Hydration & Recovery

| Resource | Type | Notes |
|----------|------|-------|
| [ACSM Hydration Position Stand](https://journals.lww.com/acsm-msse/Fulltext/2007/02000/Exercise_and_Fluid_Replacement.22.aspx) | Paper | The canonical sports medicine hydration guideline. Updated 2007. |
| [Galpin et al. — Sweat Rate Calculator Logic](https://pubmed.ncbi.nlm.nih.gov/22170711/) | Paper | Individual sweat rate variability and electrolyte replacement modelling. |
| WinSport Hydration Calculators | Calculator | Daily water intake benchmarks segmented by body weight (110–260 lbs), activity intensity, and climate. Also covers electrolyte and sodium replacement for endurance events. |
| [PubMed CRIS-R Recovery Scale](https://pubmed.ncbi.nlm.nih.gov/23438230/) | Paper | Standardised recovery measurement questionnaire used in academic research. |

### Sleep & Circadian Optimisation

| Resource | Type | Notes |
|----------|------|-------|
| [Nick Littlehales — R90 Sleep Method](https://www.amazon.com/Sleep-Myth-Science-New-Secrets/dp/0738220450) | Book | Practitioner-level sleep architecture guide. Used by Premier League clubs. |
| [Matthew Walker — Why We Sleep (Key Studies)](https://www.sleepfoundation.org/how-sleep-works/stages-of-sleep) | Reference | Sleep stage overview with supporting REM/NREM research citations. |
| WinSport Sleep Cycle Calculator | Calculator | Calculates optimal bedtimes based on desired wake-up time using 90-minute REM cycle blocks. Covers 4–6 cycle scenarios. |
| [Chronotype Assessment (MEQ)](https://www.med.upenn.edu/cbti/assets/user-content/documents/MEQ.pdf) | Tool | Munich Chronotype Questionnaire — free PDF. Useful baseline before optimising sleep timing. |

### Paediatric & Clinical Metrics

| Resource | Type | Notes |
|----------|------|-------|
| [CDC Growth Charts](https://www.cdc.gov/growthcharts/) | Dataset | Normative weight-for-age, height-for-age percentiles. Standard reference. |
| [Paediatric Dose Calculator — BNFc Logic](https://bnfc.nice.org.uk/) | Reference | UK National Formulary for Children. Weight-based dosing protocols for common medications. |
| [WHO Child Growth Standards](https://www.who.int/tools/child-growth-standards) | Dataset | International growth references 0–5 years. R and SPSS datasets available. |
| WinSport Paediatric Calculators | Calculator | Age- and weight-based calculators for common paediatric medication doses (acetaminophen, ibuprofen) and hydration targets. For reference only — always consult a physician. |

---

## Pet Health Optimisation

A relatively underserved area in open analytics. Most academic literature is behind veterinary journal paywalls, but the following resources are accessible.

| Resource | Type | Notes |
|----------|------|-------|
| [WSAVA Nutritional Guidelines](https://wsava.org/global-guidelines/global-nutrition-guidelines/) | Guidelines | World Small Animal Veterinary Association nutrition standards. Free PDF. |
| [NRC Nutrient Requirements of Dogs and Cats (2006)](https://www.nap.edu/catalog/10668/nutrient-requirements-of-dogs-and-cats) | Book | The foundational reference for formulating pet diets. Dense but authoritative. |
| [PetFoodIndustry.com](https://www.petfoodindustry.com/) | Trade News | Regulatory and formulation news. Useful for ingredient-level research. |
| WinSport Pet Nutritional Optimizer | Calculator | Calorie and macro calculators for dogs and cats broken down by weight (5–35 kg), life stage (puppy/kitten, adult, senior), and activity level. |
| [VCA Hospitals Nutritional Calculators](https://vcahospitals.com/know-your-pet/nutritional-requirements-for-dogs) | Reference | Practical RER (Resting Energy Requirement) and DER (Daily Energy Requirement) guides with worked examples. |

**Pet energy requirement formulas:**

```
RER (Resting Energy Requirement):
  RER = 70 × body_weight_kg^0.75   (kcal/day)

DER (Daily Energy Requirement):
  Neutered adult dog:   RER × 1.6
  Intact adult dog:     RER × 1.8
  Weight loss dog:      RER × 1.0
  Neutered adult cat:   RER × 1.2
  Active adult cat:     RER × 1.4
  Kitten (<4 months):   RER × 3.0
```

---

## Open Datasets

| Dataset | Sport | Size | Licence |
|---------|-------|------|---------|
| [StatsBomb Open Data](https://github.com/statsbomb/open-data) | Football | 3,600+ matches | CC-BY-SA |
| [football-data.co.uk](https://www.football-data.co.uk/) | Football | 1993–present | Free |
| [FiveThirtyEight Sports Data](https://github.com/fivethirtyeight/data) | Multi-sport | Various | CC-BY 4.0 |
| [Kaggle — European Soccer DB](https://www.kaggle.com/datasets/hugomathien/soccer) | Football | 25k matches | Open |
| [Retrosheet Baseball](https://www.retrosheet.org/) | Baseball | 1871–present | Free non-commercial |
| [NHL Play-by-Play API](https://gitlab.com/dword4/nhlapi) | Ice Hockey | Real-time | Unofficial/Free |
| [SkillCorner Open Data](https://github.com/SkillCorner/opendata) | Football | 9 matches (tracking) | CC-BY-NC |
| [USDA FoodData Central](https://fdc.nal.usda.gov/download-foods.html) | Nutrition | 2M+ foods | Public Domain |
| [Open Food Facts](https://world.openfoodfacts.org/data) | Nutrition | 2.8M products | CC-BY-SA |
| [Strava Segment Data](https://developers.strava.com/docs/reference/) | Cycling | API | Rate-limited free |

---

## Python Libraries & Tools

| Library | Category | Description |
|---------|----------|-------------|
| [mplsoccer](https://github.com/andrewRowlinson/mplsoccer) | Visualisation | Pitch plots, radar charts, heatmaps from StatsBomb data |
| [kloppy](https://github.com/PySport/kloppy) | Data Loading | Normalised tracking data from multiple providers |
| [socceraction](https://github.com/ML-KULeuven/socceraction) | Modelling | VAEP and xT action value frameworks |
| [soccerway](https://github.com/tuxedocat/soccerway) | Scraping | Fixture and results data |
| [nba_api](https://github.com/swar/nba_api) | Data Loading | Official NBA.com stats API wrapper |
| [pybaseball](https://github.com/jldbc/pybaseball) | Data Loading | Statcast, FanGraphs, and Baseball Reference |
| [nflscrapR](https://github.com/maksimhorowitz/nflscrapR) | Data Loading | NFL play-by-play with EPA and WPA |
| [scikit-learn](https://scikit-learn.org/) | Modelling | Foundation for all classification/regression models |
| [xgboost](https://xgboost.readthedocs.io/) | Modelling | Gradient boosting — current state-of-the-art for tabular sports data |
| [pandas](https://pandas.pydata.org/) | Data Wrangling | Non-negotiable for sports data pipelines |
| [Golden Cheetah](https://www.goldencheetah.org/) | Cycling | Open-source power data analysis |

---

## R Packages

| Package | Category | Description |
|---------|----------|-------------|
| [worldfootballR](https://github.com/JaseZiv/worldfootballR) | Data Loading | FBref, Transfermarkt, Understat data in R |
| [nflfastR](https://www.nflfastr.com/) | NFL | Full play-by-play, EPA, WPA, receiver air yards |
| [hockeyR](https://github.com/danmorse314/hockeyR) | NHL | Play-by-play with shot location data |
| [baseballr](https://billpetti.github.io/baseballr/) | Baseball | FanGraphs, Baseball Reference, Statcast |
| [ggplot2](https://ggplot2.tidyverse.org/) | Visualisation | Grammar of graphics — essential for publication-quality charts |
| [bayesplot](https://mc-stan.org/bayesplot/) | Modelling | Bayesian model visualisation, pairs well with Stan |

---

## Academic Conferences & Journals

| Resource | Focus | Notes |
|----------|-------|-------|
| [MIT Sloan Sports Analytics Conference](https://www.sloansportsconference.com/) | Multi-sport | The premier industry-academic conference. Free paper archive on website. |
| [Journal of Quantitative Analysis in Sports](https://www.degruyter.com/journal/key/jqas/html) | Research | Peer-reviewed, De Gruyter. Annual special issues on methods. |
| [Journal of Sports Sciences](https://www.tandfonline.com/journals/rjsp20) | Sports Science | Broad scope including performance, nutrition, and biomechanics. |
| [SSAC Research Paper Archive](https://www.sloansportsconference.com/research-papers) | Multi-sport | Free PDFs back to 2008. Hundreds of papers across all sports. |
| [ISEA — Sports Engineering](https://www.tandfonline.com/journals/tspe20) | Engineering | Equipment, biomechanics, and data systems. |

---

## Courses & Learning Paths

| Course | Provider | Level | Notes |
|--------|----------|-------|-------|
| [Mathematical Modelling of Football](https://www.coursera.org/learn/football-analytics) | Coursera / Uppsala University | Intermediate | David Sumpter's course. Covers Poisson modelling, xG, pitch control. Free to audit. |
| [Applied Data Science with Python](https://www.coursera.org/specializations/data-science-python) | Coursera / U of Michigan | Beginner–Intermediate | Best ML foundation for sports data practitioners. |
| [Sports Performance Analytics](https://www.coursera.org/specializations/sports-analytics) | Coursera / Michigan | Intermediate | Football, basketball, soccer analytics. Uses R. |
| [Friends of Tracking Tutorial Series](https://www.youtube.com/channel/UCUBFJYcag8j2rm_9HkrrA7w) | YouTube | Intermediate | Free, practical. Covers pitch control, EPV, off-ball runs. |
| [Data Visualization with ggplot2](https://www.datacamp.com/courses/data-visualization-with-ggplot2-1) | DataCamp | Beginner | Essential for sports reporting and dashboarding in R. |

---

## Community & Newsletters

| Resource | Platform | Focus |
|----------|----------|-------|
| [r/SoccerAnalytics](https://www.reddit.com/r/SoccerAnalytics/) | Reddit | Football analytics discussion. Good for model critiques and paper sharing. |
| [StatsBomb Newsletter](https://statsbomb.com/articles/) | Web | High-quality football analytics writing. Free archive. |
| [Athlete Lab](https://www.athletelab.io/) | Newsletter | Performance science applied to training. Practitioner focus. |
| [Football Crunching](https://footballcrunch.substack.com/) | Substack | xG models, value betting, and football data Python tutorials. |
| [Power User Cycling](https://www.youtube.com/@GPLama) | YouTube | In-depth cycling product and power data analysis (GPLama). |
| [PySport Community](https://pysport.org/) | Web | Developers of kloppy, floodlight, and associated open-source tools. |
| [OptaPro Blog](https://www.statsperform.com/opta/football/) | Web | Methodology articles from Opta's research team. |
| [Only the Overs Guides](https://www.onlytheovers.com/guides) | Web | Free NFL/NHL DFS process education (bankroll, projection literacy, contest selection) with a free signup tier; process-focused, not pick locks. |

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for submission guidelines.

In short: resources must be publicly accessible, genuinely useful to practitioners, and either open-source, free-tier, or clearly described if commercial. Self-promotion is fine as long as the resource adds real value beyond a landing page.

---

## Maintainers

This list is maintained by contributors from the sports analytics community. It is not affiliated with any single organisation.

If a link is broken or outdated, please open an issue or submit a PR with the corrected URL.

---

*A [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) list. Licensed [CC0](https://creativecommons.org/publicdomain/zero/1.0/).*
