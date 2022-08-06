# BananaNet

 BananaNet is a model re-trained from the ResNet-18 network; its purpose is to identify whether a banana is ripe or unripe. Determining whether food is ripe or unripe is useful on a day-to-day basis (e.g. going grocery shopping) and can also be applied to ensure the consistent quality of food in factories and production lines.
 
![bananas](https://user-images.githubusercontent.com/86124524/183235282-bb5f54c6-5955-4e9c-af7e-698aa57146ed.png)

Image from: https://unsplash.com/@giorgiotrovato

The images I used in my dataset to train the model are all Cavendish bananas (which are the most common banana variety).

## The Algorithm

To create BananaNet, I re-trained the ResNet-18 image classification network using pytorch. For this project, I assembled my own dataset of banana images. This dataset had training, testing, and validation folders along with a labels text file that had a total of two classes: ripe and unripe. The training, testing, and validation folders each contained banana images from both of these classes. To classify images using the re-trained model, I ran the already existing imagenet.py file on the Jetson Nano.

## Running this project

### Materials:
- Jetson Nano 2GB With SD Card Inserted and Headless Setup
- USB to MicroUSB Data Cable
- USBC Power Supply
- Internet Connection on Jetson Nano (via Ethernet Cable or WiFi Dongle)
- Separate Computer, Mouse, and Keyboard With Powershell Installed
- Python3 Installed on Jetson Nano and Powershell
- ResNet-18 Network Installed on Jetson Nano

### Preparation:
1. Download the imagenet.py file (if not already on your Jetson Nano), BananaNet.tar.gz, and resnet18.onnx file from this repository.
2. scp the BananaNet.tar.gz from your host computer over to your Jetson Nano by typing in the following command template into PowerShell, and enter your Nano’s password when prompted:

scp path/to/local/file.ext user@remote-host:path/to/remote/file.ext

Your command and results will look similar to this:
![demo3](https://user-images.githubusercontent.com/86124524/183235531-26ccddd9-9d7f-46e5-91ec-5f0e30d5abe2.jpg)

3. Repeat this scp process with the imagenet.py file and resnet18.onnx file.

3. Afterwards, ssh into your Jetson Nano from PowerShell on your host device using the command ssh nvidia@<remote-host> (replace <remote-host> with the IP address of the Jetson Nano, which is usually 192.168.55.1; however, my IP address is different, which is why you will see a different address in some of my demonstration images, including the one below):

![demo4](https://user-images.githubusercontent.com/86124524/183235612-975a9f50-358e-48ff-b913-9fdc994edadc.jpg)

4. Change directories so that you are in jetson-inference/python/training/classification/data, then unzip your folder by entering the following command into your nano:

tar xvzf name-of-archive.tar.gz

![demo5](https://user-images.githubusercontent.com/86124524/183235652-02ccb76b-ad8d-4c3f-a5c2-b784f6c02eb2.jpg)

5. Type ls to make sure that your unzipped archive is under jetson-inference/python/training/classification/data. You will be classifying the test images using the model in the following steps.

### Classifying Images With BananaNet:
1. On your nano, make sure you are in jetson-inference/python/training/classification.
2. Use ls models/BananaNet/ to ensure that the model is on the nano; you should see a file called resnet18.onnx.

[View a video explanation here](video link)
