## Anchor Boxes estimation using KMeans Clusterring for Faster-RCNN

If you are not familiar with Faster-RCNN, Please go through [this blog](https://tryolabs.com/blog/2018/01/18/faster-r-cnn-down-the-rabbit-hole-of-modern-object-detection/).

When we train Faster RCNN for custom datasets, we often get confused over how to choose hyperparameters for the Network. Anchor boxes (one of the hyperparameters) are very important to detect objects with different scales and aspect ratios. We will get improved detection results if we get the anchors right.

The training & hypereparameters are in accordance with Tensorflow Object Detection [API](https://github.com/tensorflow/models/tree/master/research/object_detection).

### Faster-RCNN config file
```
faster_rcnn{
    # other hyperparameters
    first_stage_anchor_generator {
      grid_anchor_generator {
        height: 256
        width: 256
        height_stride: 16
        width_stride: 16
        scales: 0.9
        scales: 1.14
        scales: 1.53
        aspect_ratios: .8
        aspect_ratios: 1.15
        aspect_ratios: 2.77
      }
    }
    
}
```
#### height & width
This is the size of base anchor size. (i.e. for scale 1 and aspect ratio 1, base anchor is 256 x 256)