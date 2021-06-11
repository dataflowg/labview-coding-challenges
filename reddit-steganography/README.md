# LabVIEW Reddit Coding Challenge - June 2021

A steganography routine which encodes a hidden message into an image. Source code saved with LabVIEW 2020.

The encoding routine uses bitmap images, and encodes data in to the least significant bits of each of the RGB image components. The allows a single message byte to be encoded across 3 bytes of image data, or 1 message byte per pixel. The example image size is 1334x750 pixels or 1,000,500 pixels, so there's about 1MB of message data which can be encoded.

The embedded message is compressed using either LabVIEW's built in zip compression, or using an external compressor (7-Zip, zpaq). The external compressors are far more effective, as they have routines optimized for text compression ([PPM](https://en.wikipedia.org/wiki/Prediction_by_partial_matching), [PAQ](https://en.wikipedia.org/wiki/PAQ)).

## Results

Compressor | Size (bytes) | Composite Score | Screenshots
-----------|--------------|-----------------|------------
zip (LabVIEW) | 464,133 (1 message) | 0.00022321 | [Result](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/zip-1.png), [Score](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/zip-1-score.png)
zip (LabVIEW) | 79,366,743 (171 messages) | 0.03468135 | [Result](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/zip-171.png), [Score](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/zip-171-score.png)
7z (PPMd) | 464,133 (1 message) | **0.00006154** | [Result](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/7z-1.png), [Score](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/7z-1-score.png)
7z (PPMd) | 524,470,290 (1130 messages) | 0.03302660 | [Result](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/7z-1130.png), [Score](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/7z-1130-score.png)
zpaq (-m3) | **2,088,598,500** (4500 messages) | 0.02126609 | [Result](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/zpaq-4500.png), [Score](https://raw.githubusercontent.com/dataflowg/labview-coding-challenges/main/reddit-steganography/Results/zpaq-4500-score.png)

Minor optimizations are possible and are documented in `Encode Compressed Message.vi`, but haven't been implemented.

# Links

https://www.reddit.com/r/LabVIEW/comments/nplfq0/labview_reddit_coding_challenge_june_2021/

https://gitlab.com/qalldredge/labview-reddit-coding-challenge-june-2021
