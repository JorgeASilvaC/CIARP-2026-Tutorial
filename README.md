# Time Series Imputation using Cumulative Profiles and Pattern-Matching Algorithms

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JorgeASilvaC/CIARP-2026-Tutorial/blob/main/Tutorial_Time_Series_Cummulative.ipynb)

**Jorge A. Silva-Castro** · **Jorge Á. González-Ordiano**  
Universidad Iberoamericana Ciudad de México — Instituto de Investigación Aplicada y Tecnología (INIAT)

**29th Iberoamerican Congress on Pattern Recognition (CIARP 2026)**  
Universidad Iberoamericana, Mexico City · November 24–27, 2026

---

## About this tutorial

Missing data distorts the temporal patterns on which downstream analysis, forecasting, and decision-making rely. This tutorial frames imputation as a similarity search in a chosen feature space, and examines how cumulative quantities such as energy provide a physically meaningful representation when the integral over time carries domain significance. Participants implement the DANLI method and compare it against classical and similarity-based baselines, including mean-based imputation, linear and spline interpolation, Euclidean copy-paste, and k-NN.

The session combines a conceptual lecture, live coding, and a hands-on comparison using the Ausgrid distribution dataset with synthetic gaps. The accompanying notebook is designed to be executed sequentially: each section builds on the previous one, and every result is stored so that the analysis can be resumed if the session is interrupted.

---

## Repository contents

| File | Description |
|---|---|
| `Tutorial_Time_Series_Cummulative.ipynb` | Main notebook — open in Colab and follow the session |
| `Meadowbank_132.csv` | Unified Ausgrid extract used throughout the tutorial |
| `Ciarp_Press_2026.pdf` | Lecture slides, for later reference |

---

## How to run

### Requirements

- A personal Google account (Colab runs in the browser)
- A modern web browser
- No local installation is required

### Steps

1. Click the **Open in Colab** badge above, or use the direct link:
   ```
   https://colab.research.google.com/github/JorgeASilvaC/CIARP-2026-Tutorial/blob/main/Tutorial_Time_Series_Cummulative.ipynb
   ```
2. In the top-left of the Colab toolbar, click **File → Save a copy in Drive**. This creates an editable copy of the notebook in your own Drive.
3. Run the cells in order, from top to bottom. The dataset is loaded automatically from this repository via its raw URL, so no manual upload is needed.

It is recommended to open the Colab link once before the session to confirm that your Google account works as expected. The required Python libraries (`numpy`, `pandas`, `scipy`, `matplotlib`) are preinstalled in Colab.

---

## What the notebook covers

The notebook follows the structure of the lecture. Each section corresponds to one conceptual block and produces the inputs for the next.

1. **Data preparation** — loading the Ausgrid extract, inspecting the natural gap distribution, discarding or imputing single-point gaps, filtering to complete days, and normalizing the series.
2. **Synthetic gaps** — injecting contiguous gaps under a controlled protocol that preserves the first and last intervals of every day, storing both the ground truth and the gapped series for evaluation.
3. **Traditional imputations** — linear interpolation, global average, and average-point filling, used as classical references.
4. **Euclidean criterion** — candidate selection by point-wise similarity over the observed intervals, with single-candidate and k-nearest-neighbor variants.
5. **DANLI criterion** — candidate selection in the cumulative space, evaluating the forward and backward cumulative profiles and the total-energy consistency term under two regularization settings.
6. **Combined criterion** — a normalized convex mixture of the Euclidean and DANLI distances, evaluated at the single-candidate and k-nearest-neighbor levels.
7. **Evaluation** — RMSE and absolute energy difference computed over the gap region, comparison across methods, and paired statistical analysis of the per-day results.

---

## Dataset

The tutorial uses the **Ausgrid Distribution Zone Substation Dataset**, published by Ausgrid (New South Wales, Australia) under the Creative Commons Attribution 3.0 Australia license. The extract included in this repository corresponds to a single zone substation (`Meadowbank 132_11kV`) at 15-minute resolution, unified across multiple financial years.

The original data is available from Ausgrid at:

> https://www.ausgrid.com.au/about-us/about-ausgrid/research-data-sets/distribution-zone-substation-data

Ausgrid distributes the dataset as one ZIP archive per financial year, with one CSV per substation. Producing a continuous series from these files requires concatenating the daily rows across years and reconciling the time-of-day headers to a common grid. The notebook describes this procedure; participants who wish to work with additional substations can obtain the original files and apply the same steps.

---

## Citation

If you use this material, please cite the tutorial:

```
Silva-Castro, J. A., & González-Ordiano, J. Á. (2026).
Time Series Imputation using Cumulative Profiles and Pattern-Matching Algorithms.
Tutorial at the 29th Iberoamerican Congress on Pattern Recognition (CIARP 2026),
Mexico City, November 24–27, 2026.
```
