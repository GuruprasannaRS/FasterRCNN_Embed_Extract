# FasterRCNN_Embed_Extract
This code helps to extract the embeddings of the Images using the Faster RCNN Model

- A normal RCNN takes an image as input and returns bounding boxes with category labels for objects in the bounding boxes. 
- Extracted embeddings for objects in the bounding boxes that could then be used to train a classifier on top. 
- These embeddings can be taken out from the network before the classification layers and after the RPN layers.
