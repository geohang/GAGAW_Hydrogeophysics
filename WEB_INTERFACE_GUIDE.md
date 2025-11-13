# AQUAH Web Interface Guide

## 🌐 Web Application Overview

The AQUAH web interface provides a user-friendly, no-code way to perform geophysical data analysis using natural language.

---

## 🖥️ Interface Layout

### Main Components

```
┌─────────────────────────────────────────────────────────────────┐
│                          AQUAH                                   │
│        🌍 PyHydroGeophysX                                        │
│   AQUAH (Autonomous Query-driven Understanding Agent for        │
│            Hydrogeophysics)                                      │
├──────────────────┬──────────────────────────────────────────────┤
│                  │                                               │
│  SIDEBAR         │         MAIN CONTENT AREA                    │
│  (Configuration) │                                               │
│                  │                                               │
│  ⚙️ Configuration│  📝 Describe Your Workflow                   │
│                  │  ┌──────────────────────────────────────┐   │
│  LLM Provider    │  │ Example: I want to run a time-lapse │   │
│  [openai ▼]     │  │ ERT inversion on 5 datasets...      │   │
│                  │  │                                      │   │
│  Model Name      │  │                                      │   │
│  [gpt-4o-mini]  │  └──────────────────────────────────────┘   │
│                  │                                               │
│  API Key         │  📁 Upload Data (Optional)                   │
│  [**********]   │  ┌────────────┬────────────┬────────────┐   │
│                  │  │ ERT Data   │ Seismic    │ Electrode  │   │
│  Output Dir      │  │ Files      │ Data       │ File       │   │
│  [results/...]  │  │            │            │            │   │
│                  │  │ [Browse]   │ [Browse]   │ [Browse]   │   │
│  🚀 Initialize   │  └────────────┴────────────┴────────────┘   │
│     System       │                                               │
│                  │  🚀 Run Workflow                             │
│  ──────────────  │                                               │
│                  │                                               │
│  📊 System Status│                                               │
│  ✅ Ready        │                                               │
│                  │                                               │
│  Context agent   │                                               │
│  ready ✓         │                                               │
│  Using           │                                               │
│  BaseAgent...    │                                               │
│                  │                                               │
└──────────────────┴──────────────────────────────────────────────┘
```

---

## 🎨 User Interface Elements

### 1. Configuration Panel (Sidebar - Left)

#### LLM Provider Selection
```
┌──────────────────────┐
│ LLM Provider         │
│ ┌──────────────────┐ │
│ │ openai        ▼ │ │  ← Dropdown menu
│ └──────────────────┘ │
│ Options:             │
│   • openai           │
│   • gemini           │
│   • claude           │
└──────────────────────┘
```

#### Model Name Input
```
┌──────────────────────┐
│ Model Name           │
│ ┌──────────────────┐ │
│ │ gpt-4o-mini     │ │  ← Text input
│ └──────────────────┘ │
│ (Automatically set   │
│  based on provider)  │
└──────────────────────┘
```

#### API Key Input
```
┌──────────────────────┐
│ API Key              │
│ ┌──────────────────┐ │
│ │ ••••••••••••••• │ │  ← Password field
│ └──────────────────┘ │
│ (Secure input)       │
└──────────────────────┘
```

#### Output Directory
```
┌──────────────────────┐
│ Output Directory     │
│ ┌──────────────────┐ │
│ │ results/stream-  │ │
│ │ lit_workflow     │ │
│ └──────────────────┘ │
└──────────────────────┘
```

#### Initialize Button
```
┌──────────────────────┐
│  🚀 Initialize       │
│      System          │  ← Primary action button
└──────────────────────┘
```

#### System Status
```
┌──────────────────────┐
│ 📊 System Status     │
│                      │
│ ✅ Ready             │  ← Status indicator
│                      │
│ ✓ Context agent     │
│   ready              │
│ ✓ Using             │
│   BaseAgent.run_    │
│   unified_agent_    │
│   workflow()        │
│ ✓ Workflow type     │
│   will be auto-     │
│   detected!         │
└──────────────────────┘
```

### 2. Main Content Area (Right)

#### Natural Language Input
```
┌─────────────────────────────────────────────────────────┐
│ 📝 Describe Your Workflow                               │
│                                                          │
│ Describe what you want to do in plain English:          │
│ ┌──────────────────────────────────────────────────┐   │
│ │ Example: I want to run a time-lapse ERT          │   │
│ │ inversion on 5 datasets...                       │   │
│ │                                                  │   │
│ │                                                  │   │
│ │                                                  │   │
│ │                                                  │   │
│ │ [Large text area for natural language input]    │   │
│ │                                                  │   │
│ └──────────────────────────────────────────────────┘   │
│                                                          │
│ Be specific about data files, parameters, and           │
│ desired outputs                                          │
└─────────────────────────────────────────────────────────┘
```

#### File Upload Section
```
┌─────────────────────────────────────────────────────────┐
│ 📁 Upload Data (Optional)                               │
│                                                          │
│ 💡 You can either specify file paths in your            │
│    description OR upload files here. Uploaded files     │
│    will override paths in your description.             │
│                                                          │
│ ┌─────────────┬─────────────────┬──────────────────┐   │
│ │ ERT Data    │ Seismic Data    │ Electrode File   │   │
│ │ Files       │ (for data       │ (optional)       │   │
│ │             │  fusion)        │                  │   │
│ │             │                 │                  │   │
│ │ Drag and    │ Drag and drop   │ Drag and drop    │   │
│ │ drop files  │ file here       │ file here        │   │
│ │ here        │                 │                  │   │
│ │             │ Limit 200MB per │ Limit 200MB per  │   │
│ │ Limit 200MB │ file • DAT, TXT │ file • DAT, TXT  │   │
│ │ per file •  │                 │                  │   │
│ │ OHM, DAT... │                 │                  │   │
│ │             │                 │                  │   │
│ │ [Browse     │ [Browse files]  │ [Browse files]   │   │
│ │  files]     │                 │                  │   │
│ └─────────────┴─────────────────┴──────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

#### Run Button
```
┌─────────────────────────────────────────────────────────┐
│                  🚀 Run Workflow                         │  ← Large button
└─────────────────────────────────────────────────────────┘
```

---

## 📊 Results Display

After clicking "Run Workflow", results appear in the main area:

### Results Layout
```
┌─────────────────────────────────────────────────────────┐
│ ✅ Workflow Complete!                                    │
├─────────────────────────────────────────────────────────┤
│                                                          │
│ 💡 Interpretation                                        │
│ ┌──────────────────────────────────────────────────┐   │
│ │ The ERT inversion successfully characterized...  │   │
│ │ Water content ranges from 0.15 to 0.42...       │   │
│ │ Uncertainties are within acceptable bounds...    │   │
│ └──────────────────────────────────────────────────┘   │
│                                                          │
│ 📋 Execution Plan                                        │
│ 1. Load ERT data → ERTLoaderAgent                      │
│ 2. Run inversion → ERTInversionAgent                   │
│ 3. Convert to water content → PetrophysicsAgent        │
│ 4. Quantify uncertainty → UncertaintyAgent             │
│ 5. Generate report → ReportAgent                       │
│                                                          │
│ ──────────────────────────────────────────────────────  │
│                                                          │
│ 📊 Results Summary                                       │
│ ┌─────────────┬──────────────────┬─────────────────┐   │
│ │ Resistivity │ Water Content    │ Mesh Cells      │   │
│ │ Range (Ωm)  │ Range            │                 │   │
│ │             │                  │                 │   │
│ │  20 - 800   │  0.15 - 0.42     │     1,245       │   │
│ └─────────────┴──────────────────┴─────────────────┘   │
│                                                          │
│ 📁 Generated Files                                       │
│ 📥 Download resistivity_model                          │
│ 📥 Download water_content_mean                         │
│ 📥 Download workflow_report.md                         │
│ 📥 Download resistivity_section.png                    │
│                                                          │
│ ──────────────────────────────────────────────────────  │
│                                                          │
│ 🔧 View Generated Configuration ▼                       │
│   (Expandable section showing JSON config)              │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

---

## 🎯 Step-by-Step Usage

### First Time Setup

1. **Open Terminal**
   ```bash
   cd GAGAW_Hydrogeophysics
   streamlit run app_geophysics_workflow.py
   ```

2. **Browser Opens**
   - Automatic: `http://localhost:8501`
   - Manual: Copy/paste URL from terminal

3. **Configure (Sidebar)**
   - Select LLM provider: `openai`
   - Model: `gpt-4o-mini` (default)
   - Enter API key: `sk-...`
   - Output directory: `results/streamlit_workflow`

4. **Initialize**
   - Click "🚀 Initialize System"
   - Wait for confirmation
   - Status changes to "✅ Ready"

### Running an Analysis

5. **Describe Workflow (Main Area)**
   ```
   Example text:
   "I have ERT data from DAS-1 instrument at 
   examples/data/ERT/DAS/20171105_1418.Data 
   with electrode file at 
   examples/data/ERT/DAS/electrodes.dat
   
   Site: Snowy Range, Wyoming
   Geology: Sandy soil over granite bedrock
   
   Petrophysical parameters:
   - rho_sat = 541
   - porosity = 0.37
   - n = 1.24
   
   Convert to water content with uncertainty."
   ```

6. **Upload Files (Optional)**
   - If you have local files
   - Drag and drop into upload zones
   - Or click "Browse files"

7. **Run**
   - Click "🚀 Run Workflow"
   - Progress indicator appears
   - Wait for completion (2-10 minutes)

8. **View Results**
   - Interpretation summary
   - Execution plan
   - Key metrics
   - Download buttons for files

---

## 💡 Example Workflows in Web App

### Example 1: Standard ERT

**Paste this into the text area:**
```
We have ERT data from DAS-1 instrument.
Data file: examples/data/ERT/DAS/20171105_1418.Data
Electrode file: examples/data/ERT/DAS/electrodes.dat

Site description: Grassland in Snowy Range, Wyoming
Bedrock: Foliated gneiss in Cheyenne Belt

Use these petrophysical parameters:
- rho_sat = 541 Ωm
- porosity = 0.37
- cementation exponent n = 1.24

Please convert resistivity to water content and 
quantify uncertainty with Monte Carlo analysis.
```

### Example 2: Time-Lapse ERT

**Paste this into the text area:**
```
Run TIME-LAPSE ERT inversion on 4 E4D format files:

Files (in folder data/ERT/E4D):
1. 2022-03-26_0030.ohm (baseline)
2. 2022-04-26_0030.ohm
3. 2022-05-26_0030.ohm
4. 2022-06-26_0030.ohm

Inversion settings:
- Type: TIME-LAPSE with difference method
- Temporal regularization parameter: 10
- Spatial lambda: 15
- Max iterations: 10

Climate data integration:
- Site: Mt. Snodgrass, Colorado
- Coordinates: 38.92584°N, -106.97998°W
- Date range: March 2022 to June 2022
- Variables: precipitation, temperature, solar radiation
- Calculate PET using Penman-Monteith method
```

### Example 3: Data Fusion

**Paste this into the text area:**
```
Perform multi-method data fusion to characterize 
subsurface water content:

Step 1 - Seismic Analysis:
- Data file: data/Seismic/srtfieldline2.dat
- Run velocity inversion
- Extract interface at threshold 1000 m/s
  (boundary between regolith and fractured bedrock)

Step 2 - Structure-Constrained ERT:
- Data file: data/ERT/Bert/fielddataline2.dat
- Use seismic interface as structural constraint
- Regularization lambda: 20
  (moderate smoothing due to constraints)

Step 3 - Petrophysical Transformation:
Use layer-specific parameters:

REGOLITH LAYER (above interface):
- rho_sat: 50-250 Ωm
- cementation exponent n: 1.3-2.2
- porosity: 0.25-0.5

FRACTURED BEDROCK LAYER (below interface):
- rho_sat: 165-350 Ωm
- cementation exponent n: 2.0-2.2
- porosity: 0.2-0.3

Step 4 - Uncertainty Analysis:
- Monte Carlo: 100 realizations
- Account for parameter uncertainties
- Generate layer-specific water content maps
```

---

## 🎨 Visual Features

### Color Coding

- **Green boxes** - Success messages
- **Blue boxes** - Information messages
- **Orange boxes** - Warnings
- **Red boxes** - Errors
- **Gray boxes** - Code/configuration

### Icons

- 🚀 - Action buttons
- ✅ - Success indicators
- ⚠️ - Warnings
- ❌ - Errors
- 📊 - Status displays
- 💡 - Help/tips
- 📝 - Input areas
- 📁 - File operations
- 🔧 - Configuration
- ⚙️ - Settings

---

## 📱 Responsive Design

The web app adapts to different screen sizes:

- **Desktop:** Full sidebar + main area layout
- **Tablet:** Collapsible sidebar
- **Mobile:** Stacked layout (not recommended for complex workflows)

---

## 🐛 Troubleshooting

### "System not initialized"
- Click "Initialize System" button in sidebar
- Ensure API key is entered correctly
- Check console for error messages

### "API key not found"
- Enter API key in sidebar
- Or set environment variable before launching

### "File upload failed"
- Check file size (max 200MB)
- Verify file format (.ohm, .dat, .Data, .txt)
- Ensure file is not corrupted

### "Workflow failed"
- Check interpretation text for details
- Verify file paths are correct
- Review natural language description
- Try with example data first

---

## 💾 Saving and Loading

### Outputs Saved To:
```
results/streamlit_workflow/
├── run_YYYYMMDD_HHMMSS/
│   ├── inversion/
│   ├── petrophysics/
│   ├── visualizations/
│   └── reports/
```

### Downloading Results:
- Click download buttons in results section
- Files download to browser's download folder
- Can download individual files or reports

---

## 🔒 Security Note

**API Keys:**
- Entered keys are not stored
- Session-based only
- Lost when browser closed
- Enter each time you start app

**Uploaded Files:**
- Stored temporarily
- Deleted after processing
- Not shared or uploaded externally

---

## 🎓 Tips for Best Results

1. **Be Specific:** Include file paths, instrument type, site description
2. **Use Context:** Geological descriptions help parameter estimation
3. **Start Simple:** Try default settings first, then refine
4. **Check Examples:** Use provided examples as templates
5. **Upload or Specify:** Either upload files OR specify paths, not both
6. **Review Config:** Expand configuration view to verify parsing

---

## 📞 Getting Help

**In-App:**
- Hover over (?) icons for help
- Read placeholder text in input fields
- Check example workflows at bottom

**Documentation:**
- README.md - Complete guide
- QUICK_START_AQUAH.md - Getting started
- AQUAH_SYSTEM_OVERVIEW.md - Technical details

**Support:**
- GitHub Issues: Report bugs or request features
- Email: hangchen.work@gmail.com

---

## 🎉 Enjoy AQUAH!

The web interface makes geophysical data processing accessible to everyone. No programming required - just describe what you want to analyze!

---

*Web Interface Version: 1.0*  
*Last Updated: 2025*  
*Built with Streamlit*

