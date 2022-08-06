# BananaNet

 BananaNet is a model re-trained from the ResNet-18 network; its purpose is to identify whether a banana is ripe or unripe. Determining whether food is ripe or unripe is useful on a day-to-day basis (e.g. going grocery shopping) and can also be applied to ensure the consistent quality of food in factories and production lines.

![The images I used in my dataset to train the model are all Cavendish bananas (which are the most common banana variety).](https://imgur.com/Sm5NS15)

## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here.
To create BananaNet, I re-trained the ResNet-18 image classification network using pytorch. For this project, I assembled my own dataset of banana images. This dataset had training, testing, and validation folders along with a labels text file that had a total of two classes: ripe and unripe. The training, testing, and validation folders each contained banana images from both of these classes. To run the re-trained model, I used the already existing imagenet.py file on the Jetson Nano.

## Running this project

Materials:
- Jetson Nano 2GB with SD Card Inserted and Headless Setup
- USB to MicroUSB Data Cable
- USBC Power Supply
- Internet Connection on Jetson Nano (via Ethernet Cable or WiFi Dongle)
- Separate Computer, Mouse, and Keyboard With Powershell Installed
- Python3 Installed on Jetson Nano and Powershell
- ResNet-18 Network Installed on Jetson Nano

1. scp the tar directory from your host device to your Jetson Nano by typing in the following command into PowerShell, and enter your Nano’s password when prompted:

1. On your nano, make sure you are in jetson-inference/python/training/classification.
2. Use ls models/BananaNet/ to ensure that the model is on the nano; you should see a file called resnet18.onnx.

[View a video explanation here](video link)
