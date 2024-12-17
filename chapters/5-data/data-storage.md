# Data storage problem

Microscopy experiments can generate significant amount of data that needs to be archived and preserved often for years. Sometimes it takes long time to process the data, or to collect the whole datasets, and even longer to prepare data for publication. Re-analysis often required in the process of writing the research paper or addressing the review process. Even modest datasets can occupy 100s of gigabytes. [We have discussed data storage previously](https://arxiv.org/abs/2108.07631), mainly focussing on three solutions:

- cloud-based data storage
- local, server-based solutions
- institute data storage

## Local storage

## Cloud is someone else's computer

"Cloud" is used as a general term for computer infrastructure with convenient interfacing that is maintained by someone else. Dropbox or Google Drive are one of the most user-friendly examples. While these systems provide affordable and reliable solutions it is important to remember that "cloud" is nothing more than a network-attached computers and have limitations inherent to every computer system. It can have downtime or long outages; it depends on your network connectivity; data can be accessed by others without permission; it can take long time to upload or download large datasets. You should acknowledge these risks and either just accepts potential issues or build redundant systems, such as local primary storage (in your lab) with cloud back-ups.

## Data compression

In order to decrease costs associated with storing data, and to speed up data transfer (for example, between collaborators) [data compression](https://en.wikipedia.org/wiki/Lossless_compression) can be utilized. Compression uses statistical algorithms to decrease amount of space required to store the same amount of information. For example, if image is 2048x2048 black (value 0) pixels at 16 bit (8MB), it can be compressed to binary data (0.5MB) without any losses. When datasets are more complex, compression can be performed with lower efficiency but following the same principles. Compression requires knowledge of specific algorithm that was used to compress data so that de-compression can be performed. [Microscopy images can be compressed without losses](https://www.biorxiv.org/content/10.1101/2023.01.24.525380v1) with up to 3x compression ratio. There are examples (such as [JetRaw](https://x.com/aandr314/status/1456305679736578061)) that use specific camera/microscope performance data to perform lossy compression and provide plugins for ImageJ to perform de-compression. Algorithms with highest compression ratio usually have lower compression/decompression speed.
