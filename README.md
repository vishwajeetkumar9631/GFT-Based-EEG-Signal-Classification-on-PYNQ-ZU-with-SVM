# GFT-Based-EEG-Signal-Classification-on-PYNQ-ZU-with-SVM
This project implements a Graph Fourier Transform (GFT)-based feature extraction pipeline for EEG signal classification using the ASU imagined speech dataset. The complete processing pipeline has been deployed and tested on a PYNQ-ZU FPGA board, achieving a classification accuracy of 87.23% using an SVM (Support Vector Machine) classifier.

Project Overview
The project is focused on classifying EEG signals using advanced techniques in graph signal processing (GSP), specifically the Graph Fourier Transform (GFT). It targets imagined speech signals (thought-level activity without vocalizing), which are very challenging to classify due to the complexity and noise in EEG signals.

This work stands out by not only implementing the algorithm in Python but also deploying it on a real FPGA board (PYNQ-ZU) — bridging research with practical hardware realization.
Workflow Explanation
1. Dataset Used
You used the ASU Imagined Speech Dataset, which contains EEG recordings of users imagining speech.

The dataset has two classes and 100 trials per class, and each trial is a matrix of shape 64×512 (channels × timepoints).

2. Preprocessing
Bandpass filter (0.5–45 Hz): Removes low-frequency drift and high-frequency muscle/artifact noise.

Notch filter at 60 Hz: Specifically removes electrical interference from power lines (common in EEG recordings).

3. Feature Extraction with GFT
Each EEG trial (64 channels) is converted into a graph, where each node is a channel and edge weights are based on correlation between signals.

The graph Laplacian is computed to capture the structure of the EEG signal as a network.

Graph Fourier Transform (GFT) is applied to the signals, projecting the data from the spatial domain into the graph frequency domain — where patterns related to brain activity are more distinct.

4. Classification
Features from the GFT-transformed signals are passed to an SVM classifier (Support Vector Machine with RBF kernel).

The classifier learns to distinguish between the two imagined speech classes.

5. Hardware Deployment
The entire pipeline (filtering, GFT, and SVM classification) is implemented and run on a PYNQ-ZU board (a Zynq UltraScale+ FPGA with embedded ARM cores and programmable logic).

Code is executed using Jupyter Notebook hosted on the PYNQ board itself.

📊 Results and Performance
The model achieved a classification accuracy of 87.23%, which is quite good for imagined speech EEG.

This result validates that graph-based features (GFT) are effective for representing EEG signal structures.

Real-time feasibility on PYNQ-ZU shows that the model is lightweight and fast enough for deployment on embedded devices — which is essential for portable BCI (Brain-Computer Interface) systems.

🧠 Key Takeaways
You combined advanced signal processing (GFT) with ML (SVM) and hardware implementation (PYNQ-ZU) into a full-stack solution.

The result — 87.23% accuracy — demonstrates that the model not only works in theory but is deployable in real-time systems.

This kind of work is valuable for neuroprosthetics, assistive communication tools, and brain-computer interfaces where low-latency, embedded EEG analysis is critical.
