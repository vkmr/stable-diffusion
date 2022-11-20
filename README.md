# stable-diffusion
In this guide, I will show how to generate novel images based on a text prompt using multiple implementation of stability.ai's text-to-image model, [Stable Diffusion.](https://arxiv.org/abs/2112.10752)

Stable Diffusion is a powerful, open-source text-to-image generation model. While there exist multiple open-source implementations that allow you to easily create images from textual prompts, 

1. [KerasCV](https://keras.io/guides/keras_cv/generate_images_with_stable_diffusion) implementation: KerasCV's implementation offers a few distinct advantages. These include XLA compilation and mixed precision support, which together achieve state-of-the-art generation speed on NVIDIA GPUs. There are three models: text-encoder, diffusion model and image decoder combined in a pipeline to generate images based on text prompt. Few commands for enironment setup:
* (base) vivek@adhyayan-marvel:~$ conda create --name stable-diffusion
* (base) vivek@adhyayan-marvel:~$ conda activate stable-diffusion
* (stable-diffusion) vivek@adhyayan-marvel:~$ conda install jupyter notebook
* (stable-diffusion) vivek@adhyayan-marvel:~$ jupyter notebook&

Please refer to [notebook](https://github.com/vkmr/stable-diffusion/blob/main/keras-cv-implementation.ipynb) for implementation details.

2. [HuggingFace](https://huggingface.co/CompVis/stable-diffusion-v1-4) implementation: Found huggingface implementation to be very quick on NVIDIA GPU compared to keras. Key environment setting is to login on huggingface hub to accept terms and licenses. 
Few commands for environment setup:
 * $ conda create --name stable-diffusion-huggingface python=3.10
 * $ conda activate stable-diffusion-huggingface
 * $ pip install --upgrade diffusers transformers scipy
 * $ pip install huggingface_hub
 * $ huggingface-cli login
 * $ conda install jupyter notebook
 * $ conda install -c conda-forge pytorch-gpu
 * $ conda install -c conda-forge gcc=12.1.0
 * $ jupyter notebook

Please refer to [notebook](https://github.com/vkmr/stable-diffusion/blob/main/stable-diffusion-huggingface.ipynb) for implementation details.

3. Intel PyTorch implementation:

4. Intel OpenVINO implementation:
