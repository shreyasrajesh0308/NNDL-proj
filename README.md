# NNDL-project

Authors : Shreyas, Sid, Paul, Nithin. 

**TASK** : Time series classification, the goal is to look at BCI data and classify the data into 4 possible classes. Each unit of data has 22 sensor data with 1000 time steps for each. 

1. Project Data contains parsed and cleaned data. 
2. Check out the the Data and project python notebook for an overview of the project plan and some basic analysis of provided Data. 
3. Please update the same notebook as and when there are any updates to the project. 
  

| Architecture  | Paper/Article Link | Train Data | Test Data | Model Chars |Data Preprocessing| HyperParams | Test Accuracy | 
| ------------- | ------------- | ------------- | ------------- |------------- |------------- |-------------|------------- |
| CNN  | [Keras Article](https://keras.io/examples/timeseries/timeseries_classification_from_scratch/)  | Subject 1 Data | Subject 1 Data | 4 Layer 1D Conv | No| 32-batch size, 0.5 - dropout rate, 500 - epochs(early stopping) |0.46000000834465027
 CNN  | [Keras Article](https://keras.io/examples/timeseries/timeseries_classification_from_scratch/)  | All Subject Data | Subject 1 Data | 4 Layer 1D Conv |No| 32-batch size, 0.5 - dropout rate, 500 - epochs(early stopping) |0.5600000023841858
  CNN  | [Keras Article](https://keras.io/examples/timeseries/timeseries_classification_from_scratch/)  | All Subject Data | All Subject Data | 4 Layer 1D Conv | No | 32-batch size, 0.5 - dropout rate, 500 - epochs(early stopping) |0.5417607426643372
  CNN  | [Keras Article](https://keras.io/examples/timeseries/timeseries_classification_from_scratch/)  | All Subject Data | All Subject Data | 4 Layer 1D Conv | Yes | 32-batch size, 0.5 - dropout rate, 500 - epochs(early stopping) |0.56207674741745
| LSTM  | [Keras Article](https://towardsdatascience.com/time-series-classification-for-human-activity-recognition-with-lstms-using-tensorflow-2-and-keras-b816431afdff)  | Subject 1 Data | Subject 1 Data | 1 Hidden LSTM layer- 128 neurons| No | |0.2199999988079071
 LSTM  | [Keras Article](https://towardsdatascience.com/time-series-classification-for-human-activity-recognition-with-lstms-using-tensorflow-2-and-keras-b816431afdff)  | All Subject Data | Subject 1 Data | 1 Hidden LSTM layer- 128 neurons| No | |0.2400
  LSTM  | [Keras Article](https://towardsdatascience.com/time-series-classification-for-human-activity-recognition-with-lstms-using-tensorflow-2-and-keras-b816431afdff)  | All Subject Data | All Subject Data  | 1 Hidden LSTM layer- 128 neurons| No | | 0.2415
| LSTM  | [Keras Article](https://towardsdatascience.com/time-series-classification-for-human-activity-recognition-with-lstms-using-tensorflow-2-and-keras-b816431afdff)  | Subject 1 Data | Subject 1 Data | 1 Hidden LSTM layer- 32 neurons| No | |0.2800000011920929
 LSTM  | [Keras Article](https://towardsdatascience.com/time-series-classification-for-human-activity-recognition-with-lstms-using-tensorflow-2-and-keras-b816431afdff)  | All Subject Data | Subject 1 Data | 1 Hidden LSTM layer- 32 neurons| No | |0.22
  LSTM  | [Keras Article](https://towardsdatascience.com/time-series-classification-for-human-activity-recognition-with-lstms-using-tensorflow-2-and-keras-b816431afdff)  | All Subject Data | All Subject Data | 1 Hidden LSTM layer- 32 neurons| No | |0.2686
| GRU  |   | All Data | Subject 1 Data | 64 neurons in GRU layer, 4096x4096 in Dense.| No | 16-batch size, 0.5 - dropout rate, 30 - epochs, HeNorm - init. | 0.345
| GRU  |   | All Data | All Data | 64 neurons in GRU layer, 4096x4096 in Dense.| No | 16-batch size, 0.5 - dropout rate, 30 - epochs, HeNorm - init.| 0.3634311556816101
| Cascade RNN |   | All Data | All Data | As mentioned in Paper| Yes | No tuning yet | 0.6523702144622803
| CNN + GRU |   | All Data | All Data | | Yes | No Tuning yet| 0.749
| CNN + LSTM |   | All Data | All Data | | Yes | No Tuning yet| 0.6727
| Space Conv |   | All Data | All Data | | Yes | No Tuning yet| 0.7697516679763794

**Literature Review**:

*Overview*:
[Deep learning techniques for classification of electroencephalogram (EEG) motor imagery (MI) signals: a review](https://link.springer.com/article/10.1007/s00521-021-06352-5)
Overall Notes - Seems like most of the networks that just use FC nets have some method to perform data preprocessing before feeding into the NN. I don't think this is within the scope of the project, so I think we can skip most of them. Further most of them just use a toolbox in MATLAB for the preprocessing. The only preprocessing technique we should *maybe* look at incorporating is Epoch Extraction.

*Autoencoders*
1. [Multi-Person Brain Activity Recognition via Comprehensive EEG Signal Analysis](https://arxiv.org/abs/1709.09077)
2. [Deep Learning of Multifractal Attributes from Motor Imagery Induced EEG](https://link.springer.com/chapter/10.1007/978-3-319-12637-1_63)


*RNN*
1. [Cascade and Parallel Convolutional Recurrent Neural Networks on EEG-based Intention Recognition for Brain Computer Interface](https://arxiv.org/abs/1708.06578) - Personally think this is the most promising model. Has two different implementations of an LSTM based RNN (Cascade and Parallel config). Also compare output with 1D,2D and 3D conv baselines.

*Deep Belief Networks*
1. [A Deep Learning Method for Classification of EEG Data Based on Motor Imagery](https://link.springer.com/chapter/10.1007/978-3-319-09330-7_25)

*Preprocessing + Fully Connected*
1. [Deep learning for hybrid EEG-fNIRS brain???computer interface: application to motor imagery classification](https://iopscience.iop.org/article/10.1088/1741-2552/aaaf82) - uses NN with 4 hidden layers. Accept eeg as input, along with some other signals. Can potentialy use to discover best activation functions + initial choice of hyperparameters
2. [Automated classification of L/R hand movement EEG signals using advanced feature extraction and machine learning](https://arxiv.org/pdf/1312.2877.pdf): Data preprocessing - MATLAB toolbox for filtering, Automatic Artifact Removal, Epoch Extraction and ICA. Basic comparison between performance of nn vs svm. Can potentialy maybe incorporate Epoch Extraction for preprocessing.
3. [The effects of pre-filtering and individualizing components for electroencephalography neural network classification](https://ieeexplore.ieee.org/document/7925289): data preprocessing - butterworth filter followed by ICA. Uses basic NN architecture.



*Transformers*
1. [BENDR: Using Transformers and a Contrastive Self-Supervised Learning Task to Learn From Massive Amounts of EEG Data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8261053/): pretrains on some massive EEG datasets (MMI, BCIC, ERN, SSC, P300) and then finetunes for tasks (note this paper does not focus on MI). Uses bert inspired architecture (specifically mimics wav2vec2.0 as the paper focuses on speech extraction from EEG), with CTC loss and contrastive learning.
2. [EEG Classification with Transformer-Based Models](https://ieeexplore.ieee.org/abstract/document/9391844) - most relevant transformer model for our use case? Uses a couple of different transformer models (both spatial (across different electrodes) and temporal) as well different positional embeddings and compares performace. However I think it needs a large dataset to be effective, but can definitely run this as one of the models if we have time for some bonus marks for creativity

*GAN*
1. [Combining generative adversarial networks and multi-output CNN for motor imagery classification](https://iopscience.iop.org/article/10.1088/1741-2552/abecc5/meta)
2. [MIEEG-GAN: Generating Artificial Motor Imagery Electroencephalography Signals](https://ieeexplore.ieee.org/abstract/document/9206942)

*Data Augmentation*
1. [Data Augmentation for Motor Imagery Signal Classification Based on a Hybrid Neural Network](https://www.mdpi.com/1424-8220/20/16/4485)
2. [Conditional Adversarial Domain Adaptation Neural Network for Motor Imagery EEG Decoding](https://www.mdpi.com/1099-4300/22/1/96)
3. [Dynamic Joint Domain Adaptation Network for Motor Imagery Classification](https://ieeexplore.ieee.org/abstract/document/9354668)
4. [Priming Cross-Session Motor Imagery Classification with A Universal Deep Domain Adaptation Framework](https://arxiv.org/abs/2202.09559)
5. [Classify Motor Imagery by a Novel CNN with Data Augmentation](https://ieeexplore.ieee.org/abstract/document/9176361)
6. [Data augmentation for deep-learning-based electroencephalography](https://www.sciencedirect.com/science/article/pii/S0165027020303083)
7. [A Novel Deep Learning Approach With Data Augmentation to Classify Motor Imagery Signals](https://ieeexplore.ieee.org/abstract/document/8630915)
8. [Data augmentation for self-paced motor imagery classification with C-LSTM](https://iopscience.iop.org/article/10.1088/1741-2552/ab57c0/meta)



| Architecture  | Train Data | Test Data | Test Accuracy | 
| ------------- | ------------- | ------------- | ------------- |
| CNN  | Subject 1 Data | Subject 1 Data  |0.46000000834465027
| CNN  | All Subject Data | Subject 1 Data | 0.5600000023841858
| CNN  | All Subject Data | All Subject Data |0.5417607426643372
| CNN  | All Subject Data | All Subject Data |0.56207674741745
| LSTM  | Subject 1 Data | Subject 1 Data |0.2199999988079071
| LSTM  | All Subject Data | Subject 1 Data  |0.2400
| LSTM  | All Subject Data | All Subject Data  | 0.2415
| LSTM  | Subject 1 Data | Subject 1 Data |0.2800000011920929
| LSTM  | All Subject Data | Subject 1 Data  |0.22
| LSTM  | All Subject Data | All Subject Data |0.2686
| GRU   | All Subject Data | Subject 1 Data | 0.345
| GRU   | All Subject Data | All Subject Data | 0.3634311556816101
| Cascade RNN | All Subject Data | All Subject Data | 0.6523702144622803
| CNN + GRU   | All Subject Data | All Subject Data | 0.749
| CNN + LSTM  | All Subject Data | All Subject Data | 0.6727
| Space Conv  | All Subject Data | All Subject Data | 0.7697516679763794
