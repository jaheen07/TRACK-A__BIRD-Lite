# TRACK A - BIRD Lite

### Dependencies
- pip install opencv-python numpy

### What approach I used and why:
- I used a rule-based classical cv approach with: (1) rotation correction, then (2) structure detection. I chose this approach because correcting tilt first using rules makes the code more efficient to detect accuract structure(lines/roofs/windows/doors).
- The dataset is developed programatically. It includes 32 mix samples of line-drawing style house images such as: clean, thick-line, thin-line, distorted-line, rotated, dotted-line and dashed-line images.

### My Assumptions: 
- Drawings are mostly black-on-light background, mostly one main building per image, trianglular/flat roofs are near top 35% of image, and windows/doors appear below the roof baseline.
- Angle estimated from Hough lines on binary edge map. Correction applied only when angle ≥ 2.0° threshold to avoid unnecessary warping.
- Morphological preprocessing + HoughLinesP + segment merging + duplicate suppression for clean geometric lines.

### What worked: 
- Full code ran on 32 images and can accuratly detect most of the house parts. A simple check gave: 19 roof detections (11 triangle, 8 flat), 169 windows (8 false positive), 40 doors (11 false positive).

### What did not fully work (failure case): 
- In some images, diagonal roof lines are not fully extended at corners (short at junctions). This happens when corner pixels break during thinning/Canny and strict duplicate suppression trims line endpoints. 

### One simple evaluation/check I used: 
- I manually evaluated the code with 5 hand-drawn house images containing windows,doors and roofs. And it can detect 90% of the parts accurately.

### Robustness:
- Code can handle rotation and detect thicker lines properly.

### What I would improve in future:
- With more time, I would improve junction handling using endpoint-aware line extension, evaluate performance using precision and recall on a labeled validation set, and enhance the model to handle noisy data.



## Tools Usage Disclouser:

- I used python-libraries: "OpenCV", "numpy", "dataclasses", "json", AI assistant: "Chatgpt (codex)".
- To develop the full code, I used the python and it's mentioned libraries. But I took help of Chatgpt for creating synthetic image data programmatically.
- Additionally I used Codex for fixing some bugs and to refining my code structure which gave better result later.
- My personal contribution in this work is developing logics, writing it's code and setting rules to detect the line segments and rectangular shapes. Then I validated the model outputs through iterative testing with hand-drawn image samples. 


