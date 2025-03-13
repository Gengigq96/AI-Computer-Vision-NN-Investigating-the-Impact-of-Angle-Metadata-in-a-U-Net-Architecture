# Investigating the Impact of Angle Metadata in a U-Net Architecture

## 📌 Overview

This project explores how incorporating **angle metadata** in a **U-Net** architecture affects performance in image segmentation tasks. The angle information has been integrated at different stages of the network:

✅ As a **4th dimension** in RGB images  
✅ In the **bottleneck layer** during encoding-decoding  
✅ In the **Attention Gate layer** of the decoder  
✅ **Combination of last two approaches**   
✅ **Combination of all three approaches**  

Additionally, the dataset was modified to introduce **extreme noise**, making it impossible for humans to recognize objects, ensuring the model relies purely on learned features.

## 🎯 Objectives

- **Preprocess video data** by converting frames into individual images.  
- **Generate segmentation masks** using **SAM-2**.  
- **Apply extreme noise** to obscure images beyond human recognition.  
- **Train multiple U-Net models**:
  - **Baseline model** (without angle metadata).  
  - **Three separate models**, each incorporating angle metadata at a different stage.  
  - **A final model**, combining all angle integrations.  
- **Evaluate performance** and compare predictions.  

## 🖼️ Dataset Preparation  

1. **Video to Image Conversion**:  
   - Extract individual frames from videos.  
2. **Mask Generation**:  
   - Use **SAM-2** to generate segmentation masks.  
3. **Noise Application**:  
   - Apply extreme noise to the original images to remove human-recognizable details.  

---

## 🏗️ Model Architecture & Angle Integration  

The angle information was incorporated in different parts of the **U-Net** architecture:

| Model Version | Angle Integration |  
|--------------|------------------|  
| **Baseline** | No angle information used |  
| **Model 1** | Angle as a **4th channel** in input images (RGB+A) |  
| **Model 2** | Angle added in the **bottleneck layer** (encoder-decoder transition) |  
| **Model 3** | Angle incorporated in the **Attention Gate** of the decoder |  
| **Model 3** | Combination of model 2 and 3 |  
| **Model 4** | Combination of all three methods above |  

---

## 📊 Results  

The GIF below **compares the predictions** of the **Baseline Model** vs. the **Best Model** (which incorporates angle metadata at all stages).  

**🔽 Predictions Comparison (Baseline vs. Best Model) 🔽**  
![Model Comparison](./predictions_comparison.gif)  

### Key Observations:
✅ The **angle-enhanced model** provides more refined segmentation.  
✅ The network effectively **learns from angle metadata**, even under extreme noise.  
✅ The best results are obtained when integrating angle information **at all stages**.  

---

## 🛠️ How to Run the Project  

### 1️⃣ Install Dependencies  

```bash
pip install numpy opencv-python matplotlib tensorflow keras segment-anything
>>>>>>> 968c354 (aproach u-net model approach)
