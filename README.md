Indian Sign Language Translator

Satyam Agrawal<br>
Mithil Chaudhary<br>
Atharva Chandras<br>
Hamza Ansari<br>

The Indian Sign Language Translator was our 5th Semester major project.<br>

It made use of a pre-trained model which was trained over a custom dataset, this dataset was prepared by refining and mixing up three different datasets picked up from Kaggle
and by adding some of our own images.

The python script to capture images and naming them can be found on our repo.

The entire project closely follows the official tutorial from TensorFlow's documentation.
This was done as TensorFlow's Model Zoo offers a wide variety of pre-trained models to choose from.
We chose the SSD ResNet50 V1 FPN 640x640 (RetinaNet50) because of mobile nature and accurate results in less time which was important for realtime detection.

https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html -- Official Documentation used

The instructions in the above link were followed to the dot, except for a few minor changes while making the .record files.
Instead of running the script given in the tutorial we used a different script which doesn't use the label map file and instead links the XML files directly to the classes from 
inside the script and constructs the .record files.

https://github.com/datitran/raccoon_dataset/blob/master/generate_tfrecord.py -- Python script used

We also used Google Colab's cloud computing to train our model and then exported it using the same command given in the documentation, with a few minor tweaks to match the
version changes.

!python exporter_main_v2.py --input_type image_tensor --pipeline_config_path models/my_ssd_resnet50_v1_fpn/pipeline.config --trained_checkpoint_dir models/my_ssd_resnet50_v1_fpn --output_directory exported-models/my_model
MUST BE TWEAKED ACCORDING TO THE DIRECTORY CHANGES

After exporting the inference graph and saving it inside the 'exported-models' folder, run the object_detection_tutorial.ipynb file to run the model with the webcam for realtime detection.
