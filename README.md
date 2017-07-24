# Deep-learning-with-cats

This repository is a "toy" project so I can gain experience building deep neural networks. My first goal is generating pictures of cats using Generative Adversarial Networks. My second goal is making art with cats by applying styles to pictures of cats using deep convolutional neural networks. (^._.^)

![](/images/DCGAN_220epochs.gif)

**Updates** 
  * 17/07/2017 : Added CycleGAN for style transfer, so far doesn't work well with the CAT dataset and it's so slow (20-24h to fully train it). I'm leaving it here for those interested but I probably will try fast neural style instead.
  * 15/07/2017 : Many people were concerned about whether the generated images are really novel or rather just copies of the training dataset so I made a python function that output the 5 most similar training (real) images to the given generated (fake) images. See: https://github.com/AlexiaJM/Generative-model-most-similar-images.

**Objectives (so far)**
* Generate images of cats using various types of Generative Adversarial Networks (GAN)
  * use **DCGAN** (Done)
  * use **WGAN** (Done)
  * use **WGAN-GP** (Done)
  * use **LSGAN** (Done)
  * use **BEGAN**
* Transform real cats into art pieces 
  * use **CycleGAN** (Code done)
  * use **Fast neural style** (Almost ready)
* Various/Others
  * Try adding Frechet Inception Distance (FID) as per https://arxiv.org/pdf/1706.08500.pdf
  * Try soft and noisy labels as per https://github.com/soumith/ganhacks
  * Try adding decaying noise to input as per https://github.com/soumith/ganhacks
  
**Needed**

* Python 3.6, PyTorch, Tensorflow (for TensorBoard)
* Cat Dataset (https://web.archive.org/web/20150703060412/http://137.189.35.203/WebUI/CatDatabase/catData.html)
* TensorBoard logger (https://github.com/TeamHG-Memex/tensorboard_logger)

**To run**
```bash
$ # Download dataset and preprocess cat pictures 
$ # Create two folders, one for cats bigger than 64x64 and one for cats bigger than 128x128
$ sh setting_up_script.sh
$ # Move to your favorite place
$ mv cats_bigger_than_64x64 "your_input_folder_64x64"
$ mv cats_bigger_than_128x128 "your_input_folder_128x128"
$ # Generate 64x64 cats using DCGAN
$ python Meow_DCGAN.py --input_folder "your_input_folder_64x64" --output_folder "your_output_folder"
$ # Generate 128x128 cats using DCGAN
$ python Meow_DCGAN.py --input_folder="your_input_folder_128x128" --image_size 128 --G_h_size 64 --D_h_size 64 --SELU True
$ # Generate 64x64 cats using WGAN
$ python Meow_WGAN.py --input_folder "your_input_folder_64x64" --output_folder "your_output_folder"
$ # Generate 64x64 cats using WGAN-GP
$ python Meow_WGAN-GP.py --input_folder "your_input_folder_64x64" --output_folder "your_output_folder" --SELU True
$ # Generate 64x64 cats using LSGAN (Least Squares GAN)
$ python Meow_LSGAN.py --input_folder "your_input_folder_64x64" --output_folder "your_output_folder"
```
**To see TensorBoard plots of the losses**
```bash
$ tensorboard --logdir "your_input_folder"
```

# Results

**Discussion of the results at https://ajolicoeur.wordpress.com/cats.**

**DCGAN 64x64**

![](/images/DCGAN_209epoch.png)

**DCGAN 128x128 with SELU**

![](/images/DCGAN_SELU_128x128_epoch605.png)

**WGAN 64x64**

![](/images/WGAN_1408epoch.png)

**WGAN-GP 64x64 with SELU**

![](/images/WGAN_GP_iter15195.png)
