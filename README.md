DINOv2 + SAM Image Matcher

This application combines Meta's Segment Anything Model (SAM) with Facebook Research's DINOv2 to enable interactive image segmentation and feature matching between images. Users can segment objects in one image and transfer those segmentations to similar objects in another image through a simple click-based interface.

Key Features
🖼️ Interactive image segmentation with SAM

🔍 Feature matching with DINOv2

↔️ Transfer segmentation masks between images

🎯 Click-based interface for precise control

📊 Visual connection lines showing feature correspondences

⚡ GPU acceleration support

Installation
Prerequisites
Python 3.10+

NVIDIA GPU with CUDA support (recommended)

SAM checkpoint

DINOv2 checkpoint

Step-by-Step Setup:

-> Install PyTorch with CUDA support (select the appropriate CUDA version):

    # Replace cu121 with your CUDA version:

    # CUDA 11.8 → cu118

    # CUDA 12.1 → cu121

    # CUDA 12.4 → cu124

    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126


-> Install other dependencies:

    pip install gradio Pillow numpy matplotlib opencv-python-headless scikit-learn segment-anything tqdm


-> Clone the DINOv2 repository:

    git clone https://github.com/facebookresearch/dinov2.git    


-> Download model checkpoints:

    wget https://dl.fbaipublicfiles.com/segment_anything/sam_vit_b_01ec64.pth
    wget https://dl.fbaipublicfiles.com/dinov2/dinov2_vitb14/dinov2_vitb14_pretrain.pth


-> Usage
    Run the application:

    python app.py
    Open your browser to http://127.0.0.1:7860

-> Use the interface:

    Upload two images in the respective panels

    Click twice on Image 1:

    First click: Object to segment (positive)

    Second click: Background area (negative)

    Click "Process Images" to see the segmentation transfer

    Use "Clear Clicks" to reset


-> How It Works:

    Image Segmentation (SAM):

        Segment Anything Model creates precise masks based on user clicks

        First click identifies the object, second click identifies background

    Feature Matching (DINOv2):

        DINOv2 extracts visual features from both images

        Feature vectors are compared to find correspondences

        Click positions are transferred based on feature similarity

    Segmentation Transfer:

        Transferred clicks guide SAM segmentation in the second image

        Results are visualized with masks and connection lines

