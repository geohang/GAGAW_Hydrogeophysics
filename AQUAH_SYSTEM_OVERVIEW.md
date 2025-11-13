# AQUAH System Overview

## Autonomous Query-driven Understanding Agent for Hydrogeophysics

### 🎯 Vision

AQUAH transforms complex geophysical data processing into a natural language conversation. Researchers and practitioners can describe their analysis goals in plain English, and AQUAH handles the rest - from workflow selection to comprehensive reporting.

---

## 🌟 Key Innovation

### From Code to Conversation

**Traditional Approach:**
```python
# Manual workflow setup (50+ lines of code)
from PyHydroGeophysX.agents import *

loader = ERTLoaderAgent()
data = loader.execute({'file': 'data.ohm'})

inverter = ERTInversionAgent()
model = inverter.execute({'data': data, 'lambda': 20})

petro = PetrophysicsAgent()
wc = petro.execute({'resistivity': model, 'params': {...}})
# ... and so on
```

**AQUAH Approach:**
```python
# Natural language workflow (3 lines!)
user_request = """
Run ERT inversion on data.ohm with lambda=20,
convert to water content using porosity=0.35
"""

results = BaseAgent.run_unified_agent_workflow(
    config=context_agent.parse_request(user_request),
    api_key=api_key, llm_model='gpt-4o-mini', 
    llm_provider='openai', output_dir='results'
)
```

---

## 🏗️ Architecture

### Three-Layer Design

```
┌─────────────────────────────────────────────────────┐
│          USER INTERFACE LAYER                       │
│  ┌──────────────────┐    ┌──────────────────┐     │
│  │   Web App        │    │  Jupyter         │     │
│  │   (Streamlit)    │    │  Notebooks       │     │
│  └──────────────────┘    └──────────────────┘     │
└─────────────────────────────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────────────┐
│       AI ORCHESTRATION LAYER                        │
│  ┌──────────────────────────────────────────────┐  │
│  │  ContextInputAgent (LLM-powered parsing)     │  │
│  │  - Extracts parameters from natural language │  │
│  │  - Handles geological descriptions           │  │
│  │  - Supports GPT-4, Gemini, Claude           │  │
│  └──────────────────────────────────────────────┘  │
│                      ↓                              │
│  ┌──────────────────────────────────────────────┐  │
│  │  WorkflowOrchestratorAgent                   │  │
│  │  - Detects workflow type (ERT/TL/Fusion)    │  │
│  │  - Coordinates agent execution               │  │
│  │  - Manages data flow                         │  │
│  └──────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────────────┐
│       SPECIALIZED AGENT LAYER                       │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │   ERT    │  │ Seismic  │  │ Climate  │         │
│  │  Agents  │  │  Agent   │  │  Agent   │         │
│  └──────────┘  └──────────┘  └──────────┘         │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │ Petro-   │  │  Report  │  │ Structure│         │
│  │ physics  │  │  Agent   │  │ Constr.  │         │
│  └──────────┘  └──────────┘  └──────────┘         │
└─────────────────────────────────────────────────────┘
```

---

## 🔄 Workflow Types

### 1. Standard ERT Workflow

**Input:** Single ERT dataset  
**Output:** Resistivity model + water content + uncertainty

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   ERT Data  │ ──> │  Inversion   │ ──> │ Resistivity │
└─────────────┘     └──────────────┘     └─────────────┘
                                                 │
                    ┌──────────────┐            ↓
                    │ Monte Carlo  │ <── ┌─────────────┐
                    │ Uncertainty  │     │ Petrophysics│
                    └──────────────┘     │  Transform  │
                            │            └─────────────┘
                            ↓                   ↓
                    ┌─────────────────────────────────┐
                    │   Water Content ± Uncertainty   │
                    └─────────────────────────────────┘
```

### 2. Time-Lapse Workflow

**Input:** Multiple ERT files over time  
**Output:** Temporal changes + climate correlation

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐
│ Time-Series │ ──> │  Temporal    │ ──> │ Resistivity  │
│  ERT Data   │     │  Inversion   │     │   Changes    │
└─────────────┘     └──────────────┘     └──────────────┘
                                                 │
┌─────────────┐     ┌──────────────┐           ↓
│ DayMet API  │ ──> │   Climate    │ ──> ┌──────────────┐
│ (automatic) │     │   Data +PET  │     │  Correlation │
└─────────────┘     └──────────────┘     │   Analysis   │
                                          └──────────────┘
```

### 3. Multi-Method Data Fusion

**Input:** Seismic + ERT data  
**Output:** Structure-constrained water content

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐
│   Seismic   │ ──> │   Velocity   │ ──> │  Interface   │
│    Data     │     │   Inversion  │     │  Extraction  │
└─────────────┘     └──────────────┘     └──────────────┘
                                                 │
                                                 ↓
┌─────────────┐                          ┌──────────────┐
│   ERT Data  │ ─────────────────────> │  Structure-  │
└─────────────┘                          │ Constrained  │
                                          │  Inversion   │
                                          └──────────────┘
                                                 │
                    ┌──────────────┐            ↓
                    │ Layer-Specific| <── ┌─────────────┐
                    │ Petrophysics  │     │ Resistivity │
                    └──────────────┘     │    Model    │
                            │            └─────────────┘
                            ↓
                    ┌─────────────────────────────────┐
                    │ Water Content by Layer ± Uncert.│
                    └─────────────────────────────────┘
```

---

## 📊 Feature Comparison

### Workflow Capabilities Matrix

|                    | Standard | Time-Lapse | Data Fusion |
|--------------------|:--------:|:----------:|:-----------:|
| **Basic Features**     |          |            |             |
| ERT Inversion          | ✅       | ✅         | ✅          |
| Water Content          | ✅       | ✅         | ✅          |
| Uncertainty (MC)       | ✅       | ✅         | ✅          |
| Topography Support     | ✅       | ✅         | ✅          |
| **Advanced Features**  |          |            |             |
| Temporal Analysis      | ❌       | ✅         | ❌          |
| Climate Integration    | ❌       | ✅         | ❌          |
| Seismic Integration    | ❌       | ❌         | ✅          |
| Structure Constraints  | ❌       | ❌         | ✅          |
| Layer-Specific Params  | ❌       | ❌         | ✅          |
| **Output Products**    |          |            |             |
| Resistivity Model      | ✅       | ✅         | ✅          |
| Water Content Maps     | ✅       | ✅         | ✅          |
| Time-Series Plots      | ❌       | ✅         | ❌          |
| Climate Correlation    | ❌       | ✅         | ❌          |
| Velocity Model         | ❌       | ❌         | ✅          |
| Interface Coordinates  | ❌       | ❌         | ✅          |

---

## 🎯 Use Cases

### 1. Academic Research

**Scenario:** PhD student studying soil moisture dynamics  
**Challenge:** Limited programming experience  
**AQUAH Solution:**
```
"I have monthly ERT surveys from June to September.
Compare resistivity changes with precipitation data
from weather station at 40.5°N, -105.2°W."
```
→ Automatic time-lapse analysis with climate integration

### 2. Environmental Consulting

**Scenario:** Characterize contaminated site geology  
**Challenge:** Complex bedrock interface  
**AQUAH Solution:**
```
"Use seismic to find bedrock at 1200 m/s threshold,
then run ERT constrained by this interface.
Convert to water content for upper soil (porosity 0.4)
and lower bedrock (porosity 0.15)."
```
→ Structure-constrained multi-method fusion

### 3. Hydrological Monitoring

**Scenario:** Track seasonal water table changes  
**Challenge:** Need climate context for interpretation  
**AQUAH Solution:**
```
"Process 8 quarterly ERT surveys from 2023-2024.
Fetch precipitation and temperature for the site.
Calculate potential evapotranspiration."
```
→ Time-lapse with automated climate analysis

---

## 🚀 Getting Started

### Quick Start (3 Steps)

1. **Install PyHydroGeophysX:**
   ```bash
   pip install pyhydrogeophysx
   ```

2. **Get an LLM API key:**
   - OpenAI: https://platform.openai.com/
   - Google: https://ai.google.dev/
   - Anthropic: https://www.anthropic.com/

3. **Launch AQUAH Web App:**
   ```bash
   cd GAGAW_Hydrogeophysics
   streamlit run app_geophysics_workflow.py
   ```

### Your First Analysis

1. Enter your API key in the sidebar
2. Click "Initialize System"
3. Describe your workflow:
   ```
   "I have ERT data from DAS-1 instrument.
   File: data/ERT/DAS/survey.Data
   Electrode positions: data/ERT/DAS/electrodes.dat
   Site: sandy soil over granite bedrock.
   Convert to water content."
   ```
4. Click "Run Workflow"
5. Download results!

---

## 📈 Performance

### Benchmarks (Typical Datasets)

| Workflow | Dataset Size | Processing Time | Agent Calls |
|----------|-------------|-----------------|-------------|
| Standard ERT | 500 measurements | 2-3 minutes | 4-5 |
| Time-Lapse (4 times) | 2000 measurements | 5-8 minutes | 6-8 |
| Data Fusion | Seismic + ERT | 8-12 minutes | 8-10 |

*Times include inversion, uncertainty quantification, and report generation*

### LLM Token Usage (Approximate)

| Task | Tokens | Cost (GPT-4-mini)* |
|------|--------|-------------------|
| Natural Language Parsing | 1,000-2,000 | $0.001-0.002 |
| Parameter Extraction | 500-1,000 | $0.0005-0.001 |
| Report Generation | 2,000-3,000 | $0.002-0.003 |
| **Total per Workflow** | **3,500-6,000** | **$0.004-0.006** |

*Costs as of 2025, using GPT-4o-mini pricing

---

## 🔍 Advanced Features

### 1. Automatic Parameter Estimation

AQUAH understands geological descriptions:

**Input:**
```
"Mountain meadow with shallow fractured bedrock.
Sandy loam soil above weathered granite."
```

**AQUAH Interprets:**
- Soil layer: Higher porosity (0.35-0.45), lower resistivity
- Bedrock: Lower porosity (0.15-0.25), higher resistivity
- Boundary: Likely 2-4m depth from "shallow"

### 2. Multi-Format Support

Automatic detection of:
- E4D (*.ohm)
- BERT (*.dat)
- DAS-1 (*.Data)
- Syscal (*.dat with specific format)
- Generic formats with coordinate information

### 3. Intelligent Quality Control

AQUAH automatically:
- Detects outliers in apparent resistivity
- Checks electrode spacing consistency
- Validates data-model fit (chi-squared)
- Warns about poor data coverage
- Suggests regularization parameter adjustments

### 4. Climate Data Integration

**Automated Fetching:**
- DayMet: North American high-resolution daily data
- Open-Meteo: Global weather API
- Automatic coordinate conversion
- PET computation (Penman-Monteith, Priestley-Taylor)

**Derived Features:**
- Antecedent precipitation (1, 3, 7, 14 days)
- P-PET water balance
- Growing degree days
- Temporal alignment with ERT timestamps

---

## 📚 Example Gallery

### Standard ERT: Soil Moisture Mapping

**Natural Language Input:**
```
ERT survey at Wyoming test site using DAS-1 instrument.
Data: survey_20231015.Data
Electrodes: electrodes.dat
Site: grassland over shale bedrock
Estimate water content with uncertainty
```

**AQUAH Output:**
- Resistivity: 20-800 Ωm
- Water Content: 0.15-0.42
- Uncertainty: ±0.05 (mean std)
- Coverage: 85% of model domain
- Chi-squared: 1.2 (excellent fit)

### Time-Lapse: Infiltration Monitoring

**Natural Language Input:**
```
Monitor irrigation infiltration with 5 time-lapse ERT surveys.
Baseline: pre_irrigation.ohm
Times 1-4: day1.ohm, day2.ohm, day3.ohm, day7.ohm
Fetch weather data for coordinates (40.2°N, -105.5°W)
Calculate water balance
```

**AQUAH Output:**
- Resistivity change: -40% in top 1m (wetting)
- Infiltration rate: ~15 cm/day
- Climate correlation: P-PET = +25mm during period
- Drainage phase: Starting day 4

### Data Fusion: Bedrock Characterization

**Natural Language Input:**
```
Characterize regolith-bedrock interface using seismic + ERT.
Seismic: traveltime_line1.dat
ERT: resistivity_line1.dat
Velocity threshold: 1500 m/s
Layer-specific petrophysics:
- Regolith: porosity 0.3-0.5, highly variable
- Bedrock: porosity 0.1-0.2, more uniform
```

**AQUAH Output:**
- Interface depth: 2.8m (±0.3m uncertainty)
- Regolith: 45-180 Ωm, water content 0.25-0.45
- Bedrock: 250-1200 Ωm, water content 0.05-0.15
- Structure constraint improves ERT resolution by ~30%

---

## 💡 Best Practices

### Writing Effective Natural Language Requests

**✅ DO:**
- Specify file paths or upload files
- Include geological context when available
- Mention specific parameter values if known
- State your analysis goals clearly

**❌ DON'T:**
- Be overly vague ("process my data")
- Mix incompatible workflow types
- Omit critical information (instrument type, site location)

### Example Requests

**Good:**
```
"Run standard ERT inversion on E4D data file survey.ohm
located in clay-rich floodplain. Use lambda=15 for
moderate smoothing. Convert to water content assuming
porosity of 0.4."
```

**Could be better:**
```
"Process survey.ohm and get water content"
```
(Missing instrument, geological context, regularization)

---

## 🐛 Troubleshooting

### Common Issues

**1. "API key not found"**
- Set environment variable: `export OPENAI_API_KEY='your-key'`
- Or enter in web app sidebar

**2. "Workflow type could not be determined"**
- Be more specific about data types (ERT, seismic)
- Explicitly state workflow type if needed

**3. "Climate data fetch failed"**
- Check internet connection
- Verify coordinates are within DayMet range (North America)
- Allow conda environment creation on first run

**4. "Inversion did not converge"**
- Data quality issues (check pseudo-section)
- Try different lambda value
- Check electrode spacing consistency

---

## 🔬 Under the Hood

### How AQUAH Works

1. **Natural Language Understanding:**
   - LLM extracts structured configuration from text
   - Geological context → parameter estimates
   - Ambiguity resolution through domain knowledge

2. **Workflow Detection:**
   - Rule-based analysis of configuration
   - File count, keywords, method combinations
   - Fallback to explicit user specification

3. **Agent Coordination:**
   - WorkflowOrchestrator manages execution plan
   - Agents pass data through standardized interfaces
   - Error handling and recovery at each step

4. **Result Synthesis:**
   - ReportAgent aggregates outputs
   - LLM generates interpretations
   - Visualizations created automatically

### Technology Stack

- **Frontend:** Streamlit (web app)
- **LLM Integration:** OpenAI API, Google Generative AI, Anthropic
- **Geophysics:** PyGIMLi, RESIPY
- **Climate Data:** DayMet API, Open-Meteo
- **Scientific Computing:** NumPy, SciPy, Matplotlib
- **Data Processing:** pandas, xarray

---

## 📖 Further Reading

### Documentation
- [AQUAH GitHub](https://github.com/geohang/GAGAW_Hydrogeophysics)
- [PyHydroGeophysX Docs](https://pyhydrogeophysx.readthedocs.io/)

### Scientific Background
- Waxman-Smits Model: Waxman & Smits (1968) SPE Journal
- Time-Lapse ERT: Karaoulis et al. (2011) Geophysics
- Structure Constraints: Doetsch et al. (2012) Geophysics

### Related Tools
- PyGIMLi: https://www.pygimli.org/
- RESIPY: https://gitlab.com/hkex/resipy
- DayMet: https://daymet.ornl.gov/

---

## 🎉 Summary

**AQUAH democratizes geophysical data processing by:**
- ✅ Eliminating programming barriers
- ✅ Automating workflow selection and coordination
- ✅ Providing AI-powered interpretation
- ✅ Integrating multiple data sources seamlessly
- ✅ Generating publication-ready outputs

**Try AQUAH today and experience the future of geophysical data analysis!**

---

*Documentation Version: 1.0 | Last Updated: 2025 | Maintainer: Hang Chen (hangchen.work@gmail.com)*

