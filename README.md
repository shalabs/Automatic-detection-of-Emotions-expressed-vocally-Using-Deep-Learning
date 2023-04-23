Emotion plays a significant role in the way humans understand the true meaning of human-spoken languages. The emotion implicitly expressed by a speaker can change the entire underlying meaning of a sentence. Thus, many studies have investigated methods to identify the speaker’s emotions of spoken languages automatically. This task is very challenging, even for humans, and requires some expertise due to the subtle differences between some emotions (e.g., surprise and anger). Automatic Speech Emotion Recognition (SER) is an application of Artificial Intelligence, where Machine Learning models are used to predict the emotion expressed by speakers (Kerkeni et al., 2019). In this work, we use a hierarchical classification approach to see if it can improve the performance of the classical 1-level classifiers in predicting emotions expressed in speech.


Methodology


Deep learning, more specifically Convolutional Neural Networks (CNNs), have shown promising results for SER. It is considered more suited over traditional techniques because of their advantages like scalability, all-purpose parameter fitting, and infinitely flexible function (Wani et al., 2021).
Inspired by object recognition and sentiment analysis of text, where many models rely on using a hierarchical deep learning framework, which is built where the easy task of classification is performed at the top level, and more challenging tasks are solved at the end level. I use the same approach in classifying the emotion expressed in audio samples.


1- Dataset:
Audio recordings from RAVIDESS dataset (SR et al., 2018), which contains 24 professional actors (12 female, 12 male), vocalizing two lexically-matched statements in a neutral North American accent. Speech emotions include calm, happy, sad, angry, fearful, surprise, and disgust expressions. Each expression is produced at two levels of emotional intensity (normal, strong), with an additional neutral expression, totaling around 3000 samples.
2- Feature Extraction:
Features are extracted from the audio recordings using MFCC, where audio is represented as a 2-dimensional matrix. MFCC can be defined as the short-term power spectrum of a voice signal measured as the linear cosine transformation of the log power spectrum on a non-linear Mel frequency scale. This Mel scale approximates the human auditory system's response more closely than the linearly-spaced frequency bands used in case of cepstrum (Sha et al., 1997).

3- Classification

 <img width="1166" alt="image" src="https://user-images.githubusercontent.com/80707214/233836667-0c7ba7d2-ea7d-47f8-b658-d25c15e1d64e.png">

A- Baseline model.
With the baseline models. The audio samples are divided into 14 classes, each class represents one of the 7 emotions with the gender of the speaker (e.g., angry-female, angry-male). The gender of the speaker was considered as the pitch of the male and female voice differ significantly and contribute to the model accuracy. The three baseline models are used: CNN , RNN and SVM.
CNN and RNN both are classes of Artificial Neural Networks and consist of an input, hidden and output layers. Long Short-Term Memory (LSTM) is a special kind of RNN interested in time and has short memory. SVM constructs hyperplanes in a high/infinite dimensional space. Experimenting with these models will help us figure out if hierarchical classification can improve model performance.
B- The hierarchical classification approach
To achieve hierarchical classification, multiple CNNs are staked in a hierarchical manner to recognize the emotion expressed in each audio sample. In the first hierarchical model (Figure 1), the first classifier is used to identify the gender of the speaker. For the next level of classification, two CNNs were used, one for classifying the emotion expressed by the female speakers and the other for the male speakers.
In the second hierarchical model (Figure 2), the first classifier recognizes if the emotion expressed by the speaker is either positive or negative, then in the second layer of classification, two CNNs were used, one for the positive emotions, where each of the samples that were classified as "positive" in the first layer are classified into one of the positive emotions (i.e., calmness, happiness, surprise). The second CNN classifier did the same task for the negatively-classified samples, where each sample is classified into one of the negative emotions (i.e., sadness, disgust, fear, anger).
