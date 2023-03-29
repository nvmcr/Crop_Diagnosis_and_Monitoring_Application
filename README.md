# Crop_Diagnosis_and_Monitoring_Application
## Table of Contents
1. [Outcome](#outcome)
2. [Motivation](#motivation)
3. [Methodology](#methodology)
  1. [Crop Diagnosis](#crop-diagnosis)
      1. [Data Acquisition](#data-acquisition)
      2. [Data Preparation](#data-preparation)
      3. [Diagnosis](#diagnosis)
      4. [Results](#results)
        1. [Results with Default Conditions](#Results-with-Default-Conditions)
## Outcome
This project outcomes includes a single mobile application with crop disease detection, crop monitoring and farming recommendations.
* Farmer can take a picture of unhealthy leaf and app would detect the disease of the leaf.
* The application acts as a dashboard for the sensors deployed in the field and farmer can control actuators like water pump, sound sensor and LEDs from the application.
* Based on the data received from the sensors and the detected disease, the app will suggest what should be done next.
## Motivation
During my volunteer work at the Centre for Social Action, a socio-economic organization in CHRIST University, I had the opportunity to attend a camp in Kolar, a village situated near the border of Andhra Pradesh and Karnataka in India. During my three-day stay, I interacted with the villagers, who were all farmers, and discovered that there were several issues that required attention, but most of them were beyond my capacity to solve. Despite the camp being unrelated to academics, I identified a problem that I believed I could address. I observed that the majority of the villagers had limited knowledge about which fertilizers to use for their crops. Typically, they used 2-3 brands of fertilizers for each type of disease and applied the same chemical ratios to their crops, even when confronted with various diseases. This realization became the impetus for this project.
## Note
I lost most of my codes in my university drive. But the below resources contain most of the information about my work.
1. [My Undergrad Thesis](https://github.com/nvmcr/Crop_Diagnosis_and_Monitoring_Application/blob/main/ProjectReport_compressed.pdf) (Its more than 100 pages and includes code snippets, all hardware schematic diagrams and concepts involved.)
2. N. V. Megha Chandra Reddy, K. A. Reddy, G. Sushanth and S. Sujatha, "A versatile approach based on convolutional neural networks for early identification of diseases in tomato plants," International Journal of Wavelets, Multiresolution and Information Processing (IJWMIP), pp. 2150043, 2021, doi: 10.1142/S0219691321500430. [Link](https://doi.org/10.1142/S0219691321500430)
3. N. V. Megha Chandra Reddy, K. A. Reddy, Sushanth. G and Sujatha. S, "Plant Disease Diagnosis and Solution System Based on Neural Networks," Indian Journal of Computer Science and Engineering (IJCSE), vol. 12, no. 4, pp. 1084-1092, 2021, doi: 10.21817/indjcse/2021/v12i4/211204218. [Link]( https://doi.org/10.21817/indjcse/2021/v12i4/211204226)

## Methodology
The main aim of this project is to create an end-to-end system for the farmers providing
every technological solution to the problems they face. This project aims to achieve the
monitoring of the crop using IoT. The significant factors affecting crop productivity such
as humidity, temperature, the moisture content in the soil, rain, and animal intrusion
should be monitored. Actuators should be used based on the processing of the sensor’s
data. In case of any disease attack, disease detection should be done effectively and
efficiently. All these tasks should be available in a single mobile application for the
farmer. The entire project can be divided into four sub-categories of diagnosis, monitoring, recommendation and mobile application.
### Crop Diagnosis
The detailed flow diagram of the proposed system is shown in below figure. The flow chart
can be broadly classified into 3 parts namely Data Acquisition, Data processing and
Classification. 
![Flowchart](images/flowchart.png)
#### Data Acquisition
Images of diseased leaves were taken from an open access repository of images called PlantVillage. The dataset includes over 87000 images of 14 crops, such as tomatoes, apples,
blueberry, grapes, raspberry, potatoes, strawberry, soybeans and squash. Tomato
was selected as the target crop from the above mentioned 14 crops. Training and validation sets are generated from the total dataset in the ratio of 80:20 respectively. Around 50 images in every category from the training set are randomly picked and are withdrawn from training folders for
testing purpose. The size of all the images is 256 x 256 and the format employed
is jpeg.

#### Data Preparation
For Convoluted Neural Network (CNN) classifier, dataset images should be preprocessed to gain stability for improved feature extraction. The noise in the images of
the dataset used is minimal, so noise removal was not used in this data preprocessing. For CNN classifiers used, the image size requirement is 224 x 224 pixels. So, the
images were resized to the required pixels. Data standardization is performed by
splitting all pixel values. It is also ensured that the several default values involved
in initialization and termination are as per requirement.

Typical deep convolutional neural networks contain millions of parameters; therefore, stupendous amounts of data are required. Otherwise, the deep neural network
may not be robust or it overfits. The main purpose of using augmentation is to
populate the dataset and introduce slight distortion to the images which help in
reducing overfitting while training the model. The data augmentation process was
conducted to the training database which includes rescaling, setting both sheer and
zoom range to 0.2 and doing a horizontal flip. Whereas only rescaling was done
for the testing set.
#### Diagnosis
Generally, convolutional neural networks (CNN) are used for creating a machine learning model that works on the unlabeled image inputs and converts them to corresponding
classification output labels. But, to train such neural networks, a lot of data is needed
which is not feasible. But with transfer learning, a solid machine learning model can
be built with comparatively minimal training data because the model is already pretrained but on different data. For leaf disease detection, from popular
architectures like VGG, ResNet, Inception, MobileNet and DenseNet, one model per
architecture is analyzed.The models used are VGG19, ResNet152V2, InceptionV3, InceptionResNet152V2, Xception, MobileNetV2 and DenseNet201. The architecture of
the proposed model for a single crop shown below consists of a pre-trained model followed by a reshape layer, a flatten layer, a dense layer, and finally followed by a Softmax activation
function to do classification. 
![Architecture](images/architecture.png)
#### Results
##### Results with Default Conditions
For all models, a batch size of 32 has been used and the model has been trained for 30
epochs. The number of steps per epoch was equal to the length of the training set and
the number of validation steps was equal to the length of the test set. Model accuracy, loss,
precision, recall and AUC are plotted to evaluate the performance of each model. From Table, it can be inferred that DenseNet201 performed with the highest accuracy of 98.43% and loss of 0.3873 followed closely by
ResNet152V2 and MobileNetV2 with 97.86% and 97.31% accuracies respectively.
But DenseNet201 and ResNet152V2 took a large training time too. VGG19 trained
exceptionally well with a loss of 0.1524 but can only attain an accuracy of 95.63%.
![Accuracy](images/defacc.png)
![Loss](images/defloss.png)
![AUC](images/defaoc.png)
![Table](images/deftable.png)
