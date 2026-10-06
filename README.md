# GAGAW Hydrogeophysics

Example notebooks for **AQUAH**, the hydrogeophysics assistant built on the **GAGAW** (Generalizable Automated Geophysical Agent Workflow) framework. The agent code now lives in **[PyHydroGeophysX](https://github.com/geohang/PyHydroGeophysX)**. This repository keeps only runnable examples and the field data they read, and installs PyHydroGeophysX as a dependency.

> Earlier versions of this repository carried their own copy of the workflow code and the Streamlit app. Both moved to PyHydroGeophysX (see [Where the Code Went](#where-the-code-went)). The last snapshot of the old layout is commit [`d42d26d`](https://github.com/geohang/GAGAW_Hydrogeophysics/tree/d42d26d748f99fb418ab8bcb63f5d91234eec8a3).

## Examples

| Notebook | Workflow | Data |
|---|---|---|
| [`Ex_Unified_Workflow_ex1.ipynb`](Ex_Unified_Workflow_ex1.ipynb) | One DAS-1 ERT survey from the Snowy Range, Wyoming: inversion, water content, Monte Carlo uncertainty, report | `data/ERT/DAS/` |
| [`Ex_Unified_Workflow_ex2.ipynb`](Ex_Unified_Workflow_ex2.ipynb) | Time-lapse ERT on four E4D surveys (March to June 2022) with daily climate and potential evapotranspiration | `data/ERT/E4D/`, `data/climate/` |
| [`Ex_Unified_Workflow_ex3.ipynb`](Ex_Unified_Workflow_ex3.ipynb) | Data fusion: a seismic refraction interface constrains the ERT inversion, then layer-specific water content with uncertainty | `data/Seismic/`, `data/ERT/Bert/` |

Each notebook states the task in plain language, lets a language model turn it into a workflow configuration, and runs it through `BaseAgent.run_unified_agent_workflow()`. The notebooks are saved with their outputs, so the results can be read on GitHub without running anything. Without an API key, a notebook falls back to its recorded configuration and still runs the workflow. Outputs are written to `results/`, which Git ignores.

The notebooks and data were copied from PyHydroGeophysX `examples/` at commit `e8c0c5c` (version 0.5.0). Data sources and terms are listed in [`data/README.md`](data/README.md).

## Installation

The notebooks target PyHydroGeophysX 0.5.0. PyPI has 0.3.0, so `requirements.txt` installs from GitHub:

```bash
git clone https://github.com/geohang/GAGAW_Hydrogeophysics.git
cd GAGAW_Hydrogeophysics
pip install -r requirements.txt
```

PyGIMLi links against C++ libraries. If the pip install fails on it, install it with conda first (`conda install -c gimli pygimli`), then rerun `pip install -r requirements.txt`.

To let the language model parse the requests, set `OPENAI_API_KEY`; the notebooks use OpenAI `gpt-4o-mini` by default. To use Gemini or Claude, change `llm_provider`, `llm_model`, and the `os.getenv(...)` line in the API configuration cell. Start Jupyter from the repository root, because the data paths in the notebooks are relative to it:

```bash
jupyter lab
```

## Where the Code Went

| Previously in this repository | Now in PyHydroGeophysX |
|---|---|
| Multi-agent code (request parsing, workflow orchestration, ERT, seismic, petrophysics, climate, and report agents) | [`PyHydroGeophysX/agents/`](https://github.com/geohang/PyHydroGeophysX/tree/main/PyHydroGeophysX/agents) |
| Streamlit app `app_geophysics_workflow.py` | [`examples/app_geophysics_workflow.py`](https://github.com/geohang/PyHydroGeophysX/blob/main/examples/app_geophysics_workflow.py), also hosted at <https://pyhydrogeophysx.streamlit.app/> |
| Usage instructions | [Agent documentation](https://geohang.github.io/PyHydroGeophysX/agents/index.html): [quick start](https://geohang.github.io/PyHydroGeophysX/agents/quick_start.html), [workflows](https://geohang.github.io/PyHydroGeophysX/agents/workflows.html), [web app](https://geohang.github.io/PyHydroGeophysX/agents/webapp.html) |

## Citation

If you use the agent workflow in your research, please cite:

```bibtex
@article{chen2026agentworkflow,
  author  = {Chen, Hang},
  title   = {A Generalizable Automated Geophysical Agent Workflow for
             Accessible Subsurface Hydrology Analysis},
  journal = {Big Data and Earth System},
  pages   = {100042},
  year    = {2026}
}

@article{chen2026pyhydrogeophysx,
  author  = {Chen, Hang and Niu, Qifei and Wu, Yuxin},
  title   = {PyHydroGeophysX: An Extensible Open-Source Platform for Integrating
             Hydrological Models with Geophysical Measurements},
  journal = {SoftwareX},
  year    = {2026},
  note    = {In press},
  url     = {https://github.com/geohang/PyHydroGeophysX}
}
```

When you use the example data, please also cite the sources in [`data/README.md`](data/README.md).

## Contact

Please report problems with the agent code in the [PyHydroGeophysX issue tracker](https://github.com/geohang/PyHydroGeophysX/issues), and problems with these notebooks or data in this repository's issues.

## License

Apache License 2.0; see [LICENSE](LICENSE). Third-party data in `data/` keep their own terms, listed in [`data/README.md`](data/README.md).
