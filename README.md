# FUNGUSAFE : Forage without Fear
 
FUNGUSAFE is an image classification program with the purpose of determining whether a fungus is poisonous or safe based on an image of its sporocarp, or main fruiting body.*
It identifies fungi into one of four labels: edible mushroom sporocarp, edible sporocarp, poisonous mushroom sporocarp, and poisonous sporocarp. 
Though this model is NOT recommended for actual use in foraging, a more refined version of it could eventually be able to aid new foragers and make foraging more widespread. This in turn reduces carbon emissions and costs of buying produce, lending our planet a hand in these trying times.


###### A sample run of FUNGUSAFE with the poisonous fly agaric mushroom (Amanita muscaria)
<a href="https://imgbb.com/"><img src="https://i.ibb.co/6Z5Pr2W/Screenshot-2023-07-07-205714.png" alt="Screenshot-2023-07-07-205714" border="0"></a>

## The Algorithm

FUNGUSAFE is a retrained model of ImageNet image classification using resnet-18. The dataset contains over 3,000 images of fungi and was sourced from Kaggle, titled 'edible and poisonous fungi' created by Marcos Volpato. The link to the dataset is here: https://www.kaggle.com/datasets/marcosvolpato/edible-and-poisonous-fungi. This dataset was split into test, train and var folders, test and var holding around 100 images per category, while train had around 800 per category, along with a labels.txt document listing all the categories.

FUNGUSAFE was trained for 30 epochs, which despite the lengthy training time, still only had a training accuracy of around 40% (thus it is recommended that FUNGUSAFE not be used in the wild)

## Running this project

1. Open SSH
   
2. Download both fungusdata and fungusmodel into your nano. Ensure that both the resnet-18 network and jetson-inference library are accessible on your nano.
   
3. Move fungusdata into the /jetson-inference/python/training/classification/data directory, and unzip using the unzip command on the terminal
   
4. Move fungusmodel into the /jetson-inference/python/training/classification/models directory

5. Finding the image that you want to identify, import it anywhere into the nano and copy the file path
   
6. Opening into /jetson-inference/python/training/classification on the terminal, enter these two lines of code:
``` bash
NET=models/fungusmodel
DATASET=data/fungusdata
```
   
7. Using the file path in your clipboard, classify the image:
``` bash
imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt <pasted file path> <output>.jpg
```
The image should appear in the classification folder.

[View a video explanation here](video link)

#### *THE TRAINING OF THIS MODEL WAS NOT ABLE TO MAKE IT RELIABLE AND THUSLY IT IS VERY EXPERIMENTAL, PLEASE DO EXTERNAL RESEARCH IF YOU PLAN ON ACTUALLY EATING FUNGI IN THE WILD
