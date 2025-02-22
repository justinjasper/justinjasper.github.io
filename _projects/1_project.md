---
layout: page
title: Image Processing for Tumor Detection
description: Computer Vision (CV)-based image processing pipeline for CT and Ultrasound imaging of suspected cancerous growths.
img: assets/img/tumor_screenshot.png
importance: 1
category: Computer Vision
related_publications: true
---

I developed this project as part of my Stanford undergraduate coursework in Bioengineering 103: Systems Physiology and Design.

`PART 1:` For the first half of the project, I analyzed lung CT scans. CT scans are more likely to show lung abnormalities, including infections and tumors, than routine chest X-rays. This is partially due to the fact that we can use CT scans to create detailed 3D reconstructions of the lungs composed from multiple cross-sectional slices, allowing for comprehensive visualization.


I started by taking in a set of lung CT scans and applying K-means clustering from Scikit-learn to segment the images by tissue type:


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/original_lung_image.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gray_lung_image.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/kmeans_lung_image.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


Then, I utilized OpenCV image processing functions to further isolate the lung tissue in the image segmentation:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/clear_border_lungs.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/black_areas_lungs.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/white_areas_lungs.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Finally, I applied these image masks to all of the CT scans in the collection, and was able to make a 3D reconstruction of the lungs:



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Lung_image_napari.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    3D Lung Reconstruction from CT images using Napari.
</div>


`PART 2:` 




You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
