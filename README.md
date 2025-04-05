# bluedetector
step 1: Input Acquisition
Capture or load the input RGB image from a camera or storage.

Step 2: Convert RGB to HSV Color Space
HSV (Hue, Saturation, Value) is more effective for color segmentation than RGB.

Formula (conceptually):

ini
Copy code
HSV_image = RGB_to_HSV(RGB_image)
Step 3: Define Blue Color Range in HSV
Set lower and upper thresholds for blue hue values. For example:

makefile
Copy code
Hue: 100-140 (approx for blue)
Saturation: 150-255
Value: 50-255
These ranges can be tuned depending on lighting conditions.

Step 4: Create a Binary Mask
Apply thresholding to segment blue regions:

ini
Copy code
mask = (Hue ∈ [100,140]) AND (Sat ≥ 150) AND (Val ≥ 50)
This produces a binary image where blue regions are white (1) and the rest are black (0).

Step 5: Noise Reduction
Apply morphological operations to reduce noise:

Erosion + Dilation (Opening) to remove small artifacts.

Dilation + Erosion (Closing) to fill small holes.

ini
Copy code
cleaned_mask = Morphological_Opening(mask)
Step 6: Object Detection
Label connected components or use contour detection to identify individual objects.

ini
Copy code
objects = Find_Contours(cleaned_mask)
Step 7: Filtering (Optional)
Filter objects by area, shape, or aspect ratio to discard false positives.

Step 8: Bounding and Output
Draw bounding boxes or mark the blue objects on the original image.

Output the result or coordinates of the blue object(s).
