# ADPLS (NMR Proximal Hybrid Baseline Corrector)

ADPLS is an advanced baseline correction tool for 1D NMR spectra combining adaptive reweighted penalised least squares (arPLS) with interactive hard-anchor constraints.

---

## Features
- **Adaptive Baseline Fitting**: Uses the arPLS algorithm to effectively estimate complex baseline distortions commonly observed in cryogenic probe measurements without accidental peak suppression.
- **Interactive Hard-Anchor Constraints**: Powered by the **ADMM optimization framework**, allowing users to manually specify fixed baseline regions to protect broad signals (such as synthetic polymer $^{13}\text{C}$ peaks) from being distorted.
- **Bruker TopSpin Integration**: Direct importing from Bruker 1D binary data (`1r`) and seamless exporting of corrected spectra back into new `pdata` directories.
- **Flexible Workflow**: Operates fully automatically as a standard arPLS corrector, or interactively with user-guided anchor regions.

---

## System Requirements
- **OS**: Windows 11 (64-bit recommended)
- **Runtime**: Self-contained executable (Portable GUI Application)

---

## How to Use & Data Preparation

### 1. Data Processing in Bruker TopSpin
- Ensure your 1D NMR spectrum (e.g., $^{13}\text{C}$ or $^{1}\text{H}$) has already undergone **Fourier Transformation (FT)** and **Phase Correction** in TopSpin.

### 2. Loading Data
1. Launch the ADPLS application.
2. In **1. Experiment Directory**, set the path (`Dir`) to your TopSpin experiment directory (`EXPNO`).
3. Set the original processed data directory number in `pdata` (e.g., `1`).
4. Click **Load 1r**. The original spectrum will be loaded and displayed in gray in the plot area.

### 3. Baseline Correction & Parameter Adjustment
1. **Range Filtering (`Range (ppm)`)**: Set the target chemical shift range to exclude distorted edge regions from baseline calculation.
2. **Rigidity (`Lambda`)**: Adjust the smoothing parameter. 
   - Smaller values fit tighter to peaks.
   - Larger values create a smoother, more rigid baseline (recommended when using anchor regions).
3. **Run Calculation**: Click **Run Baseline Correction**.

### 4. Specifying Baseline Regions (Anchor Mode - Optional)
- To protect specific peak regions (e.g., polymer broad signals), left-click and drag across the plot to select green **Anchor (Fixed)** regions.
- Multiple anchor regions can be set. To reset, click **Clear Anchor Regions**.
- *Note*: Ensure navigation/zoom tools on the plot toolbar are deactivated before dragging to select regions.

### 5. Exporting Results
- Enter a destination directory number in **New pdata No.** (e.g., `999`).
- Click **Export to TopSpin**.
- The original processing settings and spectrum parameters from `pdata 1` will be cloned into the new `pdata` directory along with the baseline-corrected `1r` file. Verify the newly created `pdata` inside TopSpin.

---

## Advanced Options

- **`Rho (ADMM Sync)`**: Controls the ADMM constraint enforcement step size (Default: `0.1`).
- **`Max Iterations`**: Maximum convergence iterations for the solver (Default: `300`).
- *Recommendation*: Keep these parameters at their default values unless handling specific non-convergent cases.

---

## License & Terms of Use

Provided under a custom End-User License Agreement (EULA).
- **Academic & Non-Commercial Use**: Free for personal, educational, academic, and research purposes.
- **Commercial Use Restricted**: Commercial use or integration into commercial services requires a separate commercial license.
- For full details, please refer to **`LICENSE.txt`**.

---

## Community & Support

- **Community**: Please use [GitHub Discussions](https://github.com/your-username/ADPLS/discussions) to ask questions, share usage examples, and exchange information with other users.
- **Disclaimer**: Provided "as is" for evaluation and research purposes. Individual technical support or customized bug fixes are not provided.

---

## Author & Acknowledgments

- **Author**: Ryuichi Tanigawa (TANIGAWA AGRISCIENCE)
- **Technical Support**: Developed with technical assistance from generative AI tools, including Google Gemini.