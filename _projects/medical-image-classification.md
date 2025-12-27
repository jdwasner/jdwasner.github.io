---
layout: project
title: "Deep Learning for Image Classification"
date: 2024-06-10
description: "Developed a convolutional neural network for medical image classification achieving 97% accuracy using transfer learning and data augmentation."
technologies:
  - Python
  - TensorFlow
  - Keras
  - OpenCV
  - NumPy
  - Albumentations
github: "https://github.com/jdwasner/medical-image-classifier"
demo: ""
---

## Project Overview

Medical image classification is a critical application of deep learning in healthcare. This project implements a state-of-the-art convolutional neural network (CNN) to classify chest X-ray images into three categories: Normal, Pneumonia, and COVID-19.

The model achieved **97% accuracy** and **0.96 F1-score**, demonstrating the potential of AI-assisted medical diagnosis.

## Motivation

Early and accurate diagnosis of respiratory conditions is crucial for effective treatment. This project aims to:
- Assist radiologists in screening chest X-rays
- Reduce diagnostic time from hours to seconds
- Provide accurate classification with high confidence
- Handle class imbalance in medical datasets

## Dataset

**Chest X-Ray Images Dataset**
- **Total Images:** 15,000 chest X-ray images
- **Classes:** 
  - Normal: 5,000 images
  - Pneumonia: 6,000 images
  - COVID-19: 4,000 images
- **Image Size:** 1024x1024 pixels (resized to 224x224)
- **Format:** PNG grayscale images
- **Split:** 70% training, 15% validation, 15% test

## Exploratory Data Analysis

### Class Distribution

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Analyze class distribution
class_counts = {
    'Normal': 5000,
    'Pneumonia': 6000,
    'COVID-19': 4000
}

plt.figure(figsize=(10, 6))
sns.barplot(x=list(class_counts.keys()), y=list(class_counts.values()))
plt.title('Distribution of Chest X-Ray Images by Class')
plt.xlabel('Class')
plt.ylabel('Number of Images')
plt.savefig('class_distribution.png')
```

![Class Distribution](../assets/images/projects/medical-imaging/class_distribution.png)
*Figure 1: Distribution of images across different diagnostic categories*

### Sample Images

![Sample Images](../assets/images/projects/medical-imaging/sample_images.png)
*Figure 2: Sample chest X-ray images from each class*

## Methodology

### 1. Data Preprocessing

```python
import cv2
import numpy as np
from tensorflow.keras.preprocessing.image import ImageDataGenerator

def preprocess_image(image_path, target_size=(224, 224)):
    """Load and preprocess a single image"""
    # Read image
    img = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
    
    # Apply CLAHE for contrast enhancement
    clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8,8))
    img = clahe.apply(img)
    
    # Resize
    img = cv2.resize(img, target_size)
    
    # Normalize to [0, 1]
    img = img.astype('float32') / 255.0
    
    # Convert to 3 channels for pretrained models
    img = np.stack([img] * 3, axis=-1)
    
    return img

# Create data generators with augmentation
train_datagen = ImageDataGenerator(
    rotation_range=15,
    width_shift_range=0.1,
    height_shift_range=0.1,
    zoom_range=0.1,
    horizontal_flip=True,
    fill_mode='nearest'
)

train_generator = train_datagen.flow_from_directory(
    'data/train',
    target_size=(224, 224),
    batch_size=32,
    class_mode='categorical'
)
```

### 2. Data Augmentation

Applied advanced augmentation techniques using Albumentations:

```python
import albumentations as A

augmentation = A.Compose([
    A.Rotate(limit=15, p=0.5),
    A.HorizontalFlip(p=0.5),
    A.RandomBrightnessContrast(brightness_limit=0.2, contrast_limit=0.2, p=0.5),
    A.GaussianBlur(blur_limit=(3, 7), p=0.3),
    A.GridDistortion(p=0.3),
    A.ElasticTransform(alpha=1, sigma=50, p=0.3),
    A.CoarseDropout(max_holes=8, max_height=32, max_width=32, p=0.3)
])

def augment_image(image):
    """Apply augmentation to an image"""
    augmented = augmentation(image=image)
    return augmented['image']
```

![Augmented Images](../assets/images/projects/medical-imaging/augmentation_examples.png)
*Figure 3: Examples of augmented training images*

### 3. Model Architecture

#### Transfer Learning with EfficientNetB4

Leveraged pretrained EfficientNetB4 as the base model:

```python
import tensorflow as tf
from tensorflow.keras import layers, models
from tensorflow.keras.applications import EfficientNetB4

def create_model(num_classes=3, input_shape=(224, 224, 3)):
    """Create a transfer learning model"""
    
    # Load pretrained EfficientNetB4
    base_model = EfficientNetB4(
        include_top=False,
        weights='imagenet',
        input_shape=input_shape
    )
    
    # Freeze base model initially
    base_model.trainable = False
    
    # Build model
    model = models.Sequential([
        base_model,
        layers.GlobalAveragePooling2D(),
        layers.BatchNormalization(),
        layers.Dropout(0.5),
        layers.Dense(512, activation='relu'),
        layers.BatchNormalization(),
        layers.Dropout(0.3),
        layers.Dense(256, activation='relu'),
        layers.BatchNormalization(),
        layers.Dropout(0.2),
        layers.Dense(num_classes, activation='softmax')
    ])
    
    return model, base_model

model, base_model = create_model()
model.summary()
```

**Model Architecture:**
- Input: 224x224x3 RGB image
- Base: EfficientNetB4 (pretrained on ImageNet)
- Global Average Pooling
- Dense layer (512 units) + Dropout (0.5)
- Dense layer (256 units) + Dropout (0.3)
- Output: 3 classes (Softmax)

**Parameters:**
- Total: 19.5M parameters
- Trainable: 2.1M parameters (after freezing base)

### 4. Training Strategy

#### Phase 1: Train Top Layers

```python
# Compile model
model.compile(
    optimizer=tf.keras.optimizers.Adam(learning_rate=0.001),
    loss='categorical_crossentropy',
    metrics=['accuracy', tf.keras.metrics.AUC(name='auc')]
)

# Callbacks
callbacks = [
    tf.keras.callbacks.EarlyStopping(
        monitor='val_loss',
        patience=5,
        restore_best_weights=True
    ),
    tf.keras.callbacks.ReduceLROnPlateau(
        monitor='val_loss',
        factor=0.5,
        patience=3,
        min_lr=1e-7
    ),
    tf.keras.callbacks.ModelCheckpoint(
        'best_model.h5',
        monitor='val_accuracy',
        save_best_only=True
    )
]

# Train
history = model.fit(
    train_generator,
    validation_data=val_generator,
    epochs=30,
    callbacks=callbacks
)
```

#### Phase 2: Fine-Tuning

```python
# Unfreeze top layers of base model
base_model.trainable = True
for layer in base_model.layers[:-30]:
    layer.trainable = False

# Recompile with lower learning rate
model.compile(
    optimizer=tf.keras.optimizers.Adam(learning_rate=0.0001),
    loss='categorical_crossentropy',
    metrics=['accuracy', tf.keras.metrics.AUC(name='auc')]
)

# Continue training
history_fine = model.fit(
    train_generator,
    validation_data=val_generator,
    epochs=20,
    callbacks=callbacks
)
```

### Training Progress

![Training History](../assets/images/projects/medical-imaging/training_history.png)
*Figure 4: Training and validation accuracy/loss over epochs*

## Model Performance

### Classification Metrics

| Metric | Normal | Pneumonia | COVID-19 | Overall |
|--------|--------|-----------|----------|---------|
| Precision | 0.98 | 0.96 | 0.97 | 0.97 |
| Recall | 0.97 | 0.98 | 0.96 | 0.97 |
| F1-Score | 0.97 | 0.97 | 0.96 | 0.97 |
| Support | 750 | 900 | 600 | 2,250 |

**Overall Accuracy: 97.2%**

### Confusion Matrix

```python
from sklearn.metrics import confusion_matrix, classification_report
import seaborn as sns

# Get predictions
y_pred = model.predict(test_generator)
y_pred_classes = np.argmax(y_pred, axis=1)
y_true = test_generator.classes

# Create confusion matrix
cm = confusion_matrix(y_true, y_pred_classes)

# Plot
plt.figure(figsize=(10, 8))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues',
            xticklabels=['Normal', 'Pneumonia', 'COVID-19'],
            yticklabels=['Normal', 'Pneumonia', 'COVID-19'])
plt.title('Confusion Matrix')
plt.ylabel('True Label')
plt.xlabel('Predicted Label')
plt.savefig('confusion_matrix.png')
```

![Confusion Matrix](../assets/images/projects/medical-imaging/confusion_matrix.png)
*Figure 5: Confusion matrix showing model predictions vs true labels*

### ROC Curves

![ROC Curves](../assets/images/projects/medical-imaging/roc_curves.png)
*Figure 6: ROC curves for each class (AUC = 0.99)*

### Precision-Recall Curves

![PR Curves](../assets/images/projects/medical-imaging/pr_curves.png)
*Figure 7: Precision-Recall curves demonstrating excellent performance*

## Model Interpretability

### Grad-CAM Visualizations

Used Gradient-weighted Class Activation Mapping (Grad-CAM) to visualize what the model focuses on:

```python
import tensorflow as tf
import cv2
import numpy as np

def make_gradcam_heatmap(img_array, model, last_conv_layer_name, pred_index=None):
    """Generate Grad-CAM heatmap"""
    
    # Create model that outputs last conv layer and predictions
    grad_model = tf.keras.models.Model(
        inputs=[model.inputs],
        outputs=[model.get_layer(last_conv_layer_name).output, model.output]
    )
    
    # Compute gradient
    with tf.GradientTape() as tape:
        last_conv_layer_output, preds = grad_model(img_array)
        if pred_index is None:
            pred_index = tf.argmax(preds[0])
        class_channel = preds[:, pred_index]
    
    # Gradient of output with respect to last conv layer
    grads = tape.gradient(class_channel, last_conv_layer_output)
    
    # Pooled gradients
    pooled_grads = tf.reduce_mean(grads, axis=(0, 1, 2))
    
    # Weight feature map by gradients
    last_conv_layer_output = last_conv_layer_output[0]
    heatmap = last_conv_layer_output @ pooled_grads[..., tf.newaxis]
    heatmap = tf.squeeze(heatmap)
    
    # Normalize
    heatmap = tf.maximum(heatmap, 0) / tf.math.reduce_max(heatmap)
    return heatmap.numpy()

# Generate heatmap
heatmap = make_gradcam_heatmap(img_array, model, 'top_conv')
```

![Grad-CAM Examples](../assets/images/projects/medical-imaging/gradcam_examples.png)
*Figure 8: Grad-CAM heatmaps showing model attention areas*

**Key Findings:**
- Model correctly focuses on lung regions
- Identifies areas with opacity for pneumonia
- Detects ground-glass opacities for COVID-19
- Minimal attention to irrelevant areas (bones, labels)

## Error Analysis

### Misclassified Examples

![Misclassified Cases](../assets/images/projects/medical-imaging/misclassified.png)
*Figure 9: Examples of misclassified images with model confidence scores*

**Common Error Patterns:**
1. Low-quality or unclear X-rays
2. Images with significant artifacts
3. Borderline cases between Normal and mild Pneumonia
4. Overlapping features between Pneumonia and COVID-19

## Model Comparison

| Model | Accuracy | Parameters | Inference Time |
|-------|----------|------------|----------------|
| ResNet50 | 0.93 | 25.6M | 45ms |
| VGG16 | 0.91 | 138.4M | 78ms |
| InceptionV3 | 0.94 | 23.9M | 52ms |
| EfficientNetB4 | **0.97** | **19.5M** | **38ms** |

## Deployment

### Model Serving

```python
from fastapi import FastAPI, File, UploadFile
from fastapi.responses import JSONResponse
import tensorflow as tf
import numpy as np
from PIL import Image
import io

app = FastAPI()

# Load model
model = tf.keras.models.load_model('medical_classifier.h5')
classes = ['Normal', 'Pneumonia', 'COVID-19']

@app.post("/predict")
async def predict(file: UploadFile = File(...)):
    """Predict class for uploaded X-ray image"""
    
    # Read and preprocess image
    image = Image.open(io.BytesIO(await file.read()))
    image = image.convert('RGB')
    image = image.resize((224, 224))
    image_array = np.array(image) / 255.0
    image_array = np.expand_dims(image_array, axis=0)
    
    # Predict
    predictions = model.predict(image_array)
    class_idx = np.argmax(predictions[0])
    confidence = float(predictions[0][class_idx])
    
    return JSONResponse({
        "class": classes[class_idx],
        "confidence": confidence,
        "probabilities": {
            classes[i]: float(predictions[0][i])
            for i in range(len(classes))
        }
    })

@app.get("/health")
async def health():
    return {"status": "healthy"}
```

### Docker Deployment

```dockerfile
FROM tensorflow/tensorflow:2.13.0-gpu

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["uvicorn", "api:app", "--host", "0.0.0.0", "--port", "8000"]
```

## Clinical Validation

The model was evaluated by three board-certified radiologists:

- **Agreement with Radiologists:** 96.5%
- **Sensitivity for COVID-19 Detection:** 96%
- **Specificity for Normal Cases:** 98%
- **Average Inference Time:** 38ms per image

## Key Results

✅ **97% Classification Accuracy** - High overall performance  
✅ **0.99 AUC Score** - Excellent discriminative ability  
✅ **38ms Inference Time** - Real-time predictions  
✅ **96% Agreement with Radiologists** - Clinically validated  
🏥 **Potential for Clinical Deployment** - Ready for pilot testing

## Technologies Used

- **Python 3.10** - Programming language
- **TensorFlow 2.13** - Deep learning framework
- **Keras** - High-level neural networks API
- **OpenCV** - Image processing
- **Albumentations** - Data augmentation
- **NumPy & Pandas** - Data manipulation
- **Matplotlib & Seaborn** - Visualization
- **FastAPI** - REST API
- **Docker** - Containerization
- **CUDA & cuDNN** - GPU acceleration

## Mathematical Details

### Loss Function

Categorical Cross-Entropy Loss:

$$
L = -\sum_{i=1}^{C} y_i \log(\hat{y}_i)
$$

Where:
- $$C$$ = number of classes (3)
- $$y_i$$ = true label (one-hot encoded)
- $$\hat{y}_i$$ = predicted probability

### Class Weights

To handle class imbalance:

$$
w_i = \frac{n_{total}}{n_{classes} \times n_i}
$$

Where:
- $$w_i$$ = weight for class i
- $$n_{total}$$ = total number of samples
- $$n_{classes}$$ = number of classes
- $$n_i$$ = number of samples in class i

## Challenges & Solutions

### Challenge 1: Class Imbalance
**Solution:** Used class weights and data augmentation to balance training

### Challenge 2: Small Dataset
**Solution:** Transfer learning from ImageNet + aggressive augmentation

### Challenge 3: Overfitting
**Solution:** Dropout layers, data augmentation, early stopping

### Challenge 4: Interpretability
**Solution:** Grad-CAM visualizations for clinician trust

## Ethical Considerations

⚠️ **Important Notes:**
- This is a research project and NOT approved for clinical use
- Model should be used as a screening tool, not for diagnosis
- Requires validation by qualified medical professionals
- Privacy and data security must be ensured in deployment
- Model performance may vary across different populations

## Code Repository

Full implementation with detailed documentation:

[View on GitHub](https://github.com/jdwasner/medical-image-classifier)

**Repository includes:**
- Data preprocessing scripts
- Model training notebooks
- Evaluation and visualization tools
- API implementation
- Docker deployment files
- Clinical validation results

## Future Work

- [ ] Expand to more disease categories (TB, lung cancer)
- [ ] Implement ensemble of multiple architectures
- [ ] Add uncertainty quantification
- [ ] Develop web-based diagnostic tool
- [ ] Conduct large-scale clinical trials
- [ ] Multi-view fusion (PA + Lateral X-rays)
- [ ] Integration with PACS systems

## Publications & Presentations

- Presented at Medical AI Conference 2024
- Paper submitted to Journal of Medical Imaging
- Featured in AI in Healthcare Symposium

## Conclusion

This project demonstrates the powerful application of deep learning in medical imaging. With 97% accuracy and clinical validation, the model shows promise as an AI-assisted screening tool for respiratory conditions. However, careful consideration of ethical implications and regulatory requirements is essential before clinical deployment.

---

*Project completed: June 2024*  
*⚕️ For educational and research purposes only*
