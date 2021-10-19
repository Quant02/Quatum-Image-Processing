# Quantum Image Processing using QPIE
## The Team

- Varun Srivatsav 
- Gargi Chandrakar
- Masih Ahmed
- Jatan Trivedi
- Rohit Malawat

## Problem Statement

We implement, using qiskit, a model called Quantum Probability Image Encoding, a.k.a QPIE, for processing quantum images. In this model, we encode the pixel values of an image into the probability amplitudes of a pure quantum state and their positions into computational basis states. This method has the proven advantage of using exponentially fewer qubits than its classical counterparts.

The objective of this project is to exploit the Quantum Fourier Transform to convert the image, encoded using QPIE, into the frequency domain for image processing purposes such as denoising, edge detection, image classifiers etc

The QPIE model is explained in the following paper: [Implementation and Analysis of Quantum Fourier Transform in Image Processing](https://www.researchgate.net/publication/331674710_Implementation_and_Analysis_of_Quantum_Fourier_Transform_in_Image_Processing)


## Goals
The goal is to develop a Python module using Qiskit to achieve the following

- Classical image processing
- Apply Quantum Probability Image Encoding (QPIE)
- Apply various Quantum Image Processing 



## Proposed Implementation

**Classical Image Processing**
This step is required to make sure the image is ready to be processed by a Quantum Computer with ease
- Changing from RGB to grayscale format
- Split the image into 8 x 8 chunks for easier processing using a Quantum Simulator

**Quantum Probability Image Encoding (QPIE)**
The quantum encoding or Quantum Image Representation (QImR) step involves the transformation of the data from a classical to a quantum image representation model. We decided to use QPIE because of its notable advantage of using the least amount of qubits for encoding.
This is done by converting the 2D image matrix to a 1D array and normalising it. The normalised array is passed as a Statevector to the quantum circuit.

**Quantum Image Processing**

We tried implementing denoising and edge detection. 

Denoising was performed by applying a QFT gate to the Statevector passed initially. The frequency vector is measured and the higher frequency amplitudes are set to zero under the assumption that most of the noise resides in higher frequencies. The new Statevector is re-normalised and passed through an inverse QFT to retrieve the image.

Edge detection was performed using QHED algorithm. The image is split into 8 x 8 chunks and each tile is passed through the edge detection module. Once all tiles are processed, they are stitched back together to form back the original dimensions of the image, consisting of the edges only.  


