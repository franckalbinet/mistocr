

<table>
<thead>
<tr>
<th>training data</th>
<th>COCO train</th>
<th></th>
<th>COCO trainval</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td>test data</td>
<td>COCO val</td>
<td></td>
<td>COCO test-dev</td>
<td></td>
</tr>
<tr>
<td>mAP</td>
<td>@.5</td>
<td>@[.5, .95]</td>
<td>@.5</td>
<td>@[.5, .95]</td>
</tr>
<tr>
<td>baseline Faster R-CNN (VGG-16)</td>
<td>41.5</td>
<td>21.2</td>
<td></td>
<td></td>
</tr>
<tr>
<td>baseline Faster R-CNN (ResNet-101)</td>
<td>48.4</td>
<td>27.2</td>
<td></td>
<td></td>
</tr>
<tr>
<td>+box refinement</td>
<td>49.9</td>
<td>29.9</td>
<td></td>
<td></td>
</tr>
<tr>
<td>+context</td>
<td>51.1</td>
<td>30.0</td>
<td>53.3</td>
<td>32.2</td>
</tr>
<tr>
<td>+multi-scale testing</td>
<td>53.8</td>
<td>32.5</td>
<td>55.7</td>
<td>34.9</td>
</tr>
<tr>
<td>ensemble</td>
<td></td>
<td></td>
<td>59.0</td>
<td>37.4</td>
</tr>
</tbody>
</table>

Table 9. Object detection improvements on MS COCO using Faster R-CNN and
ResNet-101.

<table style="width:100%;">
<colgroup>
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
</colgroup>
<thead>
<tr>
<th>system</th>
<th>net</th>
<th>data</th>
<th>mAP</th>
<th>arco</th>
<th>bike</th>
<th>bird</th>
<th>boat</th>
<th>bottle</th>
<th>bus</th>
<th>car</th>
<th>cat</th>
<th>chair</th>
<th>cow</th>
<th>table</th>
<th>dog</th>
<th>horse</th>
<th>mbike</th>
<th>person</th>
<th>plant</th>
<th>sheep</th>
<th>sofa</th>
<th>train</th>
<th>tv</th>
</tr>
</thead>
<tbody>
<tr>
<td>baseline</td>
<td>VGG-16</td>
<td>07+12</td>
<td>73.2</td>
<td>76.5</td>
<td>79.0</td>
<td>70.9</td>
<td>65.5</td>
<td>52.1</td>
<td>83.1</td>
<td>84.7</td>
<td>86.4</td>
<td>52.0</td>
<td>81.9</td>
<td>65.7</td>
<td>84.8</td>
<td>84.6</td>
<td>77.5</td>
<td>76.7</td>
<td>38.8</td>
<td>73.6</td>
<td>73.9</td>
<td>83.0</td>
<td>72.6</td>
</tr>
<tr>
<td>baseline</td>
<td>ResNet-101</td>
<td>07+12</td>
<td>76.4</td>
<td>79.8</td>
<td>80.7</td>
<td>76.2</td>
<td>68.3</td>
<td>55.9</td>
<td>85.1</td>
<td>85.3</td>
<td>89.8</td>
<td>56.7</td>
<td>87.8</td>
<td>69.4</td>
<td>88.3</td>
<td>88.9</td>
<td>80.9</td>
<td>78.4</td>
<td>41.7</td>
<td>78.6</td>
<td>79.8</td>
<td>85.3</td>
<td>72.0</td>
</tr>
<tr>
<td>baseline+++</td>
<td>ResNet-101</td>
<td>COCO+07+12</td>
<td>85.6</td>
<td>90.0</td>
<td>89.6</td>
<td>87.8</td>
<td>80.8</td>
<td>76.1</td>
<td>89.9</td>
<td>89.9</td>
<td>89.6</td>
<td>75.5</td>
<td>90.0</td>
<td>80.7</td>
<td>89.6</td>
<td>90.3</td>
<td>89.1</td>
<td>88.7</td>
<td>65.4</td>
<td>88.1</td>
<td>85.6</td>
<td>89.0</td>
<td>86.8</td>
</tr>
</tbody>
</table>

Table 10. Detection results on the PASCAL VOC 2007 test set. The
baseline is the Faster R-CNN system. The system “baseline+++” include
box refinement, context, and multi-scale testing in Table 9.

<table style="width:100%;">
<colgroup>
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
<col style="width: 4%" />
</colgroup>
<thead>
<tr>
<th>system</th>
<th>net</th>
<th>data</th>
<th>mAP</th>
<th>arco</th>
<th>bike</th>
<th>bird</th>
<th>boat</th>
<th>bottle</th>
<th>bus</th>
<th>car</th>
<th>cat</th>
<th>chair</th>
<th>cow</th>
<th>table</th>
<th>dog</th>
<th>horse</th>
<th>mbike</th>
<th>person</th>
<th>plant</th>
<th>sheep</th>
<th>sofa</th>
<th>train</th>
<th>tv</th>
</tr>
</thead>
<tbody>
<tr>
<td>baseline</td>
<td>VGG-16</td>
<td>07++12</td>
<td>70.4</td>
<td>84.9</td>
<td>79.8</td>
<td>74.3</td>
<td>53.9</td>
<td>49.8</td>
<td>77.5</td>
<td>75.9</td>
<td>88.5</td>
<td>45.6</td>
<td>77.1</td>
<td>55.3</td>
<td>86.9</td>
<td>81.7</td>
<td>80.9</td>
<td>79.6</td>
<td>40.1</td>
<td>72.6</td>
<td>60.9</td>
<td>81.2</td>
<td>61.5</td>
</tr>
<tr>
<td>baseline</td>
<td>ResNet-101</td>
<td>07++12</td>
<td>73.8</td>
<td>86.5</td>
<td>81.6</td>
<td>77.2</td>
<td>58.0</td>
<td>51.0</td>
<td>78.6</td>
<td>76.6</td>
<td>93.2</td>
<td>48.6</td>
<td>80.4</td>
<td>59.0</td>
<td>92.1</td>
<td>85.3</td>
<td>84.8</td>
<td>80.7</td>
<td>48.1</td>
<td>77.3</td>
<td>66.5</td>
<td>84.7</td>
<td>65.6</td>
</tr>
<tr>
<td>baseline+++</td>
<td>ResNet-101</td>
<td>COCO+07++12</td>
<td>83.8</td>
<td>92.1</td>
<td>88.4</td>
<td>84.8</td>
<td>75.9</td>
<td>71.4</td>
<td>86.3</td>
<td>87.8</td>
<td>94.2</td>
<td>66.8</td>
<td>89.4</td>
<td>69.2</td>
<td>93.9</td>
<td>91.9</td>
<td>90.9</td>
<td>89.6</td>
<td>67.9</td>
<td>88.2</td>
<td>76.8</td>
<td>90.3</td>
<td>80.0</td>
</tr>
</tbody>
</table>

We select two adjacent scales from the pyramid following \[33\]. RoI
pooling and subsequent layers are performed on the feature maps of these
two scales \[33\], which are merged by maxout as in \[33\]. Multi-scale
testing improves the mAP by over 2 points (Table 9).

Using validation data. Next we use the 80k + 40k trainval set for
training and the 20k test-dev set for evaluation. The test-dev set has
no publicly available ground truth and the result is reported by the
evaluation server. Under this setting, the results are an mAP@.5 of
55.7% and an mAP@\[.5, .95\] of 34.9% (Table 9). This is our
single-model result.

Ensemble. In Faster R-CNN, the system is designed to learn region
proposals and also object classifiers, so an ensemble can be used to
boost both tasks. We use an ensemble for proposing regions, and the
union set of proposals are processed by an ensemble of per-region
classifiers. Table 9 shows our result based on an ensemble of 3
networks. The mAP is 59.0% and 37.4% on the test-dev set. This result
won the 1st place in the detection task in COCO 2015.

### PASCAL VOC … page 11

We revisit the PASCAL VOC dataset based on the above model. With the
single model on the COCO dataset (55.7% mAP@.5 in Table 9), we fine-tune
this model on the PASCAL VOC sets. The improvements of box refinement,
context, and multi-scale testing are also adopted. By doing so

Table 11. Detection results on the PASCAL VOC 2012 test set
(http://host.robots.ox.ac.uk:8080/leaderboard/displaylb.php?challengeid=11&compid=4).
The baseline is the Faster R-CNN system. The system “baseline+++”
include box refinement, context, and multi-scale testing in Table 9.

<table>
<thead>
<tr>
<th></th>
<th>val2</th>
<th>test</th>
</tr>
</thead>
<tbody>
<tr>
<td>GoogLeNet [44] (ILSVRC’14)</td>
<td>-</td>
<td>43.9</td>
</tr>
<tr>
<td>our single model (ILSVRC’15)</td>
<td>60.5</td>
<td>58.8</td>
</tr>
<tr>
<td>our ensemble (ILSVRC’15)</td>
<td>63.6</td>
<td>62.1</td>
</tr>
</tbody>
</table>

Table 12. Our results (mAP, %) on the ImageNet detection dataset. Our
detection system is Faster R-CNN \[32\] with the improvements in Table
9, using ResNet-101.

we achieve 85.6% mAP on PASCAL VOC 2007 (Table 10) and 83.8% on PASCAL
VOC 2012 (Table 11) <sup>6</sup> . The result on PASCAL VOC 2012 is 10
points higher than the previous state-of-the-art result \[6\].

### ImageNet Detection … page 11

The ImageNet Detection (DET) task involves 200 object categories. The
accuracy is evaluated by mAP@.5. Our object detection algorithm for
ImageNet DET is the same as that for MS COCO in Table 9. The networks
are pretrained on the 1000-class ImageNet classification set, and are
fine-tuned on the DET data. We split the validation set into two parts
(val1/val2) following \[8\]. We fine-tune the detection models using the
DET training set and the val1 set. The val2 set is used for validation.
We do not use other ILSVRC 2015 data. Our single model with ResNet-101
has
