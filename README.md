Descritpion of problem:

Data is 96 by 96 by 3 images of body scans either containing metastatic caner or not. There are 220k images in the test data with a label 0 if negative and 1 if positive. I missed this when I first stated but the label is only within the center 32 by 32 by 3 area.

EDA:
I viewed a couple training samples images that were positve and some that were negative.  I also looked at different histograms of their intesity of color to see if there were trends that made some negative and some positive. The big data cleaning was when i implemented the keras model of taking the center 32 by 32.   I added some padding to not lose the filtering on the borders. My plan is to run a keras model that has multiple convulutional layers (filtering,pooling,normalization) to then fit agianst the train to improve AUC ROC.

Architecture: I first wanted to load in the shape of the correct shape of the whole data that we have. I then wanted to scale the 3 colors to between 0 and 1 by dividing by 255. Since the true label is found through the center 32 x 32 I chose to crop through the center with padding of 2 on all the sides. I tried different amounts of layers, filter sizes and batches, and dropouts. The more parameters the slower the model. I also experiemented with the learning rate trying to converge without have to run too many epochs.

Results and analysis.

After trying many different iterations i was able to move my score up from 70 into the low 80s.  I ran a early stopping to try and maximize the AUC to know when to stop. I experiemented with different # layers and had more success when parameter were not enormous as it slowed down the fit. I also experemented with different learning rates to increae convergence. The largest value add came from reducing paramenters and the intial filtering of the center.

Conclusion:
I learned that it is important to understand to fully undertand the problem and the data before trying to write code to solve it. I learned that it is important to not have too many parameters and too small of batch size as it can take the model too long to converage.  I learned that it is good to use early stopping on model fits as this allows you to run model and walk away.  I spent a long time trying to rerun models with different parameters.  I think using a validation set(portion of the training data to test on would help me understand when the model is properly converged and fit as a faster way to get better perfomance.
