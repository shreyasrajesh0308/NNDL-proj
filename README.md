# NNDL-project

Authors : Shreyas, Sid, Paul, Nithin. 

**TASK** : Time series classification, the goal is to look at BCI data and classify the data into 4 possible classes. Each unit of data has 22 sensor data with 1000 time steps for each. 

1. Project Data contains parsed and cleaned data. 
2. Check out the the Data and project python notebook for an overview of the project plan and some basic analysis of provided Data. 
3. Please update the same notebook as and when there are any updates to the project. 


The following experiments are underway:

1. (Baseline) CNN model: Model as in [paper](https://arxiv.org/abs/1611.06455). A keras implementation can be found [here](https://keras.io/examples/timeseries/timeseries_classification_from_scratch/). **Test Accuracy: 0.46000000834465027**



**Literature Review**:

*Autoencoders*
1. [Multi-Person Brain Activity Recognition via Comprehensive EEG Signal Analysis](https://arxiv.org/abs/1709.09077)
2. [Deep Learning of Multifractal Attributes from Motor Imagery Induced EEG](https://link.springer.com/chapter/10.1007/978-3-319-12637-1_63)


*RNN*
1. [Cascade and Parallel Convolutional Recurrent Neural Networks on EEG-based Intention Recognition for Brain Computer Interface](https://arxiv.org/abs/1708.06578) - Personally think this is the most promising model. Has two different implementations of an LSTM based RNN (Cascade and Parallel config). Also compare output with 1D,2D and 3D conv baselines.

*Deep Belief Networks*
1. [A Deep Learning Method for Classification of EEG Data Based on Motor Imagery](https://link.springer.com/chapter/10.1007/978-3-319-09330-7_25)

*Preprocessing + Fully Connected*
1. [Deep learning for hybrid EEG-fNIRS brain–computer interface: application to motor imagery classification](https://iopscience.iop.org/article/10.1088/1741-2552/aaaf82) - uses NN with 4 hidden layers. Accept eeg as input, along with some other signals. Can potentialy use to discover best activation functions + initial choice of hyperparameters
2. [Automated classification of L/R hand movement EEG signals using advanced feature extraction and machine learning](https://arxiv.org/pdf/1312.2877.pdf): Data preprocessing - MATLAB toolbox for filtering, Automatic Artifact Removal, Epoch Extraction and ICA. Basic comparison between performance of nn vs svm. Can potentialy maybe incorporate Epoch Extraction for preprocessing.
3. [The effects of pre-filtering and individualizing components for electroencephalography neural network classification](https://ieeexplore.ieee.org/document/7925289): data preprocessing - butterworth filter followed by ICA. Uses basic NN architecture.



*Transformers*
1. [BENDR: Using Transformers and a Contrastive Self-Supervised Learning Task to Learn From Massive Amounts of EEG Data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8261053/): pretrains of some massive EEG datasets (MMI, BCIC, ERN, SSC, P300) and then fintunes for tasks (not this paper does not focus on MI). Uses bert inspired architecture (specifically mimics wav2vec2.0 as the paper focuses on speech extraction from EEG), with CTC loss and contrastive learning.

