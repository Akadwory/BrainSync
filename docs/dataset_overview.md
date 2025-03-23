# BrainSync Dataset Overview: BCI Competition IV - Dataset 2a

## Overview  
This project utilizes **BCI Competition IV - Dataset 2a**, which is a **motor imagery EEG dataset** designed for brain-computer interface (BCI) research. The dataset contains **EEG recordings from 9 subjects**, where each subject performed **four different motor imagery tasks**.

---

## Dataset Details  
| **Category**   | **Description** |
|---------------|----------------|
| **Subjects**  | 9 (A01 - A09) |
| **Tasks**     | Motor imagery of left hand, right hand, both feet, tongue |
| **Channels**  | 22 EEG electrodes |
| **Sampling Rate** | 250 Hz |
| **Recording Length** | ~4 minutes per task |
| **File Format** | `.gdf` (General Data Format for Biosignals) |

Each subject has **two types of EEG recordings**:
- **Training Set (`A0xT.gdf`)** → Used for model training.
- **Evaluation Set (`A0xE.gdf`)** → Used for testing.

---

## Data Files & Structure  
data/ │── raw/
│ ├── A01T.gdf # Subject 1 - Training EEG data │ ├── A01E.gdf # Subject 1 - Evaluation EEG data │ ├── A02T.gdf # Subject 2 - Training EEG data │ ├── ... │── processed/
│ ├── A01T_preprocessed.fif # Preprocessed EEG file │ ├── ... │── metadata/
│ ├── labels.csv # Event markers & corresponding labels │ ├── channels.txt # List of EEG electrode positions

- **`raw/`** → Contains original EEG `.gdf` files.  
- **`processed/`** → Contains preprocessed EEG signals for AI training.  
- **`metadata/`** → Stores labels, channel locations, and event markers.  

---

## EEG Electrode Placement (Based on 10-20 System)  
The dataset uses **22 EEG electrodes**, positioned as follows:

Fz    |    FC3   FCz   FC4
C3    |    Cz    C4    
CP3   |    CPz   CP4   
Pz    |    P3    P4
O1    |         O2



These electrodes are placed on the **motor cortex**, capturing **brain signals related to movement planning and execution**.

---

## Event Markers & Labels  
Each `.gdf` file contains **event markers** that indicate when a subject was performing a specific motor imagery task.

| **Event Code** | **Motor Imagery Task** |
|--------------|----------------|
| **1**       | Left Hand |
| **2**       | Right Hand |
| **3**       | Both Feet |
| **4**       | Tongue |

**Why does this matter?**  
- These event markers allow the AI model to **map EEG signals to movement intentions**.  
- We use these markers for **training supervised & self-supervised deep learning models**.  

---

## Preprocessing Steps  
Before EEG signals can be used for AI models, they must go through **preprocessing** to remove noise and artifacts.

 **Bandpass Filtering** → Removes unwanted frequencies (0.5 Hz - 100 Hz).  
 **Notch Filtering** → Eliminates power-line noise (50 Hz).  
 **Independent Component Analysis (ICA)** → Removes eye/muscle artifacts.  
 **Epoch Extraction** → Converts continuous EEG into fixed time-windows.  
 **Normalization & Standardization** → Ensures models learn efficiently.  

 **These preprocessing steps ensure that the EEG data is clean and optimized for AI-based decoding.**  

---

## Why This Dataset?  
 **Trusted in Neuroscience Research** → Used in **hundreds of BCI studies**.  
 **Clear Labels for Deep Learning** → Enables **high-performance neural decoding**.  
 **Rich EEG Data** → Provides **diverse brain activity for AI models**.  

This dataset forms the **foundation for our groundbreaking BrainSync pipeline**, allowing us to **train deep learning models that can decode human thoughts**.

---

## References  
- **BCI Competition IV Dataset**: [Official Link](http://www.bbci.de/competition/iv/)  
- **MNE Library for EEG Processing**: [MNE Docs](https://mne.tools/stable/)  

---

## Contributors  
- **Adam Kadwory** – Machine Learning Engineer & Neuroengineering Specialist  

---

## Next Steps  

Now that the **dataset structure and preprocessing details** are documented, the next step is to **define the AI model pipeline** for EEG decoding.  

 **Up Next: `docs/PIPELINE_DESIGN.md`**  
- How raw EEG data moves through the **BrainSync pipeline**.  
- Detailed steps of **feature extraction, deep learning models, and inference**.  
- How the AI will learn to **decode brain signals in real-time**.  

 **BrainSync is shaping up to be an industry-standard Brain-AI project. Let’s keep executing with precision.**  
