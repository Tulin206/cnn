# TUD CNN 2026: Convolutional Neural Networks

Lecture materials and practical notebooks for learning convolutional neural networks (CNNs) through image classification with CIFAR-10.

**Instructor:** Israt Jahan Tulin, HZDR  
**Lecture date:** November 11, 2026

## Materials and learning objectives

Start with the [lecture slides](Lecture_Materials/TUD_CNN_2026.pdf). They cover:

- Fully connected networks versus CNNs and local connectivity.
- Convolution, filters, feature maps, and RGB image channels.
- Padding, stride, and calculating output dimensions.
- Pooling, flattening, and the role of dense layers.
- AlexNet and VGG architectures.
- PyTorch examples and an appendix on tensor shapes and visualizing convolution outputs.

The practical notebooks offer parallel implementations in **TensorFlow/Keras and PyTorch** to build simplified AlexNet-like and VGG-like networks for 32 × 32 RGB images. They train models from scratch; they do not use pretrained AlexNet or VGG models. Choose either framework, or work through both versions to compare their APIs and training workflows.

Basic Python, familiarity with notebooks, and an introductory understanding of neural networks will help you follow the exercises.

## Practical notebooks

Follow this order after reviewing the slides:

| Step | TensorFlow/Keras | PyTorch | What you will do |
| --- | --- | --- | --- |
| 1 | [AlexNet example](code/CNN/09_alexnet_cifar10.ipynb) | [AlexNet example](code/CNN/09_alexnet_cifar10_pytorch.ipynb) | Build five convolutional layers, train for 10 epochs, and inspect accuracy, confusion matrices, and predictions. |
| 2 | [VGG exercise](code/CNN/10_vgg_cifar10_exercise.ipynb) | [VGG exercise](code/CNN/10_vgg_cifar10_pytorch_exercise.ipynb) | Complete the architecture, training, plotting, and evaluation TODOs. |
| 3 | [VGG solution](code/CNN/10_vgg_cifar10.ipynb) | [VGG solution](code/CNN/10_vgg_cifar10_pytorch.ipynb) | Compare with the worked solution using three paired convolution blocks, dropout, and 30 training epochs. |

Both versions normalize CIFAR-10 pixels to [0, 1], use Adam with learning rate 0.001, and train with a batch size of 64. The PyTorch notebooks explain `Dataset`/`DataLoader`, channel-first image tensors, `nn.Module`, explicit training loops, device selection (CUDA, Apple MPS, or CPU), and evaluation mode.

Keras uses a softmax output with sparse categorical cross-entropy. PyTorch returns raw logits for `nn.CrossEntropyLoss`; softmax is only applied when displaying probabilities. The notebook comparison tables connect these concepts across frameworks.

The exercises intentionally contain unfinished code. Complete the TODO cells in order; the PyTorch exercise raises `NotImplementedError` until the relevant sections are implemented.

**Evaluation note:** The original Keras notebooks reuse the test set for validation. The PyTorch versions split the original training data into 45,000 training and 5,000 validation images, reserving the 10,000 test images for final evaluation. For a controlled framework comparison, use the same data split and training settings in both versions; their default accuracy results are not directly comparable.

## Run the notebooks

### Option 1: Google Colab

1. Download the notebook you want to use from `code/CNN/`.
2. Open [Google Colab](https://colab.research.google.com/) and upload the `.ipynb` file.
3. Select a GPU runtime if available to speed up training.
4. Run cells from top to bottom, completing the TODOs if you are using the exercise notebook.

The original TensorFlow notebooks' embedded Colab badges still point to the earlier `erumhub_deep-learning_2026` repository. Upload the files from this repository to work with these materials.

Install the dependencies for your chosen framework if imports are missing. For TensorFlow/Keras:

```python
%pip install tensorflow numpy matplotlib pandas seaborn scikit-learn
```

For PyTorch:

```python
%pip install torch torchvision numpy matplotlib pandas seaborn scikit-learn
```

### Option 2: Run locally

Use a Python version supported by your chosen framework on your operating system. From the `TUD_CNN_2026` directory, create an environment and install the notebook dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
# Install both frameworks to work through both versions.
python -m pip install tensorflow torch torchvision numpy matplotlib pandas seaborn scikit-learn jupyterlab
python -m jupyterlab
```

On Windows, create the environment with `python -m venv .venv` and activate it in PowerShell with `.venv\Scripts\Activate.ps1`.

Open a notebook from `code/CNN/` in JupyterLab. An internet connection is needed for the initial CIFAR-10 download. Training can take considerable time on a CPU; for an initial check, reduce the epoch count before running the full exercise.

## Participant feedback

Please share your feedback in the **[TUD CNN 2026 feedback Etherpad](https://pad.shoplatein.de/p/TUD_CNN_2026_Feedback)** at the end of the session.

Add your comments below other participants' contributions. Your name is optional. Please answer these two questions:

1. **What did you like?** Which explanations, examples, or exercises helped you most?
2. **What could we improve?** What was unclear, too fast, too slow, or missing? What would make the lecture or coding exercises more useful?

You can copy this short template into the pad:

```text
Name (optional):
What I liked:
What could be improved:
Other questions or suggestions:
```

## Repository structure

```text
TUD_CNN_2026/
├── README.md
├── LICENSE
├── Lecture_Materials/
│   └── TUD_CNN_2026.pdf
└── code/
    └── CNN/
        ├── 09_alexnet_cifar10.ipynb
        ├── 09_alexnet_cifar10_pytorch.ipynb
        ├── 10_vgg_cifar10_exercise.ipynb
        ├── 10_vgg_cifar10.ipynb
        ├── 10_vgg_cifar10_pytorch_exercise.ipynb
        └── 10_vgg_cifar10_pytorch.ipynb
```

## License

This repository is distributed under the [MIT License](LICENSE).
