# stable-diffusion
In this guide, I will show how to generate novel images based on a text prompt using multiple implementation of stability.ai's text-to-image model, [Stable Diffusion.](https://arxiv.org/abs/2112.10752)

Stable Diffusion is a powerful, open-source text-to-image generation model. While there exist multiple open-source implementations that allow you to easily create images from textual prompts, I tried to provide easy and quick solution using popular frameworks keras and huggig face. With environment setup instructions below, one can easily set up it on local PC/Laptop/Desktop/Macs. You can use notebooks on local machine or upload to colab environment on cloud as well. Performance on GPU is faster than CPU. If you don't have GPU, these instructions and notebook still work with some tweaks as mentioned. 

Few performance notes: notebooks in step #1, #2 and #5 work fine with NVIDIA GPU >= 8GB memory. Some sections of notebooks #3, #4 do require GPU of memory size >= 12 GB. If running on CPU, there is no restriction of memory as long as system memory(RAM) >= 16 GB. Please be patient to see results while running on CPU. And, feel free to drop questions in case of issue running on CPUs.

1. [KerasCV](https://keras.io/guides/keras_cv/generate_images_with_stable_diffusion) implementation: KerasCV's implementation offers a few distinct advantages. These include XLA compilation and mixed precision support, which together achieve state-of-the-art generation speed on NVIDIA GPUs. There are three models: text-encoder, diffusion model and image decoder combined in a pipeline to generate images based on text prompt. Few commands for enironment setup:
* (base) vivek@adhyayan-marvel:~$ conda create --name stable-diffusion
* (base) vivek@adhyayan-marvel:~$ conda activate stable-diffusion
* (stable-diffusion) vivek@adhyayan-marvel:~$ conda install jupyter notebook
* (stable-diffusion) vivek@adhyayan-marvel:~$ jupyter notebook

Please refer to [notebook](https://github.com/vkmr/stable-diffusion/blob/main/keras-cv-implementation.ipynb) for implementation details.

2. [HuggingFace](https://huggingface.co/CompVis/stable-diffusion-v1-4) implementation: Found huggingface implementation to be very quick on NVIDIA GPU compared to keras. Key environment setting is to login on huggingface hub to accept terms and licenses. 
Few commands for environment setup:
 * (base) vivek@adhyayan-marvel:~$ conda create --name stable-diffusion-huggingface python=3.10
 * (base) vivek@adhyayan-marvel:~$ conda activate stable-diffusion-huggingface
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ pip install --upgrade diffusers transformers scipy
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ pip install huggingface_hub
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ huggingface-cli login
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ conda install jupyter notebook
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ conda install -c conda-forge pytorch-gpu (if you have GPU, else just install pytorch)
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ conda install -c conda-forge gcc=12.1.0
 * (stable-diffusion-huggingface) vivek@adhyayan-marvel:~$ jupyter notebook

Please refer to [notebook](https://github.com/vkmr/stable-diffusion/blob/main/stable-diffusion-huggingface.ipynb) for implementation details.

Use environment set up of #2 on following three notebooks

3. [Image generation using text prompt](https://github.com/vkmr/stable-diffusion/blob/main/Stable_Diffusion_with_%F0%9F%A7%A8_diffusers.ipynb) implementation: This notebook has step by step implementation using StableDiffusionPipeline from huggingface. Additionally, it provides illustrated impact of variation of seed, number_inference_stops, resolution. Final section of notebook disucss how to use a custom scheduler to design new StableDiffusionPipeline. In this section, all three models of text encoder, unet and autoencoder are loaded individually.

4. [Image generation using input image and text prompt](https://github.com/vkmr/stable-diffusion/blob/main/image_2_image_using_diffusers.ipynb) implementation: This notebook shows diffusers pipeline for text-guided image-to-image generation with Stable Diffusion model. Step by step instruction and Illustration of input/output images and text prompt is provided. Impact of other input parameters like strength, scheduler and guidance scale on impact can be observed.

5. [Image in-painting using input image, mask guidance and text prompt](https://github.com/vkmr/stable-diffusion/blob/main/in_painting_with_stable_diffusion_using_%F0%9F%A7%A8diffusers.ipynb) implementation: This notebook shows diffusers pipeline for ext-guided in-painting with Stable Diffusion model. Step by step instruction and Illustration of input/output images and text prompt is provided. Additionally, an interactive interface is provided for Stable Diffusion In-Painting to upload new image, mask and text guide to generate new images.

Hope you like to enjoy and play around with these notebooks. And, please feel free to drop in your comment and feedback!

