## Open Curve Detection via Minimum Path Keypoints Detection ##

This partial implementation of a research paper focus on the tools and applications for open curve detection.<br\>
Given an input image of a simple or complex and unparametrized curve, we would like to automaticaaly derive a discrete parametrisation 
that fit the 2D curve. The applications are for example in medical image analysis where we would like to derive for example
the vessels or aortic valves.

### Fast-Marching and 2D distance map ###

First, we use the Fast-Marching Algorithm to create a distance map on the image. For example, starting from the following:\
![Teaser Image](/illustration_results/01-sample_curve.png)\
the Fast-Marching, derives automatically the potential map shown below:\
![Teaser Image](/illustration_results/03-final_fast_marching.png)\
The Fast-Marching algorithm might be implemented via two techniques:
- Djisktra (L1 norm neighborhood)
- Eikonal equation (L2 norm neighborhood)

### Automatic path specification ###

Using this algorithm, on a open curve:\
![Teaser Image](/illustration_results/04-other_sample_curve.png)\
We derive the chart distance:\
![Teaser Image](/illustration_results/05-final_fast_marching.png)\
And using back propagation to find the geodesic, we find a potential path on the image:\
![Teaser Image](/illustration_results/06-backpropagation_parametric_path.png)

### Complex curve ###

On more complex curves, this technique is not robust, see the following figures:\
![Teaser Image](/illustration_results/07-complex_curve.png)\
![Teaser Image](/illustration_results/08-failure_backpropag.png)

### Minimal Path Keypoint Detection ###

To avoid this, the authors introduce a method based on intermediary computation of keypoints
(kind of step by step geodesic), that will be more robust than the Fast-Marching applied directly.

![Teaser Image](/illustration_results/09-minimal_keypoint.png)\
![Teaser Image](/illustration_results/10-keypoint_detection.png)\

Using some conditions specifications on the distance between three following keypoints, we can even 
come up with a method where we don't need to specify starting and ending points. See the figures below:\
![Teaser Image](/illustration_results/11-check_distance.png)\
![Teaser Image](/illustration_results/12-open_curve_detection.png)\

The program proposed in the notebooks does not go as far as the research paper but the computations are
very  interesting anyway.
