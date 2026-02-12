

<table>
<thead>
<tr>
<th style="text-align: left;">training data</th>
<th style="text-align: center;">COCO train</th>
<th style="text-align: center;">COCO trainval</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">test data</td>
<td style="text-align: center;">COCO val</td>
<td style="text-align: center;">COCO test-dev</td>
</tr>
<tr>
<td style="text-align: left;">mAP</td>
<td style="text-align: center;">@. 5</td>
<td style="text-align: center;">@[.5, .95]</td>
</tr>
<tr>
<td style="text-align: left;">baseline Faster R-CNN (VGG-16)</td>
<td style="text-align: center;">41.5</td>
<td style="text-align: center;">21.2</td>
</tr>
<tr>
<td style="text-align: left;">baseline Faster R-CNN (ResNet-101)</td>
<td style="text-align: center;">48.4</td>
<td style="text-align: center;">27.2</td>
</tr>
<tr>
<td style="text-align: left;">+box refinement</td>
<td style="text-align: center;">49.9</td>
<td style="text-align: center;">29.9</td>
</tr>
<tr>
<td style="text-align: left;">+context</td>
<td style="text-align: center;">51.1</td>
<td style="text-align: center;">30.0</td>
</tr>
<tr>
<td style="text-align: left;">+multi-scale testing</td>
<td style="text-align: center;">53.8</td>
<td style="text-align: center;">32.5</td>
</tr>
<tr>
<td style="text-align: left;">ensemble</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
</tr>
</tbody>
</table>

Table 9. Object detection improvements on MS COCO using Faster R-CNN and
ResNet-101.

<table style="width:100%;">
<colgroup>
<col style="width: 4%" />
<col style="width: 5%" />
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
<th style="text-align: left;">system</th>
<th style="text-align: center;">net</th>
<th style="text-align: right;">data</th>
<th style="text-align: right;">mAP</th>
<th style="text-align: right;">area</th>
<th style="text-align: right;">bike</th>
<th style="text-align: right;">bird</th>
<th style="text-align: right;">boat</th>
<th style="text-align: right;">bottle</th>
<th style="text-align: right;">bus</th>
<th style="text-align: right;">car</th>
<th style="text-align: right;">cat</th>
<th style="text-align: right;">chair</th>
<th style="text-align: right;">cow</th>
<th style="text-align: right;">table</th>
<th style="text-align: right;">dog</th>
<th style="text-align: right;">horse</th>
<th style="text-align: right;">mbike</th>
<th style="text-align: right;">person</th>
<th style="text-align: right;">plant</th>
<th style="text-align: right;">sheep</th>
<th style="text-align: right;">sofa</th>
<th style="text-align: right;">train</th>
<th style="text-align: right;">tv</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">baseline</td>
<td style="text-align: center;">VGG-16</td>
<td style="text-align: right;"><span
class="math inline">07 + 12</span></td>
<td style="text-align: right;">73.2</td>
<td style="text-align: right;">76.5</td>
<td style="text-align: right;">79.0</td>
<td style="text-align: right;">70.9</td>
<td style="text-align: right;">65.5</td>
<td style="text-align: right;">52.1</td>
<td style="text-align: right;">83.1</td>
<td style="text-align: right;">84.7</td>
<td style="text-align: right;">86.4</td>
<td style="text-align: right;">52.0</td>
<td style="text-align: right;">81.9</td>
<td style="text-align: right;">65.7</td>
<td style="text-align: right;">84.8</td>
<td style="text-align: right;">84.6</td>
<td style="text-align: right;">77.5</td>
<td style="text-align: right;">76.7</td>
<td style="text-align: right;">38.8</td>
<td style="text-align: right;">73.6</td>
<td style="text-align: right;">73.9</td>
<td style="text-align: right;">83.0</td>
<td style="text-align: right;">72.6</td>
</tr>
<tr>
<td style="text-align: left;">baseline</td>
<td style="text-align: center;">ResNet-101</td>
<td style="text-align: right;"><span
class="math inline">07 + 12</span></td>
<td style="text-align: right;">76.4</td>
<td style="text-align: right;">79.8</td>
<td style="text-align: right;">80.7</td>
<td style="text-align: right;">76.2</td>
<td style="text-align: right;">68.3</td>
<td style="text-align: right;">55.9</td>
<td style="text-align: right;">85.1</td>
<td style="text-align: right;">85.3</td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;">56.7</td>
<td style="text-align: right;">87.8</td>
<td style="text-align: right;">69.4</td>
<td style="text-align: right;">88.3</td>
<td style="text-align: right;">88.9</td>
<td style="text-align: right;">80.9</td>
<td style="text-align: right;">78.4</td>
<td style="text-align: right;">41.7</td>
<td style="text-align: right;">78.6</td>
<td style="text-align: right;">79.8</td>
<td style="text-align: right;">85.3</td>
<td style="text-align: right;">72.0</td>
</tr>
<tr>
<td style="text-align: left;">baseline+++</td>
<td style="text-align: center;">ResNet-101</td>
<td style="text-align: right;">COCO+07+12</td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>5</strong><strong>.</strong><strong>6</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>0</strong><strong>.</strong><strong>0</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>6</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>7</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>0</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>7</strong><strong>6</strong><strong>.</strong><strong>1</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;">89.6</td>
<td style="text-align: right;"><span
class="math inline"><strong>7</strong><strong>5</strong><strong>.</strong><strong>5</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>0</strong><strong>.</strong><strong>0</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>0</strong><strong>.</strong><strong>7</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>6</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>0</strong><strong>.</strong><strong>3</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>1</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>8</strong><strong>.</strong><strong>7</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>6</strong><strong>5</strong><strong>.</strong><strong>4</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>8</strong><strong>.</strong><strong>1</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>5</strong><strong>.</strong><strong>6</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>0</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>6</strong><strong>.</strong><strong>8</strong></span></td>
</tr>
</tbody>
</table>

Table 10. Detection results on the PASCAL VOC 2007 test set. The
baseline is the Faster R-CNN system. The system “baseline+++” include
box refinement, context, and multi-scale testing in Table 9.

<table style="width:100%;">
<colgroup>
<col style="width: 4%" />
<col style="width: 5%" />
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
<th style="text-align: left;">system</th>
<th style="text-align: center;">net</th>
<th style="text-align: right;">data</th>
<th style="text-align: right;">mAP</th>
<th style="text-align: right;">area</th>
<th style="text-align: right;">bike</th>
<th style="text-align: right;">bird</th>
<th style="text-align: right;">boat</th>
<th style="text-align: right;">bottle</th>
<th style="text-align: right;">bus</th>
<th style="text-align: right;">car</th>
<th style="text-align: right;">cat</th>
<th style="text-align: right;">chair</th>
<th style="text-align: right;">cow</th>
<th style="text-align: right;">table</th>
<th style="text-align: right;">dog</th>
<th style="text-align: right;">horse</th>
<th style="text-align: right;">mbike</th>
<th style="text-align: right;">person</th>
<th style="text-align: right;">plant</th>
<th style="text-align: right;">sheep</th>
<th style="text-align: right;">sofa</th>
<th style="text-align: right;">train</th>
<th style="text-align: right;">tv</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">baseline</td>
<td style="text-align: center;">VGG-16</td>
<td style="text-align: right;"><span
class="math inline">07 + +12</span></td>
<td style="text-align: right;">70.4</td>
<td style="text-align: right;">84.9</td>
<td style="text-align: right;">79.8</td>
<td style="text-align: right;">74.3</td>
<td style="text-align: right;">53.9</td>
<td style="text-align: right;">49.8</td>
<td style="text-align: right;">77.5</td>
<td style="text-align: right;">75.9</td>
<td style="text-align: right;">88.5</td>
<td style="text-align: right;">45.6</td>
<td style="text-align: right;">77.1</td>
<td style="text-align: right;">55.3</td>
<td style="text-align: right;">86.9</td>
<td style="text-align: right;">81.7</td>
<td style="text-align: right;">80.9</td>
<td style="text-align: right;">79.6</td>
<td style="text-align: right;">40.1</td>
<td style="text-align: right;">72.6</td>
<td style="text-align: right;">60.9</td>
<td style="text-align: right;">81.2</td>
<td style="text-align: right;">61.5</td>
</tr>
<tr>
<td style="text-align: left;">baseline</td>
<td style="text-align: center;">ResNet-101</td>
<td style="text-align: right;"><span
class="math inline">07 + +12</span></td>
<td style="text-align: right;">73.8</td>
<td style="text-align: right;">86.5</td>
<td style="text-align: right;">81.6</td>
<td style="text-align: right;">77.2</td>
<td style="text-align: right;">58.0</td>
<td style="text-align: right;">51.0</td>
<td style="text-align: right;">78.6</td>
<td style="text-align: right;">76.6</td>
<td style="text-align: right;">93.2</td>
<td style="text-align: right;">48.6</td>
<td style="text-align: right;">80.4</td>
<td style="text-align: right;">59.0</td>
<td style="text-align: right;">92.1</td>
<td style="text-align: right;">85.3</td>
<td style="text-align: right;">84.8</td>
<td style="text-align: right;">80.7</td>
<td style="text-align: right;">48.1</td>
<td style="text-align: right;">77.3</td>
<td style="text-align: right;">66.5</td>
<td style="text-align: right;">84.7</td>
<td style="text-align: right;">65.6</td>
</tr>
<tr>
<td style="text-align: left;">baseline+++</td>
<td style="text-align: center;">ResNet-101</td>
<td style="text-align: right;">COCO+07++12</td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>3</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>2</strong><strong>.</strong><strong>1</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>8</strong><strong>.</strong><strong>4</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>4</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>7</strong><strong>5</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>7</strong><strong>1</strong><strong>.</strong><strong>4</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>6</strong><strong>.</strong><strong>3</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>7</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>4</strong><strong>.</strong><strong>2</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>6</strong><strong>6</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>4</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>6</strong><strong>9</strong><strong>.</strong><strong>2</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>3</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>1</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>0</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>9</strong><strong>.</strong><strong>6</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>6</strong><strong>7</strong><strong>.</strong><strong>9</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>8</strong><strong>.</strong><strong>2</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>7</strong><strong>6</strong><strong>.</strong><strong>8</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>9</strong><strong>0</strong><strong>.</strong><strong>3</strong></span></td>
<td style="text-align: right;"><span
class="math inline"><strong>8</strong><strong>0</strong><strong>.</strong><strong>0</strong></span></td>
</tr>
</tbody>
</table>

Table 11. Detection results on the PASCAL VOC 2012 test set
(http://host.robots.ox.ac.uk:8080/leaderboard/
displaylb.php?challengeid=11&compid=4). The baseline is the Faster R-CNN
system. The system “baseline+++” include box refinement, context, and
multi-scale testing in Table 9.

We select two adjacent scales from the pyramid following \[33\]. RoI
pooling and subsequent layers are performed on the feature maps of these
two scales \[33\], which are merged by maxout as in \[33\]. Multi-scale
testing improves the mAP by over 2 points (Table 9).

Using validation data. Next we use the 80k + 40k trainval set for
training and the 20 k test-dev set for evaluation. The testdev set has
no publicly available ground truth and the result is reported by the
evaluation server. Under this setting, the results are an mAP@.5 of
55.7% and an mAP@\[.5, .95\] of 34.9% (Table 9). This is our
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
single model on the COCO dataset ( 55.7% mAP@.5 in Table 9), we
fine-tune this model on the PASCAL VOC sets. The improvements of box
refinement, context, and multi-scale testing are also adopted. By doing
so

<table>
<thead>
<tr>
<th style="text-align: left;"></th>
<th style="text-align: center;">val2</th>
<th style="text-align: center;">test</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">GoogLeNet [44] (ILSVRC’14)</td>
<td style="text-align: center;">-</td>
<td style="text-align: center;">43.9</td>
</tr>
<tr>
<td style="text-align: left;">our single model (ILSVRC’15)</td>
<td style="text-align: center;">60.5</td>
<td style="text-align: center;">58.8</td>
</tr>
<tr>
<td style="text-align: left;">our ensemble (ILSVRC’15)</td>
<td style="text-align: center;"><span
class="math inline"><strong>6</strong><strong>3</strong><strong>.</strong><strong>6</strong></span></td>
<td style="text-align: center;"><span
class="math inline"><strong>6</strong><strong>2</strong><strong>.</strong><strong>1</strong></span></td>
</tr>
</tbody>
</table>

Table 12. Our results (mAP, %) on the ImageNet detection dataset. Our
detection system is Faster R-CNN \[32\] with the improvements in Table
9, using ResNet-101. we achieve 85.6% mAP on PASCAL VOC 2007 (Table 10)
and 83.8% on PASCAL VOC 2012 (Table 11) <sup>6</sup>. The result on
PASCAL VOC 2012 is 10 points higher than the previous state-of-the-art
result \[6\].

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

\[^0\] \[^0\]: <sup>6</sup>
http://host.robots.ox.ac.uk:8080/anonymous/302402.html, submitted on
2015-11-26.
