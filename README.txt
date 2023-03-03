MCSA involves analyzing the current signature of a motor to detect changes in its characteristics, which can indicate the presence of faults such as rotor bar breakage, bearing wear, and misalignment. The technique is based on the fact that the current drawn by a motor is affected by the condition of the rotor and stator windings, as well as the load on the motor. By analyzing the frequency spectrum of the current signal, it is possible to detect changes in the signature that are indicative of specific types of faults.
If there will be any defect in the motor or mechanical component that can be seen in the current waveform.
The approach taken here is that all the peaks(maxima) and crests(minima) are noted for the waveform.  Then these points are studied and the outliers among them are given the possibility of carrying defects.
One important point to note here is that the current signature for the normal working of the device is not given. Hence, we cannot be sure that the changes in the current signature are exactly defects or some other activity. But yes, we can be sure that if the current signature is changing then obviously some or the other activity is happening.

Dataset: The dataset has observations of a 3-phase AC motor(3.2hp).


The model-making and accuracy estimation is done using a random forest classifier.

Please note before predicting the faults in the new data, it has to go under preprocessing which includes smoothening and finding the peaks and crests of the smoothened waveform.



methodology followed:

Actually to detect the anomaly we need the current readings for the normal functioning of the machine. There was no reference datum to compare the data with. The change can be due many reasons like changing the mode of a machine, or like changing a gear etc. Therefore I just detected the abnormalities in the waveform and assign them as value 1 (which were basically the outliers of the altitudes of the waveform)

I read the files as txt and then plot them. After plotting them I observed the pattern of the waveform and saw some unusual altitudes. I tried smoothening the graph in order to have just one peak or crest wherever the abnormalities were. After that I calculated all the peaks and crest. Finally among all those peaks and crest I found the outliers which I named as defect or unusual. And then on this data I created the Random Forest classification for each phase. Since it is a 3 phase therefore having fault in 1 phase can be compensated by the other 2 phase but since we don’t have the reference readings, I just tried to predict the abnormalities in each phase separately.

So now to predict the abnormalities on the new data we need to separate the reading for each phase and then smoothen it and then find the peaks and crests and then we can detect the abnormalities which can be traced back to the time or range of values before smoothening.
