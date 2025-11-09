# GAGAW Hydrogeophysics

Demonstration workflows for AI-powered hydrogeophysical analysis using PyHydroGeophysX.

## 📋 Overview

This repository contains practical applications of [PyHydroGeophysX](https://github.com/geohang/PyHydroGeophysX) multi-agent AI system for processing geophysical data. The workflows demonstrate automated processing of electrical resistivity tomography (ERT), seismic refraction, and climate data to estimate subsurface hydrological properties using natural language interfaces and AI-powered data fusion.

## 🎯 Key Features

- 🤖 **Natural Language Workflows**: Configure complex geophysical processing pipelines using plain English descriptions
- 📊 **Multi-Method Data Fusion**: Integrate ERT, seismic refraction, and climate data for comprehensive hydrological insights
- 🔬 **Uncertainty Quantification**: Monte Carlo methods for robust parameter estimation
- 🎯 **AI-Powered Parameter Estimation**: Automatic petrophysical parameter selection from site descriptions
- 📝 **Automated Reporting**: AI-generated analysis reports with visualizations

## 📂 Repository Structure

```
GAGAW_Hydrogeophysics/
├── direct_ERT_converion.ipynb          # Direct ERT to water content conversion
├── Ex_DataFusion_NaturalLanguage.ipynb # Multi-method data fusion workflow
├── data/                                # Example geophysical data
│   ├── climate/                         # Climate data and PET estimates
│   ├── ERT/                             # Electrical resistivity data
│   │   ├── Bert/                        # BERT format data
│   │   ├── DAS/                         # DAS inversion results
│   │   └── E4D/                         # E4D format time-series
│   └── Seismic/                         # Seismic refraction data
└── results/                             # Processing results
    ├── data_fusion/                     # Data fusion outputs
    ├── direct_ert_conversion/           # Direct conversion results
    └── Time-lapse_agent/                # Time-lapse analysis
```

## 🚀 Getting Started

### Prerequisites

1. **Python Environment**: Python 3.8 or higher
2. **PyHydroGeophysX**: The main dependency
   ```bash
   pip install pyhydrogeophysx
   ```
3. **LLM API Key**: Get an API key from one of:
   - [OpenAI](https://platform.openai.com/) (GPT-4/GPT-3.5)
   - [Google AI](https://ai.google.dev/) (Gemini)
   - [Anthropic](https://www.anthropic.com/) (Claude)

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/GAGAW_Hydrogeophysics.git
   cd GAGAW_Hydrogeophysics
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set your API key as an environment variable:
   ```bash
   # For OpenAI
   export OPENAI_API_KEY='your-api-key-here'
   
   # For Gemini
   export GEMINI_API_KEY='your-api-key-here'
   
   # For Claude
   export ANTHROPIC_API_KEY='your-api-key-here'
   ```

### Quick Start

Open and run the Jupyter notebooks:

```bash
jupyter notebook direct_ERT_converion.ipynb
```

Or for data fusion:

```bash
jupyter notebook Ex_DataFusion_NaturalLanguage.ipynb
```

## 📖 Workflows

### 1. Direct ERT to Water Content Conversion

**Notebook**: `direct_ERT_converion.ipynb`

Demonstrates three scenarios with increasing specification detail, showing how the AI agents adapt to different levels of input:

- **Scenario 1 - Simple**: Minimal natural language input
  ```
  "Process ERT data and convert to water content"
  ```
  The agents use default parameters and generate standard outputs.

- **Scenario 2 - Geology-Informed**: Include site description for context-aware processing
  ```
  "Process ERT data from a mountain meadow with shallow fractured bedrock at 3m depth.
   Sandy loam soil above weathered granite bedrock."
  ```
  The agents interpret geological context and estimate appropriate petrophysical parameters.

- **Scenario 3 - Fully Specified**: Detailed petrophysical parameters for precise control
  ```json
  {
    "soil_layer": {"porosity": 0.42, "n": 2.1, "rhos": 80},
    "bedrock_layer": {"porosity": 0.18, "n": 1.9, "rhos": 800}
  }
  ```
  The agents use exact parameters while maintaining workflow automation.

**Methodology**:
- Natural language interpretation and parameter extraction
- Automated petrophysical parameter estimation from geological descriptions
- Layer-specific resistivity-to-water content conversion using Waxman-Smits models
- Monte Carlo uncertainty quantification with spatially-correlated sampling
- Automated report generation with workflow documentation

### 2. Multi-Method Data Fusion

**Notebook**: `Ex_DataFusion_NaturalLanguage.ipynb`

Demonstrates intelligent integration of multiple geophysical methods through AI-coordinated workflows:

**Workflow Components**:
1. **Seismic Refraction Tomography**: Velocity inversion to identify subsurface structure
2. **Velocity-Based Interface Extraction**: Automated detection of geological boundaries from velocity gradients
3. **Structure-Constrained ERT Inversion**: Resistivity inversion using seismic-derived interfaces as constraints
4. **Climate Data Integration**: Precipitation and potential evapotranspiration (PET) for temporal context
5. **Petrophysical Transform**: Multi-layer resistivity-to-water content conversion with uncertainty

**Example Natural Language Request**:
```
"Perform structure-constrained data fusion using seismic refraction to identify 
bedrock interface, then run ERT inversion constrained by this structure. Convert 
to water content considering alpine meadow soil above fractured granite bedrock."
```

**Methodology**:
- AI-powered coordination of multi-method workflows
- Automated extraction of geological interfaces from velocity models
- Cross-method constraint application (seismic → ERT)
- Layer-specific petrophysical parameter estimation from natural language
- Integrated climate data analysis with temporal alignment
- Comprehensive uncertainty propagation through the workflow
- Automated visualization and reporting

## 📊 Example Data

The repository includes example geophysical datasets to demonstrate the workflows:

- **ERT Data**: Multiple formats (BERT, E4D, DAS inversion results) showing time-lapse acquisitions
- **Seismic Data**: First-arrival travel times for refraction tomography
- **Climate Data**: Daily meteorological variables and computed potential evapotranspiration (PET)

These datasets are provided to allow users to:
- Test the AI-powered workflow automation
- Understand natural language configuration options
- Explore multi-method data fusion approaches
- Evaluate uncertainty quantification methods

## 🔬 Scientific Background

### Electrical Resistivity Tomography (ERT)

ERT measures subsurface electrical resistivity by injecting current and measuring voltage. Resistivity is sensitive to:
- Water content (higher water → lower resistivity)
- Salinity (higher ions → lower resistivity)
- Temperature (higher temp → lower resistivity)
- Geological structure (clay vs sand vs bedrock)

### Petrophysical Transforms

Convert resistivity (ρ) to water content (θ) using the Waxman-Smits model:

$$
\rho = \frac{\rho_w \cdot F}{\left(1 + \frac{B \cdot Q_v}{\sigma_w}\right)}
$$

Where:
- F = a·φ⁻ᵐ (formation factor, Archie's Law)
- φ = porosity
- m = cementation exponent
- ρ_w = pore water resistivity
- Q_v, B = clay parameters

### Uncertainty Quantification

Monte Carlo sampling accounts for:
- Measurement noise in resistivity
- Uncertainty in petrophysical parameters (porosity, cementation exponent)
- Spatial variability in geological properties
- Model resolution and regularization effects

## 📈 Outputs

Workflow outputs are saved in the `results/` directory:

- **Inversion Models**: Resistivity/velocity models (`.npy`, `.bms`)
- **Hydrological Products**: Water content and saturation with uncertainty (`.npy`)
- **Visualizations**: Cross-sections, time-series plots (`.png`)
- **Reports**: Markdown summaries with embedded figures (`.md`)

**Generated Visualizations Include**:
- Resistivity pseudo-sections with data quality metrics
- Seismic velocity models with picked interfaces
- Structure-constrained inversion results showing boundary adherence
- Water content distributions with uncertainty bounds
- Multi-panel comparison plots for method integration
- Temporal evolution analysis for time-lapse datasets

## 🤝 Contributing

Contributions are welcome! This repository demonstrates practical applications of PyHydroGeophysX. If you have:

- Additional field datasets to include
- Improved workflow configurations
- Bug fixes or enhancements
- Documentation improvements

Please open an issue or submit a pull request.

## 📝 Citation

If you use these workflows in your research, please cite:

**PyHydroGeophysX package**:
```bibtex
@software{chen2025pyhydrogeophysx,
  author = {Chen, Hang and Niu, Qifei and Wu, Yuxin},
  title = {PyHydroGeophysX: An Extensible Open-Source Platform for Bridging 
           Hydrological Models and Geophysical Measurements},
  year = {2025},
  publisher = {Water Resources Research (under review)},
  url = {https://github.com/geohang/PyHydroGeophysX}
}
```

**This repository**:
```bibtex
@software{gagaw2024,
  author = {Chen, Hang and Niu, Qifei},
  title = {GAGAW Hydrogeophysics: AI-Powered Geophysical Analysis Workflows},
  year = {2024},
  publisher = {GitHub},
  url = {https://github.com/yourusername/GAGAW_Hydrogeophysics}
}
```

## 📄 License

This project is licensed under the Apache License 2.0 - the same license as PyHydroGeophysX. See the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **PyHydroGeophysX** development team for the multi-agent framework
- **PyGIMLi** developers for geophysical modeling tools
- **RESIPY** developers for ERT data processing capabilities
- Open-source scientific Python community

## 📧 Contact

For questions about:
- **Workflows**: Open an issue in this repository
- **PyHydroGeophysX**: Visit the [main repository](https://github.com/geohang/PyHydroGeophysX)

## 🔗 Related Resources

- [PyHydroGeophysX Documentation](https://pyhydrogeophysx.readthedocs.io/)
- [PyGIMLi Documentation](https://www.pygimli.org/)
- [RESIPY Documentation](https://gitlab.com/hkex/resipy)

---

**Note**: This repository contains example workflows demonstrating AI-powered geophysical analysis methods. The included datasets are for demonstration and educational purposes.
