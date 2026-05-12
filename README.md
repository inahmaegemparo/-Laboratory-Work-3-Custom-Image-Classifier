# Laboratory Work 3 | Custom Image Classifier

# Google Collab

[CLICK HERE TO VIEW THE COLLAB](https://colab.research.google.com/drive/1_OII1G63TI00tIsbKt_eJXzeT9ZPN_Fe?usp=sharing).


## Guide Questions (Student Reflection & Explanation)

1. Dataset Preparation

1.1 How did you organize your dataset in Google Drive?

I collected 20 different medicinal plant with 250 pictures each category as per instructed. I then upload it in the google drive using the format provided. The folder named as IMAGEDATASET, and inside that folder is also the folders of 20 categories with their corresponding images inside.
1.2 Why is folder structure important for TensorFlow image loading?

It is important because TensorFlow uses the folder structure as an automatic labeling system. By placing images into named subfolders, the software instantly knows which category each image belongs to without needing a separate list or spreadsheet. This organized layout also allows the computer to load images in small, manageable batches, making the training process faster and preventing your memory from overloading.
2. Model Training

2.1 What is the role of convolutional layers in image classification?

Convolutional layers act as automated feature detectors that scan an image to identify patterns. In the beginning layers, they find simple edges and textures; as the data moves deeper, these layers combine those simple shapes to recognize complex features like eyes, wheels, or leaves. By sliding small filters across the pixels, they preserve the spatial relationship between parts of the image, allowing the model to understand what an object looks like regardless of where it appears in the frame.
2.2 Why do we split data into training and validation sets?

Spliting data is ensuring the model to actually learns instead of just memorizing. The training set is like a practice exam where the model sees the answers and learns the patterns, while the validation set acts as a mock test with data it hasn't seen before. This separation allows to catch overfitting, which happens when a model performs perfectly on its practice work but fails in the real world. By checking performance on the validation set, it can tune the model's settings and confidently predict how it will handle entirely new images once it's deployed.
3. Performance Analysis

3.1 What accuracy did your model achieve?

My model achieved a validation accuracy of approximately 61.7% (0.6169999837875366). This means the model correctly identified the images in the validation set about 62% of the time.
3.2 How did the number of images affect the model’s performance?

The number of images acted as the foundation for how well the model could generalize.
4. Critical Thinking

4.1 What challenges did you encounter while using your own dataset?

It's the testing part, some plants won't accurately or 99 percentage detect its name upon testing.
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

The primary indicator was the large gap between training and validation accuracy. While training accuracy climbed toward 100%, the validation accuracy plateaued much lower. Additionally, the Validation Loss began to rise sharply after a few epochs, showing the model was memorizing specific pixels rather than learning general features.
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
