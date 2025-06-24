### `README.md`

```markdown
# Graph Autoencoder for Environmental and Disease Data Analysis

This project implements a **Graph Autoencoder (GAE)** using PyTorch Geometric to model and visualize relationships among air pollutants, diseases, and health indicators based on correlation patterns in time-series data across different Korean regions and months.

---

## Key Features

- ✅ Graph construction from correlation matrices (thresholded)
- ✅ GCN-based autoencoder for embedding and reconstruction
- ✅ Visualization of learned graphs (monthly and regional)
- ✅ Export of:
  - Edge correlation table
  - Predicted adjacency matrices
- ✅ Modular design to adapt for other datasets

---

## Project Structure

```

GAE\_Project/
├── data/                        # CSV data files (monthly & regional)
│   ├── 2023\_GAE\_input\_03.csv
│   ├── 2023\_GAE\_input\_08.csv
│   ├── 2023\_GAE\_input\_12.csv
│   ├── 2023\_Busan\_monthly.csv
│   ├── 2023\_Chungbuk\_monthly.csv
├── outputs/                     # Generated output (created automatically)
│   ├── 2023\_Region\_Graphs.png
│   ├── 2023\_Monthly\_Graphs.png
│   ├── Excel outputs (.xlsx)
├── GAE\_0610.py                  # Main GAE script
├── requirements.txt             # Dependencies
├── .gitignore                   # Files/folders to exclude from Git
├── LICENSE                      # License (MIT)
└── README.md                    # This file

````

---

## Requirements

Install Python packages using:

```bash
pip install -r requirements.txt
````

### Python Packages Used

* `torch`
* `torch-geometric`
* `pandas`
* `numpy`
* `matplotlib`
* `networkx`
* `scikit-learn`

---

## How to Run

1. **Clone the repository:**

```bash
git clone https://github.com/yourusername/GAE_Project.git
cd GAE_Project
```

2. **Place your `.csv` data files** into the `data/` directory. You may use the provided 2023 example files.

3. **Run the script:**

```bash
python GAE_0610.py
```

4. **Check `outputs/`** for:

   * `.png` graph visualizations
   * `.xlsx` files with correlation tables and reconstructed adjacency matrices

---

## Data Format

Each `.csv` file should:

* Have **row names** as features (e.g., `"PM2.5"`, `"NO2"`, `"Stroke"`)
* Have **columns as time steps** (e.g., months, weeks)

Example:

|                | Jan | Feb | Mar | ... |
| -------------- | --- | --- | --- | --- |
| PM2.5          | 32  | 28  | 25  | ... |
| NO2            | 15  | 17  | 18  | ... |
| IschemicStroke | 120 | 130 | 115 | ... |

---

## Outputs

### Graphs

* Monthly graphs and regional graphs saved as `.png`
* Each node represents a health/pollution feature
* Edges represent strong correlations & decoder-predicted links

### Excel Files

* Correlation values used in graph construction
* Predicted adjacency matrix from GAE decoder

---

## Configuration

You can adjust the correlation threshold and decoder strength in `run_gae_for_structure()`:

```python
run_gae_for_structure(..., min_corr=0.4, max_corr=1.0)
```

---

## Model Architecture

```text
Input (scaled time-series vectors)
   ↓
Graph Construction (correlation-based edges)
   ↓
GCN Encoder (2 layers)
   ↓
Latent Representation (2D)
   ↓
Inner product decoder → Predicted adjacency
```

---

## Use Cases

* Environmental epidemiology research
* Regional health pattern analysis
* Air pollution & chronic disease link visualization
* Teaching material for GNN/GAE

---

## License

This project is licensed under the MIT License — see `LICENSE` for details.

---

## Acknowledgments

Developed by **Seungpil Jeong**
For academic and public health research use.

---

```
