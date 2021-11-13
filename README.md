# Image Quality Assessment using Contrastive Learning

**Pavan C. Madhusudana**, Neil Birkbeck, Yilin Wang, Balu Adsumilli and Alan C. Bovik

This is the official repository of the paper [Image Quality Assessment using Contrastive Learning](https://arxiv.org/abs/2110.13266)

## Usage
The code has been tested on Linux systems with python 3.6. Please refer to [requirements.txt](requirements.txt) for installing dependent packages.

### Running CONTRIQUE
In order to obtain quality score using CONTRIQUE model, checkpoint needs to be downloaded. The following command can be used to download the checkpoint.
```
wget -L https://utexas.box.com/shared/static/rhpa8nkcfzpvdguo97n2d5dbn4qb03z8.tar -O models/CONTRIQUE_checkpoint25.tar -q --show-progress
```
Alternatively, the checkpoint can also be downloaded using this [link](https://utexas.box.com/s/rhpa8nkcfzpvdguo97n2d5dbn4qb03z8).

### Obtaining Quality Scores
We provide trained regressor models in [models](models) directory which can be used for predicting image quality using features obtained from CONTRIQUE model. For demonstration purposes, some sample images provided in the [sample_images](sample_images) folder.

For blind quality prediction, the following commands can be used.
```
python3 demo_score.py --im_path sample_images/60.bmp --model_path models/CONTRIQUE_checkpoint25.tar --linear_regressor_path models/CLIVE.save
python3 demo_score.py --im_path sample_images/img66.bmp --model_path models/CONTRIQUE_checkpoint25.tar --linear_regressor_path models/LIVE.save
```

For Full-reference quality assessment, the folllowing command can be employed.
```
python3 demos_score_FR.py --ref_path sample_images/churchandcapitol.bmp --dist_path sample_images/img66.bmp --model_path models/CONTRIQUE_checkpoint25.tar --linear_regressor_path models/CSIQ_FR.save
```

## Training CONTRIQUE
### Download Training Data
Create a directory ```mkdir training_data``` to store images used for training CONTRIQUE.
1. KADIS-700k : Download [KADIS-700k](http://database.mmsp-kn.de/kadid-10k-database.html) dataset and execute the supllied codes to generate synthetically distorted images. Store this data in the ```training_data/kadis700k``` directory.
2. AVA : Download [AVA](https://github.com/mtobeiyf/ava_downloader) dataset and store in the ```training_data/UGC_images/AVA_Dataset``` directory.
3. COCO : [COCO](https://cocodataset.org/#download) dataset contains 330k images spread across multiple competitions. We used 4 folders ```training_data/UGC_images/test2015, training_data/UGC_images/train2017, training_data/UGC_images/val2017, training_data/UGC_images/unlabeled2017``` for training.
4. CERTH-Blur : [Blur](https://mklab.iti.gr/results/certh-image-blur-dataset/) dataset images are stored in the ```training_data/UGC_images/blur_image``` directory.
5. VOC : [VOC](http://host.robots.ox.ac.uk:8080/pascal/VOC/voc2012/) images are stored in the ```training_data/UGC_images/VOC2012``` directory.

## Contact
Please contact Pavan (pavan.madhusudana@gmail.com) if you have any questions, suggestions or corrections to the above implementation.

## Citation
```
@article{madhusudana2021st,
  title={Image Quality Assessment using Contrastive Learning},
  author={Madhusudana, Pavan C and Birkbeck, Neil and Wang, Yilin and Adsumilli, Balu and Bovik, Alan C},
  journal={arXiv:2110.13266},
  year={2021}
}
```
