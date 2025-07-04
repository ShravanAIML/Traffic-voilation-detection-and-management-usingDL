# Traffic-voilation-detection-and-management-usingDL
This project presents a comprehensive, AI-powered traffic monitoring system aimed at enhancing road safety and optimizing urban traffic flow. Leveraging advanced deep learning models, the system performs real-time object detection using YOLOv12 to identify vehicles, lane markings, traffic signals, and detect violations such as helmet-less riding, red-light jumping, and wrong-lane driving directly from surveillance video streams.

To address traffic congestion proactively, a Long Short-Term Memory (LSTM) network is trained on time-series traffic data extracted from the video feed, enabling the system to predict congestion levels 15 minutes in advance. For finer-grained tasks—like license plate recognition or traffic sign classification—models such as CNN or RCNN are seamlessly integrated.

Upon detecting a violation, the system employs OCR techniques to extract license plate numbers and automatically references a connected vehicle database to generate and log fines. A built-in alert module notifies traffic authorities of imminent congestions or detected infractions, supporting timely decision-making.

Developed and tested on Google Colab, this solution utilizes key frameworks including OpenCV, TensorFlow, and PyTorch. Performance is evaluated using metrics like mAP (mean Average Precision) for detection accuracy and RMSE (Root Mean Squared Error) for predictive modeling—ensuring both robustness and reliability.

![image](https://github.com/user-attachments/assets/3d54c4c0-cb56-473a-8879-6d1fca1fb7c2)

#Video Input (Surveillance Camera)
        ↓
  Frame Extraction (OpenCV)
        ↓
  YOLOv12 → Object Detection (vehicle, helmet, signal, lane)
        ↓
  CNN/RCNN → Fine classification (violation, number plate)
        ↓
  OCR → License plate recognition
        ↓
  Fine Generation & Logging (Database)
        ↓
  LSTM → Congestion Prediction (15 min ahead)
        ↓
  Alert System → Authority Notification #

![image](https://github.com/user-attachments/assets/160a1382-1e70-4146-929f-af4dc046af43)

📊 Model Evaluation Summary
The model's performance has been assessed using three key visualizations: the confusion matrix, the precision-recall (PR) curve, and training-validation metric plots. Together, these provide a comprehensive understanding of the object detection model’s strengths and limitations.

🔄 Confusion Matrix Insights
The confusion matrix reveals that the model performs exceptionally well in detecting motorcycles, achieving 758 correct predictions. However, it struggles significantly with other object classes such as cars, trucks, and buses, where predictions are either absent or highly inaccurate. There is also notable misclassification of the background as motorcycles and vans, suggesting difficulties in distinguishing object classes from non-object regions. This issue may stem from dataset imbalance or poor annotation quality, both of which could misguide the model during training.

📈 Precision-Recall Curve Analysis
The PR curve corroborates these findings:

The motorcycle class achieves a strong mean Average Precision (mAP) of 0.849, indicating the model can detect and localize motorcycles with high confidence.

In contrast, car and truck classes score an mAP of 0.000, signifying complete detection failure.

The van and bus classes show modest performance with mAP values of 0.255 and 0.217, respectively.

The overall mAP@0.5 across all classes is 0.334, suggesting that while the model has potential, it lacks consistency and generalization across different object categories.

📉 Training and Validation Metrics
The training logs show that the model is learning effectively over 15 epochs:

Box loss, classification loss, and DFL loss consistently decrease across epochs, indicating stable convergence.

Precision and recall improve steadily, as do both mAP@0.5 and mAP@0.5:0.95, which further confirms the model is generalizing well on the validation set.

Despite these improvements, the low detection accuracy for several classes points to necessary enhancements in:

Data balancing to ensure all classes are equally represented.

Data augmentation techniques to improve the model’s robustness.

Model tuning or architectural adjustments to better capture underrepresented object features.
