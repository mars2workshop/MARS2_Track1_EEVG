# 🧭 Intruduction

This repository provides a batch inference pipeline using EEVG for Multimodal Reasoning Competition Track1 [(VG-RS)](https://eval.ai/web/challenges/challenge-page/2552/overview). Given a set of image-question pairs, the model outputs the corresponding bounding box coordinates.

---

## 📦 Environment Requirements

This script is tested with the following setup:

- Python 3.9.10
- PyTorch 1.9.0 + cu111 + cp39
- Check requirements.txt for other dependencies.

---

## 🗂 Directory Structure

```
project_root/
├── eval_for_MARS2.py                          # Main inference script
├── trans_to_origin_box.py                     # Convert script
├── show_origin_box.py                         # Visualize script
├── images/                                    # Folder with images
│   └── *.jpg / *.png
├── VG-RS-question.json                        # Input questions and image paths
├── EEVG_VG_predictions.json                   # Output predictions (bounding boxes xywh)
└── EEVG_VG_predictions_final.json             # Output predictions (bounding boxes x1y1x2y2)
```

---
## 🧪 How to Run Inference

### ✍️ Prepare Input JSON

The file `VG-RS-question.json` should be a list of entries in this format:

```json
[
  {
    "image_path": "images\\example.jpg",
    "question": "What object is next to the red car?"
  },
  ...
]
```

### 🚀 Run Script

```
# Step 1: Run evaluation script to get xywh predictions
python eval_for_MARS2.py

# Step 2: (Optional) Visualize the predicted boxes
python show_origin_box.py

# Step 3: Convert xywh boxes to x1y1x2y2 format for evaluation
python trans_to_origin_box.py
```

---

## 📤 Output Format

The result will be saved as a JSON file containing predicted bounding boxes for each input:

```json
[
  {
    "image_path": "images\\example.jpg",
    "question": "What object is next to the red car?",
    "result": [[x1, y1], [x2, y2]]
  },
  ...
]
```

> Note: Bounding boxes are in the format `[[x_min, y_min], [x_max, y_max]]`.

---

## 📝 Reference

If you use this code and our data, please cite:
> @article{yao2025lens,  
> title={LENS: Multi-level Evaluation of Multimodal Reasoning with Large Language Models},  
> author={Yao, Ruilin and Zhang, Bo and Huang, Jirui and Long, Xinwei and Zhang, Yifang and Zou, Tianyu and Wu, Yufei and Su, Shichao and Xu, Yifan and Zeng, Wenxi and others},  
> journal={arXiv preprint arXiv:2505.15616},  
> year={2025}  
> }

> @inproceedings{chen2024efficient,  
> title={An efficient and effective transformer decoder-based framework for multi-task visual grounding},   
> author={Chen, Wei and Chen, Long and Wu, Yu}, 
> booktitle={European Conference on Computer Vision},   
> pages={125--141},     
> year={2024},  
> organization={Springer}   
} 

---

## 💬 Contact

If you encounter any issues or have questions, feel free to open an issue on GitHub.