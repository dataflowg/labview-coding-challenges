# LabVIEW Reddit Coding Challenge - June 2021

A steganography routine which encodes a hidden message into an image. Source code saved with LabVIEW 2020.

The encoding routine uses bitmap images, and encodes data in to the least significant bits of each of the RGB image components. The allows a single message byte to be encoded across 3 bytes of image data, or 1 message byte per pixel. The example image size is 1334x750 pixels or 1,000,500 pixels, so there's about 1MB of message data which can be encoded.

The embedded message is compressed using either LabVIEW's built in zip compression, or using an external compressor (7-Zip). The external compressor is far more effective, as it has routines optimized for text compression ([PPM](https://en.wikipedia.org/wiki/Prediction_by_partial_matching)).

## Results

Compressor | Size (bytes) | Composite Score
-----------|------|----------------
zip (LabVIEW) | 464,133 (1 message) | 0.00061616
zip (LabVIEW) | 79,366,743 (171 messages) | 0.0345245
7z (PPMd) | 464,133 (1 message) | 0.000147606
7z (PPMd) | 524,470,290 (1130 messages) | 0.0330266

Minor optimizations are possible and are documented in `Encode Compressed Message.vi`, but haven't been implemented.

# Links

https://www.reddit.com/r/LabVIEW/comments/nplfq0/labview_reddit_coding_challenge_june_2021/

https://gitlab.com/qalldredge/labview-reddit-coding-challenge-june-2021
