# SentinelSequenesFloodingDataset

## What is this dataset about?

This dataset is an extension of the satellite subtask of Multimedia Satellite Task 2020 from MediaEval. 
Participants receive a set of sequences of satellite images that depict a certain region over a certain length of time. They are required to create a binary classifier that determines whether or not there was a flooding event ongoing in that region at that time. Because this is the first year we work with sequences of satellite images, the data will be balanced so that the prior probability of the image sequence depicting a flooding event is 50%. This design decision will allow us to better understand the task. Challenges of the task include cloud cover, and ground-level changes with non-flood causes.

We keep more updates to the dataset.
 - segmentation masks
 - 



## Where can I get the data? 

Here, we provide information about the released development and test sets for all subtasks. For details on the data format and provided features please refer to the task-specific dataset details.

Development Set
The development set for the City-centered satellite sequences task consists of image sequences and can be found here. We provide the following files in the dev-set folder:

devset_image_sequences.zip contains the subfolders for each sequence with the multiple images
devset_labels.jsonlcontains the Ground Truth labels for all satellite sequences
Test Set
The test set for this subtask consists of image sequences and can be found here. We provide the following files in the test-set folder:

testset_image_sequences.zip contains the subfolders for each sequence with the multiple images



## What data do I get?

The City-centered satellite sequences dataset consists of about 500 satellite image sequences which have been extracted for flooding events and non flooding events. We supply participants with the following information:

For each image sequence the following information is provided:
* a class label: (only for devset, see section [Ground Truth](#ground-truth-file-2))
* the image bands as timeseries (see section [Image Sequences](#image-sequences))


### Ground Truth File
The dataset has been created from past flooding events that have been mapped and validated by human annotators for the emergency response service EMSR. Rather than relying on a single image or a pair of images, we consider a sequence of images. The label is created based on the intersection of the mapped flood extend (overlap with image sequence=1, no overlap=0). For each sequence we provide the corresponding label to participants in a json-lines file **devset_sequences_labels.jsonl** with the corresponding keys "sequence_id", "label". An example is presented below: 

```
{"sequence_id": "5060", "label": 0}
{"sequence_id": "593", "label": 1}
...
{"sequence_id": "412", "label": 0}
```

### Image Sequences

Each image sequence is stored in one specific folder that contains images and a **timeseries.txt**. The timeseries.txt contains the timesteps for each time series with the following three lines of information: DATE, FLOODING, FULL-DATA-COVERAGE (whether the area is fully covered by the image).

```
Layer_1_DATE: 2018-12-18,
Layer_1_FLOODING: True,
Layer_1_FULL-DATA-COVERAGE: True,
Layer_2_DATE: 2018-12-28,
Layer_2_FLOODING: True,
Layer_2_FULL-DATA-COVERAGE: True,
Layer_3_DATE: 2019-01-02,
Layer_3_FLOODING: False,
Layer_3_FULL-DATA-COVERAGE: True,
```

The timesteps are encoded into a tiff file, where the number of channels corresponds to the length of the time-series. Each image band of Sentinel2 is stored in the corresponding file (e.g. band 4 is stored in ''B4_series.tif''). Sentinel-2 comes with 13 bands and we provide timeseries tiff files for all 13 bands. In the following table, we provide an overview of the bands. You can use bands 4,3,2 to create RGB images, but also use other bands to create a False color image or feed more than three bands to your classifier. Please note that the bands have a different spatial resolution and might require upscaling.



## Who are the organizers/contributors?

### Task organizers of the Multimedia Satellite Task 2020
* Benjamin Bischke, German Research Center for Artificial Intelligence (DFKI), Germany (first.last at dfki.de)
* Patrick Helber, German Research Center for Artificial Intelligence (DFKI), Germany (first.last at dfki.de)
* Erkan Basar, Radboud University & FloodTags, Netherlands, 
* Simon Brugman, Radboud University, Netherlands
* Zhengyu Zhao, Radboud University, Netherlands
* Konstantin Pogorelov, Simula Research Laboratory, Norway

### Task auxiliaries
* Martha Larson, Radboud University, Netherlands
* Jens de Bruijn, Floodtags, Netherlands
* Tom Brouwer, Floodtags, Netherlands

If you need help or have any questions please contact Benjamin Bischke (firstname.lastname at dfki.de).
