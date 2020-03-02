## Self-Supervised learning for Deepfake detection

This GitHub showcases the results of my Master's Thesis, that is detecting facial manipulations without a priori knowledge about the method.

<p align="center">
  <src="https://i.imgur.com/chG950e.png">
</p>

The Model achives a classification accuracy (fake or real) of ~90% for the [Faceforensics++](https://github.com/ondyari/FaceForensics) Dataset across all 4 methods: Real Images, DeepFakes, FaceSwap, Face2Face.

## Method
The Method is based on the self-supervised splice detector from [Huh et Al.](https://github.com/minyoungg/selfconsistency). Instead of a siamese RN50 network with added FC layers, we instead use [Hard Triplet Mining](https://arxiv.org/abs/1503.03832), to adress the known problem of trivial training samples. This speeds up the training by about x10 or alternatively halves the final error rate for same-image predictions. 

Like [Huh et Al.](https://github.com/minyoungg/selfconsistency) we only train on original photography from Flickr. To manage to adapt the domain to low-res video crops we also include scale augmentions in training and then rescale the patches to adequate size in test time. This is an important step which boosts the accuracy from about 60% to ~90% for the FaceForensics++ c0 data. At the moment, the accuracy of the method drops significantly when applying compression to the images.
## Demo

Run `demo.py` for model download and visual demo. (Requires cuDNN capable GPU)
