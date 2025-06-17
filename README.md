# Introduction

This project is about figuring out how to recognize individual speakers from a set of unlabelled audio recordings. There are over 200 unique speakers, but no labels. The challenge is to explore how we might group or identify them based on just the audio itself.

Given my background in software development and backend systems, I approached this by combining some light data exploration, a bit of signal processing, and unsupervised learning techniques. I haven't done production-level audio work before, but I do have experience working with raw data, so I approached this as a technical problem that can be broken down and tested step-by-step.

---

## 1. Data Exploration & Analysis (10%)
### Initial Thoughts
Unlabelled audio data is tricky because:
- There's no way to directly verify your clustering is "correct"
- People can sound very similar or very different depending on how/when they talk
- Recording conditions (microphone quality, noise, etc.) can introduce a lot of variability

### What I Would Do First
- [ ] **Listen to samples:** Randomly pick 10–15 files to understand quality, length, noise, etc
- [ ] **Visualize waveforms:** Use Python libraries like `librosa` or `scipy` to plot waveforms and spectrograms
- [ ] **Check durations:** Are all recordings similar in length? Some speakers might dominate if not
- [ ] **Basic patterns:** Even without labels, maybe certain speech rhythms, pitch ranges, or energy levels could hint at different speakers

---

## 2. Proposed Solutions & Justification (10%)
