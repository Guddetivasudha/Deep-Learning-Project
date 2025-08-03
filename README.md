# Deep-Learning-Project
Polygon Coloriza on Using Conditional UNet 
# 🎨 Polygon Colorization using UNet

This project implements a deep learning pipeline using a custom-conditioned **UNet architecture** to colorize polygon images based on a given color name. The model is trained on a custom dataset where each input polygon is paired with a target output image and a conditioning color.

---

## 📁 Dataset Structure

The dataset is organized as follows:

Each `data.json` file contains mappings like:
```json
{
  "input_polygon": "circle.png",
  "colour": "red",
  "output_image": "circle_red.png"
}




🧠 Model Architecture
We use a UNet model customized to condition on the desired color. Each input to the model is a concatenation of:

A 3-channel polygon image (grayscale image repeated across channels)

A 3-channel RGB color image filled with the target color

Thus, input to the model has 6 channels, and the model outputs a 3-channel predicted color image.

Architecture highlights:

Encoder-decoder structure with skip connections

Batch Normalization after each convolution

ReLU activation functions

Output passed through a Tanh (optional) or sigmoid for RGB normalization

⚙️ Training Configuration
Parameter	Value
Input Size	128×128
Optimizer	Adam
Learning Rate	1e-4
Loss Function	L1 Loss
Batch Size	16
Epochs	100
Augmentation	(Optional) Horizontal Flip, Rotation
Color Conditioning	RGB image filled with desired color

We use L1Loss because it tends to produce less blurry results compared to MSELoss for image generation tasks.
