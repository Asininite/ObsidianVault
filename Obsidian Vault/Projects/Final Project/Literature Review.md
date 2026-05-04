This is an incredibly smart way to prepare, Ashwin. Evaluators frequently flip to the Literature Survey section to see if you actually understand the landscape or if you just copy-pasted abstracts to hit a page requirement. When they ask about these papers, they are testing your ability to justify your engineering trade-offs.

Your universal defense for almost all of these papers is twofold: **Either the paper entirely ignored adversarial robustness, or it was far too computationally expensive for a practical, deployable tool.**

Here is your cheat sheet for all 10 papers, breaking down what they are and exactly how to defend why you didn't use their approach.

### 1. 3D Face Mesh-Based Detection (2023)

- **What it does:** Reconstructs a 3D mesh of the face and analyzes geometric consistencies to catch deepfakes.
    
- **Why you didn't use it (Your Defense):** "While 3D mesh analysis is robust to basic 2D attacks, it requires highly computationally intensive 3D feature extraction and specialized data. Our AFSL framework applied to a 2D CNN is much more practical for real-time media verification while still achieving high adversarial robustness."
    

### 2. Compression-Aware Wavelet + Conv3D Detection (2022)

- **What it does:** Uses wavelets and 3D convolutions to achieve 99.16% accuracy on highly compressed deepfake videos.
    
- **Why you didn't use it (Your Defense):** "This architecture is excellent at handling compression artifacts, but it entirely ignores the threat of adversarial attacks. Our system trades a few percentage points of clean accuracy to ensure the detector doesn't collapse under PGD attacks, which this model would."
    

### 3. Reversible Face De-Identification with FPE (2023)

- **What it does:** Uses Format-Preserving Encryption to protect personal images by cryptographically scrambling the face.
    
- **Why you didn't use it (Your Defense):** "Encryption-based privacy requires complex key management to reverse the process. We wanted a user-friendly, model-agnostic approach. Our C&W Privacy Filter uses imperceptible adversarial noise instead, protecting the image from AI without needing passwords or keys."
    

### 4. WaViT-CDC: Spatial-Frequency Fusion (2023)

- **What it does:** Combines Vision Transformers (ViT) and wavelets to look at both spatial and frequency features for better generalization.
    
- **Why you didn't use it (Your Defense):** "This is a highly complex, multi-component architecture that was primarily tested on grayscale inputs. Instead of building an overly complex multi-scale extractor, our AFSL approach focuses on making a standard ResNet-50 feature extractor fundamentally invariant to perturbations."
    

### 5. StatAttack: Adversarial Consistency Attack (2024)

- **What it does:** Creates natural-looking adversarial attacks that degrade images specifically to fool deepfake detectors with an 89.6% success rate.
    
- **Why you didn't use it (Your Defense):** "This paper proposes an _attack_, not a defense. We included it to demonstrate the severity of the exact vulnerability that our AFSL framework is designed to fix."
    

### 6. Lightweight Attention-Enhanced CNN (2024)

- **What it does:** Uses an extremely lightweight attention mechanism (only 0.046G FLOPs) to hit 98% accuracy, ideal for mobile devices.
    
- **Why you didn't use it (Your Defense):** "It achieves incredible speed, but it suffers from a significant generalization gap and lacks any adversarial robustness evaluation. For a forensic media verification tool, security and reliability under attack are far more critical than extreme edge-device optimization."
    

### 7. AVA Attack: Attribute-Level Perturbation (2023)

- **What it does:** Uses a GAN to generate semantically meaningful adversarial noise (like slightly shifting a smile) rather than just random pixel noise.
    
- **Why you didn't use it (Your Defense):** "Like StatAttack, this is a sophisticated attack methodology, not a defense. Standard detectors fail entirely against these semantic shifts, which further justifies why our explicit feature-level alignment (ASL) is necessary."
    

### 8. Standard Adversarial Defense for CNN Detectors (2022)

- **What it does:** A basic 7-layer CNN that just uses standard adversarial training (feeding it noisy images).
    
- **Why you didn't use it (Your Defense):** "This establishes the baseline for standard adversarial training, but as we noted, it is vulnerable to unseen attacks and poor generalization. Our AFSL framework goes significantly further by using dual-loss (ASL+SRL) to explicitly align features, preventing the model from just blindly memorizing the noise."
    

### 9. Multi-Modal Comparative Analysis on Audio Deepfakes (2023)

- **What it does:** Uses hybrid DNNs to analyze audio spectrums to catch voice cloning.
    
- **Why you didn't use it (Your Defense):** "This architecture is specifically optimized for the audio modality. Our project scope is strictly focused on visual deepfake detection and facial manipulation. However, our visual AFSL system could easily run in parallel with this audio system in a real-world setting."
    

### 10. Ensemble-TabTransformer for Deepfake Detection (2024)

- **What it does:** Combines 3D landmarks with a Tabular Transformer to achieve a 97.18% F1-score.
    
- **Why you didn't use it (Your Defense):** "This is a very strong detector, but it relies on a computationally intensive extraction pipeline and, crucially, includes no adversarial robustness evaluation. In fact, our AFSL dual-loss framework could theoretically be applied on top of this architecture to give it the robustness it currently lacks."
    

---

If an evaluator tries to corner you by asking why you didn't use the newest Vision Transformers or 3D models, firmly remind them: **"Accuracy on clean data is a solved problem. Our project trades a few points of that clean accuracy to solve the unsolved problem: adversarial vulnerability."**

Are there any of these papers you feel shaky on, or do you want to move on to anticipating questions about your final conclusion?