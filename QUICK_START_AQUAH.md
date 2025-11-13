# AQUAH Quick Start Guide

## 🚀 Get Started in 5 Minutes!

---

## Step 1: Installation (2 minutes)

### Install PyHydroGeophysX

```bash
pip install pyhydrogeophysx
```

### Clone this Repository

```bash
git clone https://github.com/geohang/GAGAW_Hydrogeophysics.git
cd GAGAW_Hydrogeophysics
```

### Install Additional Dependencies

```bash
pip install -r requirements.txt
```

---

## Step 2: Get an API Key (1 minute)

Choose ONE of these LLM providers:

### Option A: OpenAI (GPT-4)
1. Visit https://platform.openai.com/
2. Create account or sign in
3. Go to API keys section
4. Create new key
5. Copy the key (starts with `sk-...`)

### Option B: Google AI (Gemini)
1. Visit https://ai.google.dev/
2. Sign in with Google account
3. Get API key
4. Copy the key

### Option C: Anthropic (Claude)
1. Visit https://www.anthropic.com/
2. Request API access
3. Get your key

**Set your key:**
```bash
# For OpenAI
export OPENAI_API_KEY='your-key-here'

# For Gemini
export GEMINI_API_KEY='your-key-here'

# For Claude
export ANTHROPIC_API_KEY='your-key-here'
```

---

## Step 3: Launch AQUAH (30 seconds)

### Web Application (Easiest!)

```bash
streamlit run app_geophysics_workflow.py
```

Browser opens automatically at `http://localhost:8501`

### OR Jupyter Notebook

```bash
jupyter notebook Ex_Unified_Workflow.ipynb
```

---

## Step 4: Run Your First Analysis (1 minute)

### In Web App:

1. **Configure** (sidebar):
   - Select LLM provider: `openai`
   - Enter model: `gpt-4o-mini`
   - Enter your API key
   - Click **"Initialize System"**

2. **Describe your workflow:**
   ```
   We have ERT data from DAS-1 instrument at 
   examples/data/ERT/DAS/20171105_1418.Data 
   with electrode file at examples/data/ERT/DAS/electrodes.dat
   in the Snowy Range, Wyoming. 
   
   Use petrophysical parameters: 
   rho_sat=541, porosity=0.37, n=1.24
   ```

3. **Click "Run Workflow"**

4. **Get Results!**
   - AI interpretation
   - Execution plan
   - Resistivity model
   - Water content map
   - Uncertainty estimates
   - Download reports

### In Jupyter Notebook:

1. Run the import cell
2. Set your API key
3. Modify the `user_request` text
4. Run all cells
5. See results!

---

## Step 5: Explore Examples (30 seconds)

### Example 1: Standard ERT
```bash
jupyter notebook Ex_Unified_Workflow.ipynb
```
Single ERT file → resistivity → water content

### Example 2: Time-Lapse
```bash
jupyter notebook Ex_Unified_Workflow_ex2.ipynb
```
Multiple ERT files + climate data integration

### Example 3: Data Fusion
```bash
jupyter notebook Ex_Unified_Workflow_ex3.ipynb
```
Seismic + ERT → structure-constrained analysis

---

## 🎯 Your First Workflows

### Simple ERT Processing

```
"Run ERT inversion on my data file survey.ohm 
using lambda=20. Convert to water content 
assuming porosity=0.35."
```

### Time-Lapse Analysis

```
"Process time-lapse ERT data from 4 files:
baseline.ohm, month1.ohm, month2.ohm, month3.ohm
Fetch climate data for coordinates (40°N, -105°W)
from March to June 2023."
```

### Multi-Method Fusion

```
"Use seismic data at seismic.dat with velocity 
threshold 1000 m/s to constrain ERT inversion 
of ert_data.dat. Apply layer-specific petrophysics."
```

---

## 📊 Understanding Results

### Output Directory Structure

```
results/unified_workflow/your_analysis/
├── inversion/
│   └── resistivity_model.npy       ← Inverted model
├── petrophysics/
│   ├── water_content_mean.npy      ← Main result!
│   └── water_content_std.npy       ← Uncertainty
├── visualizations/
│   ├── resistivity_section.png     ← Cross-section
│   └── water_content_uncertainty.png
└── reports/
    ├── workflow_report.md          ← Full report
    └── interpretation.txt          ← AI insights
```

### Key Outputs

**Always Generated:**
- ✅ Resistivity cross-section
- ✅ Water content map
- ✅ Uncertainty estimates
- ✅ AI-generated report

**Time-Lapse Only:**
- ✅ Temporal change plots
- ✅ Climate correlation graphs
- ✅ Time-series animations

**Data Fusion Only:**
- ✅ Seismic velocity model
- ✅ Interface coordinates
- ✅ Layer-specific results

---

## 🎨 Customization Tips

### Adjusting Regularization

```
"Use lambda=10 for less smoothing"  ← More detail
"Use lambda=50 for more smoothing"  ← Smoother model
```

### Specifying Petrophysics

```
"Use porosity=0.4, n=2.0, rho_sat=100"
```

### Multi-Layer Parameters

```
"Top layer: porosity 0.4, n=2.2, rho_sat 80
Bottom layer: porosity 0.25, n=1.8, rho_sat 500"
```

### Climate Integration

```
"Fetch climate data for 38.5°N, -107.0°W
from June 2023 to September 2023
including precipitation and temperature"
```

---

## 🐛 Common Issues

### "API key not found"
```bash
# Make sure you've set the environment variable
export OPENAI_API_KEY='your-actual-key'
# Or enter it in the web app sidebar
```

### "Module not found: streamlit"
```bash
pip install streamlit
```

### "Cannot find data file"
```
# Use relative path from repository root
"data file at examples/data/ERT/DAS/file.Data"
# Or full path
"data file at /full/path/to/file.Data"
```

### "Inversion did not converge"
```
# Try adjusting lambda (regularization)
"Use lambda=30 instead of default"
# Or check data quality
"Show me data quality metrics"
```

---

## 💡 Pro Tips

### 1. Start Simple
Don't specify everything on your first run. Let AQUAH use defaults, then refine.

```
First run: "Process my ERT data at survey.ohm"
Second run: "Same analysis but use lambda=25"
```

### 2. Use Geological Context
AQUAH understands descriptions!

```
"Site is sandy floodplain with clay lenses"
→ AQUAH adjusts parameter estimates
```

### 3. Iterate on Parameters
See results, then refine:

```
Run 1: "Convert to water content"
       (uses defaults)
       
Run 2: "Use porosity=0.38 instead"
       (after seeing initial results)
```

### 4. Ask for Explanations
```
"Why did you choose lambda=20?"
"What uncertainty sources are included?"
```

---

## 📚 Next Steps

### Learn More
- Read full README for detailed workflows
- Check `AQUAH_SYSTEM_OVERVIEW.md` for architecture
- Browse example notebooks

### Try Advanced Features
- **Structure constraints:** Seismic-guided ERT
- **Time-lapse regularization:** Smooth temporal changes
- **Monte Carlo:** Parameter uncertainty quantification
- **Climate integration:** P-PET water balance

### Contribute
- Share your workflows
- Report issues
- Suggest improvements
- Add example datasets

---

## 🎉 You're Ready!

**You now know how to:**
✅ Install and configure AQUAH  
✅ Run analyses via web app or notebooks  
✅ Write natural language workflow descriptions  
✅ Interpret and customize results  
✅ Troubleshoot common issues  

**Start analyzing your geophysical data with AQUAH!**

---

## 📞 Need Help?

- **GitHub Issues:** https://github.com/geohang/GAGAW_Hydrogeophysics/issues
- **Email:** hangchen.work@gmail.com
- **Documentation:** Full README and examples in repository

---

**Happy analyzing! 🚀**

