# Detection of Covid-19 Using Transfer Learning

<p align="justify">The rapidly developed Corona virus, also known as Covid-19, with the first case confirmed in Wuhan, China, has spread around the globe and is classified as one of the greatest crisis in this centenary. The disease has driven researchers to develop more intelligent and efficient detection methods since it has proved pervasive demands for diagnosis. The purpose of this research is to provide an effective Covid-19 detection model by using neural networks and transfer learning on two data sets of healthy and unhealthy classified images that we have collected. Transfer learning is applied by adapting the pre-trained VGG-16 architecture together with the prepared data set. The result of our experiments show that the utilized model can provide a very high classification accuracy for our given data set. To examine what our network learnt to identify, image occlusion was applied and the results, that covering the lungs decreases performance, were discussed. Along with these results and our concluding next step implementations, this deep learning model has potential to be used to detect Covid-19 on x-ray images with high certainty. I carried out this project with two colleagues. Here you can find our code. There were many different versions of the program used, but CODE.ipynb should give you a good overview. In Colab Noteboks/ there are some notebooks used and in Results/ we have saved the notebook (with the results) and its picture for most of the important runs.
The following datasets were used:</p>

https://github.com/ieee8023/covid-chestxray-dataset

https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia/data

# Data exploratory & training analysis

<p align="justify">When looking at the healthy images and comparing them to the unhealthy set, the former ones were more consequentially similar among themselves and "cleaner" indifferent to the unhealthy set which had miscellaneous differences such as obscure angles, picture with manually added arrows and texton the images. This could eventually lead to a high accuracy due to the fact that the healthy images are always cleaner instead of the network being able to actually spot Covid-19. Thereby, we choose to go through all these 377 and filtered out "filtered" (i.e.  comparable to the healthy pictures) vs "unfiltered" for experimentation, seen in figure 1 and figure 2. We also isolated out the confirmed Covid-19 cases and out of these, whereby only 97 images turned out to be comparable to the healthybatch (i.e. no medical equipment such as pace-marker or monitoring equipment attached during scan,text or arrows on the image, size of the images and angles of the scans).</p>

![](https://github.com/alexanderbea/Detection-of-Covid-19-Using-Transfer-Learning/blob/main/Images/Figure%201.PNG)

<p align="justify">Another step consisted of applying the input modification method, by modifying the input and and measure the resulting changes in the output. By this method the locality of Covid-19 features and important part of the images can be analyzed. More specifically, the "Occlusion method" is used. By systematically covering up parts of the images with a black box, seen in figure 3 and figure 4, and notice the change in accuracy, the robustness of the network can be analyzed. By applying this method, it will be a useful tool to analyze if the network still achieves a high accuracy when vital areas of the images are covered i.e. Covid-19 parts. If the accuracy is lower, then the network can be classified as robust [10]. In contrast, if the accuracy does not change notably, it is more likely that the network has learned to recognize the difference of the backgrounds between Normal and Covid images and not the parts where disease is present. </p>

![](https://github.com/alexanderbea/Detection-of-Covid-19-Using-Transfer-Learning/blob/main/Images/Figure%202.PNG)

<p align="justify">AThe first experiment conducted, consisted of removing the original dense layers from VGG-16 and replacing them with one dense layer, consisting of 128 nodes with ReLU as its activation function, followed by the output layer, consisting of one node with the sigmoid function as its activation function. The results of this are shown in figure 5 and figure 6 below, with the two different data sets unfiltered in color and filtered in grayscale.</p>

![](https://github.com/alexanderbea/Detection-of-Covid-19-Using-Transfer-Learning/blob/main/Images/Figure%203.PNG)

<p align="justify">Next, to check the robustness of the model, boxes covering different parts of the images were added to the inputs during training. The results can be seen in figure 7 and figure 8</p>

![](https://github.com/alexanderbea/Detection-of-Covid-19-Using-Transfer-Learning/blob/main/Images/Figure%204.PNG)

<p align="justify">Also, further augmentation of the data was performed by in one case also applying re-scaling more aggressively (55-50% of the original image) and in another case by using a more image augmentation, namely rotation, a increased re-scaling (85-60% of the original image) and shifting the image</p>

![](https://github.com/alexanderbea/Detection-of-Covid-19-Using-Transfer-Learning/blob/main/Images/Figure%205.PNG)
