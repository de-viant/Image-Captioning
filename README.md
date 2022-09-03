# Image-Captioning using python
Using Inception V3 and LSTM

# **Problem Statement**
The process of creating a written description of an image is known as image captioning. [picture → caption] is the format of the dataset. The dataset is made up of input photographs and the captions corresponding to them.
## **How does it work?**
### **CNN (Encoder)**
A Convolutional Neural Network (ConvNet/CNN) is a Deep Learning system that can take an input image, assign relevance (learnable weights and biases) to various aspects/objects in the image, and distinguish between them. The CNN (Convolutional Neural Network) is a type of encoder. CNN is given the input image and is tasked with extracting the features. The CNN's final hidden state is linked to the Decoder.
### **LSTM(Decoder)**
Recurrent neural networks RNNs have an issue with long-term dependency (due to the vanishing gradient problem), and LSTM networks were created to solve that problem. Unlike more standard feedforward neural networks, LSTMs feature feedback connections. This trait allows LSTMs to process complete data sequences (e.g. time series) without having to handle each point in the sequence separately, instead of preserving important knowledge about prior data in the sequence to aid in processing incoming data points.

As a result, LSTMs excel at processing data sequences like text, speech, and time series in general.

The Decoder is a Recurrent Neural Network (generally LSTM ) that does language modeling up to the word level. The first time step receives the encoded output from the encoder and also the <START> vector.
## **Model Architecture**

  ![Aspose Words 3de110da-8574-42c4-aee7-55d4a4347f59 004](https://user-images.githubusercontent.com/54477816/146561120-9b896d3e-3cb4-41df-a823-e294ed75b71b.png)

 ![Aspose Words 3de110da-8574-42c4-aee7-55d4a4347f59 005](https://user-images.githubusercontent.com/54477816/146561124-be92c286-1076-4b0c-945b-ec1b0ba81679.png)

In our model, we have implemented a CNN model which is Inception V3.
In our case, whose last softmax function has been removed.
We then take the feature vector at the fully connected layer (1\*1\*2048) and pass it through a linear layer which maps the size of the input to the LSTM input.

For the encoder part, the pretrained CNN extracts the feature vector from a given input image. The feature vector is linearly remodeled to have the same dimension as the input dimension of the LSTM network. For the decoder part, supply and target texts are predefined. For example, if the image description is "Giraffes standing next to every other", the source sequence may be a list containing ['<start>', 'Giraffes', 'standing, 'next', 'to', 'each', 'other'] and also the target sequence is a list containing ['Giraffes', 'standing, 'next', 'to', 'each', 'other', '<end>']. victimization of these source and target sequences and the feature vector, the LSTM decoder is trained as a language model conditioned on the feature vector.

## **Dataset:** 
Pre-processing and cleaning data is an important part of building a model. When we understand the data, we can build more accurate models.

We used the **Flickr8k dataset.** It is a freely available dataset for image captioning dataset containing 5 labels (Captions) for each image.
  
https://www.kaggle.com/dataset/e1cd22253a9b23b073794872bf565648ddbe4f17e7fa9e74766ad3707141adeb
  
The details about the dataset are:

- There are 8092 images in this Flickr8k\_Dataset, all in JPEG format with different shapes and sizes. They are divided between training, testing, and development.
- The flickr8k\_text folder contains the text files describing the train\_set and the test\_set. There are 5 captions for each image in Flickr8k.token.txt, totaling 40460 captions.
## **Training:**
The model has been trained to only around 80 epochs, with intermittent allowing backpropagation through LSTM  and CNN+LSTM. 
## **Metric used for evaluation:**
### **BLEU Score**
The Bilingual Evaluation Understudy Score, or BLEU for short, is a measurement for assessing a produced sentence to a reference sentence. 
An ideal match brings about a score of 1.0, while an ideal befuddle brings about a score of 0.0.
  
## **Implement**
  -> Clone this repository\
  -> Download the flickr8 dataset and place as follows\
  **flickr8k\
          |__images\
          |__captions**
  
  
  Run train.py to start training.
  
  Examine/change model.py to affect network model.

## **To Do**
  Add Attention mechanism in the code.
  Include BLEU Score as a metric while trainining so we monitor BLEU Score with epochs.
  Train for more Epochs
  
 
  
 

