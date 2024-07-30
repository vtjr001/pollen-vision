# pollen-vision


### **1. Setting Up Pollen Vision**

#### **System Requirements**
- **Operating System**: Linux or macOS or Windows
- **Python Version**: Python 3.8 or higher
- **Dependencies**: Ensure you have CUDA installed if using a GPU for faster processing.

#### **Installation Steps**
1. **Clone the Repository**
   ```bash
   git clone https://github.com/pollen-robotics/pollen-vision.git
   cd pollen-vision
   ```

2. **Set Up a Virtual Environment (Optional but Recommended)**
   ```bash
   python3 -m venv pollen-venv
   source pollen-venv/bin/activate  # On Windows use `pollen-venv\Scripts\activate`
   ```

3. **Install Dependencies**
   ```bash
   pip install .[all]
   ```

4. **Additional Setup for GPU (Optional)**
   - Ensure you have the appropriate CUDA version installed for your GPU. Check the documentation for specific CUDA versions supported by the dependencies.

### **2. Using Pollen Vision**

Here's a basic example of how to use Pollen Vision for object detection and segmentation:

#### **Code Example**
```python
from pollen_vision.vision_models.object_detection import OwlVitWrapper
from pollen_vision.vision_models.object_segmentation import MobileSamWrapper
from pollen_vision.vision_models.utils import Annotator, get_bboxes

# Initialize models
owl = OwlVitWrapper()
sam = MobileSamWrapper()
annotator = Annotator()

# Load an image (replace with your image path or data)
im = ...  

# Object detection using text prompts
predictions = owl.infer(im, ["paper cups"])
bboxes = get_bboxes(predictions)

# Object segmentation based on bounding boxes
masks = sam.infer(im, bboxes=bboxes)
annotated_im = annotator.annotate(im, predictions, masks=masks)

# Display or save the annotated image
```

#### **Explanation**
- **`OwlVitWrapper`**: Detects objects using text prompts (zero-shot learning).
- **`MobileSamWrapper`**: Segments the detected objects.
- **`Annotator`**: Visualizes the results by adding bounding boxes and masks to the image.
- * **Execution and Visualization** * After running the code, the library will output an annotated image, highlighting the detected and segmented objects based on the given descriptions.

This setup provides a straightforward way to implement object detection and segmentation in robotic applications, utilizing the power of zero-shot models for versatile and adaptable AI solutions.
