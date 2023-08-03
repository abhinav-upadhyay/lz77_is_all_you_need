# LZ77 Is All You Need for Text Classification?
This repo contains code for the article [LZ77 Is All You Need? Why Gzip + KNN Works for Text Classification](https://codeconfessions.substack.com/p/lz77-is-all-you-need)

A paper published at ACL 2023 showed that using gzip compression in combination with k-nearest neighbours
for text classification achieves near state-of-the-art performance on many benchmarks.

I wrote an article investigating why exactly gzip works so well for text classification. If you peel all the
layers of compression techniques such as gzip, LZMA, and zstd, you will find that LZ77 is at their heart.
And if you understand how LZ77 works, then you would quickly figure out how it can take advantage of
repeated patterns in two pieces of texts from same class.

This repo contains code for the article. It consists of Jupyter notebook with a synthetic dataset. The dataset
consists of four classes:

- Sports
- Astronomy
- Cooking
- Gardening

Each class in this dataset contains only two samples.

The idea is to take each sample from each class and find its nearest neighbour using different compression algorithms.
We evaluate four algorithms: gzip, Huffman coding, LZ77 (LZ4 to be precise) and bzip2 (just the first two stages of bzip2: BWT + MFT).

The results of the experiment are shown below:
![Results](https://github.com/abhinav-upadhyay/lz77_is_all_you_need/blob/490e4d3b16c72cfb3c5c2bde75c14f6420514313/results.png)
