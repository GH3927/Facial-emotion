# Facial-emotion

This project was performed with human face data provided by Nota(https://nota.ai/)

## Architecture
Facial emotion classification algorithm consists of 2 stages. First, when an image is input, the face detector finds the area of the human face.  
Then, the found human face area is resized to the desired size and input to the emotion classifier. Finally, the emotion classifier predicts emotion.  
<img src="https://user-images.githubusercontent.com/45653968/100177618-c2907d80-2f15-11eb-8bf6-3b5b616e402a.JPG" width="800" height="400">

## Deep learning odel
Face detection has already been studied by many people. So I used dilib's human face detection model, which is widely used.  
As you can see from the figure below, memory only increases by about __7MB__ when declaring the model.  
![dilib_memory](https://user-images.githubusercontent.com/45653968/100175735-4fd1d300-2f12-11eb-964b-6281a863f574.JPG)


mobilenet-v2 was selected as a model for emotion classification. It is also a model with small memory and pretrained-weight learned with ImageNet in Pytorch is provided,
so I thought it would be possible to satisfy both performance and memory. As you can see from the figure below, the memory of mobilenet-v2 is only __37MB__.  
Mobilenet-v3 has a fully connected layer of 1000 at the end, but changed it to 5. This is because there are five types of emotion: neutral, anger, surprise, smile, and sad.

![mobilenet_memory](https://user-images.githubusercontent.com/45653968/100175715-45173e00-2f12-11eb-9ffa-8c5e8533e267.JPG)


## Dataset
Because human face images are input to mobilenet-v2, the given train dataset cannot be used as it is.  
So, human face images were created using the boundingbox coordinates in the xml file and used as training data.  
<img src="https://user-images.githubusercontent.com/45653968/100176277-51e86180-2f13-11eb-9818-245807979ef7.JPG" width="550" height="200">

In order to input various images in training, rotation is applied from -10 to 10 degrees, and images are resized to 280x280, and then randomly cropped to 256x256.  
![train_data](https://user-images.githubusercontent.com/45653968/100174453-d1743180-2f0f-11eb-8971-c834d560df14.JPG)  
The table below shows the number of data by data set type.
dataset |number
------|------
train|1300
validation|388
test|184


## Loss function
The emotion string type value obtained from the .xml file was changed from 0 to 4 int type.
The output of the deep learning model was input to softmax, and cross entropy loss is used as the loss function.
<img src="https://user-images.githubusercontent.com/45653968/100178746-eb197700-2f17-11eb-8c81-1ef983118f46.JPG" width="500" height="400"
