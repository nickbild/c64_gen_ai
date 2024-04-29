# Commodore 64 AI Image Generator

Make creative retro game sprites on the Commodore 64 with generative AI.

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/logo.jpg)

## How It Works

AI image generators are very popular these days, and the results are used in all sorts of creative projects. This made me wonder what it would have been like if image generators had existed during the early personal computer revolution in the 1980s. What would they have been like, and what would the images have been used for?

Today's algorithms, like Stable Diffusion, require a huge amount of computational resources that simply cannot be made to work (in any reasonable way) on machines of the era. But with some work, a simpler generative algorithm could be used to produce images. So I decided to adapt a probabilistic PCA algorithm to run on a Commodore 64, with the goal of producing 8x8 retro game sprites that could have been used to inspire a game design.

I started by building a model using a modified version of the Python code found in [this tutorial](https://github.com/smrfeld/python_prob_pca_tutorial). I made about 100 retro-inspired sprites (represented as [binary strings](https://github.com/nickbild/c64_gen_ai/blob/main/train_c64.txt)) with the help of a [spreadsheet](https://github.com/nickbild/c64_gen_ai/blob/main/create_sprites.ods) I made. This data was used to train the model on a modern computer with modified scripts from the tutorial.

This produces a number of parameter values (a mean matrix, covariance matrix, etc.) that only need to be calculated once for a given dataset. These were then plugged into a [script](https://github.com/nickbild/c64_gen_ai/blob/main/pca_custom.py) I created with simplified logic — no NumPy or other libraries — to run the randomization and generative parts of the algorithm. This simplification made it easy to convert the logic into [BASIC code](https://github.com/nickbild/c64_gen_ai/blob/main/make_basic.py) that is compatible with the Commodore 64. That code is then loaded onto a C64 to generate unique images drawn from the distribution of the training data. Finally, the 8x8 images are expanded to 64x64 and displayed on the screen.

The number of iterations the algorithm goes through can be varied. More iterations produces better results generally, but takes longer. At 94 iterations, it takes about 20 minutes to run on a C64. Not really too bad consiering how long a modern image generator would take on a modern computer without a GPU.

## Media

Running on a C64:

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/running_start_sm.jpg)

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/running_finished_sm.jpg)

Samples of generated images:

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/sample1.png)

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/sample2.png)

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/sample3.png)

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/sample4.png)

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/sample5.png)

![](https://raw.githubusercontent.com/nickbild/c64_gen_ai/main/media/sample6.png)

## Bill of Materials

- 1 x Commodore 64

## About the Author

[Nick A. Bild, MS](https://nickbild79.firebaseapp.com/#!/)
