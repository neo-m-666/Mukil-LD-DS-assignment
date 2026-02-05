# Mukil-LD-DS-assignment

The aim of this assignment is to carry out zero-shot product detection across various images using Meta’s SAM2 segmentation model.

For each product category in the CMU10_3D dataset:
The first image and its ground-truth mask are used for initialization.SAM 2 is then given the bounding box derived from the above mask.
The initialized object is then tracked and segmented in all the remaining images.The final bounding boxes are obtained from the prediction mask.

The pipeline starts by initializing SAM2’s video predictor, which treats the reference image and the target image as forming a “video composed of two frames.” The bounding box resulting from the first image is injected into frame zero, establishing identity. SAM2 then applies its internal object tracking and attention mechanisms to advance this object into the second frame and generate segmentation for this unseen image.

Two types of object detection performance are taken into account: intersection over union (IoU), which is calculated as the ratio of overlap area between predicted and ground truth bounding boxes and the union area between the predicted and ground truth bounding boxes, where the detection is considered successful if it is above 0.5.

While no product-wise logic or code is employed, it is possible to calculate mean IoU and accuracy over all the images, which are then aggregated with respect to the whole system performance.
