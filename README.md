# Custom Image Classifier
Google Colab Link Here: https://colab.research.google.com/drive/1nbuTrgRi6nqxlNpMEQGIBr5e9K2V8FwV?usp=sharing


# Guide Questions (Student Reflection & Explanation)

**1. Dataset Preparation**
-
○ How did you organize your dataset in Google Drive?
- The dataset was organized in Google Drive within a main directory named ImageDataset. Inside this directory, there are subdirectories, where each subdirectory corresponds to a specific class (e.g., alfalfa, amaranth, artichoke). Each of these class subdirectories contains the images belonging to that class.
  
○ Why is folder structure important for TensorFlow image loading?
- The folder structure is crucial because TensorFlow's tf.keras.utils.image_dataset_from_directory utility relies on this specific hierarchical organization to automatically infer class labels. Each subdirectory name becomes a class label, and all images within that subdirectory are assigned to that class. This simplifies the data loading and labeling process significantly, preventing the need for manual labeling of thousands of images.

**2. Model Training**
-
○ What is the role of convolutional layers in image classification?
- Convolutional layers (Conv2D) are the core building blocks of Convolutional Neural Networks (CNNs) for image classification. Their primary role is to automatically learn hierarchical features from the input images. They do this by applying filters (kernels) that scan across the image, detecting patterns such as edges, textures, shapes, and more complex structures. Early layers detect simple features, while deeper layers combine these simple features to recognize more abstract patterns relevant for distinguishing between different classes.
  
○ Why do we split data into training and validation sets?
- We split data into training and validation sets to accurately evaluate the model's performance on unseen data and to detect overfitting.The training set is used to teach the model, allowing it to learn patterns and relationships within the data.The validation set is used to tune the model's hyperparameters and to monitor its performance during training. By evaluating the model on data it hasn't seen during training, we can get an unbiased estimate of its generalization capability. If the model performs very well on the training set but poorly on the validation set, it's a strong indication of overfitting (where the model has memorized the training data rather than learning generalizable patterns).
  
**3. Performance Analysis**
-
○ What accuracy did your model achieve?
-  The initial model (before data augmentation and dropout) achieved a validation accuracy of 0.9894 (approximately 98.94%) after 10 epochs. The improved model with data augmentation and dropout was still training when the notebook state was captured, showing an accuracy of about 0.6882 on the training data and improving validation accuracy.
  
○ How did the number of images affect the model’s performance?
- In general, a larger and more diverse dataset (more images) usually leads to better model performance. More images provide the model with a broader range of examples to learn from, which helps it generalize better to new, unseen images and reduces the risk of overfitting. Conversely, a small dataset can lead to overfitting because the model might simply memorize the limited examples rather than learning robust features.

-In this notebook, we started with ~7500 images, and after removing problematic ones, ~7552 images were loaded. This is a reasonably good number for a custom dataset, contributing to the high accuracy observed.

**4. Critical Thinking**
-
○ What challenges did you encounter while using your own dataset?
- A significant challenge encountered was dealing with problematic image files. The initial attempt to load images resulted in TensorFlow errors due to unknown image file formats. This required implementing steps to:

- 1.Identify non-image or corrupted files using Pillow.
- 2.Perform a more rigorous TensorFlow-specific validation to find files that TensorFlow could not decode.
- 3.Remove these problematic files from the dataset directory to ensure smooth data loading and model training.

○ How can data augmentation improve your model?
- Data augmentation improves the model by artificially increasing the diversity of the training dataset without collecting new data. This is achieved by applying various random transformations to the existing images (e.g., random flips, rotations, zooms, shifts). Its benefits include:

- Reducing Overfitting: By presenting the model with slightly altered versions of the same image, it learns to be more robust to variations in position, orientation, and scale, making it less likely to memorize the exact training examples.
- Improving Generalization: A more diverse training set helps the model learn more generalizable features, leading to better performance on unseen data.
- Handling Limited Data: It's especially useful when the original dataset is small, as it effectively expands the dataset size.
  
**5. Application**
○ Suggest a real-world application for your trained model.
- Given that the model is trained on different types of plants (e.g., alfalfa, mustard, sisal), a real-world application could be automated agricultural monitoring and plant identification. This system could be used by:

- Farmers: To quickly identify crops, weeds, or specific plant diseases based on visual cues, allowing for targeted interventions and improved crop management.
- Botanists/Ecologists: For biodiversity surveys, identifying plant species in field research, or monitoring invasive species.
- Gardening Apps: As a feature to help users identify plants they encounter.
  
○ How can this system be integrated into a mobile or web application?
- This image classification system can be integrated into mobile or web applications in several ways:

Mobile Application (e.g., Android/iOS):

- Client-side inference (on-device): The trained .keras model can be converted to a mobile-optimized format like TensorFlow Lite (.tflite). The mobile app would then use the device's camera to capture an image, preprocess it, and run the inference directly on the phone. This offers low latency and offline capabilities.
Server-side inference: The mobile app captures an image and uploads it to a backend server. The server, which hosts the full TensorFlow model, performs the prediction and sends the result back to the app. This allows for more powerful models but requires internet connectivity.

Web Application:

- Backend API: A web application (e.g., built with Flask, Django, Node.js) can serve as an API endpoint. Users upload an image via a web form or drag-and-drop interface. The backend receives the image, passes it to the loaded TensorFlow model for prediction, and returns the classification result (e.g., JSON response) to the front-end (HTML/CSS/JavaScript) for display. This is the most common approach for complex models.
- Client-side inference (browser-based): With libraries like TensorFlow.js, the model can be converted to a JavaScript-compatible format and run directly in the user's web browser. This reduces server load and can provide a more interactive experience, but model size and complexity are limitations.
