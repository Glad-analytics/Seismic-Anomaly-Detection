# Seismic-Anomaly-Detection
This project investigates how machine learning models behave when detecting rare seismic events within continuous, noisy background data. Using waveform recordings from Raspberry Shake stations across urban, rural, and industrial environments, the work explores both the strengths and limitations of unsupervised anomaly detection when applied to real-world sensing systems.

## Project Aim  
Train an autoencoder on non-earthquake background data to learn normal signal behaviour, then identify earthquake events as deviations from this learned baseline. A secondary goal was to understand where and why this approach breaks down in the presence of human-generated noise.

## Methods  
Models were evaluated not only on classification performance, but on how well their outputs could support practical decision-making in ambiguous conditions.
- **Data**: 20 Raspberry Shake stations (rural, urban, industrial).  
- **Preprocessing**: Segmentation (5s windows), z-score normalization.  
- **Models**:  
  - Autoencoder (unsupervised)  
  - Random Forest on 64D bottleneck features  
- **Thresholding**: q95 (95 percentile) vs ROC-optimal (Youden’s J).  
- **Exploratory Analysis**: RF probabilities aggregated to detect human activity trends.  

## Results  
Earthquake events generally produced higher reconstruction error than background data; however, significant overlap remained, particularly in urban and industrial environments where human activity produced EQ-like signals.
- AE achieved ROC-AUC ≈ 0.72 (F1 ≈ 0.79).  
- RF classifier on latent features: ROC-AUC ≈ 0.75.

## Interpretation and Limitations
While the autoencoder–Random Forest pipeline demonstrated useful separation between earthquake and non-earthquake signals, the results highlight an important limitation of purely automated anomaly detection. In environments with strong human activity, reconstruction error alone is insufficient for reliable decision-making. This reinforces the need for context-aware thresholds, station-specific calibration, and human-assisted approaches when deploying such systems in practice.

## Future Work  
- Station-specific thresholds and calibration strategies.  
- Sequence models (CNNs, LSTMs, Transformers) for temporal context.
- Continuous background monitoring and long-term trend analysis.
- Variational approaches to model uncertainty explicitly. 

## Technologies  
- Python (NumPy, pandas, scikit-learn, TensorFlow/Keras, Matplotlib)  
- Jupyter Notebook  
- GitHub for version control.
  
## Notebooks
1. **Baseline notebook** — waveform download, segmentation, first AE baseline  
   - [Notebook 1 (IPYNB)](notebooks/PROJECT.ipynb)  
   - If GitHub can’t render it, open the **[HTML view](notebooks/PROJECT.html)** (same content, with outputs).
     *(⚠️ Large file — please download and open locally in a browser to see code + outputs).*

2. **Improved model + Human Activity Trends** — refined AE, RF on bottlenecks, activity analysis  
   - [Notebook 2 (IPYNB)](notebooks/ProjectCONTD2.ipynb)

3. **Stress test (M7.5–M8.8 earthquakes)** — separation checks on large events  
   - [Notebook 3 (IPYNB)](notebooks/PROJT3.ipynb)

## Reports
- **[Final Project Report (PDF)](reports/Final%20Project%20Report.%20Anomaly%20Detection.pdf)**  
  A comprehensive write up covering background, methodology, experiments, results, discussion, and future directions.  
