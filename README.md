# Laboratory Work 3 | Custom Image Classifier

# Google Collab

[CLICK HERE TO VIEW THE COLLAB](https://colab.research.google.com/drive/1_OII1G63TI00tIsbKt_eJXzeT9ZPN_Fe?usp=sharing).


## Guide Questions (Student Reflection & Explanation)

1. Dataset Preparation

1.1 How did you organize your dataset in Google Drive?

Following the instructions provided, I assembled a dataset of 20 distinct medicinal plant species, capturing 250 images for each category. I organized these into a main directory titled ImageDataset on Google Drive, with each of the 20 classes stored in its own dedicated subfolder to ensure proper formatting for the model

1.2 Why is folder structure important for TensorFlow image loading?

This structure is essential because TensorFlow leverages the directory hierarchy as an automated labeling mechanism. By categorizing images into named subfolders, the framework dynamically assigns labels to each image, eliminating the need for manual spreadsheets or external metadata. Furthermore, this organized arrangement facilitates efficient batch loading, which accelerates the training process and prevents system memory exhaustion.

2. Model Training

2.1 What is the role of convolutional layers in image classification?

Convolutional layers function as autonomous feature extractors that systematically scan an image to detect specific patterns. The initial layers focus on low-level details, such as edges, gradients, and textures. As the data progresses through deeper layers, the model aggregates these basic shapes to identify more sophisticated structures, such as the specific ribbing of a leaf or the unique contour of a petal. By convolving small filters (kernels) across the pixel grid, these layers maintain the spatial hierarchy of the data, enabling the network to recognize an object’s characteristics regardless of its orientation or position within the frame.

2.2 Why do we split data into training and validation sets?

Splitting the dataset is a critical step to ensure the model develops generalization capabilities rather than simply memorizing the input data. This division is the primary defense against overfitting—a scenario where a model excels at identifying its training photos but fails to categorize new images. By monitoring validation performance, developers can fine-tune hyperparameters and ensure the model will remain accurate when deployed in real-world scenarios.

3. Performance Analysis

3.1 What accuracy did your model achieve?

My model achieved a validation accuracy of 52.1% (0.5210) as shown in the evaluation step and the final training epoch.

3.2 How did the number of images affect the model’s performance?

The number of images acted as the foundation for how well the model could generalize.

4. Critical Thinking

4.1 What challenges did you encounter while using your own dataset?

The main challenge was high overfitting in the initial model. In Part 3, while training accuracy reached nearly 99.7%, the validation accuracy was stuck at 52.1%, and the validation loss was actually increasing (rising to 2.86), indicating the model was just memorizing the training photos.

4.2 How can data augmentation improve your model?

Data augmentation improves your model by artificially creating variety from your existing images, which prevents the network from simply memorizing specific photos. By applying random transformations like rotations, flips, and zooms during training, the model is forced to focus on the actual features of the plants such as leaf shape and texture rather than getting distracted by specific angles or lighting conditions.

5. Application

5.1 Suggest a real-world application for your trained model.

A real-world application for my model is a Mobile Field Guide for Community Health Workers, which allows users to instantly identify medicinal plants using a smartphone camera. In rural areas where access to pharmacies is limited, this tool provides local health volunteers and residents with an accurate way to verify plant species for traditional remedies, such as treating coughs or skin ailments. By confirming the correct plant ID on the spot, the application ensures that traditional medicine is used safely and effectively while preventing the dangerous misuse of toxic "look-alike" species.

5.2 How can this system be integrated into a mobile or web application?

To integrate this system, I would first convert my trained model into TensorFlow Lite for mobile or TensorFlow.js for web use to ensure it runs efficiently on consumer devices. For a mobile app, the model would be embedded directly into the application, allowing health workers to identify plants offline by simply using their phone’s camera. For a web-based approach, I can use a Flask or FastAPIbackend to create an API that receives uploaded images, processes them through the model, and returns the identification results and medicinal instructions to a user- friendly interface built with HTML and JavaScript.

Guide Questions (Student Explanation & Reflection)

Visualization & Overfitting

What signs indicated overfitting in your first model?

The plots in Part 3 show a clear "divergence." The Training Loss dropped close to 0, while the Validation Loss started increasing after epoch 3. Similarly, Training Accuracy hit nearly 100%, but Validation Accuracy plateaued near 50%.

How did data augmentation affect validation accuracy?

Data augmentation helped the validation accuracy align more closely with training accuracy. Although it made the "training phase" harder, it prevented the validation score from crashing or fluctuating, resulting in a more stable and reliable performance on unseen data.
Model Improvement

What is the purpose of dropout layers?

Dropout layers randomly "turn off" a percentage of neurons during training. This prevents the model from becoming overly dependent on specific nodes, forcing the network to find multiple independent paths to recognize a plant, which reduces memorization.
Why does data augmentation improve generalization?

Data augmentation improves generalization by exposing the model to variations (flips, rotations, lighting changes) that it will likely encounter in the real world. By training on these modified images, the model learns the "essence" of the medicinal leaf rather than just one specific photo.
Performance Comparison

Compare accuracy before and after improvements.

Before improvements, the model had a high training accuracy but a failing validation score due to overfitting. After improvements, the training and validation accuracies are synchronized, reaching approximately 61.7%. This represents "honest" accuracy that will hold up in real-world use.

Which technique contributed most to improvement?

Data Augmentation contributed the most. It directly addressed the limited variety in the original 5,000 images by creating infinite variations, which was the key to stopping the validation loss from exploding.
Deployment & Application

Why is saving the model important?

Saving the model (as an .h5 or .keras file) captures the weights and architecture learned during training. This allows you to "export" the model’s brain so it can be used instantly in other applications without having to re-train it for hours.
How can this model be deployed in a real-world system?

This model can be deployed via TensorFlow Lite for a mobile app or a Flask/FastAPI web server. It would allow users to upload photos of plants in the field and receive instant identification and medicinal preparation instructions based on the model's predictions.
