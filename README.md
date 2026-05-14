# Custom Image Classifier
Google Colab Link Here: https://colab.research.google.com/drive/1nbuTrgRi6nqxlNpMEQGIBr5e9K2V8FwV?usp=sharing


# Guide Questions (Student Reflection & Explanation)


# **1. Dataset Preparation**

○ How did you organize your dataset in Google Drive?
- The dataset was organized in Google Drive using a main folder named “ImageDataset”, where each crop category had its own subfolder containing corresponding images. This folder structure allowed TensorFlow to automatically identify and classify images into their respective classes.

○ Why is folder structure important for TensorFlow image loading?
- Folder structure is important because TensorFlow uses subfolder names as class labels when loading images through image_dataset_from_directory(). Proper organization ensures that images are correctly categorized and loaded without errors.

# **2. Model Training**

○ What is the role of convolutional layers in image classification?
- Convolutional layers are responsible for extracting important image features such as edges, shapes, textures, and patterns. These layers help the model recognize visual characteristics that are useful for classifying images into different categories.

○ Why do we split data into training and validation sets?
- The dataset is split into training and validation sets to evaluate how well the model performs on unseen data. The training set helps the model learn patterns, while the validation set measures its generalization ability and helps detect overfitting.

# **3. Performance Analysis**

○ What accuracy did your model achieve?
- The model achieved a validation accuracy of 99.34%, showing excellent performance in classifying the crop image dataset.

○ How did the number of images affect the model’s performance?
- The large number of images (7,552 images across 20 classes) helped improve the model’s performance by providing enough data for learning different patterns and reducing classification errors.

# **4. Critical Thinking**

○ What challenges did you encounter while using your own dataset?
_ One challenge encountered was handling image format and dataset validation issues, including checking for corrupted or unsupported image files. Proper image organization was also important to avoid loading errors during training.

○ How can data augmentation improve your model?
- Data augmentation can improve the model by creating more diverse training examples through techniques such as rotation, flipping, zooming, and shifting. This helps reduce overfitting and improves the model’s ability to generalize to new images.

# **5. Application**

○ Suggest a real-world application for your trained model.
- The trained model can be applied in smart agriculture, where farmers can automatically identify crop species and monitor agricultural plants more efficiently.

○ How can this system be integrated into a mobile or web application?
- The system can be integrated into a mobile or web application by allowing users to upload or capture crop images, which are then processed by the trained AI model to provide instant classification results and recommendations.


# **Visualization & Overfitting**

# **1. What signs indicated overfitting in your first model?**
- Overfitting was indicated by the gap between training accuracy and validation accuracy. The first model performed very well on training data, but validation performance was lower, suggesting that the model memorized training patterns instead of generalizing well to unseen data.

# **2. How did data augmentation affect validation accuracy?**
- Data augmentation helped improve validation performance by increasing the diversity of training images through transformations such as flipping, rotation, and zooming. This reduced overfitting and helped the model generalize better to unseen data.

# **Model Improvement**

# **3. What is the purpose of dropout layers?**
-Dropout layers help prevent overfitting by randomly disabling neurons during training. This forces the model to learn more generalized features instead of depending too heavily on specific neurons.

# **4. Why does data augmentation improve generalization?**
- Data augmentation improves generalization because it exposes the model to more variations of images, helping it recognize patterns better and perform well on new or unseen data.

# **Performance Comparison**

# **5. Compare accuracy before and after improvements.**
- Before improvements, the model achieved high training accuracy but showed signs of overfitting. After applying techniques such as data augmentation and dropout, validation performance became more stable and the model generalized better on unseen data.

# **6. Which technique contributed most to improvement?**
- Data augmentation contributed the most to improvement because it increased dataset diversity and reduced overfitting, helping the model learn more robust image features.

# **Deployment & Application**

# **7. Why is saving the model important?**
- Saving the model is important because it allows the trained model to be reused without retraining. This saves time and enables deployment in real-world applications.

# **8. How can this model be deployed in a real-world system?**
- The model can be deployed in a mobile or web-based system where users upload images, and the trained AI model automatically classifies them. This can be useful in applications such as smart agriculture, crop monitoring, and plant identification.
