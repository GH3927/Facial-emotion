# Facial-emotion

This project is performed with human face data provided by Nota(https://nota.ai/)

## Model
Face detection has already been studied by many people.
So I used dilib's face detection model, which is widely used.
As you can see from the figure below, memory only increases by about 37MB when declaring the model.

![dilib_memory](https://user-images.githubusercontent.com/45653968/100174837-98888c80-2f10-11eb-9769-64b4f869fbe9.JPG)

## Train dataset
In order to input various train data, rotation is applied from -10 to 10 degrees,
and images is resized to 280x280, and then randomly cropped to 256x256.
![train_data](https://user-images.githubusercontent.com/45653968/100174453-d1743180-2f0f-11eb-8971-c834d560df14.JPG)
