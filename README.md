# Facial-emotion

This project was performed with human face data provided by Nota(https://nota.ai/)

## Model
Face detection has already been studied by many people.
So I used dilib's human face detection model, which is widely used.
As you can see from the figure below, memory only increases by about __7MB__ when declaring the model.
![dilib_memory](https://user-images.githubusercontent.com/45653968/100175735-4fd1d300-2f12-11eb-964b-6281a863f574.JPG)


mobilenet-v2 was selected as a model for emotion classification.
It is also a model with small memory and pretrained-weight learned with ImageNet in Pytorch is provided,
so I thought it would be possible to satisfy both performance and memory.
As you can see from the figure below, the memory of mobilenet-v2 is only __37MB__.

![mobilenet_memory](https://user-images.githubusercontent.com/45653968/100175715-45173e00-2f12-11eb-9ffa-8c5e8533e267.JPG)


## Dataset
Because human face images are input to mobilenet-v2, the given train dataset cannot be used as it is.
So, human face images were created using the boundingbox coordinates in the xml file and used as training data.
![crop](https://user-images.githubusercontent.com/45653968/100176277-51e86180-2f13-11eb-9818-245807979ef7.JPG)


In order to input various images in training, rotation is applied from -10 to 10 degrees,
and images are resized to 280x280, and then randomly cropped to 256x256.
![train_data](https://user-images.githubusercontent.com/45653968/100174453-d1743180-2f0f-11eb-8971-c834d560df14.JPG)

The table below shows the number of data by data set type.
dataset |number
------|------
train|1300
validation|388
test|184
