# Seismic-Anomaly-Detection
This Project explores anomaly detection in global seismology data using Autoencoders (AE) and Random Forests (RF) on Raspberry Shake waveforms.

## Project Aim  
Detect earthquake (EQ) events by training an AE on non-earthquake (Non-EQ) background data and treating high reconstruction errors as anomalies.  

## Methods  
- **Data**: 20 Raspberry Shake stations (rural, urban, industrial).  
- **Preprocessing**: Segmentation (5s windows), z-score normalization.  
- **Models**:  
  - Autoencoder (unsupervised)  
  - Random Forest on 64D bottleneck features  
- **Thresholding**: q95 (95 percentile) vs ROC-optimal (Youden’s J).  
- **Exploratory Analysis**: RF probabilities aggregated to detect human activity trends.  

## Results  
- AE achieved ROC-AUC ≈ 0.72 (F1 ≈ 0.79).  
- RF classifier on latent features: ROC-AUC ≈ 0.75.  
- EQs show higher reconstruction error than Non-EQ, but overlap remains.  
- Human activity patterns (urban/industrial) often look EQ-like.  

## Future Work  
- Continuous background monitoring.  
- More advanced models (CNN, LSTM, Transformer, VAE(Variational Autoencoders)).  
- Station-specific thresholds.  

## Technologies  
- Python (NumPy, pandas, scikit-learn, TensorFlow/Keras, Matplotlib)  
- Jupyter Notebook  
- GitHub for version control.
