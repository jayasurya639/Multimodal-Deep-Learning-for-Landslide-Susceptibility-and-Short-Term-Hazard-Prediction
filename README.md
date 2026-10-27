# Multimodal Deep Learning for Landslide Susceptibility and Short-Term Hazard Prediction

A proposed system combining terrain data, satellite imagery, and rainfall observations to estimate landslide susceptibility and short-term hazard. This repository currently provides a project scaffold, synthetic sample records, validation tests, and design documentation—not a trained or validated prediction model.

## Project status

**Prototype scaffold / research proposal.** Model training, reliable datasets, evaluation, and deployment are not yet implemented. The sample data is synthetic and must not be used for real-world risk decisions.

## Proposed capabilities

- Terrain feature processing from Digital Elevation Models (DEM).
- Satellite-image quality checks, including cloud/shadow handling where applicable.
- Explicit handling of missing or unusable satellite observations.
- Separate terrain, satellite, and rainfall encoders with feature fusion.
- Two outputs: susceptibility mapping and short-term hazard estimation.
- Geographic train/validation/test separation.
- Confidence-filtered pseudo-labeling and controlled periodic retraining as future capabilities.

## Technology plan

Python, PyTorch, NumPy, pandas, scikit-learn, Rasterio/GDAL, GeoPandas, and optionally FastAPI and PostgreSQL/PostGIS. The current starter only uses Python's standard library and pytest for sample-data validation.

## Setup

### 1. Requirements

- Python 3.10 or newer
- pip
- Git (optional)

### 2. Create and activate a virtual environment

**Windows (PowerShell):**
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure environment variables

Copy `.env.example` to `.env` and adjust values for your environment. The current scaffold reads no secrets and does not automatically load `.env`; these variables document planned configuration for future components. Do not commit credentials or private API keys.

### 5. Run sample-data validation

```bash
python -m pytest
```

Expected result: tests validate the synthetic CSV structure and basic value constraints. These tests do **not** test a trained model.

## Repository layout

```text
landslide-hazard-estimation/
├── README.md
├── LICENSE
├── .env.example
├── requirements.txt
├── data/
│   └── sample/
│       ├── sample_observations.csv
│       └── README.md
├── docs/
│   └── technical-design.md
├── src/
│   └── data_validation.py
└── tests/
    └── test_sample_data.py
```

## Sample data

`data/sample/sample_observations.csv` contains illustrative synthetic rows with terrain variables, recent rainfall, satellite availability, and a placeholder target label. The values are fabricated for software testing and are not derived from a real location or verified landslide event.

## Validation and safety notes

- Do not treat the synthetic records as scientific evidence or ground truth.
- Define the short-term prediction horizon before training.
- Avoid spatial and temporal leakage between data splits.
- Keep verified labels separate from pseudo-labels.
- Report region-wise metrics and uncertainty.
- Do not issue public warnings from this scaffold; operational use requires expert review, validation, monitoring, and coordination with responsible authorities.

## Documentation

See [`docs/technical-design.md`](docs/technical-design.md) for the proposed architecture, data flow, validation approach, risks, and implementation stages.

## License

This project scaffold is provided under the MIT License. See [`LICENSE`](LICENSE).
