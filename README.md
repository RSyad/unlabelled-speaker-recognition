# Unlabelled Speaker Recognition Project

## 1. Data Exploration and Analysis
### Characteristics & Challenges
- **Unlabelled nature**: No ground truth for validation
- **Potential issues**: Background noise, varying recording quality, speaker overlap
- **Diversity**: 200 speakers likely have varying vocal characteristics

### Initial Exploration Steps
- [ ] Visualize waveform amplitudes across samples
- [ ] Generate MFCC/specrogram visualizations for 10-20 samples
- [ ] Compute duration statistics (min/max/avg recording length)
- [ ] Attempt qualitative clustering with t-SNE/UMAP on raw features

## 2. Proposed Solution
### Primary Approach: Self-Supervised Speaker Embedding + Clustering
**Pipeline:**
1. Preprocessing
   - Voice activity detection (pyannote.voice or simple amplitude threshold)
   - Noise reduction (optional spectral gating)

2. Feature Extraction
   - Extract speaker embeddings using pre-trained model (ECAPA-TDNN, x-vectors)
   - Alternative: MFCCs + Delta features as baseline

3. Clustering
   - HDBSCAN (handles unknown cluster count)
   - OPTICS (for density-based clustering)
   - Spectral clustering (if clear manifold structure exists)

**Justification:**
- Pre-trained models capture speaker characteristics without labels
- Density-based clustering works better than K-means for unknown speaker count
- Visualization of embeddings provides qualitative validation

### Alternative Approach: Contrastive Learning
- Train Siamese network to learn discriminative features
- Requires careful pair sampling strategy

## 3. Implementation Strategy
```python
# Pseudocode
def process_audio():
   for recording in dataset:
       # VAD & preprocessing
       clean_audio = remove_noise(recording)
       segments = detect_voice_activity(clean_audio)
       
       # Feature extraction
       embeddings = ecapa_model.extract(segments)
       
       # Clustering
       cluster_labels = hdbscan.fit_predict(embeddings)# Unlabelled Speaker Recognition Project

## 1. Data Exploration and Analysis
### Characteristics & Challenges
- **Unlabelled nature**: No ground truth for validation
- **Potential issues**: Background noise, varying recording quality, speaker overlap
- **Diversity**: 200 speakers likely have varying vocal characteristics

### Initial Exploration Steps
- [ ] Visualize waveform amplitudes across samples
- [ ] Generate MFCC/specrogram visualizations for 10-20 samples
- [ ] Compute duration statistics (min/max/avg recording length)
- [ ] Attempt qualitative clustering with t-SNE/UMAP on raw features

## 2. Proposed Solution
### Primary Approach: Self-Supervised Speaker Embedding + Clustering
**Pipeline:**
1. Preprocessing
   - Voice activity detection (pyannote.voice or simple amplitude threshold)
   - Noise reduction (optional spectral gating)

2. Feature Extraction
   - Extract speaker embeddings using pre-trained model (ECAPA-TDNN, x-vectors)
   - Alternative: MFCCs + Delta features as baseline

3. Clustering
   - HDBSCAN (handles unknown cluster count)
   - OPTICS (for density-based clustering)
   - Spectral clustering (if clear manifold structure exists)

**Justification:**
- Pre-trained models capture speaker characteristics without labels
- Density-based clustering works better than K-means for unknown speaker count
- Visualization of embeddings provides qualitative validation

### Alternative Approach: Contrastive Learning
- Train Siamese network to learn discriminative features
- Requires careful pair sampling strategy

## 3. Implementation Strategy
```python
# Pseudocode
def process_audio():
   for recording in dataset:
       # VAD & preprocessing
       clean_audio = remove_noise(recording)
       segments = detect_voice_activity(clean_audio)
       
       # Feature extraction
       embeddings = ecapa_model.extract(segments)
       
       # Clustering
       cluster_labels = hdbscan.fit_predict(embeddings)
