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
1. On your Powershell, ssh into your nano. From the home directory, go into the jetson-inference/python/training/classification/models directory by typing `cd jetson-inference/python/training/classification/models`, as shown below.

![demo](https://user-images.githubusercontent.com/86124524/183264206-6cb8524f-2675-42e1-841f-217df62de619.png)

2. To clone this repository, type in your nano: `git clone https://github.com/Audrey-Huynh/BananaNetProject.git`

3. Type `ls`. You will see that you now have a directory called BananaNetProject (circled in red below)

![demo2](https://user-images.githubusercontent.com/86124524/183264268-a53cb95e-3e6d-496d-87eb-e811102b707a.png)

Your results from the previous two steps will look similar to this image.

4. Change directories so that you are in the BananaNetProject directory by typing `cd BananaNetProject`, and type `ls` to view the contents. The files you should see listed are BananaNet.tar.gz, imagenet.py, readme.md, and resnet18.onnx.
5. Type `cd ..`, `cd ..` again, and `cd data` to go into the data directory

![demo3](https://user-images.githubusercontent.com/86124524/183264319-1cf37c42-f452-48f8-9db7-a40464749de9.png)

6. Type `cp -rf ~/jetson-inference/python/training/classification/models/BananaNetProject/BananaNet.tar.gz .`
7. Type `ls`. In your folder, you should now have a file called BananaNet.tar.gz. Next, unzip this folder by entering the following command into your nano: `tar xvzf BananaNet.tar.gz`
8. Type `ls`. You should now have an additional folder called BananaNet (shown below).

![demo4](https://user-images.githubusercontent.com/86124524/183264395-36f3999c-68bf-49ee-b932-4d6ae8564c38.png)

This BananaNet folder contains a dataset of banana images. You will be classifying the test images from this folder in the following steps.

### Classifying Images With BananaNet:
1. On your nano, cd into the jetson-inference directory by typing `cd` and then `cd jetson-inference`.
2. Type `./docker/run.sh`, and enter your Jetson Nano password when prompted
3. From the jetson-inference folder, type `cd python/training/classification`
4. Use `ls models/BananaNetProject` to ensure that the model is on the nano; you should see a file called resnet18.onnx.
5. Set the NET and DATASET variables:
`NET=models/BananaNetProject`
`DATASET=data/BananaNet`

![demo5](https://user-images.githubusercontent.com/86124524/183264563-ae895c16-b386-455a-bce6-087e2adf1f11.png)

6. Run this command to see how the model operates on an image from the unripe folder.
`imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/unripe/1.jpg data/unripe_banana.jpg`
7. When done, open Powershell in a new window and use scp to look at the image on your host computer, and enter your Jetson Nano password when prompted (replace <nanousername> with your Jetson Nano username, and replace <hostusername> with your host computer username):
Windows: `scp <nanousername>@192.168.55.1:/home/<nanousername>/jetson-inference/python/training/classification/data/unripe_banana.jpg “C:\Users\<hostusername>\Desktop”`
Note: “C:\Users\<hostusername>\Desktop” could possibly be “C:\Users\<hostusername>\OneDrive\Desktop”; this depends on where your Desktop folder is located within your local drive on your host computer.

![demo8](https://user-images.githubusercontent.com/86124524/183265459-317307f3-691b-4708-a5ef-74948065112a.png)

8. Navigate to your desktop folder and click open the unripe_banana.jpg. Your result will look similar to this:

![demo9](https://user-images.githubusercontent.com/86124524/183265485-73a15718-54c9-4885-9019-1c4819bd1308.png)

[View a video explanation here](video link)
